# Generate The Boilerplate Codes
We are going to create a Java Spring web project in this step.

**Step 1** - Spring requires java so first download nodejs on your system.
Download and install Java SE Development Kit from [here](https://www.oracle.com/ca-en/java/technologies/javase/javase8-archive-downloads.html).

**Step 2** -  Follow the installation steps. Accept all default settings.

**Step 3** - Create a project folder.

Let's create a folder to keep all our work organized.
Open your terminal and run the following commands to create a folder (in mac).
For Windows or Linux use equivalent commands.

```sh
mkdir spring-app
cd spring-app/
```

**Step 4** - Create our project from boilerplate code. We follow the recommended steps here

Go to https://start.spring.io.
Choose _Gradle project_ and Java 8.
Set artifact name to `hellospring`.
From the _Add Dependencies_ option on the right, select _Spring Web_ and click _Generate_.
This will download your boilerplate code as a zip file.
Extract the zip file and move the contents inside hello-spring.

**Step 5** - Let's test if our project working locally

```sh
cd hellospring/
```

Open `src/main/java/hellospring/Application.java` in your favorite editor 
and paste the following code there.

```java
package hellospring;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@SpringBootApplication
@RestController
public class Application {

  @RequestMapping("/")
  public String home() {
    return "Hello Docker World";
  }

  public static void main(String[] args) {
    SpringApplication.run(Application.class, args);
  }

}
```

To build your project, if you are on linux or mac, run
```sh
./gradlew build
```

Or, if you are one Windows, run

```sh
.\gradlew.bat build
```

If everything goes well, you should see the same results after building your application:

![image](https://user-images.githubusercontent.com/13452649/134735786-567e5f47-9316-48ea-8f68-b3094a49ce9e.png)

Now we are going to run our application and test it locally.
Execute the following command to run your project:

```sh
java -jar build/libs/gs-spring-boot-docker-0.1.0.jar
```

By default, your project will be listening to port 8080.
Here is an example of the correct execution of your application:

![image](https://user-images.githubusercontent.com/13452649/134735993-ff189c89-de95-4852-b8b2-8a8204786e8b.png)

Your application is running on http://localhost:8080
Let's visit our application:

![image](https://user-images.githubusercontent.com/13452649/134736163-069137c0-d9a9-43f6-902f-440c110f5206.png)

Congratulations! You are running your app successfully in your local environment.

# Dockerize The App

**Step 1**: Create a dockerfile
Inside your project directory (`hellospring`).

Create a new file named `Dockerfile`. Then paste the following content inside the file.

```dockerfile
# Choose a base image
FROM openjdk:8-jdk-alpine

# Copy the project files into the image
WORKDIR /usr/app
COPY . .

# Build the project
RUN ./gradlew build

# Start the web server
ENTRYPOINT ["java","-jar","build/libs/spring-0.0.1-SNAPSHOT.jar"]
# docker run -it --rm -p 8080:8080 --name hello-spring-running hello-spring

```
**Step 2**: Build the docker image. This step is something like compiling your C/Java code.

```sh
docker build -t hello-spring .
```
You should see output like the following

![image](https://user-images.githubusercontent.com/13452649/134736392-f2654806-718b-49cd-8d8b-03178f9079d2.png)

**Step 3**: Run the docker image as a container. This step is something like executing your copiled C/Java program.

```sh
docker run -it --rm -p 3000:3000 --name hello-spring-running hello-spring
```

The output is pretty like the one after running `npm start`.

![image](https://user-images.githubusercontent.com/13452649/134735993-ff189c89-de95-4852-b8b2-8a8204786e8b.png)

You can see your app again on http://localhost:8080

> NB: Every time you make some changes inside the app, you need to restart the docker container.
> To do so, press `ctrl + C` to stop the container and run the command in **Step 3**.

Good luck for your exploration!
