# Dockers

- List docker images

    ```bash
    docker images -a
    ```

- Remove Docker image

    ```bash
    docker rmi image
    # remove all images
    docker rmi $(docker images -a)
    ```

- Remove dangling images

    ```bash
    # List for docker dangling images
    docker images -f dangling=true
    # Remove dangling images
    docker rmi $(docker images -f dangling=true)

    ```

- Remove images according to patterns

    ```bash
    # Get images according patterns
    docker ps -a | grep "pattern"
    # Remove the image according paatern
    docker ps -a | grep "pattern" | awk {print $1} | xargs docker rm 
    ```

- Remove all images

    ```bash
    # List all images
    docker images -a
    # Remove all docker images
    docker rmi $(docker images -a -p)
    ```

- Remove docker container

    ```bash
    # List all docker containers
    docker ps -a
    # Remove all container
    docker rm ID_or_Name
    # Remove the container upon exit
    docker run -rm IMAGE_RUN
    ```

- Remove all exited containers

    ```bash
    # List of exited containers
    docker ps -a -f status=exited
    # Remove the list of exited container
    docker rmi $(docker ps -a -f status=exited)
    ```

- Remove containers according patterns

    ```bash
    # List containers according to patterns
    docker ps -a | grep "pattern"
    # Remove the images
    docker ps -a | grep "pattern" | awk {print $3} | xargs docker rmi
    ```

- Stop all container and Remove them

    ```bash
    # List of all container
    docker ps -a
    # Stop container
    docker stop $(docker ps -a -q)
    # Remove the container
    docker rm $(docker ps -a -q)

    ```

- Remove docker volumes

    ```bash
    # remove volume
    docker volume ls
    docker volume ls VOLUME_NAME

    ```

- Remove docker dangling volumes

    ```bash
    # List docker dangling volume
    docker volume ls -f dangling=true
    # Remove dangling volume
    docker volume rm $(docker volume ls -f dangling=true -q)

    ```

- Remove container volume

    ```bash
    docker rm -v CONTAINER_VOLUME
    ```