# 🎧 Dockerized Spotify Client (`ncspot`)

This project shows how to run an **audio application (`ncspot`) inside Docker** — even though audio access from a container is tricky due to hardware and sound system permissions.

> ✅ You’ll learn how to use Docker with ALSA and optionally PulseAudio to stream audio from a container to your host machine.

---


## Clone this repo or create the folder:

mkdir spotify-ncspot && cd spotify-ncspot

## 📁 Project Structure

spotify-ncspot/
├── Dockerfile
└── README.md


## Build the Docker image:

docker build -t ncspot-container .

## Basic Run Command (ALSA Only)

```bash
docker run --rm -it \
  --device /dev/snd \
  ncspot-container
  ```

### 🔍 What this does:

- --rm: Remove container after exit.

- -it: Run interactively (required for terminal UI).

- --device /dev/snd: Give container access to your host's sound hardware.



## 💾  With File Persistence (Keeps Your ncspot Config)

- This mounts your ~/.config/ncspot directory so settings like login info are saved:

```bash
docker run --rm -it \
  --device /dev/snd \
  -v $HOME/.config/ncspot:/root/.config/ncspot \
  ncspot-container
```
## Remove the container image:

docker rmi ncspot-container

### Remove saved config:

rm -rf ~/.config/ncspot

