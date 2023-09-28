FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/nitin3132/vprofile-project.git
RUN cd vprofile-project && git chekckout docker & mvn install

FROM tomcat:9-jre11
LABEL "Project"="vprofile"
LABEL "Author"="Nitin"
RUN rm -rf /user/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /user/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD [ "catilina.sh","run" ]