# 🧪 Dockerized Systemd (Level 4)

This project demonstrates how to run a **full Linux init system (`systemd`) inside a Docker container** — something Docker isn't meant to support, but we’ll make it work using a few advanced tricks.

> ⚠️ WARNING: This uses `--privileged` and breaks container isolation — this is **for learning and experimentation**, not production!

---

## 📁 Project Structure

```bash
fake-systemd/
├── Dockerfile
└── README.md
```
## 🧱 Build the Image

```
docker build -t systemd-docker .

```

## 🚀 Run the Container

```
docker run --rm -it \
  --name systemd-sandbox \
  --privileged \
  --cgroupns=host \
  --tmpfs /run \
  --tmpfs /run/lock \
  -v /sys/fs/cgroup:/sys/fs/cgroup \
  systemd-docker

```

## ✅ Validate systemd is running

```
ps -e | grep systemd
systemctl list-units

```

## 🧹 Cleanup

### Stop and remove persistent container
- docker stop systemd-sandbox
- docker rm systemd-sandbox

### Remove the image
- docker rmi systemd-docker
