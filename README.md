# ELK Stack for macOS Cybersecurity Telemetry

This project provides a complete ELK (Elasticsearch, Logstash, Kibana) stack using Docker Compose. It is configured to ingest and visualize cybersecurity telemetry data from a macOS host via syslog.

This is a great way to get a development environment running quickly.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) must be installed and running on your system.
- [Docker Compose](https://docs.docker.com/compose/install/) must be installed. (It is included with Docker Desktop).

## 1. Start the ELK Stack

To start the entire ELK stack, run the following command from your project directory:

```sh
docker compose up -d
```

### 2. Run the script

```sh
./run-elasticsearch.sh
```

This will pull the Elasticsearch image (if you don't have it) and start a container named `es01` in detached mode.

## Verifying the Setup

Once the container is running, you can verify that Elasticsearch is up by sending a request to its REST API. It might take a minute for the service to fully initialize.

```sh
curl -X GET "localhost:9200"
```

You should see a JSON response similar to this, confirming that your node is running:

```json
{
  "name": "es01",
  "cluster_name": "docker-cluster",
  "cluster_uuid": "...",
  "version": {
    "number": "9.1.3",
    "build_flavor": "default",
    "build_type": "docker",
    "build_hash": "...",
    "build_date": "...",
    "build_snapshot": false,
    "lucene_version": "10.2.2",
    "minimum_wire_compatibility_version": "8.19.0",
    "minimum_index_compatibility_version": "8.0.0"
  },
  "tagline": "You Know, for Search"
}
```

## Managing the Container

- **To see the logs:**

  ```sh
  docker logs -f es01
  ```

- **To stop the container:**

  ```sh
  docker stop es01
  ```

- **To start the container again:**

  ```sh
  docker start es01
  ```

- **To remove the container (this will delete any data inside it):**
  ```sh
  docker rm es01
  ```
