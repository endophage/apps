# Run atom in a container 
#
# docker run --rm \
#	-v /etc/localtime:/etc/localtime:ro \
#	-v atom:/home/atom \
#	-v /dev/shm:/dev/shm \
#	-v /tmp/.X11-unix:/tmp/.X11-unix \
#	-e XAUTHORITY=/tmp/Xauthority \
#	-e DISPLAY=unix$DISPLAY \
#   --name atom \
#   endophage/apps:atom-ubuntu
FROM ubuntu:16.04

ENV HOME /home/atom

RUN apt-get update && apt-get install -y --no-install-recommends \
		apt-transport-https \
		ca-certificates \
		curl \
		gconf2 \
		git \
		gconf-service \
		gvfs-bin \
		hunspell-en-us \
		libcanberra-gtk-module \
		libgcrypt20 \
		libgl1-mesa-dev \
		libgl1-mesa-dri-lts-wily \
		libgnome-keyring0 \
		libgtk2.0-0 \
		libnotify4 \
		libnss3 \
		libudev1 \
		libxss1 \
		libxtst6 \
		libxtst6 \
		locales \
		python \
		xdg-utils \
		xauth \
	&& echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen \
	&& locale-gen en_US.utf8 \
	&& /usr/sbin/update-locale LANG=en_US.UTF-8 \
	&& curl -sSL https://atom.io/download/deb > /tmp/atom.deb \
	&& dpkg -i /tmp/atom.deb \
	&& adduser --disabled-login --home $HOME --gecos "" atom \
	&& chown -R atom:atom $HOME \
	&& rm -rf /var/lib/apt/lists/* \
	&& rm /tmp/atom.deb \
	&& apt-get remove --purge -y \
	    curl \
		libgl1-mesa-dev 

ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8

WORKDIR $HOME
USER atom

ENTRYPOINT [ "atom" ]
