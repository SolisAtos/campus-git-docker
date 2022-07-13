# Commands to run the Official Docker Hello World container

From https://hub.docker.com/_/hello-world

First make sure that Docker Desktop is running to avoid the `error during connect: This error may indicate that the docker daemon is not running.` error.

## Pulling the image
```sh
docker pull hello-world
```

## Running the container
```sh
docker run hello-world
```

## Obtained output
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

## Conclusion
The output obtained shows that the container ran successfuly.