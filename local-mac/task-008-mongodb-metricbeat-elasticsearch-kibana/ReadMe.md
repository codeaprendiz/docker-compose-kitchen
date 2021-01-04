## Objective
- To create MongoDB dashboard on kibana by sending metrics of mongodb to elasticsearch using metricbeat.
- All mongodb, metricbeat, elasticsearch, kibana all should be deployed locally.

```bash
$ docker-compose up
.
Successfully built 74bc3e9797e1
Successfully tagged task-008-mongodb-metricbeat-elasticsearch-kibana_metricbeat:latest
WARNING: Image for service metricbeat was built because it did not already exist. To rebuild this image you must use `docker-compose build` or `docker-compose up --build`.
Creating es01               ... done
Creating metricbeat-mongodb             ... done
Creating metricbeat-metricbeat-services ... done
Creating kibana-sandbox                 ... done
Attaching to es01, metricbeat-mongodb, metricbeat-metricbeat-services, kibana-sandbox
.
metricbeat-metricbeat-services |    --> Waiting for elasticsearch_service:9200
.
metricbeat-metricbeat-services |    --> Waiting for kibana:5601
.
metricbeat-mongodb       | {"t":{"$date":"2020-08-16T18:37:05.226+00:00"},"s":"I",  "c":"NETWORK",  "id":22944,   "ctx":"conn34","msg":"connection ended","attr":{"remote":"192.168.160.4:33458","connectionCount":0}}
.
.
```


- MongoDB Dashboard

![](https://github.com/codeaprendiz/_assets/blob/master/metricbeat-dashboards/mongodb_local.png)

