FROM ubuntu:16.04

RUN apt-get update -q
RUN apt-get upgrade -yq
RUN apt-get install -yq openjdk-8-jre-headless screen wget
RUN useradd -ms /bin/bash minecraft
USER minecraft
WORKDIR /home/minecraft
RUN wget https://launcher.mojang.com/v1/objects/3737db93722a9e39eeada7c27e7aca28b144ffa7/server.jar -O minecraft_server.1.13.jar
RUN echo "eula=true" > eula.txt
EXPOSE 25565 25675
CMD [ "java", "-Xms1024M", "-Xmx1024M", "-jar", "minecraft_server.1.13.jar", "-o", "true" ]

# docker build -t my-serv-minecraft .
# docker run -it my-serv-minecraft
