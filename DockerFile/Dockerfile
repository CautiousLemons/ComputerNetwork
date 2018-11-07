FROM jitsi/base

#config jitsi/java-base
RUN	\
	mkdir -p /usr/share/man/man1 && \
	apt-dpkg-wrap apt-get update && \
	apt-dpkg-wrap apt-get install -y openjdk-8-jre-headless && \
	apt-cleanup

#config jitsi/web
RUN \
	apt-dpkg-wrap apt-get update && \
	apt-dpkg-wrap apt-get install -y cron nginx-extras jitsi-meet-web && \
	apt-dpkg-wrap apt-get install -y -t stretch-backports certbot && \
	apt-cleanup && \
	rm -f /etc/nginx/conf.d/default.conf && \
	rm -f /usr/share/jitsi-meet/interface_config.js

COPY web_rootfs/ /

#config jicofo
RUN \
	apt-dpkg-wrap apt-get update && \
	apt-dpkg-wrap apt-get install -y jicofo && \
	apt-cleanup

COPY jicofo_rootfs/ /

#config prosody
RUN \
	apt-dpkg-wrap apt-get update && \
	apt-dpkg-wrap apt-get install -t stretch-backports -y prosody && \
	apt-cleanup && \
	rm -rf /etc/prosody
	
COPY prosoby_rootfs/ /

#config jvb
RUN \
	apt-dpkg-wrap apt-get update && \
	apt-dpkg-wrap apt-get install -y jitsi-videobridge && \
	apt-cleanup

COPY jvb_rootfs/ /

EXPOSE 80 443 5222 5269 5347 5280

VOLUME /config