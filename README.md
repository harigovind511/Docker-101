# What is Containerization?
Containerization is the packaging together of software code with all it’s necessary components like libraries, frameworks, and other dependencies so that they are isolated in their own "container."

[Read More](https://www.redhat.com/en/topics/cloud-native-apps/what-is-containerization)

# Docker-101

### What is Docker?
Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications.

[Read More](https://docs.docker.com/get-started/overview/)

### VM vs Container

| VM        | Container         |
| ------------- |:-------------:|
| Use Hypervisors to virtualy emulate physical hardware. | Use the OS Kernal to access underlying host hardware. |
| Slow start up, as the VM OS needs to be launched first | Quick start up, as containers only need to access the OS Kernal. |
| Difficult depenceny managed for applications to be deployed. | Easy dependeny management, as containers natively isolate and load all the dependencies into the internal File system. |
| Require high effort to backup and restore applications, as all the dependencies go on single File system. | Applications can be easily migrated between machines and environments, as each container can be represented as 1 Docker file. |

### Key Concepts
1.  **Dockerfile:** This is a text document, that contains all the commands required to assemble the Image of the application. Docker can automatically build images by reading instructions within the Dockerfile document.
      
      [Read More](https://docs.docker.com/engine/reference/builder/)

2.  **Image:** A Docker image is a file used to execute code in a Docker container. Docker images act as a set of instructions to build a Docker container, like a template.

      [Read More](https://searchitoperations.techtarget.com/definition/Docker-image)

3. **Container:** A container is an instance of an image, with all the dependencies and runtime managed required to run the application. This also has access to Host OS Kernal to access the underlying physical hardware.

      [Read More](https://www.docker.com/resources/what-container)

4. **Registry:** A registry is a storage and content delivery system, holding named Docker images, available in different tagged versions. Images are also refered as Repositories.

      [Read More](https://docs.docker.com/registry/introduction/)


### Docker Architecture
<img width="496" alt="Drawing" src="https://user-images.githubusercontent.com/30496850/143784915-4d8cd80d-79ac-4fc0-b7d7-de306ead35d0.png">

## Working Session:
### How to Dockerize an Application


#### Steps:
1. Create a new docker definition file in the root directory of your application and name the file as ##### Dockerfile
2. Add following commands to the Dockerfile:
> For JavaScript/Node Application
```dockerfile
FROM node:alpine
COPY . /app
WORKDIR /app
CMD node <JS_FILE_NAME>
```
> For ASP.Net Core Application
```dockerfile
 FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
 WORKDIR /app
 EXPOSE 80
 FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
 WORKDIR /src
 COPY ["<PROJECT_NAME>.csproj", ""]
 RUN dotnet restore "./<PROJECT_NAME>.csproj"
 COPY . .
 WORKDIR "/src/."
 RUN dotnet build "<PROJECT_NAME>.csproj" -c Release -o /app/build
 FROM build AS publish
 RUN dotnet publish "<PROJECT_NAME>.csproj" -c Release -o /app/publish
 FROM base AS final
 WORKDIR /app
 COPY --from=publish /app/publish .
 ENTRYPOINT ["dotnet", "<PROJECT_NAME>.dll"]
```

3. Open a Command Prompt/PowerShell/Terminal at the root directory of the application to be Containerized.
4. Build the Docker Image for the application using Docker Build Command, as below:
```dockerfile
docker build -t <IMAGE_NAME> .
```

Wait for build to finish.
5. Run the Docker image, using the Docker Run command.
```dockerfile
docker run <IMAGE_NAME>
```

6. To push Docker image to Docker Hub, use Docker Login command to login to the Registry.
```dockerfile
docker login
```

7. Assign a Tag to Docker Image before pushing, using the Docker Tag command as below:
```dockerfile
docker tag <IMAGE_NAME> <DOCKER_HUB_USERNAME:IMAGE_NAME>
```

8. Push Docker Image, to Docker Hub using the Push command as follows:
```dockerfile
docker push <DOCKER_HUB_USERNAME:IMAGE_NAME>
```
Wait for push activity to be successful.

> NOTE: The pushed Docker Image, can now be pulled on any host machine running Docker Daemon using the Docker Pull Command and then can be ran easily as below:
```dockerfile
docker pull <DOCKER_HUB_USERNAME:IMAGE_NAME>
docker run -d -p 8080:80 <DOCKER_HUB_USERNAME:IMAGE_NAME>
```
