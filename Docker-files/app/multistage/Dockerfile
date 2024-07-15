FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
#Clone the source code from vprofile repo
RUN git clone https://github.com/itsparan/vprofile-project.git
#run the source code for manien build
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11

RUN rm -rf /usr/local/tomcat/webapps/*
#copy artificate id from build iamge path to tomcat/webapps
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
