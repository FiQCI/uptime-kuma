# About

This is the repository for building and maintaining the status website for the Finnish Quantum-Computing Infrastructure (FiQCI). It is based on uptime-kuma https://github.com/louislam/uptime-kuma

## Development & re-building Docker Image
* Clone the repository, checkout to a new branch and make changes

```bash
git clone https://github.com/FiQCI/uptime-kuma.git
cd uptime-kuma
git checkout <your-branch-name>
```
* use `npm run build-docker` to build a docker image (`npm run build-docker-fiqci-mac`) for mac users
* login to rahti registry on your terminal. Guide here : [rathi-registry] (https://registry-console.rahti.csc.fi/registry) and [csc-docs] (https://docs.csc.fi/cloud/rahti/images/creating/)
* push image to rahti registry
* commit changes

## 🔧 How to Install

### 🐳 Docker

```bash
docker run -d --restart=always -p 3001:3001 -v uptime-kuma:/app/data --name uptime-kuma docker-registry.rahti.csc.fi/fiqci-workspace/uptime-kuma:v1.0
```

### 🐳 Docker Compose

```bash
docker compose up -d
```

Uptime Kuma is now running on http://localhost:3001

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

# Option 1. Try it
node server/server.js

# (Recommended) Option 2. Run in the background using PM2
# Install PM2 if you don't have it:
npm install pm2 -g && pm2 install pm2-logrotate

# Start Server
pm2 start server/server.js --name uptime-kuma
```

Uptime Kuma is now running on http://localhost:3001
see https://github.com/FiQCI/uptime-kuma/blob/master/CONTRIBUTING.md for additional information on the stacks