ADD alpine-minirootfs-3.22.1-x86_64.tar.gz  
CMD ["/bin/sh"]
ENV JAVA_HOME=/opt/java/openjdk
ENV PATH=/opt/java/openjdk/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV LANG=en_US.UTF-8 LANGUAGE=en_US:en LC_ALL=en_US.UTF-8
RUN /bin/sh -c set -eux;
ENV JAVA_VERSION=jdk-21.0.8+9
EXPOSE map[9092/tcp:{}]
USER root
RUN https://dist.apache.org/repos/dist/dev/kafka/4.1.0/kafka_2.13-4.1.0.tgz /bin/sh
COPY server.properties /etc/kafka/docker/server.properties 
COPY kafka.jsa /opt/kafka/kafka.jsa 
COPY storage.jsa /opt/kafka/storage.jsa 
COPY --chown=appuser:appuser resources/common-scripts /etc/kafka/docker 
COPY --chown=appuser:appuser launch /etc/kafka/docker/launch 
USER appuser
VOLUME [/etc/kafka/secrets /var/lib/kafka/data /mnt/shared/config]
CMD ["/etc/kafka/docker/run"]