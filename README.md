# easy-docker-compose

> Ready-to-use Docker Compose templates for 31+ services — spin up any stack in seconds.

No configuration headaches. Just `cd` into the folder you need and run `docker-compose up`.

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
| CockroachDB | [`cockroachDB/`](./cockroachDB) | 26257 |
| Elasticsearch | [`elasticsearch/`](./elasticsearch) | 9200 |
| SQL Server | [`sqlserver/`](./sqlserver) | 1433 |
| Oracle | [`oracle/`](./oracle) | 1521 |
| Memcached | [`memcached/`](./memcached) | 11211 |

### Message Brokers & Task Queues

| Service | Folder | Default Port |
|---|---|---|
| RabbitMQ | [`rabbitMQ/`](./rabbitMQ) | 5672 |
| Celery + Redis | [`celery/`](./celery) | — |

### Web Servers & Proxies

| Service | Folder | Default Port |
|---|---|---|
| Nginx | [`nginx/`](./nginx) | 80 |
| Apache HTTPD | [`apacheHttpd/`](./apacheHttpd) | 80 |

### Monitoring & Observability

| Service | Folder | Default Port |
|---|---|---|
| Grafana | [`grafana/`](./grafana) | 3000 |
| Prometheus | [`prometheus/`](./prometheus) | 9090 |
| Graylog | [`graylog/`](./graylog) | 9000 |

### Auth & Orchestration

| Service | Folder | Default Port |
|---|---|---|
| Keycloak (+ Postgres) | [`keycloak/`](./keycloak) | 9080 |
| Apache Airflow | [`airflow/`](./airflow) | 8080 |

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
| CentOS | [`centos/`](./centos) |
| BusyBox | [`busyBox/`](./busyBox) |
| Hello World | [`helloWorld/`](./helloWorld) |

---

## Environment Variables

Each `docker-compose.yaml` comes with sensible defaults so it works out of the box. For production use, override credentials via a `.env` file in the service folder:

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
