# Run retroarch in a container
#
# docker build -t retroarch .
# docker run -ti -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix --name retroarch retroarch
#

FROM ubuntu:14.04

RUN apt-get update && apt-get install -y software-properties-common
RUN add-apt-repository ppa:libretro/stable && apt-get update && apt-get install retroarch* -y

# Replace 1000 with your user / group id
RUN export uid=1000 gid=1000 && \
    mkdir -p /home/retroarch && \
    echo "retroarch:x:${uid}:${gid}:retroarch,,,:/home/retroarch:/bin/bash" >> /etc/passwd && \
    echo "retroarch:x:${uid}:" >> /etc/group && \
    echo "retroarch ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/retroarch && \
    chmod 0440 /etc/sudoers.d/retroarch && \
    chown ${uid}:${gid} -R /home/retroarch

USER retroarch
ENV HOME /home/retroarch

ENTRYPOINT	[ "/usr/bin/retroarch" ]