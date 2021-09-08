# Generate The Boilerplate Codes
We are going to create a Nextjs project in this step.

**Step 1** - Nextjs requires nodejs so first download nodejs on your system

![image](https://user-images.githubusercontent.com/13452649/132540099-c9d76abb-45f3-4320-a7cf-5bc40b2a4a38.png)

**Step 2** -  Follow the installation steps. Accept all default settings.

**Step 3** - Create a project folder.

Let's create a folder to keep all our work organized. Open your terminal and run the following commands to create a folder (in mac). For Windows or Linux use equivalent commands.

```sh
mkdir nextjs-app
cd nextjs-app/
```

**Step 4** - Create our project from boilerplate code. We follow the recommended steps here

```sh
npx create-next-app <your project name>
Example:
npx create-next-app hello-docker
```

**Step 5** - Let's test if our project working locally

```sh
cd hello-docker/
```

Install all dependencies using:
```sh
npm i
```

Build your project now:
```sh
npm run build
```

If everything goes well, you should see the same results after building your application:

![image](https://user-images.githubusercontent.com/13452649/132540738-67d5970a-3af5-472b-8df6-d2eba7acc2ec.png)


Now we are going to run our application and test it locally.
Execute the following command to run your project:

```sh
npm start
```

By default, your project will be listening to port 3000. Here is an example of the correct execution of your application:

![image](https://user-images.githubusercontent.com/13452649/132541097-a3746698-281b-42ba-9fdf-2d55bd130e26.png)


Your application is running on HTTP://localhost:3000
Let's visit our application:

![image](https://user-images.githubusercontent.com/13452649/132541151-51c14f2a-17b9-47e9-b135-d317e61995c7.png)


Congratulations! You are running your app successfully in your local environment.

# Dockerize The App

**Step 1**: Create a dockerfile
Inside your project directory (`hello-docker`).

Create a new file named `Dockerfile`. Then paste the following content inside the file.

```dockerfile
# Choosing a base image
FROM node:14.15.4-alpine

# copy your application files
# to the /usr/app directory inside the container
WORKDIR /usr/app
COPY . .

# build your project
ENV NODE_ENV production
RUN npm run build

# here we go
CMD [ "npm", "start" ]

```
**Step 2**: Build the docker image. This step is something like compiling your C/Java code.

```sh
docker build -t hello-docker .
```
You should see output like the following

![image](https://user-images.githubusercontent.com/13452649/132543086-e438c411-fbdc-459a-9773-28967b5a9c72.png)


**Step 3**: Run the docker image as a container. This step is something like executing your copiled C/Java program.

```sh
docker run -it --rm -p 3000:3000 --name hello-docker-running hello-docker
```

The output is pretty like the one after running `npm start`.

![image](https://user-images.githubusercontent.com/13452649/132543179-529a35b1-d95c-4fb1-9221-d9383a7caf59.png)

You can see your app again on HTTP://localhost:3000

> NB: Every time you make some changes inside the app, you need to restrart the docker container.
> To do so, press `ctrl + C` to stop the container and run the command in **Step 3**.

Good luck for your exploration!
