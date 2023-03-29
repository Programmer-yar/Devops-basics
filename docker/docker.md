# Docker

## Container
- A way to package application with all the necessary dependencies and configurations.
- Container is a layer of images
    - Most of them have Linux image as base image because they are small in size. Mostly Linux alpine because that is lightest
    - For example, an image of postgresql can contain:
        - Linux alpine image
        - some other images
        - postgres application image
    - Container can also be described as running version of the image
    - is a running environment for an image
- A container consists of application image, file system, environment configs
- Portable artifacts, easily moved and shared around
- makes development and deployment more efficient.
- Also has port binding, e.g port 5432 associated with postgres container
- Containers can also be created without docker
- When we search for an artifact on DockerHub we are searching for an image not a container. Container can be called a running environment of an image.
- [Read more](https://www.ibm.com/topics/containers) about containers
- We can start containers for 2 different versions of the same application
- Container can be described as a virtual environment running on a machine

### Container storage/location
- Can be stored in public or private repositories
- Public repositories are hosted on DockerHub

### Need of Containers
- Without container every person who initializes the application in local or production environment, will need to install dependencies.
    - For example, an application may require python, redis, postgresql & Apache as dependencies. There are different binaries/installation packages & process for different environments which will need to be configured first.
    - There are many steps required for setup and things can go wrong at any step. There can be version upgrades which can cause compatibility issues.
    - Lengthy detailed steps can cause confusion & misunderstandings.
- With containers, just download the container and run it.
    - no need to install binaries or dependencies
    - containers have their own isolated environment
    - They are packaged with all needed configuration

### Containers for different versions of same application
Let's say we downloaded different version images of the same application like redis.
- When we run them they run in different containers but same port, how do we connect with them if both are running on same port?
    - In that case we use port binding
    - The running containers on host machine are connected to host machine through ports, a container listening on port 3000 can bind with host machine port 3000. But if there are 2 containers listening on port 3000 then they can not interact/bind with host machine on port 3000, because host machine has only one port 3000. one of the containers need to bind at port 3001 or some different port.
- ![ports-binding-image](../images/port-binding.png)

## Docker Commands
- See all existing images `docker images`
- See all running containers `docker ps`
- Run the container in:
    - attached mode `docker run <image_name>` (will run in terminal and can be ended by `Ctrl + c`)
    - detached mode `docker run -d <image_name>`
- Stop the container using `docker stop <Container ID>`
- Start the container `docker start <Conatiner ID>`
- Get the history of all the containers (ID, Status) `docker ps -a`
