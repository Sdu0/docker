# 编译
FROM debian:10

RUN apt update && apt install -y wget net-tools apt-transport-https ca-certificates dirmngr \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv E0C56BD4 \
    && echo "deb https://repo.clickhouse.tech/deb/stable/ main/" | \
        tee /etc/apt/sources.list.d/clickhouse.list \
    && apt update && apt install -y clickhouse-server clickhouse-client \
    && service clickhouse-server start

CMD ["/bin/sh", "'clickhouse' -c '/usr/bin/clickhouse-server --config-file /etc/clickhouse-server/config.xml"]