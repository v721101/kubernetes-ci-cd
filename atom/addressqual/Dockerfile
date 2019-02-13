FROM openjdk:8-jre-alpine
ENV artifact atom-address-qualification-1.0.0-SNAPSHOT.jar
WORKDIR /root/apps
COPY . /root/apps
EXPOSE 8080
ENTRYPOINT [ "sh", "-c" ]
CMD ["echo hi from gopi"]
CMD ["java -Dbootstrap.servers=bkcttplna012.ebiz.verizon.com:6667 -jar atom-address-qualification-1.0.0-SNAPSHOT.jar"]
