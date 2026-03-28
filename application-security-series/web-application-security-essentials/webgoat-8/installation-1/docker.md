---
title: Docker
layout: default
nav_order: 2
parent: "WebGoat Installation | Web Application Security | Cycubix Docs"
grand_parent: "WebGoat | Web Application Security Essentials | Cycubix Docs"
---
# Docker

## Method 1 - WebGoat and WebWolf All-in-One Image

The easiest way to start WebGoat as a Docker container is to use the **All-in-One WebGoat image** which contains both WebGoat and WebWolf as well as an NGINX reverse proxy. 

1. Run the following command to download the All-in-One image from DockerHub, and consequently install and execute both WebGoat and WebWolf.

```
docker run -it -p 127.0.0.1:8080:8080 -p 127.0.0.1:9090:9090 -e TZ=Europe/Amsterdam webgoat/webgoat
```

## Method 2 - WebGoat and WebWolf Docker Compose

Another way to deply WebGoat and WebWolf in a more advanced way is to use a compose-file such as the `docker-compose.yml`[ <mark style="color:green;">file</mark>](https://github.com/docker/compose) from the WebGoat Github repository. This will start both containers and it also takes care of setting up the connection between WebGoat and WebWolf.

1. Create folder WASE in your laptop / PC and go into that folder.
2. Run the following command from the folder WASE.

```
curl https://raw.githubusercontent.com/WebGoat/WebGoat/develop/docker-compose.yml | docker-compose -f - up
```

> ℹ️ **Info**
>
> **Important**: the current directory on your host will be mapped into the container for keeping state.

Using the `docker-compose` file will simplify getting WebGoat and WebWolf up and running.

## How Docker and WebGoat Work Together?

1. **Docker Container**:
   * When you run `docker run -d -p 8080:8080 webgoat/webgoat-8.0`, Docker creates a container from the WebGoat image. This container is a lightweight, standalone, and executable package that includes everything needed to run the application, including the code, runtime, libraries, and dependencies.
2. **Port Mapping**:
   * The `-p 8080:8080` flag in the Docker command maps port 8080 on your host machine (Windows 11) to port 8080 in the Docker container where WebGoat is running.
   * This means that any network traffic sent to port 8080 on your host machine is forwarded to port 8080 inside the container.
3. **Web Server**:
   * Inside the Docker container, WebGoat runs a web server that listens for HTTP requests on port 8080.

### Accessing WebGoat in a Browser

1. **Open a Web Browser**:
   * Launch your preferred web browser (e.g., Chrome, Firefox, Edge).
2. **Enter the URL**:
   * Type `http://localhost:8080/WebGoat` in the address bar and press Enter.
   * `localhost` refers to your local machine, and `8080` is the port that Docker is forwarding to the WebGoat container.

### **Communication Flow**

1. **Browser Request**:
   * When you enter the URL and press Enter, your browser sends an HTTP request to `http://localhost:8080/WebGoat`.
2. **Docker Port Forwarding**:
   * Docker receives the request on port 8080 of your host machine.
   * Docker forwards this request to port 8080 inside the WebGoat container.
3. **WebGoat Server**:
   * The WebGoat server running inside the container receives the request.
   * WebGoat processes the request and generates a response (e.g., an HTML page).
4. **Response to Browser**:
   * The WebGoat server sends the response back to Docker.
   * Docker forwards the response from port 8080 in the container to port 8080 on your host machine.
   * Your browser receives the response and renders the WebGoat application.

### Visual Representation

Here's a visual representation of the communication flow:

<figure><img src="../../../../.gitbook/assets/communication docker and webgoat.png" alt=""><figcaption></figcaption></figure>

```
```
