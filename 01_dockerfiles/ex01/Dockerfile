FROM debian

RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install -y curl && apt-get install -y bzip2

EXPOSE 9987/udp 30033 10011

WORKDIR /home/teamspeak
RUN curl -O http://dl.4players.de/ts/releases/3.7.1/teamspeak3-server_linux_amd64-3.7.1.tar.bz2
RUN tar xpfv teamspeak3-*.bz2

WORKDIR teamspeak3-server_linux_amd64
ENTRYPOINT ["sh", "ts3server_minimal_runscript.sh"]

# docker build -t ex01 ~/sgoinfre/docker/01_dockerfiles/ex01
# docker run -d -e TS3SERVER_LICENSE=accept -p 9987:9987/udp -p 10011:10011 -p 30033:30033 --name=maboye-ts3-server ex01
# docker logs -f maboye-ts3-server
