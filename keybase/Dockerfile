# docker run -it --rm -v keybase:/home/keybase endophage/apps:keybase
FROM ubuntu:16.04

ENV HOME /home/keybase

RUN apt-get update && apt-get install -y --no-install-recommends \ 
		apt-transport-https \
		ca-certificates \
		curl \
	&& curl -O https://dist.keybase.io/linux/deb/keybase-latest-amd64.deb \
	&& dpkg -i keybase-latest-amd64.deb \
	&& adduser --disabled-login --home $HOME --gecos "" keybase \
	&& chown -R keybase:keybase $HOME 

WORKDIR $HOME
USER keybase

ENTRYPOINT [ "keybase" ]
