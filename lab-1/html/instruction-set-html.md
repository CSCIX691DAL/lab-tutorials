# Generate The Boilerplate Codes
We are going to create a html project in this step.

**Step 1** - Create a project folder.

Let's create a folder to keep all our work organized. Open your terminal and run the following commands to create a folder (in mac). For Windows or Linux use equivalent commands.

```sh
mkdir hello-html
cd hello-html/
```

**Step 2** - Add an HTML file.

Create a file named `index.html` and paste the following content there.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSCI 2690</title>
</head>
<body>
<h1>Here we go</h1>
</body>
</html>
```

# Dockerize And Run The App

**Step 1**: Create a dockerfile
Inside your project directory (`hello-docker`).

Create a new file named `Dockerfile`. Then paste the following content inside the file.

```dockerfile
# Choosing a base image
FROM httpd:2.4

# copy your application files to the
# /usr/local/apache2/htdocs/ directory inside the container
WORKDIR /usr/local/apache2/htdocs/
COPY . .
```
**Step 2**: Build the docker image. This step is something like compiling your C/Java code.

```sh
docker build -t hello-html .
```
You should see output like the following

![image](https://user-images.githubusercontent.com/13452649/134737846-6ede2c5c-5a03-4332-8cc0-6c9c50a716de.png)

**Step 3**: Run the docker image as a container. This step is something like executing your copiled C/Java program.

```sh
docker run -it --rm -p 80:80 --name hello-html-running hello-html
```
You will see the following output.

![image](https://user-images.githubusercontent.com/13452649/134738125-af782942-45d3-46c0-933f-6acc25a5c76b.png)

You can see your app on HTTP://localhost

> NB: Every time you make some changes inside the app, you need to restrart the docker container.
> To do so, press `ctrl + C` to stop the container and run the command in **Step 3**.

Good luck for your exploration!
