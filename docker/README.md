# Docker

- [ ] [The New IT Girl](https://github.com/agcdtmr/automation/blob/main/kubernetes/slides.pdf)


## [Learning Docker](https://www.linkedin.com/learning/learning-docker-17236240)

- Why do ports binding?

web-server.Dockerfile 
```
FROM ubuntu
LABEL maintainer="Carlos Nunez <dev@carlosnunez.me>"

USER root
COPY ./web-server.bash /

RUN chmod 755 /web-server.bash
RUN apt -y update
RUN apt -y install bash netcat

USER nobody

ENTRYPOINT [ "/web-server.bash" ]
```

This Dockerfile appears to set up a basic web server within a Docker container using Ubuntu as the base image. Let's break down the contents:

1. `FROM ubuntu`: Specifies that this Docker image will be built upon the official Ubuntu image, making it the base image for this container.

2. `LABEL maintainer="Carlos Nunez <dev@carlosnunez.me>"`: Adds metadata to the image to identify the maintainer/contact information. This step lets us do powerful things inside the container, almost like being a superhero.

3. `USER root`: Switches to the root user to execute commands that require elevated privileges.

4. `COPY ./web-server.bash /`: Copies a file named `web-server.bash` from the local directory into the root directory (`/`) of the container. It's like putting a special file called web-server.bash into our container.

5. `RUN chmod 755 /web-server.bash`: Changes the permissions of the copied `web-server.bash` file to make it executable (`chmod 755` grants read, write, and execute permissions to the file owner and read/execute permissions to others). This makes sure the file we put in can be used by the container.

6. `RUN apt -y update` and `RUN apt -y install bash netcat`: Updates the package list and installs `bash` and `netcat` using the package manager (`apt`) within the container. These packages are essential for running the web server.

7. `USER nobody`: Switches the user to `nobody`, a common practice for security reasons to run the container with lower privileges. We're saying that most of the time, the container should act like a regular person, not a superhero.

8. `ENTRYPOINT [ "/web-server.bash" ]`: Specifies that the default command to run when the container starts is the `web-server.bash` script. This is like saying, "When the container starts, do whatever is written in the web-server.bash file."

This Dockerfile, when used to build a Docker image and run a container, sets up a basic web server by executing the `web-server.bash` script as the entry point for the container. The script likely contains commands to start a simple web server or perform other necessary tasks to serve web content.


web-server.bash   
```   
#!/usr/bin/env bash

start_server() {
  echo "Server started. Visit http://localhost:5000 to use it."
  message=$(echo "<html><body><p>Hello! Today's date is $(date).</p></body></html>")
  length=$(wc -c <<< "$message")
  payload="\
HTTP/1.1 200 OK
Content-Length: $((length-1))

$message"
  while true
  do echo -ne "$payload" | nc -l -p 5000
  done
}

start_server
```

This `web-server.bash` file is like a set of instructions for our container to become a simple web server. Here's what it does:

- `#!/usr/bin/env bash`: This tells the computer to use the "bash" program to understand and run this file.

- `start_server() { ... }`: It's like defining a set of actions called `start_server`.

- Inside `start_server`:
  - `echo "Server started..."`: Prints a message to the console, telling us where to access the server.
  - `message=$(echo "...")`: Makes a little web page with a greeting and today's date.
  - `length=$(wc -c <<< "$message")`: Figures out how long our web page is.
  - `payload="..."`: Prepares a response that our server will send to anyone who connects.
  - `while true ... done`: Keeps sending this web page to anyone who connects to our server.

- Finally, `start_server`: Actually starts the server by running the `start_server` action.

In simple terms, this file creates a basic web server. When someone visits `http://localhost:5000` in a web browser on the computer where this server is running, it will show a page saying "Hello! Today's date is [current date]."

```
docker --help
docker container create --help
docker container create hello-world:linux
docker ps
docker ps -all
docker container start <id>
docker ps -all
docker logs <id>
docker container start --attach <id>
```


```
docker run hello-world:linux
```


```
docker build -t our-first-image .
docker run our-first-image
```



```
docker build --file server.Dockerfile --tag our-first-server .
```


Show list of containers only ID
```
docker ps -aq
```


## Port binding

```docker run -d --name hopeful_leakey -p 5001:5000 our-web-server```




remove and stop all the containers that are running
```
docker ps -aq | xargs docker rm
```
