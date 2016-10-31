# This will generate efrecon/armv7hf-scan
FROM efrecon/armv7hf-tcl
MAINTAINER Emmanuel Frecon <efrecon@gmail.com>

# Set the env variable DEBIAN_FRONTEND to noninteractive to get
# apt-get working without error output.
ENV DEBIAN_FRONTEND noninteractive

# Update underlying ubuntu image and all necessary packages.
RUN [ "cross-build-start" ]
RUN apt-get update && \
    apt-get install -y imagemagick scanbd && \
    apt-get autoremove -y
RUN sed -i "s/^\(\s*\)user\s*=.*/\1user = root/g" /etc/scanbd/scanbd.conf
RUN sed -i "s/^\(\s*\)group\s*=.*/\1group = root/g" /etc/scanbd/scanbd.conf
RUN sed -i "s/^\(\s*\)scriptdir\s*=.*/\1scriptdir = \/usr\/share\/scanbd\/scripts/g" /etc/scanbd/scanbd.conf
RUN sed -i "s/^\(\s*\)script\s*=.*/\1script = \"action.script\"/g" /etc/scanbd/scanbd.conf
RUN [ "cross-build-end" ]

# This directory is where the default scripts will place their scans
VOLUME /var/spool/scan

# This directory is where scripts are being loaded from, modify to implement
# your own actions.
VOLUME /usr/share/scanbd/scripts

ENTRYPOINT [ "scanbd", "-f" ]
