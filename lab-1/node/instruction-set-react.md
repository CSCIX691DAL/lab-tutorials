# Generate The Boilerplate Codes
We are going to create a Nextjs project in this step.

**Step 1** - Nextjs requires nodejs so first download nodejs on your system

![image](https://user-images.githubusercontent.com/13452649/132540099-c9d76abb-45f3-4320-a7cf-5bc40b2a4a38.png)

**Step 2** -  Follow the installation steps. Accept all default settings.

**Step 3** - Create a project folder.

Let's create a folder to keep all our work organized. Open your terminal and run the following commands to create a folder (in mac). For Windows or Linux use equivalent commands.

```sh
mkdir react-app
cd react-app/
```

**Step 4** - Create our project from boilerplate code. We follow the recommended steps here

```sh
npx create-react-app <your project name>
Example:
npx create-react-app hello-react
```

**Step 5** - Let's test if our project working locally

```sh
cd hello-react/
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

![image](https://user-images.githubusercontent.com/13452649/132951451-11c43b81-1fc0-4fac-a998-043cbc74992b.png)


Now we are going to run our application and test it locally.
Execute the following command to run your project:

```sh
npm start
```

By default, your project will be listening to port 3000. Here is an example of the correct execution of your application:

![image](https://user-images.githubusercontent.com/13452649/132951472-048a84d4-6bd8-45fd-89a2-2a5b8737e2cf.png)


Your application is running on http://localhost:3000
Let's visit our application:

![image](https://user-images.githubusercontent.com/13452649/132951489-86427b58-5cc1-4d5d-ab1a-f1c89a168476.png)


Congratulations! You are running your app successfully in your local environment.

# Dockerize The App

**Step 1**: Create a dockerfile
Inside your project directory (`hello-react`).

Create a new file named `Dockerfile`. Then paste the following content inside the file.

```dockerfile
FROM node:14.15.4-alpine

# copy your application files
# to the /usr/app directory inside the container
WORKDIR /usr/app
COPY . .

# install necessary packages
RUN npm i

# build your project
ENV NODE_ENV production
RUN npm run build

# here we go
CMD [ "npm", "start" ]

```
**Step 2**: Build the docker image. This step is something like compiling your C/Java code.

```sh
docker build -t hello-react .
```
You should see output like the following

![image](https://user-images.githubusercontent.com/13452649/132951537-3d50d66d-ba66-4d0d-8c48-f3cce20aec58.png)

**Step 3**: Run the docker image as a container. This step is something like executing your copiled C/Java program.

```sh
docker run -it --rm -p 3000:3000 --name hello-react-running hello-react
```

The output is pretty like the one after running `npm start`.

![image](https://user-images.githubusercontent.com/13452649/132951550-4a57bbd7-92e8-4af3-899c-22eef5578a4e.png)


You can see your app again on http://localhost:3000

> NB: Every time you make some changes inside the app, you need to restart the docker container.
> To do so, press `ctrl + C` to stop the container and run the command in **Step 3**.

Good luck for your exploration!
