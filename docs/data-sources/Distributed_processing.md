### Distributed processing

All the code collecting and analyzing these datasets is in github repository: [ATLAS-Analytics/DistributedProcessing](https://github.com/ATLAS-Analytics/DistributedProcessing). 

## Jobs

Jobs data are imported from OracleDB table __ATLAS_PANDA.JOBSARCHIVED4__ once per hour. First data is sqooped to hdfs, then preprocessed and sent to UC Elasticsearch index.  

### Enrichments

#### Parent-child relationship
When a job needs to be restarted for whatever reason, it gets a new pandaID. It can actually be restarted at more than one place. Information on parent/child relationship between jobs is stored in OracleDB table __ATLAS_PANDA.JEDI_JOB_RETRY_HISTORY__. A sqoop job gets this info to HDFS from where a pyton codes reads it and uses it to update values in ES at UC.
_At the moment code doing indexing is [here](https://gitlab.cern.ch/fhoenig/pandajobstates)_.

#### Job status
Every time job changes a state (defined [here](https://twiki.cern.ch/twiki/bin/view/PanDA/PandaShiftGuide#Job_state_definitions_in_Panda) ) one row is added to __ATLAS_PANDA.JOBS_STATUSLOG__ table with the new state and timestamp.
This information is collected by a sqoop script, and saved in hdfs. Another pig script will read it from there, calculate time job spent in any of the states and add these times to jobs archive UC Elasticsearch indices. Variables are:


## Tasks
Tasks data are imported once per hour from __ATLAS_PANDA.JEDI_TASKS__ Oracle table. 

### Enrichments

#### Output formats
In order to understand what are perfromance characheristics of different derivation productions we need to addi output formats to the tasks. K8s cron job runs sqoop to get data from __ATLAS_DEFT.T_PRODUCTION_TASK__ and updates task table.