# CPU benchmarks

For 1% of grid jobs pilot in parallel to fetching input data, runs three different benchmarks. These are:
 * fastBMK
 * 
 * 
It also collects data on node:

* CPU type
* is it VM
* is it hyperthreaded
* 

All the info gets sent to a logstash instance running at uct2-collectd.mwt2.org and from there to ES.
