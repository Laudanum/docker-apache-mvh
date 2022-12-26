FROM debian:stretch

EXPOSE 80

# updated to match debian www-user
ENV MOUNTFILE_MOUNT_UID=33 MOUNTFILE_MOUNT_GID=33

# Install Requirements
RUN apt-get update \
  && apt-get install -y apache2 \
  && apt-get install -y ca-certificates msmtp \
  && apt-get install -y vim wget \
  && apt-get install -y perl \
  # Cleanup
  && rm -rf /var/lib/apt/lists/* /tmp/*

# Host Configuration
COPY apache2.conf /etc/apache2/apache2.conf
COPY mpm_prefork.conf /etc/apache2/mods-available/
COPY mvhost.conf /etc/apache2/sites-available/
RUN rm /etc/apache2/conf-enabled/* /etc/apache2/sites-enabled/* \
  && a2dismod mpm_event \
  && a2enmod vhost_alias mpm_prefork deflate rewrite expires headers cgid \
  && a2ensite mvhost.conf \
  && mkdir -p /srv/www

ADD entry.sh /
ENTRYPOINT ["/entry.sh"]
CMD [ "/usr/sbin/apache2ctl", "-D", "FOREGROUND", "-k", "start" ]
