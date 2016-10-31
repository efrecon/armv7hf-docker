# This will generate efrecon/armv7hf-scan
FROM efrecon/armv7hf-tcl
MAINTAINER Emmanuel Frecon <efrecon@gmail.com>

# Set the env variable DEBIAN_FRONTEND to noninteractive to get
# apt-get working without error output.
ENV DEBIAN_FRONTEND noninteractive

# Update underlying ubuntu image and all necessary packages.
RUN [ "cross-build-start" ]
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y scanbd \
			imagemagick && \
    apt-get clean
RUN sed -i "s/^\(\s*\)user\s*=.*/\1user = root/g" /etc/scanbd/scanbd.conf
RUN sed -i "s/^\(\s*\)group\s*=.*/\1group = root/g" /etc/scanbd/scanbd.conf
RUN sed -i "s/^\(\s*\)scriptdir\s*=.*/\1scriptdir = \/usr\/share\/scanbd\/scripts/g" /etc/scanbd/scanbd.conf
RUN [ "cross-build-end" ]

VOLUME /usr/share/scanbd/scripts

#ENTRYPOINT [ "scanbd", "-f" ]
ENTRYPOINT [ "ash" ] 