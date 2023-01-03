# Apache Airflow dockerized guide
### *Works better with MacOS*


## _1.The docker-compose File:_
- make a local DIR as you wish
- and then curl this :

```sh
curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.3.0/docker-compose.yaml'
```


> Feel free to inspect the compose file and the services defined in it namely _airflow-scheduler_, _airflow-webserver_, _airflow-worker_, _airflow-init_, _flower_, _postgres_ and _redis_.




## _2.Setting the Airflow user:_



```sh
echo -e "AIRFLOW_UID=$(id -u)\nAIRFLOW_GID=0" > .env
```


>Inspect the content of ```.env``` using ```cat``` and ensure that it contains the two aforementioned variables:


```
cat .env
AIRFLOW_UID=501
AIRFLOW_GID=0
```

#### _3.Initialise the Airflow Database:_

> Now we initialise the Airflow Database by first starting this container:

```
docker-compose up airflow-init
```
##### when finished we have our airflow user with this credential:


| User | Password |
| ------ | ------ |
| airflow | airflow |

#### _4.Getting the service UP:_
- Now we can easily use the docker-compose file:
```
docker-compose up -d 
```

> In order to access Airflow User Interface simply head to your preferred browser and open:

[localhost:8080](localhost:8080)
