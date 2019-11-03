FROM ubuntu:16.04
LABEL maintainer="maboye@student.42.fr"

RUN apt-get update -y && apt-get upgrade -y \
    && apt-get install -y vim build-essential git vagrant zsh curl sudo valgrind net-tools network-manager
# RUN sudo apt-get install valgrind -y

RUN mkdir -p /root
WORKDIR /root

CMD ["zsh"]

# docker build -t my-ubuntu .
# docker run -it my-ubuntu
