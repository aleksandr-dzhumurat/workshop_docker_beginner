FROM ubuntu:18.04

# сборка контейнера: docker build -t pg_client:latest .
# запуск
# подключение в sh: docker run --volume $(pwd)/pg_client:/srv/pg_client --network proj_network -it --rm pg_client:latest bash

RUN apt-get update && \
    apt-get install -y curl nano python3-pip python3.6 python3.6-dev wget && \
    update-alternatives --install /usr/bin/python3 python3.6 /usr/bin/python3.6 0 && \
    pip3 install pipenv && \
    echo "deb http://apt.postgresql.org/pub/repos/apt/ stretch-pgdg main" > /etc/apt/sources.list.d/pgdg.list  && \
    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add - && \
    apt-get install -y postgresql-client-10 \
    mongodb mongo-tools

ENV \
    LC_ALL=C.UTF-8 \
    LANG=C.UTF-8

WORKDIR "/srv/pg_client"

COPY docker-entrypoint.sh /usr/local/bin/docker-entrypoint.sh
RUN chmod +x /usr/local/bin/docker-entrypoint.sh

ENTRYPOINT ["docker-entrypoint.sh"]