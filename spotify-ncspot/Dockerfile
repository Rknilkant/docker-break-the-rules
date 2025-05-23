FROM rust:slim

RUN apt update && apt install -y \
  libasound2 \
  libncurses-dev \
  libpulse-dev \
  pkg-config \
  libssl-dev \
  curl \
  build-essential

RUN cargo install ncspot

CMD ["ncspot"]
