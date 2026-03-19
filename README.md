# easy-docker-compose

> Ready-to-use Docker Compose templates for 51 services — spin up any stack in seconds.

All templates are tested and work on both **Intel** and **Apple Silicon (M1/M2/M3)** Macs, as well as Linux.

---

## Quick Start

```bash
git clone https://github.com/mohitsarewar/easy-docker-compose.git
cd easy-docker-compose/<service>
docker-compose up -d
```

To stop:

```bash
docker-compose down
```

---

## Services

### Databases

| Service | Folder | Default Port |
|---|---|---|
| PostgreSQL | [`postgres/`](./postgres) | 5432 |
| MySQL | [`mysql/`](./mysql) | 3306 |
| MariaDB | [`mariaDB/`](./mariaDB) | 3306 |
| MongoDB | [`mongoDB/`](./mongoDB) | 27017 |
| Redis | [`redis/`](./redis) | 6379 |
| Cassandra | [`cassandra/`](./cassandra) | 9042 |
| CockroachDB | [`cockroachDB/`](./cockroachDB) | 26257 · UI: 8080 |
| Elasticsearch | [`elasticsearch/`](./elasticsearch) | 9200 |
| SQL Server 2022 | [`sqlserver/`](./sqlserver) | 1433 |
| Oracle XE 21c | [`oracle/`](./oracle) | 1521 |
| Memcached | [`memcached/`](./memcached) | 11211 |
| Neo4j | [`neo4j/`](./neo4j) | 7474 (UI) · 7687 |
| InfluxDB | [`influxdb/`](./influxdb) | 8086 |
| ClickHouse | [`clickhouse/`](./clickhouse) | 8123 · 9000 |

### Message Brokers & Task Queues

| Service | Folder | Default Port |
|---|---|---|
| RabbitMQ (+ Management UI) | [`rabbitMQ/`](./rabbitMQ) | 5672 · UI: 15672 |
| Apache Kafka (KRaft) | [`kafka/`](./kafka) | 9092 |
| ZooKeeper | [`zookeeper/`](./zookeeper) | 2181 |
| Celery + Redis | [`celery/`](./celery) | — |

### Web Servers & Proxies

| Service | Folder | Default Port |
|---|---|---|
| Nginx | [`nginx/`](./nginx) | 80 |
| Apache HTTPD | [`apacheHttpd/`](./apacheHttpd) | 80 |
| Traefik | [`traefik/`](./traefik) | 80 · Dashboard: 8080 |

### Monitoring & Observability

| Service | Folder | Default Port |
|---|---|---|
| Grafana | [`grafana/`](./grafana) | 3000 |
| Prometheus | [`prometheus/`](./prometheus) | 9090 |
| Graylog (+ MongoDB + ES) | [`graylog/`](./graylog) | 9000 |
| Jaeger | [`jaeger/`](./jaeger) | UI: 16686 |
| Zipkin | [`zipkin/`](./zipkin) | 9411 |

### Auth, Secrets & Service Mesh

| Service | Folder | Default Port |
|---|---|---|
| Keycloak 24 (+ Postgres) | [`keycloak/`](./keycloak) | 9080 |
| HashiCorp Vault | [`vault/`](./vault) | 8200 |
| HashiCorp Consul | [`consul/`](./consul) | 8500 |

### Storage & Object Store

| Service | Folder | Default Port |
|---|---|---|
| MinIO (S3-compatible) | [`minio/`](./minio) | API: 9000 · UI: 9001 |
| Nextcloud (+ MariaDB) | [`nextcloud/`](./nextcloud) | 8080 |

### CI/CD & Dev Tools

| Service | Folder | Default Port |
|---|---|---|
| Jenkins | [`jenkins/`](./jenkins) | 8080 |
| SonarQube (+ Postgres) | [`sonarqube/`](./sonarqube) | 9000 |
| Gitea | [`gitea/`](./gitea) | 3000 |
| LocalStack (AWS locally) | [`localstack/`](./localstack) | 4566 |
| Portainer | [`portainer/`](./portainer) | 9443 |

### Orchestration & Data Engineering

| Service | Folder | Default Port |
|---|---|---|
| Apache Airflow | [`airflow/`](./airflow) | 8080 |
| Apache Superset (+ UI) | [`superset/`](./superset) | 8088 |

### Database Admin UIs

| Service | Folder | Default Port |
|---|---|---|
| pgAdmin 4 | [`pgadmin/`](./pgadmin) | 5050 |
| Adminer | [`adminer/`](./adminer) | 8080 |

### CMS & Apps

| Service | Folder | Default Port |
|---|---|---|
| WordPress (+ MySQL) | [`wordPress/`](./wordPress) | 80 |

### Base Images / Runtimes

| Service | Folder |
|---|---|
| Python | [`python/`](./python) |
| Node.js | [`node/`](./node) |
| Golang | [`golang/`](./golang) |
| PHP | [`php/`](./php) |
| OpenJDK | [`openJDK/`](./openJDK) |
| Alpine | [`alpine/`](./alpine) |
| Ubuntu | [`ubuntu/`](./ubuntu) |
| CentOS Stream 9 | [`centos/`](./centos) |
| BusyBox | [`busyBox/`](./busyBox) |
| Hello World | [`helloWorld/`](./helloWorld) |

---

## Apple Silicon (M1/M2/M3) Compatibility

All templates have been updated to use images with native ARM64 support:

| Service | Fix Applied |
|---|---|
| Oracle | Switched to `gvenzl/oracle-xe:21-slim-faststart` (free, ARM64-native) |
| SQL Server | Pinned to `2022-latest` — only version with ARM64 support |
| Keycloak | Migrated from `legacy` (x86-only) to `keycloak:24.0` with new start format |
| CentOS | Replaced EOL `centos:latest` with `centos:stream9` |
| Celery | Fixed broken `celery:latest` image (no such image) — uses `python:3.12-slim` |
| Elasticsearch | Added required `discovery.type: single-node` and `xpack.security.enabled: false` |
| Graylog | Added missing MongoDB + Elasticsearch dependencies |
| CockroachDB | Added required `start-single-node --insecure` command |
| Prometheus | Added missing compose file and `prometheus.yml` config |
| Airflow | Fixed volume path (`/opt/airflow`) and added `standalone` command |

---

## Environment Variables

Each `docker-compose.yaml` includes working defaults for local development. For production, override credentials via a `.env` file in the service folder:

```bash
# Example: postgres/.env
POSTGRES_USER=myuser
POSTGRES_PASSWORD=mysecretpassword
POSTGRES_DB=mydb
```

---

## Contributing

Contributions are welcome! To add a new service:

1. Fork the repo
2. Create a folder named after the service
3. Add a `docker-compose.yaml` with working defaults
4. Open a pull request

---

## License

MIT
