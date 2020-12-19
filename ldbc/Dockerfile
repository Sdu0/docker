# 编译
FROM debian:10

RUN apt update && apt install -y git maven wget unzip

WORKDIR /root/ldbc

RUN git clone https://github.com/ldbc/ldbc_snb_implementations.git \
    && git clone https://github.com/ldbc/ldbc_snb_driver.git \
    && git clone https://github.com/ldbc/ldbc_snb_datagen.git

WORKDIR /root/ldbc/ldbc_snb_driver
RUN mvn install -DskipTests

WORKDIR /root/ldbc/ldbc_snb_implementations
RUN ./build.sh

WORKDIR /root/ldbc/ldbc_snb_implementations/cypher
RUN chmod +x scripts/*.sh && ./scripts/get-neo4j.sh \
    && ./scripts/environment-variables-default.sh \
    && ./scripts/configure-neo4j.sh
