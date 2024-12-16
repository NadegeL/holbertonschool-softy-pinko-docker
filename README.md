# holbertonschool-softy-pinko-docker
Docker Infrastructure Project
Context
Docker is a platform that enables you to containerize applications, packaging them into portable, self-contained environments that can run anywhere. This allows you to move your application quickly from one environment to another, such as from your local machine to a server, without worrying about dependencies or configuration issues. Docker achieves this by using containers, which are isolated environments that contain everything needed for an application to run, including libraries, dependencies, and configurations.

Docker containers are lightweight, start and stop quickly, and are ideal for modern software development and deployment. Additionally, Docker provides tools for scaling applications by running multiple containers on different hosts or the same host, and managing them using Docker Compose or other orchestration tools.

In this project, you will create an infrastructure for an application that utilizes:

A reverse proxy
A load balancer
Two application servers
One front-end server
High-level Design
In this design, there is a single server that acts as the entry point for your application. This server serves as a reverse proxy, routing traffic to either the API servers or the front-end static-content server. It also functions as a load balancer, distributing traffic between the two API servers.

Here’s how it works:

Reverse Proxy and Static Content: If a request is made for static content, the reverse proxy will route the request to the front-end static-content server. Any static content returned will be sent back to the client, without the client directly communicating with the front-end server.

API Servers and Load Balancing: If the request is for the API servers, the reverse proxy will apply a load-balancing algorithm to determine which API server should handle the request. This project will use the Round Robin load balancing algorithm, which distributes requests evenly across the available servers in a rotating manner. Once the request is handled by an API server, the response is sent back to the client through the proxy.

What is Round Robin Load Balancing?
Round Robin load balancing is a method of distributing traffic across multiple servers in a rotating manner. Each server is assigned a request in turn, ensuring that all servers receive an equal share of traffic. For example, if there are three servers (A, B, and C), requests are sent to A, then B, then C, and this cycle repeats. This helps to prevent any one server from becoming overloaded with requests. Although this approach is simple and effective, it may not be ideal for all applications, especially those with varying workloads.

For this project, Round Robin is a sufficient method to implement for load balancing.

What You Need Before Starting
Install Docker Desktop on your local machine (not your sandbox). You can download Docker from the following link:

Docker Desktop
For installation instructions, refer to the following guides:

Windows Installation
Mac Installation
Linux Installation
Chromebook Installation
Familiarize yourself with Docker: If you're new to Docker, it's helpful to go through the Docker Tutorial to learn the basics before diving into the project.

Project Structure
The project will consist of several Docker containers, including:

Reverse Proxy and Load Balancer: This container will handle routing requests to the appropriate server (either static content or API servers) and balance the load across the API servers.
API Servers: These two containers will handle the API logic and business processes.
Front-End Server: This container will serve static content (e.g., HTML, CSS, JavaScript) to the client.
Instructions
Clone the Repository (or create a new Docker project).
Write the Dockerfile to configure the base image, install necessary dependencies, and define the container behavior.
Build the Docker Image using the docker build command.
Run the Docker Containers using the docker run command, ensuring the reverse proxy, load balancer, API servers, and front-end server are properly configured.
Verify the Load Balancing: Ensure the requests are being evenly distributed across the API servers using the Round Robin method.