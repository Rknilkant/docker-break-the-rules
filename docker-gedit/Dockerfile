# Dockerfile to run Gedit in a container with GUI support

FROM ubuntu:22.04

RUN apt update && apt install -y gedit

ENV DISPLAY=:0

CMD ["gedit"]
