# ESnet 

## Data collection
    
Thanks to Jon Dugan we can collect data from ESnet [REST interface](https://my.es.net/graphql_token) and send it to ES at UChicago. 
Collector is in [GitHub repo](https://github.com/ATLAS-Analytics/esnet) while a docker container is auto-built in dockerHub: __atlasanalyticsservice/esnet__.
    
Currently the collector runs at es-docker.mwt2.org but will be moved to a kubernetes cluster at MWT2 as soon as we have it.

## Data analysis

We still did not start analyzing this data. Once we do, it will be done using tools and services of docker container:        __opensciencegrid/network_analytics__ 