# Site administration

## Jobs
There are around 100 different metrics we collect on all jobs. There are thousands of ways to filter and visualize them but for site admins we prepared one [dashboard]() with the most important information:

 * number of jobs in time, split by status. Look for total number of jobs, a lot of failed, canceled jobs
 * fraction of different kinds of jobs (production, analysis, ...). This is important to know as they exhibit different stresses on the site, have different efficiencies, IO requirements.
 * wall time delivered, cpu efficiency
 * number of errors per node. Nodes with high percentage of failed jobs may need to be taken offline and cause investigated. 

Keep in mind that this dashboard contains only information on finished jobs. For not yet finished jobs one need to look [here]().
To make it show only information from one sites add a line like this to the search bar: ```sitnamee:MWT2```.
We suggest to try grouping nodes (based on CPU, storage, or network connectivity) and compare their performance.

## Jobs IO
Site movers collect information on all the input/output data transfers from the job. This data gets collected and indexed in ES at both CERN and UChicago. The data contains information on all the files that job accessesed or wrote, file sizes, rates, and a lot of metadata (filenames,workernode, etc.). Sites can use this data to:
 
   * spot problematics WN (full or failed scratch disk, connection issue, missconfiguration)
   * spot LAN issues (bad links, congested switches, ...)
   * optimize access type (copy-to-scratch vs. direct access)
   * make purchasing decissions (switches, NICs, disks) 

Starting point should be this [Kibana dashboard](http://atlas-kibana.mwt2.org:5601/app/kibana#/dashboard/bc828870-f566-11e7-8f2f-ab6704660c79). To make it show only information from one sites add a line like this to the search bar:
   ```sitnamee:MWT2```. First one would look at the visualization named __errors__. Nodes with more than a few errors most probably need a deep inspection. 
   
For a deeper investigation we suggest looking separately at WNs connected to the same switch. This is easiest done by making a search like this: ```sitename:MWT2 and hostname:uct2*```. Big difference in performance can point to a problem with a switch WNs are connected to, or link from that switch to the storage. Feel free to make a special visualization that splits all your WNs in groups, save it (please prepend name of your site to names of your visualizations) so you don't have to redo it every day. You can also save a copy of the dashboard and customize it to your liking. 

## Wide Area Network issues
It is very important to quickly spot WAN connectivity issues. There are two easy ways to do it: 

   * Subscribe to an alert on network issues for your site. This check is described [HERE](alarms_and_alerts/#network-issues) and will alert you to low level problems (broken or saturated link, high packet loss, unstable path)
   * Look at the FTS queues for your site. Long queues can point to bad settings in your FTS server, unusual Rucio requests, etc. Starting point for this kind of investigation is the [FTS queues]() kibana page. Simply search for all transfers where your site is a source and then where your site is a destination (eg. ```src_site:MWT2``` or ```dest_site:MWT2```). While a few files waiting in a queue for a few hours is not of big concern, a lot of transfers waiting for a long time (agreagate waiting time in years) is of concern.