# About

This is the repository for building and maintaining the status website for the Finnish Quantum-Computing Infrastructure (FiQCI). It is based on uptime-kuma https://github.com/louislam/uptime-kuma

## 🔧 How to Install

### 🐳 Docker

```bash
docker run -d --restart=always -p 3001:3001 -v uptime-kuma:/app/data --name uptime-kuma modupefalodun/uptime-kuma
```

Uptime Kuma is now running on http://localhost:3001

> [!WARNING]
> File Systems like **NFS** (Network File System) are **NOT** supported. Please map to a local directory or volume.

### 💪🏻 Non-Docker

Requirements:

- Platform
  - ✅ Major Linux distros such as Debian, Ubuntu, CentOS, Fedora and ArchLinux etc.
  - ✅ Windows 10 (x64), Windows Server 2012 R2 (x64) or higher
  - ❌ Replit / Heroku
- [Node.js](https://nodejs.org/en/download/) 14 / 16 / 18 / 20.4
- [npm](https://docs.npmjs.com/cli/) 9
- [Git](https://git-scm.com/downloads)
- [pm2](https://pm2.keymetrics.io/) - For running Uptime Kuma in the background

```bash
# Update your npm
npm install npm@9 -g

git clone https://github.com/FiQCI/uptime-kuma
cd uptime-kuma
npm run setup

# Option 1. Try it
node server/server.js

# (Recommended) Option 2. Run in the background using PM2
# Install PM2 if you don't have it:
npm install pm2 -g && pm2 install pm2-logrotate

# Start Server
pm2 start server/server.js --name uptime-kuma
```

Uptime Kuma is now running on http://localhost:3001