<p align="center">
    <a href="https://github.com/cisco-ie/telemetry" target="_blank"><img src="https://user-images.githubusercontent.com/6020066/29088554-449866a6-7c2e-11e7-9b92-8e2802619122.png"></a>
 </p>


> Open-source datasets for anyone interested in working with network anomaly based
machine learning, data science and research

########################### September 20, 2017 ##########################################

At the request of one the academic research groups, we have added an additional data set
to the inventory and will do so for each anomaly.  The new data set will have the identical 
network anomalies but there will be no application traffic running across the network.  This
will allow the modeling of the event without the additional noise of the app traffic and the
assicated events such as traffic/flow rehashing. 

########################### Update as of August 4th, 2017 ###############################

By request we have added the device log files for the bgpclear event from leaf, spine and edge
routers (dr) for natural langauge processing of the events. As this was an addition of information,
to have it be in sync with the bgpclear csv file, we configured logging to increase the amount of
information logged and reran the test.

There is a new csv file for bgpclear which is now named bgpclear08042017.csv.

Moving forward we will have log files included with all network anomalies.

#######################################################################################


### NOTE:  Leaf4 has a bad optic in port Hu0/0/0/16 and is in a shutdown state for this test
### so you will not see telemetry records for this port in the data set.

The bgp clear test clears all BGP information to represent a BGP process crash and recover.
This clears
 1) neighbors;
 2) all learned and programmed routes other than attached;
 3) all learned and programmed paths

The test scenario has ~1.3Tbps of application traffic traversing the fabric.  Traffic scenarios
included sustained:
 1) TCP flows;
 2) G.711a IP voice call (64 kbps per call);
 3) RTP Blue Ray movie (45 Mbps per stream);
 4) Skype-1050P stream;
 5) AMR-WB VOIP (23.85 kbps per call);
 6) YouTube 4K video stream

The differing application flow/stream types give us the ability to see the various performance metric
changes for the applications.  These include items such as jitter, MOS for voice,
drops for each of the various flows and protocols, etc.

This dataset reflects the impacts of clearing all bgp information at various places throughput our Clos fabric
(see ../ground_truth_docs/telemetry_topology_maps.pdf for logical topology diagram).

There is a 5 minute period of stable, clean traffic clear of any network anomalies to establish the normal behavior
baseline at the begining of the test scenario.

The first four anomoly events effect positions in the leaf and spine of the Clos.  The leafs have a different number
of downstream connections to edge routers and top of rack (ToR) switches.  The spine tests will show the effect of traffic
redistribution over the remaining equal-cost multi-path (ECMP) routes but will push the traffic rehashing back to the leafs.

Event 1 leaf1
Event 2 leaf6
Event 3 spine2
Event 4 cascade bgp clear of leaf2 followed by leaf8 30 seconds later
Event 5 cascade bgp clear of spine1 followed by spine2 and then spine3 with ~45 second gap between each event.

The last two tests have multiple devices in the event.  The first has two leafs, one on either side of the spine which
will force traffic changes back to the ToR and edge routers as well as effect traffic at the spines.  The next test effects
three spines to simulate a bgp process crash and restart cascading across three spines. This last test forces all traffic
to a single spine, effecting rehashing on all leafs.


#### Metric Information ####

Please Note:

For metrics that are sampled per interface:
 leaf and spine devices have 32 network interfaces, 1 management interface and 1 Null0 interface
 dr devices have 72 network interfaces (36 per line card), 1 management interface and 1 Null0 interface

The topology is configured for a dual stack environment with both IPv6 and IPv4 address families
_________________________

These metrics are sampled per CPU:
Cisco-IOS-XR-fib-common-oper:fib-statistics/nodes/node/drops
Cisco-IOS-XR-nto-misc-oper:memory-summary/nodes/node/summary
Cisco-IOS-XR-wdsysmon-fd-oper:system-monitoring/cpu-utilization

For these metrics,
 leaf and spine devices have one CPU (0/RP0/CPU0)
 dr devices have N CPUs where N includes one CPU per line card and one per RP
  in this sample case there are 3 CPUs (0/RP0/CPU0, 0/0/CPU/0, 0/1/CPU/0)

________________________

These metrics are sampled per device:
Cisco-IOS-XR-ip-rib-ipv4-oper:rib/vrfs/vrf/afs/af/safs/saf/ip-rib-route-table-names/ip-rib-route-table-name/protocol/bgp/as/information
Cisco-IOS-XR-ipv4-bgp-oper:bgp/instances/instance/instance-active/default-vrf/process-info

#### Files ####

bgpclear08042017.csv.gz            primary dataset
bgpclear_casedata.txt              timing and device information for inserted anomaly events
bgpclear_header.txt                list of header strings with column numbers
bgpclear_header_definitions.docx   explaination of metrics
bgpclear_header_definitions.pdf
bgpclear_no_traffic.csv.gz         same dataset, but no network traffic is flowing
bgpclear_no_traffic_casedata.txt   timing and device information for inserted anomaly events
bgpclear_no_traffic_header.txt     list of header strings with column numbers
