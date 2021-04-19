# Azure Pipelines Agent (Docker)

https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/docker?view=azure-devops#linux

## Caution

Using Docker within a Docker container
In order to use Docker from within a Docker container, you bind-mount the Docker socket.

Doing this has serious security implications. The code inside the container can now run as root on your Docker host.

## Build and push image

```
docker build -t registry.steffbeckers.eu/azure-pipelines-agent .
docker push registry.steffbeckers.eu/azure-pipelines-agent
```

OR

```
docker-compose -f docker-compose.build.yml build
docker-compose -f docker-compose.build.yml push
```

## Run the agent on a linux docker host

```
docker pull registry.steffbeckers.eu/azure-pipelines-agent
docker run -d --name=azure-pipelines-agent --restart=always -e AZP_URL=https://dev.azure.com/steffbeckers -e AZP_TOKEN=<PAT token> -e AZP_AGENT_NAME=DESKTOP-STEFF -v /var/run/docker.sock:/var/run/docker.sock registry.steffbeckers.eu/azure-pipelines-agent
```

OR

```
docker-compose pull
docker-compose up -d
```
