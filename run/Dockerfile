# FROM maven:3.8-openjdk-8 as build
# RUN git clone https://github.com/Dishair/boxfuse-origin.git /boxfuse-origin
# RUN cd /boxfuse-origin && mvn clean package

FROM tomcat:alpine as prod
COPY --from=docker-build /boxfuse-origin/target /usr/local/tomcat/webapps
# RUN cp -r webapps.dist/* webapps/

EXPOSE 8080

CMD ["catalina.sh", "run"]