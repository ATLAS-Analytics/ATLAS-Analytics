### Distributed processing

## Jobs

### Enrichments

#### Parent-child relationship
When a job needs to be restarted for whatever reason, it gets a new pandaID. It can actually be restarted at more than one place. Information on parent/child relationship between jobs is stored in OracleDN table __this__. A sqoop job gets this info to HDFS from where a pyton codes reads it and uses it to update values in ES at UC.

#### Job status
Every time job changes a state (defined [here](panda job state page) ) one row is added to panda_job_status table with the new state and timestamp.
This information is collected by a sqoop script, and saved in hdfs. Another pig script will read it from there, calculate time job spent in any of the states and add these times to jobs archive UC Elasticsearch indices. Variables are:


## Tasks


### Enrichments