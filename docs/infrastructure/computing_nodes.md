#Old infrastructure

## Nodes

### aianalytics nodes
  
  OpenStack environment variables set for Project = 'ATLAS Services Analytics'

Node | Location
-----|-------
aianalytics01 | cern-geneva-b 
aianalytics03 | cern-geneva-b
aianalytics10 | cern-geneva-a  
aianalytics12 | cern-wigner-a 
aianalytics13 | cern-wigner-a 
aianalytics14 | cern-geneva-c 
aianalytics15 | cern-geneva-c 
aianalytics16 | cern-geneva-a 

aiatlas013 | cern-wigner-b 
aiatlas025 | cern-wigner-b 

* aiatlas114.cern.ch

## Accounts
  adcmusr3 is a fax monitoring account running things on aiatlas114.cern.ch
  aflume - service account 
  
# New infrastructure

The new infrastructure is based on OpenStack project "ATLAS AnalyticsSvc". It has five m2.medium nodes.

## Kubernetes cluster
All the nodes are under "analytics" kubernetes cluster based on kubernetes-preview template. One node is a master and 4 nodes are minions. 
The cluster is monitored using Heapster which sends data to ES at UC. Dashboard showing its data is [here](http://atlas-kibana-dev.mwt2.org/goto/979a26298cd18d1230220f93b7c58bb3). 


## Using your private kubernetes cluster for analytics
While there is not much documentation the procedure is straightforward. Here the basics:

* Getting your OpenStack resources
https://openstack.cern.ch/
* Seting up kubernetes cluster
* Installing kubectl and basic commands
* Using Analytics container 
  
 
## Accounts

Name | Login | Email 
----|----|----
ATLAS analytics service | analyticssvc | analytics.service@cern.ch 
ATLAS analytics  | analytics | atlas.analytics@cern.ch


# SERVICES

To be moved from the old infrastructure
* FTS - old one to be removed (acrontab)
* PerfSONAR - old ones running on aianalytics10.

Already running on new infrastructure:
* BOINC, BOINC-dev
* Job, Task, Enrichment collectors
* FTS
* DDM accounting
* xAOD