# Docker Example for PHP

This project is to demonstrate containerization of a PHP application using Docker.

## Getting Started

### Prerequisites

- Docker

### Build Docker Image

- Clone [this](https://github.com/CSCIX691DAL/lab-tutorials) repository
- Change working directory to `lab-tutorials/lab-1/php/hello-php`
- Execute `docker build -t my-php-app .` command

You will see output like the following

![image](https://user-images.githubusercontent.com/13452649/134738588-e7b1b25a-915b-4ade-a433-5172a91b3d76.png)


### Run Docker Container

- Execute `docker run -it --rm -p 80:80 --name my-running-app my-php-app` command
You will see output like the following
  ![image](https://user-images.githubusercontent.com/13452649/134738901-56c8b2d1-b07f-49f2-bbbe-11de43e35673.png)

- Visit http://localhost. You will see the following webpage.
  ![image](https://user-images.githubusercontent.com/13452649/134738786-c59e723e-5889-4a02-ac7d-d9d8f6527e9b.png)

> NB: Every time you make some changes inside the app, you need to restrart the docker container.
> To do so, press `ctrl + C` to stop the container and run the command in **Step 3**.

Good luck for your exploration!
