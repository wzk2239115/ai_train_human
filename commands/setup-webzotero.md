---
description: 快速使用 Docker 部署 WebZotero
argument-hint: 无需参数
allowed-tools: [Bash, Write]
model: sonnet
---

# /setup-webzotero

快速使用 Docker 在 Linux 服务器上部署 WebZotero，通过浏览器访问和管理 Zotero 文献库。

## 使用方法

```
/setup-webzotero
```

直接运行命令即可，会引导你完成配置。

## 什么是 WebZotero

WebZotero 是一个开源的 Zotero Web 界面，让你能够：
- 🌐 通过浏览器访问 Zotero 文献库
- 📚 在线阅读和管理 PDF
- 🔍 搜索和筛选文献
- 📝 添加和编辑笔记
- 🔄 多设备同步访问

## 为什么选择 Docker

- ✅ 快速部署，5分钟搞定
- ✅ 环境隔离，不污染系统
- ✅ 易于更新和维护
- ✅ 开箱即用

## 这个命令的作用

1. **检查系统环境** - Docker 和 Docker Compose 版本检查
2. **创建服务目录** - 在 `webzotero/` 目录中创建所有文件（已添加到 .gitignore）
3. **生成配置文件** - 生成 docker-compose.yml 和相关配置
4. **启动服务** - 自动拉取镜像并启动 WebZotero 容器
5. **验证运行** - 检查服务状态并显示访问地址
6. **配置防火墙** - 自动配置防火墙规则（可选）

**运行完成后服务立即可用，无需手动操作！**

## 目录约定

所有 WebZotero 相关文件都存放在 `webzotero/` 目录中（已添加到 .gitignore）：

```
webzotero/              # 服务根目录
├── docker-compose.yml  # Docker Compose 配置
├── data/              # Zotero 数据目录
│   ├── zotero.sqlite  # Zotero 数据库
│   └── storage/       # PDF 附件
├── nginx/             # Nginx 配置
│   └── webzotero.conf
├── backup/            # 备份脚本
│   └── backup.sh
└── README.md          # 使用说明
```

这样设计的好处：
- ✅ 所有文件集中管理，不污染项目根目录
- ✅ 已添加到 .gitignore，个人数据不会被提交
- ✅ 易于备份和迁移
- ✅ 可以轻松删除整个目录清理环境

## 系统要求

### 最低配置
- CPU: 2 核
- 内存: 2GB
- 磁盘: 20GB（取决于文献库大小）
- 系统: Ubuntu 20.04+, Debian 11+, CentOS 8+

### 推荐配置
- CPU: 4 核
- 内存: 4GB
- 磁盘: 50GB+ SSD

## 自动化部署流程

命令会自动执行以下步骤：

### 1. 环境检查

检查 Docker 和 Docker Compose 是否已安装：

```bash
docker --version
docker compose version
```

### 2. 创建目录结构

```bash
webzotero/
├── docker-compose.yml
├── backup/
│   └── backup.sh
├── data/              # 启动后自动生成
├── nginx/
│   └── webzotero.conf
└── README.md
```

### 3. 生成配置文件

**docker-compose.yml**

```yaml
version: '3.8'
services:
  webzotero:
    image: zotero/webzotero:latest
    container_name: webzotero
    ports:
      - "8080:80"
    volumes:
      - ./data:/data
    environment:
      - ZOTERO_DATA_DIR=/data
      - TZ=Asia/Shanghai
    restart: unless-stopped
```

### 4. 启动服务

自动执行：

```bash
cd webzotero
docker compose pull    # 拉取最新镜像
docker compose up -d   # 后台启动服务
```

### 5. 验证服务

检查容器运行状态：

```bash
docker compose ps
docker compose logs --tail=20 webzotero
```

### 6. 配置防火墙

自动开放端口：

```bash
# Ubuntu/Debian
sudo ufw allow 8080/tcp

# CentOS/RHEL
sudo firewall-cmd --permanent --add-port=8080/tcp
sudo firewall-cmd --reload
```

## 访问服务

服务启动后可以直接访问：

### 本地访问

```
http://localhost:8080
```

### 远程访问

```
http://YOUR_SERVER_IP:8080
```

**提示：** 防火墙规则已自动配置，端口 8080 已开放。

## 配置域名（可选）

如果你有域名，可以配置 Nginx 反向代理：

已在 `webzotero/nginx/webzotero.conf` 生成配置模板，包含以下内容：

```nginx
server {
    listen 80;
    server_name your-domain.com;

    location / {
        proxy_pass http://localhost:8080;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

启用配置：

```bash
sudo ln -s $(pwd)/webzotero/nginx/webzotero.conf /etc/nginx/sites-available/webzotero
sudo ln -s /etc/nginx/sites-available/webzotero /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx
```

## 安全建议

1. **使用反向代理** - 配置 SSL/TLS 加密
2. **设置访问控制** - 使用 Basic Auth 或 OAuth
3. **定期备份** - 备份 Zotero 数据目录
4. **更新镜像** - 定期更新 Docker 镜像
5. **监控日志** - 监控访问日志和异常

### 配置基础认证（可选）

```bash
# 安装 htpasswd 工具
sudo apt-get install apache2-utils

