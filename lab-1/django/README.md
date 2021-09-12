# Docker Example for Django (Python)

This project is to demonstrate containerization of a Python Django application using Docker.

## Getting Started

### Prerequisites

- Docker

### Build Docker Image

- Clone [this](https://github.com/CSCIX691DAL/lab-tutorials) repository
- Change working directory to `lab-tutorials/lab-1/django/`
- Execute `docker build -t hello-django .` command

### Run Docker Container

- Execute `docker run -p 8000:8000 --name hello-django-running hello-django` command
