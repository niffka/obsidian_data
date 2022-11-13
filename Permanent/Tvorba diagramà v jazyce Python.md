---
#aliases: [Tvorba diagramů v jazyce Python]
tags: [Honza]
created: 2022-03-02
---

# Tvorba diagramů v jazyce Python
Knihovna [Diagrams](https://github.com/mingrammer/diagrams) pro Python umožňuje generovat digramy cloudové infrastruktury v pythonu.

## AWS nasazení
```python
from diagrams import Cluster, Diagram
from diagrams.aws.compute import ECS
from diagrams.aws.database import ElastiCache, RDS
from diagrams.aws.network import ELB
from diagrams.aws.network import Route53

with Diagram("Clustered Web Services", show=False):
	dns = Route53("dns")
	db = ELB("lb")
	with Cluster("Services"):
		svc_group = [ECS("web1"),
		ECS("web2"),
		ECS("web3")]
	
	with Cluster("DB Cluster"):
		db_primary = RDS("userdb")
		db_primary - [RDS("userdb ro")]
	
	memcached = ElastiCache("memcached")
	
	dns >> lb >> svc_group
	svc_group >> db_primary
	svc_group >> memcached
```

![aws.py](https://miro.medium.com/max/700/0*wJwKnJR3iEbXahYz.png)

## GCL
```python
from diagrams import Cluster, Diagram
from diagrams.gcp.analytics import BigQuery, Dataflow, PubSub
from diagrams.gcp.compute import AppEngine, Functions
from diagrams.gcp.database import BigTable
from diagrams.gcp.iot import IotCore
from diagrams.gcp.storage import GCS

with Diagram("Message Collecting", show=False):
    pubsub = PubSub("pubsub")

    with Cluster("Source of Data"):
        [IotCore("core1"),
         IotCore("core2"),
         IotCore("core3")] >> pubsub

    with Cluster("Targets"):
        with Cluster("Data Flow"):
            flow = Dataflow("data flow")

        with Cluster("Data Lake"):
            flow >> [BigQuery("bq"),
                     GCS("storage")]

        with Cluster("Event Driven"):
            with Cluster("Processing"):
                flow >> AppEngine("engine") >> BigTable("bigtable")

            with Cluster("Serverless"):
                flow >> Functions("func") >> AppEngine("appengine")

    pubsub >> flow
```

![gcp.py](https://miro.medium.com/max/700/0*CAxTHV_KtAID-pD_.png)
## On-Prem
```python
from diagrams import Cluster, Diagram
from diagrams.onprem.analytics import Spark
from diagrams.onprem.compute import Server
from diagrams.onprem.database import PostgreSQL
from diagrams.onprem.inmemory import Redis
from diagrams.onprem.aggregator import Fluentd
from diagrams.onprem.monitoring import Grafana, Prometheus
from diagrams.onprem.network import Nginx
from diagrams.onprem.queue import Kafka

with Diagram("Advanced Web Service with On-Premise", show=False):
    ingress = Nginx("ingress")

    metrics = Prometheus("metric")
    metrics << Grafana("monitoring")

    with Cluster("Service Cluster"):
        grpcsvc = [
            Server("grpc1"),
            Server("grpc2"),
            Server("grpc3")]

    with Cluster("Sessions HA")
        primary = Redis("session")
        primary - Redis("replica") << metrics
        grpcsvc >> primary

    with Cluster("Database HA"):
        primary = PostgreSQL("users")
        primary - PostgreSQL("replica") << metrics
        grpcsvc >> primary

    aggregator = Fluentd("logging")
    aggregator >> Kafka("stream") >> Spark("analytics")

    ingress >> grpcsvc >> aggregator
```

![](https://miro.medium.com/max/700/0*7TmpEfJHfgXpQcDd.png)
## Kubernetes
```python
from diagrams import Diagram
from diagrams.k8s.clusterconfig import HPA
from diagrams.k8s.compute import Deployment, Pod, ReplicaSet
from diagrams.k8s.network import Ingress, Service

with Diagram("Exposed Pod with 3 Replicas", show=False):
    net = Ingress("domain.com") >> Service("svc")
    net >> [Pod("pod1"),
            Pod("pod2"),
            Pod("pod3")] << ReplicaSet("rs") << Deployment("dp") << HPA("hpa")
```

![](https://miro.medium.com/max/700/0*cguyw_ds751E9jzV.png)
## Další knihovny
Článek pak ukazuje další možnosti pro
- [[JavaScript]] : [Mermaid](https://mermaid-js.github.io/mermaid/#/README)
- [[PlantUML]]: [PlantUML](https://plantuml.com/) a jeho nadstavbu [C4-PlantUML](https://c4model.com/)


---
- [[Python]],[[Generování diagramů]]

# Reference
1. https://alpha2phi.medium.com/code-based-diagramming-6b1bcc732aab