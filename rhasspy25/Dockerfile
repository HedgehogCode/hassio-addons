FROM rhasspy/rhasspy:2.5.8
LABEL maintainer="Benjamin Wilhelm <benjamin@b-wilhelm.de>"
ENV LANG C.UTF-8

RUN apt-get update \
	&& apt-get install -y --no-install-recommends \
	sudo \
	git \
	alsa-utils \
	dkms \
	i2c-tools \
	libasound2-plugins
RUN git clone --depth=1 https://github.com/respeaker/seeed-voicecard \
	&& cd seeed-voicecard \
	&& chmod a+x install.sh ubuntu-prerequisite.sh \
	&& ./ubuntu-prerequisite.sh \
	&& ./install.sh


ENV CONFIG_PATH /data/options.json

COPY run.sh /

ENTRYPOINT ["/run.sh"]
