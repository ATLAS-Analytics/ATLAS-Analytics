#FTS

## DOCS

*   [Main google doc](http://bit.ly/2Fy6u3g)
*   [FTS3 configuration](http://fts3-docs.web.cern.ch/fts3-docs/docs/config/config.html)
*   [FTS3 Optimizer](http://fts-docs-devel.web.cern.ch/fts-docs-devel/docs/optimizer/optimizer.html)

## FTS servers

[Configurations per FTS Server](https://monit-kibana.cern.ch/app/kibana#/dashboard/_project-FTS-Servers-Configuration)

*   [CERN](https://fts3.cern.ch:8449/fts3/ftsmon/#/optimizer/?vo=&source_se=&dest_se=&time_window=1)
*   [BNL](https://fts.usatlas.bnl.gov:8449/fts3)
## Monitoring @CERN

Monit:

*   [Grafana](https://monit-grafana.cern.ch/dashboard/db/fts-transfers-30-days)
*   [Kibana](https://monit-kibana.cern.ch/app/kibana#/dashboard/MONIT-FTS-Overview)

## Monitoring @UC

Index pattern is __fts-2*__.

To check queue lenghts and average time in queue, check this dashboard:
http://atlas-kibana-dev.mwt2.org/goto/5132d543e93e074899b0b92aa3cf1265

To check number of active transfers per activity type and per link, use index pattern __links_traffic*__.


To check ingress, egress, numbers of incomming and outcoming transfers per site, use index pattern __sites_traffic*__
and this dashboard: http://atlas-kibana-dev.mwt2.org/goto/608b3f7a29b7b37afdd50a2c62fdd12c


### OLD DASHBOARDS (until March 2018)
Globally most important [FTS queue waits.](http://atlas-kibana-dev.mwt2.org/goto/8baa7456232e317ee90c1030baecf564)

Comparissons of average queue times for transfers where destination is [US or not US.](http://atlas-kibana-dev.mwt2.org/goto/4ba2c38aad412e631694d388b87420d0)

Site specific dashboards:

*   MWT2 [Queues](http://atlas-kibana-dev.mwt2.org/goto/499bef15f2294a9ecd2f6647d34a2575) [Transfers](http://atlas-kibana-dev.mwt2.org/goto/615f7a8d984f86849a44baa66e721d59)
*   AGLT2 [Queues](http://atlas-kibana-dev.mwt2.org/goto/0478f5c220732a22efc205cc1da18662) [Transfers](http://atlas-kibana-dev.mwt2.org/goto/1c7102866827129751f8bc0c99cbff36)
*   BNL [Transfers](http://atlas-kibana-dev.mwt2.org/goto/506a4177304f267bf704508cfdb1acfa)
 

## Monitoring flow description

The new data flow started March 2018. Data is collected from the FTS AMQ and sent directly to ES at UC, so it is almost real-time. All the IDs are stored so results can be crosschecked against both RUCIO and FTS.
