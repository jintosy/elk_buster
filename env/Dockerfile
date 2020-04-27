FROM debian:10.0

RUN apt update && apt upgrade -y

RUN apt install -y curl gnupg apt-transport-https vim wget procps

RUN echo "deb http://ftp.jp.debian.org/debian/ sid main" | tee -a /etc/apt/sources.list

RUN apt update && apt install -y openjdk-8-jdk

RUN mkdir -p /var/file/

RUN wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add -

RUN echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | tee -a /etc/apt/sources.list.d/elastic-7.x.list

RUN apt update && apt install -y logstash elasticsearch kibana

CMD [ "bin/bash" ]