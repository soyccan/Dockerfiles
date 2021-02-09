# executable listen on: 1111
# gdbserver  listen on: 2222

FROM ubuntu:18.04
# FROM ubuntu:16.04

RUN \
    sed -ir "s/archive.ubuntu.com/tw.archive.ubuntu.com/g" /etc/apt/sources.list && \
    sed -ir "s/security.ubuntu.com/tw.archive.ubuntu.com/g" /etc/apt/sources.list && \
    sed -ir "s/# deb/deb/g" /etc/apt/sources.list && \
    apt-get update && \
    apt-get install -y gdbserver socat libc6-dbg && \
    true

# debug mode
# Note: debugger cannot attach to spawned shell
CMD ["socat", "TCP-LISTEN:1111,fork,reuseaddr", "EXEC:gdbserver --no-disable-randomization \\:2222 ./a.out"]

WORKDIR /root
ADD . .
