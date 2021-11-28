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

### Docker Architecture

### Key Concepts
1. Dockerfile
2. Image
3. Container
4. Registry
