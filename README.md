# Sylv
### Purpose
A (very) simple ELK stack with elasticsearch, kibana and filebeat.
The goal is to collect all access logs from the nginx container.
### To run it
```
docker-compose up -d
```
### Make sure that all containers are running with
```
docker ps
```
Sometime filebeat, can't start if all other containers (like elasticsearch are not already running) 
To make sure that filebeat is running just do
```
docker-compose start filebeat
```
After all that do another docker ps and see if all containers are running:
* nginx
* elasticsearch
* kibana
* filebeat
### Start to see logs
Now that all containers are running go to [http://localhost:8080](http://localhost:8080)
From now, you can see some logs that have been written in the nginx log directory.
So you can go to Kibana with [http://localhost:5601](http://localhost:5601)
### Check that the filebeat index exist
We have to check if the filebeat index exist, go to [http://localhost:9200/_cat/indices?v](http://localhost:9200/_cat/indices?v)
A filebeat index must be in the list, if it's not the case just go to the nginx localhost, and refresh the page
### 
The final step is now to manage the new index in elasticsearch. Go to kibana. In the left panel, click on the gear wheel icon
(the last one from bottom, "managment"). Click on Index Management in the ElasticSearch list. Choose the new index filebeat
(or search it filebeat-*) and create it.
Now that you have your index, you can explore your data in Kibana.