# 创建密码文件
sudo htpasswd -c /etc/nginx/.htpasswd admin
```

在 Nginx 配置中添加：

```nginx
auth_basic "Restricted Access";
auth_basic_user_file /etc/nginx/.htpasswd;
```

## 日常管理

所有命令都需要在 `webzotero/` 目录中执行：

### 查看容器状态

```bash
cd webzotero
docker compose ps
```

### 查看日志

```bash
cd webzotero
docker compose logs -f webzotero
```

### 重启服务

```bash
cd webzotero
docker compose restart
```

### 停止服务

```bash
cd webzotero
docker compose down
```

### 更新镜像

```bash
cd webzotero
docker compose pull
docker compose up -d
```

### 手动备份

```bash
cd webzotero
./backup/backup.sh
```

## 数据管理

### 数据目录结构

```
webzotero/data/
├── zotero.sqlite          # Zotero 数据库
├── storage/               # PDF 附件
└── styles/                # 引用样式
```

### 备份策略

在 `webzotero/backup/` 目录中创建 `backup.sh`：

```bash
#!/bin/bash
# 备份脚本
BACKUP_DIR="./backup"
DATA_DIR="./data"
DATE=$(date +%Y%m%d_%H%M%S)

mkdir -p $BACKUP_DIR
tar -czf $BACKUP_DIR/webzotero_$DATE.tar.gz $DATA_DIR

# 保留最近 7 天的备份
find $BACKUP_DIR -name "webzotero_*.tar.gz" -mtime +7 -delete
```

设置权限并添加到 crontab：

```bash
chmod +x webzotero/backup/backup.sh

# 添加每日备份任务（凌晨 2 点）
crontab -e
# 添加：0 2 * * * cd /path/to/project/webzotero && ./backup/backup.sh
```

### 恢复数据

```bash
# 停止容器
cd webzotero
docker-compose down

# 解压备份
tar -xzf backup/webzotero_20240122_120000.tar.gz -C .

# 启动容器
docker-compose up -d
```

## 故障排查

### 容器无法启动

```bash
# 查看详细日志
docker logs webzotero

# 检查端口占用
sudo netstat -tlnp | grep 8080

# 检查磁盘空间
df -h
```

### 无法访问 Web 界面

1. 检查防火墙设置
2. 检查容器状态：`docker ps`
3. 检查端口映射：`docker port webzotero`

### 数据丢失

1. 检查数据目录权限
2. 恢复最近的备份
3. 检查磁盘空间

## 清理环境

如果需要完全删除 WebZotero：

```bash
cd webzotero
docker-compose down
cd ..
rm -rf webzotero
```

所有文件都在 `webzotero/` 目录中，清理非常方便！

## 进阶配置

### 配置 SSL 证书（Let's Encrypt）

```bash
# 安装 certbot
sudo apt-get install certbot python3-certbot-nginx

# 获取证书
sudo certbot --nginx -d your-domain.com

# 自动续期
sudo certbot renew --dry-run
```

### 配置监控（Prometheus + Grafana）

在 `docker-compose.yml` 中添加 labels：

```yaml
services:
  webzotero:
    # ... existing config
    labels:
      - "prometheus.io/scrape=true"
      - "prometheus.io/port=8080"
```

## 工作流程

1. **检查系统** - 验证 Docker 和 Docker Compose
2. **创建目录** - 在 `webzotero/` 创建完整目录结构
3. **生成配置** - 生成所有配置文件
4. **拉取镜像** - 下载 WebZotero Docker 镜像
5. **启动服务** - 启动容器并验证运行状态
6. **配置防火墙** - 自动开放必要端口
7. **显示信息** - 输出访问地址和管理命令

## 输出示例

```
✅ WebZotero 环境已准备完成!

已创建的文件结构

webzotero/
├── README.md                  # 完整使用说明
├── docker-compose.yml         # Docker Compose 配置
├── backup/
│   └── backup.sh             # 自动备份脚本（可执行）
├── data/                     # Zotero 数据目录（启动后生成）
└── nginx/
    └── webzotero.conf        # Nginx 反向代理配置

🚀 服务已启动

容器状态: running
容器名称: webzotero
访问地址: http://localhost:8080

📝 常用命令

cd webzotero

# 查看状态
docker compose ps

# 查看日志
docker compose logs -f

# 重启服务
docker compose restart

# 停止服务
docker compose down

# 手动备份
./backup/backup.sh

🔧 后续配置

- 配置域名: 参考 webzotero/nginx/webzotero.conf
- SSL 证书: 使用 certbot --nginx -d your-domain.com
- 自动备份: crontab -e 添加: 0 2 * * * cd .../webzotero && ./backup/backup.sh

所有文件都已添加到 .gitignore，个人数据不会被提交。
```

## 一键启动

整个过程无需用户干预，完成后服务立即可用！

```bash
/setup-webzotero
```

就这么简单！服务启动后可以立即访问 http://localhost:8080

## 相关资源

- **Zotero 官方**: https://www.zotero.org/
- **Docker Hub**: https://hub.docker.com/r/zotero/webzotero
- **社区论坛**: https://forums.zotero.org/

## 与 Zotero 同步配合

WebZotero 可以作为 Zotero 官方同步的补充：

1. **官方同步** - 用于多设备数据同步
2. **WebZotero** - 用于 Web 访问和管理
3. **WebDAV** - 用于附件存储

推荐配置：
- 使用 Zotero 官方同步元数据
- 使用 WebDAV 存储附件
- 使用 WebZotero 提供 Web 界面

## 常见问题

**Q: WebZotero 是官方产品吗？**
A: WebZotero 是社区开发的开源项目，不是 Zotero 官方产品。

**Q: 能替代官方 Web 库吗？**
A: 不能。官方 Web 库（zotero.org）提供的是在线查看功能，WebZotero 提供的是自托管的完整界面。

**Q: 性能如何？**
A: 对于个人和小团队使用完全足够，大型机构建议使用官方 Zotero 服务或经过优化的部署方案。

**Q: 支持多人协作吗？**
A: 支持，但需要配置适当的访问控制和权限管理。
