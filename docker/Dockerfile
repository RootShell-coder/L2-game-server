FROM openjdk:21-slim-bookworm

RUN set -eux; \
  apt-get update; \
  apt-get install -y \
  supervisor \
  mariadb-server;

COPY prepare /usr/bin/
COPY supervisor /etc/supervisor
ADD L2J_Mobius_Essence_7.3_SevenSigns.tar.gz /app

RUN set -eux; \
  chmod a+x /usr/bin/prepare /app/login/LoginServerTask.sh /app/game/GameServerTask.sh; \
  mkdir -p /var/run/mysqld /app/login/log /app/game/log; \
  chown mysql:mysql /var/run/mysqld;

WORKDIR /app
ENTRYPOINT ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]
