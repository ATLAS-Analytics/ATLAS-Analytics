#Elasticsearch

## UChicago
### Infrastructure

* 5 data nodes, 3 service nodes (3 masters, 2 kibana), 15 TB of SSDs. Will be expanded to:...
* backup: each Sunday all data is incrementally backed up.

### Kibana
*   Production

[Production version](atlas-kibana.mwt2.org) is fully open but only for read access. Searches, visualization, dashboards can be created but can not be saved. To add something to it one has to create it first in the development and ask Ilija to copy it over to the production Kibana.

*   Development
[Development version](atlas-kibana-dev.mwt2.org) is read/write capable but sits behind a apache proxy, if you need a password ask Ilija Vukotic.

## IT-ES

## Monit