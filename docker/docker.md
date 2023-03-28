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
- [Read more](https://www.ibm.com/topics/containers) about containers

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
