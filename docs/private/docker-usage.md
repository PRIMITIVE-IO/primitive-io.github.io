# Running Scraper in Docker Container

The private scraper is best run inside of Docker. This allows for consistency across platforms and removes potential dependency issues when deploying across different platforms.

# Required Configuration

The private scraper relies on two main elements to run properly: a location to store the internal database and an environment file.
- See information related to environment file [here](/docs/private/environment-file.md)
- See information for required volume [here](/docs/private/volume.md)

# Importing Image from Archive

Docker images can be saved and archived for easier transport. The scraper image can be distributed via a ".tar" file rather than pulled from a registry.

```
docker load --input primitive_scraper.tar
```

Once loaded, the image should be viewable with 'docker images.' Once imported with the load command, the container can be run as outlined in following sections.

# Running Container

Once the scraper container is pulled and available to the local machine, the container can be ran. Below is an example of the command required for the scraper to execute properly.

```
docker run -d -p 3000:3000 --env-file="env.file" -v /tmp/primitive/data:/srv/primitive/data --name primitive_2.0 primitive:latest
```

Important information:
- For versions under v4.0, ports should remain 3000:3000 so the admin panel can comunicate with the scraper.
- The volume information follows the format "local:container." This means that the first path should exist on the local machine.
- The volume is used to persist data and the database. Choose a non-temporary directory.

See below for additional explaination of command flags and options:
- **'-d'** - Run the process as a daemon. Without this command, the container will execute and bind to the console. This can be removed for testing if something is failing with the run command.
- **'-p'** - Publish or expose a specific port.
- **--env-file** - This is an important one. This injects the variables found in the env file into the environment within the container. This will include environment specific information and git service credentials.
- **-v** - Mount a volume to the container. Because the scraper pulls data from your git service and saves assets to be served to the Primitive client, data persistence is important. In the example above, we are mounting a local directory (/tmp/primitive/data) to a folder inside the container(/srv/primitive/data). By doing this, the database and scraped assets will be stored outside the container and available on the local machine. Make sure that the local directory is present when running the container.
- **-name** - This will be the name of the running container. It is best to name this something that represents the function and includes the versioning.
- The last value is the image name. This will be the name of the image pulled from the registry and include the specific version being used (the example shows :latest but this may very well me a specific version.)

<em> ** NOTE: Due to the websocket calls from the admin panel, port 3000 should be used for versions below 4.0 ** </em>

# Monitoring Containers

To see what container are running or available, run docker ps. The '-a' flag can be used to show all containers and not just running ones. If a container crashes, you will have to use the '-a' flag to view it.

```
docker ps
docker ps -a
```

# Stopping Container

Stopping a container can be done through the 'docker stop' command. The container name can be found through the 'docker ps' command.

```
docker stop primitive_2.0
```

# Starting Container

Starting a container can be done through the 'docker start' command. The container name can be found through the 'docker ps' command.

```
docker start primitive_2.0
```

# Updating Container

Updating the scraper consists of stopping the current container, pulling a new version, and running the new one. Stopped containers can be maintained in case there were bugs introduced in the updates. For example:

```
docker stop primitive_1.0
docker pull <new container name>
docker run <new container name>
```

If older version of the container are no longer needed, they can be deleted.

```
docker rm primitive_1.0
```

Old images can also be viewed and removed through the 'docker image' command.

```
docker image ls
docker image rm primitive_1.0
```

# Accessing Running Process

Once the container is running you can see it with the 'docker ps' command. To access the internal process, the 'exec' command can be used.

```
docker exec -it primitive_1.0 /bin/bash
```

This binds to the container primitive_1.0 and binds to an interactive bash shell giving the ability to troubleshoot and monitor the process. Within the container, we are running PM2 (a daemon process manager for Node.js). To see running logs and the process dashboard, use the following commands.

```
pm2 logs
pm2 monit
```