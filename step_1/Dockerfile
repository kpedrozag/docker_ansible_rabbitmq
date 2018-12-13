FROM ubuntu:16.04

RUN apt -y update

RUN apt -y install iputils-ping net-tools wget

RUN wget -O - "https://github.com/rabbitmq/signing-keys/releases/download/2.0/rabbitmq-release-signing-key.asc" | apt-key add -

RUN apt-key adv --keyserver "hkps.pool.sks-keyservers.net" --recv-keys "0x6B73A36E6026DFCA"

RUN echo "deb https://dl.bintray.com/rabbitmq-erlang/debian xenial erlang\ndeb https://dl.bintray.com/rabbitmq/debian xenial main" | tee /etc/apt/sources.list.d/bintray.rabbitmq.list

RUN apt -y install apt-transport-https
RUN apt -y update
RUN apt -y install erlang-nox
RUN apt -y update
RUN apt -y install rabbitmq-server

EXPOSE 5672 15672 4369

COPY start_rabbit /bin/

RUN chmod +x /bin/start_rabbit

CMD ["start_rabbit"]