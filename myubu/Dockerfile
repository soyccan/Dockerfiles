FROM ubuntu:18.04
ENV exeport 1111
ENV gdbport 2222

RUN sed -i 's/archive\.ubuntu/tw\.archive\.ubuntu/' /etc/apt/sources.list && \
        apt-get update && \
        apt-get install -y gdbserver socat

WORKDIR /root
ADD . .
EXPOSE $gdbport $exeport

# debug mode
# Note: debugger cannot attach to spawned shell
# CMD ["socat", "TCP-LISTEN:1111,fork,reuseaddr", "EXEC:gdbserver \\:2222 ./a.out"]

CMD ["socat", "TCP-LISTEN:1111,fork,reuseaddr", "EXEC:./a.out"]

