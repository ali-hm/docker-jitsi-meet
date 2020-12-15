ARG JITSI_REPO=jitsi
FROM ${JITSI_REPO}/base

ADD https://raw.githubusercontent.com/acmesh-official/acme.sh/2.8.8/acme.sh /opt
COPY rootfs/ /

RUN \
	apt-dpkg-wrap apt-get update && \
	apt-dpkg-wrap apt-get install -y cron nginx-extras socat && \
	apt-dpkg-wrap apt-get -d install -y jitsi-meet-web-config && \
    dpkg -x /var/cache/apt/archives/jitsi-meet-web-config*.deb /tmp/pkg && \
	rm -f /etc/nginx/conf.d/default.conf && \
	apt-cleanup && \
	rm -rf /tmp/pkg /var/cache/apt && \
	cp /usr/share/jitsi-meet2/config.js /defaults && \
	cp /usr/share/jitsi-meet2/interface_config.js /defaults


EXPOSE 80 443

VOLUME ["/config", "/usr/share/jitsi-meet/transcripts"]
