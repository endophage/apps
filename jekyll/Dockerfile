FROM ruby:latest

RUN apt update \
	&& apt install -y --no-install-recommends \
		npm \
	&& rm -rf /var/lib/apt/lists/* \
	&& gem install bundler github-pages \
	&& mkdir /site

ENTRYPOINT [ "bash" ]
CMD []
