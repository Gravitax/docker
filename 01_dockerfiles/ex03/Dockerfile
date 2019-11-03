#---------------------------------IMAGE---------------------------------------#
FROM ubuntu:16.04

#---------------------------------INSTALL-------------------------------------#
RUN apt-get update -y && apt-get upgrade -y \
    && apt-get -y install curl openssh-server ca-certificates postfix
RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash
RUN apt-get update -y && apt-get install -y gitlab-ce
RUN apt-get update -y && apt-get install -y tzdata
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /var/tmp/*

RUN curl https://gitlab.com/maboye55/docker/raw/master/sshd_config > /etc/ssh/sshd_config
RUN curl https://gitlab.com/maboye55/docker/raw/master/gitlab.rb > /etc/gitlab/gitlab.rb

EXPOSE 23 80 443

#----------------------------------SSL PART-----------------------------------#
RUN mkdir -p /etc/gitlab/ssl
RUN openssl req -new -newkey rsa:2048 -days 365 -nodes -x509 \
    -subj "/C=fr/ST=fr/L=fr/O=fr/CN=fr" \
    -keyout /etc/gitlab/ssl/youhou.key -out /etc/gitlab/ssl/youhou.crt

RUN chmod 777 /etc/gitlab/ssl /etc/gitlab/ssl/youhou.key /etc/gitlab/ssl/youhou.crt

#------------------------------------START------------------------------------#
CMD sh -c "curl https://gitlab.com/maboye55/docker/raw/master/cfg.sh | bash"

# docker build -t mygitlab .
# docker run -it --rm -p 8080:80 -p 8023:23 -p 8443:443 mygitlab
# Check : https://192.168.99.100:8443

# git clone https://192.168.99.100:8443/root/test.git test
# git clone ssh://git@192.168.99.100:23/root/test.git test
