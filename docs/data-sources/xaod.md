# xAOD monitoring
 
Code that is needed in order to access xAOD data has been instrumented (WHERE???) so it collects information on containers and branches accessed by the user.

This data is reported to a RUCIO appache server that stores it in HDFS. (Who takes care of this??? Where is it documented???)

Once a day information from HDFS is processed using a pig script and a python code and sent to Elasticsearch cluster at UChicago. This code can be found in [GitHub](https://github.com/ATLAS-Analytics/xAOD-analytics.git).


## HDFS @CERN

Data is in: ```hdfs://analytix//user/rucio01/nongrid_traces/$INPD.json```

## Elasticsearch at UChicago  

Data is stored in two indices:

*   information per job.  Index is named: *xaod_accesses*  Template is [here](xaod_resources/xaod_job_accesses.template). Data is produced and indexed directly by the pig script. 

*   container or branch access. Index is named: *xaod_job_accesses*  Template is [here](xaod_resources/xaod_accesses.template).

### Dashboards

## Analysis
 Here links to relevant Jupyter notebooks.1