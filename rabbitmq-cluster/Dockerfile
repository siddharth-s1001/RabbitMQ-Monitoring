FROM rabbitmq:3.10-management

COPY definitions.json /etc/rabbitmq/definitions.json
COPY rabbitmq.conf /etc/rabbitmq/rabbitmq.conf

RUN set -eux;
RUN apt update;
RUN apt-get install -y --no-install-recommends \
                build-essential \
                gosu \
                ca-certificates \
                gnupg \
                libncurses5-dev \
                wget
RUN rabbitmq-plugins enable rabbitmq_management
RUN wget -P /opt/rabbitmq/plugins https://github.com/rabbitmq/rabbitmq-delayed-message-exchange/releases/download/3.10.2/rabbitmq_delayed_message_exchange-3.10.2.ez

RUN rabbitmq-plugins enable rabbitmq_delayed_message_exchange
RUN rabbitmq-plugins enable rabbitmq_prometheus

WORKDIR /data

EXPOSE 5672
EXPOSE 15672
EXPOSE 15692
EXPOSE 80
