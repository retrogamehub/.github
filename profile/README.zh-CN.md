# 🎮 retrogamehub.online

**retrogamehub.online** 是一个可自托管的 **在线复古游戏管理解决方案**，用于统一管理、浏览并通过 Web 访问你的复古游戏资源。

非常适合家庭服务器、NAS 以及复古游戏爱好者使用。

---

## ✨ 功能特性

- 📚 统一管理复古游戏 ROM 与媒体资源
- 🌐 基于 Web 的访问方式
- 🐳 使用 Docker 快速部署
- 🔒 资源只读挂载，避免误操作
- 💾 对 NAS 设备友好（群晖 / Unraid / TrueNAS）

---

## 🚀 快速开始（Docker Compose）

### 1️⃣ 准备资源目录

```
retrogamehub/
├── api
├── media
└── roms
```

资源包下载：

- 百度网盘：https://pan.baidu.com/s/10GCDErhvNxaFx-a5j0mXUQ  
- 提取码：`gnig`

---

### 2️⃣ docker-compose.yml 配置

```yaml
services:
  retrogamehub:
    image: liuuyuunloong/retrogamehub:latest
    container_name: retrogamehub
    restart: unless-stopped
    ports:
      - "38283:80"
    volumes:
      - /volume1/Media/Game/retrogamehub:/app/res:ro
    environment:
      - NODE_ENV=production
```

---

### 3️⃣ 启动服务

```bash
docker compose up -d
```

浏览器访问：

``
http://localhost:38283
``

