# docker-compose-kitchen
docker-compose-kitchen


- [commands]()

## gcp

### treafik
- [task-001: To implement traefik letsEncrypt TLS challenge](gcp/task-001-traefik-letsEncrypt-tls-challenge)
- [task-002: To implement traefik letsEncrypt HTTP challenge](gcp/task-002-traefik-letsEncrypt-http-challenge)

### datadog
- [task-003: To implement datadog docker-compose example](gcp/task-003-datadog)

## local

### elastic-search
- [task-004: To implement elasticsearch backup & restore on local with sample data](local-mac/task-004-elastic-search-backup-restore-local-with-sample-data)
- [task-005: To implement elastic-search and kibana using single docker-compose](local-mac/task-005-elastic-search-kibana)
- [task-006: To implement logstash docker-compose example](local-mac/task-006-logstash)
- [task-008: To get monitoring dashboard for mongodb using mongodb, metricbeat (custom image), elasticsearch, kibana docker-compose](local-mac/task-008-mongodb-metricbeat-elasticsearch-kibana)
- [task-009: To get monitoring dashboard for NATS-Streaming using NATS-Streaming, metricbeat (custom image), elasticsearch, kibana docker-compose](local-mac/task-009-natsStreaming-metricbeat-elasticsearch-kibana)
- [task-010: To get monitoring dashboard for MYSQL using MYSQL, metricbeat (custom image), elasticsearch, kibana docker-compose](local-mac/task-010-mysql-metricbeat-elasticsearch-kibana)


### Prometheus
- [task-007: To send alerts to slack using prometheus, blackboxexporter, alertmanager docker-compose](local-mac/task-007-prometheus-blackboxexporter-alertmanager)


### Nginx

- [task-011: To test whether the certs (*.domain.com) are valid by using nginx](gcp/task-011-nginx-https-domain-test)


### Caddy
- [task-012: To test whether the certs (*.domain.com) are valid by using caddy](local-mac/task-012-caddy-https-domain-test-with-custom-certs)
- [task-013: To download certs for *.domain.com using caddy and https-acme and save those certs on host](local-mac/task-013-caddy-https-acme-and-save-certs)
- [task-014: To reverse-proxy nginx-home using caddy](local-mac/task-014-reverse-proxy-nginx-home-using-caddy)


### Basics
- [task-015: To set the memory and cpu limit used by contianer](local-mac/task-015-mem-and-cpu-limit-nginx-container)