# Choose a base image
FROM openjdk:8-jdk-alpine

# Copy the project files into the image
WORKDIR /usr/app
COPY . .

# Build the project
RUN ./gradlew build

# Start the web server
ENTRYPOINT ["java","-jar","build/libs/spring-0.0.1-SNAPSHOT.jar"]

# docker build -t hello-spring .
# docker run -it --rm -p 8080:8080 --name hello-spring-running hello-spring