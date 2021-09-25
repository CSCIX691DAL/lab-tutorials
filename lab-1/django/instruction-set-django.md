# Docker Example for Django (Python)

This project is to demonstrate containerization of a Python Django
application using Docker.

## Getting Started

### Prerequisites

- Docker

### Create the project

**Step 1**: Download the latest version of `python` from [here](https://www.python.org/downloads/).

**Step 2**: Install `python`. Accept all default settings.

**Step 3**: Install `django` by running the following command.

```sh
pip install django
```

**Step 4**: Create a `django` project by running

```sh
django-admin startproject hellodjango
```

This will create a new `django` project inside the `hellodjango` directory.

**Step 5**: Go inside the directory by running

```sh
cd hellodjango
```

**Step 6**: To start the server, run the following command

```sh
python manage.py runserver
```

You will see output like the following
![image](https://user-images.githubusercontent.com/13452649/134752619-9f99a11d-3367-469b-91fb-830bfb0599b2.png)

This will start a server at http://localhost:8000. Visit the site and you will see
![image](https://user-images.githubusercontent.com/13452649/134752675-6b1580a0-a146-4a16-a8e9-96b17805b8cc.png)

Congratulations! You have successfully started a django server.
## Containerize

### Build Docker Image

**Step 1**: Create a new file named `Dockerfile`. Paste the following content there.

```dockerfile
# Select the base image
FROM python:3

# Install necessary packages
RUN pip install django
ENV PYTHONUNBUFFERED=1
WORKDIR /usr/app
COPY . .

# Here we go
CMD [ "python", "manage.py", "runserver", "0.0.0.0:8000" ]
```

**Step 2**: Build the image by running

```sh
docker build -t hello-django .
```

### Run Docker Container

- Execute `docker run -it --rm -p 8000:8000 --name hello-django-running hello-django` command.
You will see output similar to earlier.
  ![image](https://user-images.githubusercontent.com/13452649/134752619-9f99a11d-3367-469b-91fb-830bfb0599b2.png)

Visit http://localhost:8000, and you will see the same site again.

Congratulations, again! Keep exploring.
