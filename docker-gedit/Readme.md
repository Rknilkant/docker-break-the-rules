# 🐳 Dockerized GUI App (Gedit)

This project demonstrates how to Dockerize a **GUI application (Gedit)** using Docker on Linux. It's a practical way to explore containerizing apps that typically **shouldn't be containerized**, and understand Docker limitations with graphical interfaces.

> ✅ This example uses **Gedit**, but the technique can be adapted for other graphical applications.

---

## 📦 What's Inside?

- A simple `Dockerfile` that installs Gedit on a minimal Ubuntu base.
- Instructions to run Gedit from a container with X11 display support.
- Volume mounting to **persist files** from inside the container to the host.

---

## 📁 Project Structure

```bash
.
├── Dockerfile
└── README.md
```
## 🛠️ How to Build the Docker Image

```bash

docker build -t gedit-docker .
```
##  🚀 How to Run the GUI App
### 🖥️ 1. Enable X11 Access

[Tip!] This allows Docker containers to use your host display.

```bash
xhost +local:docker
```
### 📝 2. Run Gedit (Ephemeral Session)

```bash
docker run -e DISPLAY=$DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  --rm gedit-docker
```
- 💾 3. Run Gedit with File Persistence
- mkdir -p ~/gedit-files

```bash
docker run -e DISPLAY=$DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  -v ~/gedit-files:/root/Documents \
  --rm gedit-docker
```

### 🧹 Cleanup

- To revoke X11 permissions:

```bash
xhost -local:docker
```


### 🧪 Why Do This?

- This is an experimental project to understand:

- Docker + GUI (X11) compatibility

- Container filesystem behavior

- Volumes and persistence

- What shouldn't be Dockerized and why

### 📌 Limitations


- Works only on Linux (uses X11).

- Won’t work on Windows/Mac without additional setup like XQuartz or VcXsrv.

- No sound or advanced hardware acceleration.
