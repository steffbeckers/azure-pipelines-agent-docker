# Azure Pipelines Agent (Docker)

https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/docker?view=azure-devops#linux

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
docker run -d --name=azure-pipelines-agent --restart=always -e AZP_URL=https://dev.azure.com/steffbeckers -e AZP_TOKEN=<PAT token> -e AZP_AGENT_NAME=DESKTOP-STEFF registry.steffbeckers.eu/azure-pipelines-agent
```

OR

```
docker-compose pull
docker-compose up -d
```

