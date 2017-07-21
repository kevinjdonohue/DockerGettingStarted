# Docker - Getting Started
A repo to contain notes and examples from going through the Docker Getting Started guide @ docs.docker.com

## Defining a Container with a Dockerfile

This file is used to define a "container".  A container contains your application code along with any libraries, etc.

In this example from docs.docker.com's Getting Started tutorial, they have you create a container in which you can run a basic Python application.

```Dockerfile
# Official Python runtime - parent image
FROM python:2.7-slim

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
ADD . /app

# Install any needed packages specified in requirements.txt
RUN pip install -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
```

We start with a parent image (pulled from Docker?) with the Python 2.7 runtime already setup in it.

Next, we create a working directory in the container - this will be the target directory for our application.

Since we going to run a Python application, we leverage PIP to pull the required modules for our application using a requirements.txt file.

Then, in order to expose our application outside of the container, we expose port 80

Next, we add an environment variable for use in our application.

Finally, we execute our Python application via the command line

## Building a Docker Image

In order to build an Image based on our Dockerfile (which defined our container), we need to run the docker build command.

```docker
docker build -t friendlyhello .
```

If the image is built successfully, we'll be able to see it in the image of available images.

```docker
docker images
```
