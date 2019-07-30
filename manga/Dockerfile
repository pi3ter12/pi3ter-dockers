FROM ubuntu:14.04

#docker build -t manga .
#docker run -ti -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix manga

RUN apt-get update && apt-get install -y wget dpkg libgtk-3-0
#RUN wget -O manga.deb https://downloads.sourceforge.net/project/hakuneko/0.3.1/hakuneko-desktop_0.3.1_linux_i386.deb
RUN wget -O manga.deb https://downloads.sourceforge.net/project/hakuneko/0.4.0/hakuneko-desktop_0.4.0_linux_amd64.deb
RUN dpkg -i manga.deb
RUN apt install -y gconf-service libasound2 libatk1.0-0 libc6 libcairo2 libcups2 libdbus-1-3 libexpat1 libfontconfig1 libgcc1 libgconf-2-4 libgdk-pixbuf2.0-0 libglib2.0-0 libgtk-3-0 libnspr4 libpango-1.0-0 libpangocairo-1.0-0 libstdc++6 libx11-6 libx11-xcb1 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxext6 libxfixes3 libxi6 libxrandr2 libxrender1 libxss1 libxtst6 ca-certificates fonts-liberation libappindicator1 libnss3 lsb-release xdg-utils wget
RUN apt install -y libcanberra-gtk-module libcanberra-gtk3-module


# Replace 1000 with your user / group id
RUN export uid=1000 gid=1000 && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown ${uid}:${gid} -R /home/developer

USER developer
ENV HOME /home/developer
#CMD /usr/bin/hakuneko

#ENTRYPOINT	[ "/bin/sh" ]
ENTRYPOINT	[ "hakuneko-desktop" ]