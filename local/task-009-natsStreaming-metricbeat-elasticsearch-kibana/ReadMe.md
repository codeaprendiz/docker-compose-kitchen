### Objective : 

To get NATS-Streaming Dashboard on Kibana using NATS-Streaming, Elasticsearch, Kibana, Metricbeat (custom image) in docker-compose

```bash
$ doker-compose up
Creating network "task-009-natsstreaming-metricbeat-elasticsearch-kibana_host" with the default driver
Creating volume "task-009-natsstreaming-metricbeat-elasticsearch-kibana_data" with local driver
Building metricbeat
Step 1/10 : FROM docker.elastic.co/beats/metricbeat:7.8.1
.
.
Creating es01                                                                      ... done
Creating task-009-natsstreaming-metricbeat-elasticsearch-kibana_nats-streaming-1_1 ... done
Creating metricbeat-metricbeat-services                                            ... done
Creating kibana-sandbox                                                            ... done
Attaching to es01, task-009-natsstreaming-metricbeat-elasticsearch-kibana_nats-streaming-1_1, metricbeat-metricbeat-services, kibana-sandbox
```

- Dashboard images

![](https://github.com/codeaprendiz/_assets/blob/master/metricbeat-dashboards/nats_streaming_local_part1.png)

![](https://github.com/codeaprendiz/_assets/blob/master/metricbeat-dashboards/nats_streaming_local_part2.png)


