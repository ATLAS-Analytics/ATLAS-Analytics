# Accounting

## Jobs


## CPU


## Network

## Storage
 Rucio make daily dumps of their main DB table containing all the datasets at all sites.  This data is in HDFS and is indexed at ES at UChicago. The raw data is kept for x days, while aggregated data is kept indefinitely. It must be kept in mind that the raw data repeats from day to day so while making time averages is OK, making sums over more than one day have no sense. 
 Most important metrices are shown in this [dashboard](). 
  * Total storage per site in time
  * Percentage of storage in space tokens per site. Percentage of storage in space tokens in time.
  * Space occupied by different data formats, different tags.