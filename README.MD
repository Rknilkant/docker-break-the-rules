docker-break-the-rules/
├── gedit-x11/              # Level 1: GUI App (Gedit)
│   ├── Dockerfile
│   └── README.md
│
├── spotify-ncspot/         # Level 2: Audio App (ncspot)
│   ├── Dockerfile
│   └── README.md
│
├── linux-desktop-vnc/      # Level 3: Full Linux Desktop (XFCE + VNC)
│   ├── Dockerfile
│   └── README.md
│
├── fake-systemd/           # Level 4: Systemd inside Docker
│   ├── Dockerfile
│   └── README.md
│
└── README.md               # Master README (explains all levels)

|--------------------------------------------------||-------------------------------------------------- |

# 🐳 Docker Break the Rules

This repo is a multi-level challenge to containerize the things you're *not supposed to* containerize — GUI apps, audio, full desktops, even systemd!

---

## 🧪 Levels

| Level | Project              | What It Teaches                                    |
|-------|----------------------|----------------------------------------------------|
| 1     | Gedit GUI App        | X11 display, desktop integration                   |
| 2     | Spotify (ncspot)     | Audio passthrough (ALSA, PulseAudio)               |
| 3     | Linux Desktop (VNC)  | XFCE + VNC server in Docker                        |
| 4     | Systemd in Docker    | Init systems, cgroups, privileged mode             |

---

## 📂 Subprojects

### [`gedit-x11`](./gedit-x11)
Run graphical Gedit from a container using X11 socket sharing.

### [`spotify-ncspot`](./spotify-ncspot)
Run a terminal-based Spotify client with ALSA/PulseAudio from Docker.

### [`linux-desktop-vnc`](./linux-desktop-vnc)
Run a full XFCE Linux desktop inside Docker and access via VNC.

### [`fake-systemd`](./fake-systemd)
Use Docker to run a full systemd init system — with cgroups and services.

---

> 🤓 These projects push Docker beyond its intended use, to teach OS-level isolation, GUI bridging, device permissions, and system design.

---

## ⚠️ Disclaimer

These are **educational experiments** and should not be used in production environments.

