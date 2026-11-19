FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive
ENV PYTHONUNBUFFERED=1

RUN apt-get update -qq && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    git \
    tar \
    xz-utils \
    unzip \
    aria2 \
    fontconfig \
    fonts-dejavu-core \
    fonts-noto-core \
    python3 \
    python3-pip \
    python3-cryptography \
    python3-libtorrent \
    python3-requests \
    && curl -sL --connect-timeout 15 --max-time 180 https://github.com/yt-dlp/FFmpeg-Builds/releases/download/latest/ffmpeg-master-latest-linux64-gpl.tar.xz \
       | tar -xJ --strip-components=2 -C /usr/local/bin/ --wildcards "*/bin/ffmpeg" "*/bin/ffprobe" \
    && chmod +x /usr/local/bin/ffmpeg /usr/local/bin/ffprobe \
    && curl -sL --connect-timeout 15 --max-time 90 https://github.com/YouROK/TorrServer/releases/download/MatriX.148/TorrServer-linux-amd64 -o /usr/local/bin/torrserver \
    && chmod +x /usr/local/bin/torrserver \
    && pip3 install --no-cache-dir --break-system-packages pyrogram tgcrypto edge-tts \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR /github/workspace
