# PerfSONAR 

## Data collection
    
Perfsonar data gets sent to Nebraska RabbitMQ. From there it gets sent to Fermilab for storage on tape, to ES at UChicago and to ES at Nebraska. 

Collectors are in a docker container auto-built in dockerHub:              __ivukotic/perfsonar_collectors__
    
## Data analysis

There is a whole docker container with a number of tools and services:          opensciencegrid/network_analytics 

It has apache web server, neo4j server, jupyter lab server. All of it is easily deployable on a k8s cluster.
    