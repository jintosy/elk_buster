FROM debian:10.0

RUN apt update && apt upgrade -y

RUN apt install -y vim wget curl

# RUN echo "deb http://ftp.jp.debian.org/debian/ sid main" | tee -a /etc/apt/source.list

CMD [ "bin/bash" ]