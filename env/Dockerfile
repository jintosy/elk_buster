FROM debian:10.6

RUN apt update && apt upgrade -y

# 必要なパッケージ類のインスコ
RUN apt install -y curl gnupg apt-transport-https wget procps vim git

# jdk-1.8.xを入れるための準備
RUN echo "deb http://ftp.jp.debian.org/debian/ sid main" | tee -a /etc/apt/sources.list
# 後ろのをつけると Could not configure 'libc6:amd64' を回避できるっぽい?
RUN apt update && apt install -y openjdk-8-jdk -o APT::Immediate-Configure=0

# ELK環境の準備
RUN wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add -
RUN echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | tee -a /etc/apt/sources.list.d/elastic-7.x.list
RUN apt update && apt install -y logstash elasticsearch kibana

# 作業用ディレクトリの準備
RUN mkdir -p /var/work
WORKDIR /var/work

# 設定ファイルの配置
ADD ./config/elasticsearch.yml /var/work/
ADD ./config/kibana.yml /var/work
ADD ./config/pipeline.conf /var/work

# neo4jインスコ
RUN wget -O - https://debian.neo4j.com/neotechnology.gpg.key | apt-key add -
RUN echo 'deb https://debian.neo4j.com stable latest' | tee /etc/apt/sources.list.d/neo4j.list
RUN apt update && apt install -y neo4j

# 後々必要になるのでpython3インスコ
RUN apt install -y python3 python3-pip python3-scipy python3-urllib3


CMD [ "/bin/bash" ]