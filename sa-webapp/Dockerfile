# docker build -t sa-web .
# docker run -d -p 8080:8080 -e SA_LOGIC_API_URL='http://<container_ip or docker machine ip>:5000' sa-web



#CONTAINER_IP: To forward messages to the sa-logic container we need to get its IP. To do so execute:

# $ docker container list

#Copy the id of sa-logic container and execute:

# $ docker inspect <container_id>

#The Containers IP address is found under the property NetworkSettings.IPAddress, use it in the RUN command.


# ash is bash for alpine

FROM maven:3.5-jdk-8 AS build  
COPY . .
RUN mvn install






FROM openjdk:8-jdk-alpine
COPY --from=build /target/sentiment-analysis-web-0.0.1-SNAPSHOT.jar /target/sentiment-analysis-web-0.0.1-SNAPSHOT.jar
ENV SA_LOGIC_API_URL http://localhost:5000
EXPOSE 8080
CMD ["java", "-jar", "target/sentiment-analysis-web-0.0.1-SNAPSHOT.jar", "--sa.logic.api.url=${SA_LOGIC_API_URL}"]
