FROM i386/alpine:3.6
MAINTAINER NowyQuei

# Var for first config
ENV SESSIONNAME="Ark Docker" \
    SERVERMAP="TheIsland" \
    SERVERPASSWORD="" \
    ADMINPASSWORD="adminpassword" \
    MAX_PLAYERS=70 \
    UPDATEONSTART=1 \
    BACKUPONSTART=1 \
    SERVERPORT=27015 \
    STEAMPORT=7778 \
    BACKUPONSTOP=1 \
    WARNONSTOP=1 \
    ARK_UID=1000 \
    ARK_GID=1000 \
    TZ=UTC

RUN apk --no-cache add libstdc++ git lsof bzip2 perl-compress-raw-zlib curl bash \
 && addgroup -g ${ARK_GID} steam \
 && adduser -s /bin/bash -G steam -D -u ${ARK_UID} steam \

RUN mkdir /home/steam/steamcmd \
 && cd /home/steam/steamcmd \
 && curl -L http://www.archlinux.org/packages/community/i686/busybox/download/ | tar xJ \
 && curl -L http://www.archlinux.org/packages/core/i686/glibc/download/ | tar xJ \
 && curl -L http://www.archlinux.org/packages/core/i686/tar/download/| tar xJ \
 && ln -sf /etc/resolv.conf etc/ \
 && mkdir bin \
 && ln -sf ../usr/bin/busybox bin/sh \
 && ln -sf ../usr/bin/busybox bin/ln \
 && curl -sqL "https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz" | tar zxvf -