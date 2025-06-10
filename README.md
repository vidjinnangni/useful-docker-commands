# Useful Docker commands

This repository is a **personal cheatsheet** of frequently used Docker and Docker Compose commands. It's aimed at beginners and intermediate users looking for quick **CLI references**.

---

## Docker container management

```bash
# List running containers
docker ps

# List all containers (running and stopped)
docker ps -a

# Show live logs from a container
docker logs -f [container ID]

# Show processes inside a container
docker top [container ID]

# Kill a running container
docker kill [container ID]

# Remove a container forcefully
docker rm -f [container ID]
```

## Stop & remove containers

```bash
# Stop all containers
docker stop $(docker ps -a -q)

# Remove all containers
docker rm -f $(docker ps -a -q)

# Stop a container
docker container stop [container ID]

# Stop all containers (alternate syntax)
docker container stop $(docker container ls -aq)

# Remove a container
docker container rm [container ID]

# Remove all containers
docker container rm $(docker container ls -aq)

# Stop all containers and prune everything including volumes
docker container stop $(docker container ls -aq) && docker system prune -af --volumes
```

## Execute commands inside containers

```bah
# Open a shell session inside a container
docker exec -it [container ID] sh

# Run Magento CLI inside a container
docker exec -it [container ID] bin/magento

# Run Magento CLI in detached mode
docker exec -it -d [container ID] bin/magento
```

## Image & system cleanup

```bah
# Remove unused images
docker image prune

# Remove all unused images (including dangling)
docker image prune -a
```

## Docker compose

```bash
# Run a one-time command in a service container
docker-compose run --rm cli

# Run MySQL CLI in the 'db' service container
docker-compose exec db sh -c 'mysql -u magento2 -pmagento2 magento2 "$@"'
```

## PHPStan example

```bash
docker run --rm -v $PWD:/code domw/phpstan phpstan analyze --level 0
```

## See also

- [Official Docker CLI Reference](https://docs.docker.com/engine/reference/commandline/docker/)
- [Docker Compose CLI](https://docs.docker.com/compose/reference/)

---

## Contributing

Feel free to fork this repo, submit pull requests, or open issues.
Suggestions, improvements, and corrections are always welcome!