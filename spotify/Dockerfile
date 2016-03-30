# Run spotify in a container with pulseaudio
#
# docker run --rm \
#	-v /etc/localtime:/etc/localtime:ro \
#	-v $HOME/.spotify:/home/spotify \
#	-v /tmp/.X11-unix:/tmp/.X11-unix \
#	-v /run/user/$UID/pulse/native:/pulse \
#	-e DISPLAY=unix$DISPLAY \
#   --name spotify \
#   endophage/apps:spotify
FROM ubuntu:latest

ENV HOME /home/spotify
ENV PULSE_SERVER unix:/pulse

RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys BBEBDCB318AD50EC6865090613B00F1FD2C19886 \
	&& echo deb http://repository.spotify.com stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list \
	&& apt-get update \
	&& apt-get install -y --no-install-recommends \
		libcanberra-gtk-module \
		libgl1-mesa-glx \
		libpangoxft-1.0-0 \
		libxss1 \
		pulseaudio \
		software-properties-common \
		xdg-utils \
	&& apt-get install -y --force-yes \
		spotify-client \
	&& rm -rf /var/lib/apt/lists/* \
	&& adduser --disabled-login --home $HOME --gecos "" spotify \
	&& adduser spotify audio \
	&& chown -R spotify:spotify $HOME

WORKDIR $HOME
USER spotify

CMD [ "spotify" ]
