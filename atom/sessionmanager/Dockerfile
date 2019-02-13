FROM openjdk:8-jre-alpine
ENV artifact atom-sessionmanager-1.0.0-SNAPSHOT.jar
WORKDIR /root/apps
COPY . /root/apps
EXPOSE 8080
ENTRYPOINT [ "sh", "-c" ]
CMD ["echo hi from gopi"]
CMD ["java -jar atom-sessionmanager-1.0.0-SNAPSHOT.jar"]
