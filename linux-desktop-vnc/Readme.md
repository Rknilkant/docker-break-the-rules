# 🖥️ Dockerized Linux Desktop (XFCE via VNC)

This project shows how to run a **full Linux XFCE desktop environment inside Docker**, accessible using a **VNC client like Remmina**.

> 🧪 This is an experiment in containerizing what really should be virtualized — and in the process, you'll learn how to run graphical multi-process systems inside Docker!

---

## 📁 Project Structure

```bash
linux-desktop-vnc/
├── Dockerfile
└── README.md
```

## 🛠️ Dockerfile Overview

-  This image includes:

-- XFCE desktop environment

-- TightVNC server

-- User docker with password docker

-- VNC listening on port 5901

## 🔧 Setup

### Clone or Create Project Folder

```
mkdir linux-desktop-vnc && cd linux-desktop-vnc
```

## 🧱 Build the Image

```
docker build -t xfce-docker .
```

### 🚀 Run the Container

```
docker run -it -p 5901:5901 --name xfce-remote-desktop xfce-docker
```

## 🔌 Connect via VNC (Using Remmina)

#### Open Remmina

```
remmina
```

#### Create a New VNC Connection

| Field    | Value            |
| -------- | ---------------- |
| Protocol | VNC              |
| Server   | `localhost:5901` |
| Password | `docker`         |
| Username | *(leave blank)*  |
| Name     | `Docker XFCE`    |
 
-------------------------------

#### Click "Connect"

A Ubuntu vm Should be Opened!!

## 🧹 Cleanup

```
docker ps
docker stop <container_id>

```
Remove the image:

docker rmi xfce-docker
