# Run slack in a container with pulseaudio
#
# docker run --rm \
#	-v /etc/localtime:/etc/localtime:ro \
#	-v slack:/home/slack \
#	-v /dev/shm:/dev/shm \
#	-v /tmp/.X11-unix:/tmp/.X11-unix \
#	-v /run/user/$UID/pulse/native:/pulse \
#	-e XAUTHORITY=/tmp/Xauthority \
#	-e DISPLAY=unix$DISPLAY \
#   --name slack \
#   endophage/apps:slack
FROM ubuntu:latest

ENV HOME /home/slack
ENV PULSE_SERVER unix:/pulse

RUN apt-get update && apt-get install -y --no-install-recommends \
		apt-transport-https \
		ca-certificates \
		curl \
		gconf2 \
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
		pulseaudio \
		python \
		xdg-utils \
		xauth \
	&& echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen \
	&& locale-gen en_US.utf8 \
	&& /usr/sbin/update-locale LANG=en_US.UTF-8 \
	&& curl -sSL https://downloads.slack-edge.com/linux_releases/slack-desktop-2.0.5-amd64.deb > /tmp/slack-desktop.deb \
	&& dpkg -i /tmp/slack-desktop.deb \
	&& rm -rf /var/lib/apt/lists/* \
	&& adduser --disabled-login --home $HOME --gecos "" slack \
	&& adduser slack audio \
	&& chown -R slack:slack $HOME \
	&& rm -rf /var/lib/apt/lists/* 


ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8

WORKDIR $HOME
USER slack

ENTRYPOINT [ "slack" ]
