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
docker logs -f <container_id>

# Show processes inside a container
docker top <container_id>

# Kill a running container
docker kill <container_id>

# Remove a container forcefully
docker rm -f <container_id>
```

## Stop & remove containers

```bash
# Stop all containers
docker stop $(docker ps -a -q)

# Remove all containers
docker rm -f $(docker ps -a -q)

# Stop a single container
docker container stop <container_id>

# Stop all containers (alternate syntax)
docker container stop $(docker container ls -aq)

# Remove a single container
docker container rm <container_id>

# Remove all containers
docker container rm $(docker container ls -aq)

# Stop all containers and prune everything (including volumes)
docker container stop $(docker container ls -aq) && docker system prune -af --volumes
```

## Execute commands inside containers

```bah
# Open a shell session inside a container
docker exec -it <container_id> sh

# Run Magento CLI inside a container
docker exec -it <container_id> bin/magento

# Run Magento CLI in detached mode
docker exec -d -it <container_id> bin/magento
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
# Start services in the foreground (builds if needed)
docker compose up

# Start services in detached/background mode
docker compose up -d

# Stop and remove containers, networks, and volumes
docker compose down

# Rebuild services
docker compose up --build

# Rebuild only a specific service
docker compose up --build <service_name>

# Stop services
docker compose stop

# Start stopped services
docker compose start

# View logs of all services
docker compose logs

# Follow logs (like `tail -f`)
docker compose logs -f

# Run a one-time command in a service container (without restarting everything)
docker compose run --rm <service_name> <command>

# Execute a command in a running service container
docker compose exec <service_name> <command>

# Example: Open a shell in the 'app' service
docker compose exec app sh

# Example: Run MySQL CLI inside the 'db' service
docker compose exec db sh -c 'mysql -u magento2 -pmagento2 magento2'
```

## Run a container (common example)

```bash
# Start an Nginx container on port 8080
docker run -d -p 8080:80 nginx
```

## See also

- [Official Docker CLI Reference](https://docs.docker.com/engine/reference/commandline/docker/)
- [Docker Compose CLI](https://docs.docker.com/compose/reference/)

---

## Contributing

Feel free to fork this repo, submit pull requests, or open issues.
Suggestions, improvements, and corrections are always welcome!