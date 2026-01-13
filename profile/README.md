# 🎮 retrogamehub.online

> English | [中文](https://github.com/retrogamehub/.github/blob/main/profile/README.zh-CN.md)

**retrogamehub.online** is a self-hosted **online retro game management solution**, designed to help you organize, browse, and serve your retro game collection easily via the web.

Perfect for home servers, NAS devices, and retro gaming enthusiasts.

---

## ✨ Features

- 📚 Centralized management of retro game ROMs & media
- 🌐 Web-based access
- 🐳 Easy deployment with Docker
- 🔒 Read-only resource mounting for safety
- 💾 NAS-friendly (Synology / Unraid / TrueNAS)

---

## 🚀 Quick Start (Docker Compose)

### 1️⃣ Prepare Resources

Create the following directory structure on your host machine:

```
retrogamehub/
├── api
├── media
└── roms
```

You can download a prepared resource package here:

- **Baidu Pan**: https://pan.baidu.com/s/10GCDErhvNxaFx-a5j0mXUQ
- **Password**: `gnig`

---

### 2️⃣ Docker Compose Configuration

Create a `docker-compose.yml` file:

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
    logging:
      driver: json-file
      options:
        max-size: "10m"
        max-file: "3"
```

> ⚠️ **Important**
>
> - The mounted directory must contain `api`, `media`, and `roms`
> - The volume is mounted as **read-only (`:ro`)** to avoid accidental modification

---

### 3️⃣ Start the Service

```bash
docker compose up -d
```

Then open your browser:

```
http://localhost:38283
```

---

## 🗂 Directory Mapping

| Host Path     | Container Path | Description             |
| ------------- | -------------- | ----------------------- |
| retrogamehub/ | /app/res       | Root resource directory |
| api/          | /app/res/api   | API & metadata          |
| media/        | /app/res/media | Covers & assets         |
| roms/         | /app/res/roms  | Game ROMs               |

---

## 🛠 Environment Variables

| Name     | Default    | Description         |
| -------- | ---------- | ------------------- |
| NODE_ENV | production | Runtime environment |

---

## 📦 Image Info

- Image: `liuuyuunloong/retrogamehub`
- Tag: `latest`
- Platform: `linux/amd64`

---

## 📄 License

TBD

---

## 🙌 Acknowledgements

Built for retro gaming lovers who want simple deployment and clean management of their collections.
