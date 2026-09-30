![n8n Banner](assets/n8n-banner.png)
# Getting Started
Clone the repository as usual.

## Getting Started with Docker
If you need to install Docker, here are two common options:

1. Download Docker Desktop and follow installation instructions (simplest) 
   This lets you easily manage images and containers through Docker Desktop's GUI.
2. Install Docker (engine and CLI) through the terminal and install the `Container Tools` extension in VS Code (or an equivalent extension in another code editor). This provides an interface for managing images and containers.

### Spin Up Docker Containers
The complete configuration is ready in `docker-compose.yml`.

Change to the project root and run:
```
docker compose up -d
```
Note: You will need to configure credentials, such as the Discord webhook and Finnhub API key, in the n8n app.

### Import Workflows
```
docker compose exec n8n n8n import:workflow --separate --input=/workflows
```

### Export Workflows
If you are using n8n without a paid subscription, GUI export is disabled. You can export workflows through the terminal instead.

Run each command individually:
```
docker exec <n8n-CONTAINER-NAME> n8n export:workflow --backup --output=/tmp/workflows/

docker cp <n8n-CONTAINER-NAME>:/tmp/workflows/. <PATH/TO/WORKFLOWS/FOLDER>

ls <PATH/TO/WORKFLOWS/FOLDER>
```
The last command confirms that the files were copied to the workflows folder.

## Demo Workflows
### Scheduled API Call Example
Pulling opening and closing data for an AI stocks watchlist at market close, then sending the results to Discord.

![AI stocks automation result](assets/ai-stocks-automation.png)
*Final result.*

![Finnhub-to-Discord workflow](assets/n8n-finnhub-discord.png)
*Screenshot of the node and edge configuration.*

### Scheduled RSS Feed Example
![PubMed RSS-to-Discord workflow](assets/n8n-pubmedRSS-discord.png)
*Screenshot of the node and edge configuration.*