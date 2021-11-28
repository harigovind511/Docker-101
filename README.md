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
1. **Dockerfile: ** This is a text document, that contains all the commands required to assemble the Image of the application. Docker can automatically build images by reading instructions within the Dockerfile document.

[Read More](https://docs.docker.com/engine/reference/builder/)

2. **Image: ** A Docker image is a file used to execute code in a Docker container. Docker images act as a set of instructions to build a Docker container, like a template.

[Read More](https://searchitoperations.techtarget.com/definition/Docker-image)

3. **Container: ** A container is an instance of an image, with all the dependencies and runtime managed required to run the application. This also has access to Host OS Kernal to access the underlying physical hardware.

[Read More](https://www.docker.com/resources/what-container)
4. **Registry: ** A registry is a storage and content delivery system, holding named Docker images, available in different tagged versions. Images are also refered as Repositories.

[Read More](https://docs.docker.com/registry/introduction/)


### Docker Architecture
<img width="496" alt="Drawing" src="https://user-images.githubusercontent.com/30496850/143784915-4d8cd80d-79ac-4fc0-b7d7-de306ead35d0.png">

