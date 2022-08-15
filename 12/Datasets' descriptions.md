# Single event datasets
This entry consists of **75** single-event datasets. The datasets are retrieved from the routers in a lab network depicted [here](https://github.com/cisco-ie/telemetry/blob/master/topology_description_docs/telemetry_topology_maps.pdf).
The devices are connected in a Clos-topology, with 4 spines and 8 leaves. The links connecting the routers use ECMP to distribute the traffic. All leaves connect to multiple ToR (top of rack) switches, each of which aggregates the traffic from multiple traffic generator nodes. The lab uses BGP as routing protocol. All links have BFD (bi-directional forwarding detection) configured for rapid failure detection. 
The timeseries are created by retrieving several model driven telemetry (MDT) collections with an interval of 10s over spines 1-3 and leaves 3,4,7 and 8. 



## Events 
The types of changes inserted in the lab network include: 
- Enabling/disabling of interfaces using configuration commands;
- Breaking and restoring of BFD sessions (by filtering-out BFD control traffic between devices);
- Creation of routing loops (using static routes to make traffic for a particular prefix loop between dr02, dr03 and leaf8); 
- Creation of traffic blackholes (removal of Forwarding Information Base (FIB) entries for a prefix using configuration commands to cause the router to silently drop traffic destined to that prefix);
- Change of hashing behavior across equal-cost multipath (ECMP) using configuration commands.

## Traffic   
The traffic in the network is generated using Ixia traffic generator that is capable of generating different traffic profiles. The traffic generated for datasets can be either AppMix or FlowMix.  

- **FlowMix** traffic includes different TCP profiles such as *TCP low*, *TCP baseline* and *TCP small packets* as well as *Youtube 4k* traffic.
In other words, FlowMix mostly consists of simple TCP connections where each connection sends fixed-size TCP packets with fixed delays and settings. For example, the typical *small TCP* generates 64 byte payload packets with the largest TCP being 64Kb packets including random middle values. 

- **AppMix** on other hand, is not centered around packet sizes and delays but rather emulates different applications. This facilitates the request/response operations with different payload sizes. 
AppMix, in the datasets in this entry, includes multiple application profiles such as *Facebook*, *Netflix service provider*, *HTTP flash video service*, *YouTube LTE mix*, *HTTPS simulated*, *bitTorrent Cisco EMIX*, *Webex*, etc.. AppMix allows for indication of the number of users and thus changing the number of connections in the network.

- Note that the traffic type of few of the datasets is
marked as *-* which means the traffic profile is not recorded.

## Collected data  
The collected datasets often use either of the 2 mentioned collection sets. 
However, based on the router's configuration the set might slightly vary as the collector used for these datasets is designed to customize the set based on the router's configuration. 

### Collected Yang models set 1:
 - Cisco-IOS-XR-fib-common-oper_fib-statistics_nodes_node_drops
 - Cisco-IOS-XR-infra-statsd-oper_infra-statistics_interfaces_interface_latest_data-rate
 - Cisco-IOS-XR-infra-statsd-oper_infra-statistics_interfaces_interface_latest_generic-counters
 - Cisco-IOS-XR-ip-bfd-oper_bfd_client-details_client-detail
 - Cisco-IOS-XR-ip-bfd-oper_bfd_counters_packet-counters_packet-counter
 - Cisco-IOS-XR-ip-bfd-oper_bfd_session-briefs_session-brief
 - Cisco-IOS-XR-ip-bfd-oper_bfd_summary
 - Cisco-IOS-XR-ip-rib-ipv4-oper_rib_vrfs_vrf_afs_af_safs_saf_ip-rib-route-table-names_ip-rib-route-table-name_protocol_bgp_as_information
 - Cisco-IOS-XR-ipv4-bgp-oper_bgp_instances_instance_instance-active_default-vrf_process-info
 - Cisco-IOS-XR-nto-misc-oper_memory-summary_nodes_node_summary
 - Cisco-IOS-XR-pfi-im-cmd-oper_interfaces_interface-briefs_interface-brief
 - Cisco-IOS-XR-pfi-im-cmd-oper_interfaces_interface-summary
 - Cisco-IOS-XR-pfi-im-cmd-oper_interfaces_interface-xr_interface
 - Cisco-IOS-XR-wdsysmon-fd-oper_system-monitoring_cpu-utilization
 - Cisco-IOS-XR-telemetry-model-driven-oper_telemetry-model-driven_subscriptions_subscription
 
### Collected Yang models set 2:

 - Cisco-IOS-XR-drivers-media-eth-oper_ethernet-interface_statistics_statistic
 - Cisco-IOS-XR-fia-internal-tcam-oper_controller_dpa_nodes_node_internal-tcam-resources
 - Cisco-IOS-XR-fib-common-oper_fib-statistics_nodes_node_drops
 - Cisco-IOS-XR-infra-statsd-oper_infra-statistics_interfaces_interface_latest_data-rate
 - Cisco-IOS-XR-infra-statsd-oper_infra-statistics_interfaces_interface_latest_generic-counters
 - Cisco-IOS-XR-infra-statsd-oper_infra-statistics_interfaces_interface_latest_interfaces-mib-counters
 - Cisco-IOS-XR-infra-statsd-oper_infra-statistics_interfaces_interface_latest_protocols_protocol
 - Cisco-IOS-XR-ip-bfd-oper_bfd_client-details_client-detail
 - Cisco-IOS-XR-ip-bfd-oper_bfd_counters_packet-counters_packet-counter
 - Cisco-IOS-XR-ip-bfd-oper_bfd_session-briefs_session-brief
 - Cisco-IOS-XR-ip-bfd-oper_bfd_summary
 - Cisco-IOS-XR-ip-iarm-v4-oper_ipv4arm_addresses_vrfs_vrf_interfaces_interface
 - Cisco-IOS-XR-ip-iarm-v6-oper_ipv6arm_addresses_vrfs_vrf_interfaces_interface
 - Cisco-IOS-XR-ip-tcp-oper_tcp_nodes_node_statistics_ipv4-traffic
 - Cisco-IOS-XR-ip-tcp-oper_tcp_nodes_node_statistics_ipv6-traffic
 - Cisco-IOS-XR-ip-tcp-oper_tcp-connection_nodes_node_brief-informations_brief-information
 - Cisco-IOS-XR-ip-tcp-oper_tcp-connection_nodes_node_detail-informations_detail-information
 - Cisco-IOS-XR-ip-tcp-oper_tcp-connection_nodes_node_extended-information_display-types_display-type_connection-id
 - Cisco-IOS-XR-ip-tcp-oper_tcp-connection_nodes_node_statistics_clients_client
 - Cisco-IOS-XR-ip-tcp-oper_tcp-connection_nodes_node_statistics_pcbs_pcb
 - Cisco-IOS-XR-ip-tcp-oper_tcp-connection_nodes_node_statistics_summary
 - Cisco-IOS-XR-ip-tcp-oper_tcp-nsr_nodes_node_client_detail-clients_detail-client
 - Cisco-IOS-XR-ip-tcp-oper_tcp-nsr_nodes_node_session-set_brief-sets_brief-set
 - Cisco-IOS-XR-ip-tcp-oper_tcp-nsr_nodes_node_session-set_detail-sets_detail-set
 - Cisco-IOS-XR-ip-tcp-oper_tcp-nsr_nodes_node_statistics_statistic-clients_statistic-client
 - Cisco-IOS-XR-ip-tcp-oper_tcp-nsr_nodes_node_statistics_statistic-sets_statistic-set
 - Cisco-IOS-XR-ip-tcp-oper_tcp-nsr_nodes_node_statistics_summary
 - Cisco-IOS-XR-ipv4-bgp-oper_bgp_instances_instance_instance-active_default-vrf_afs_af_af-process-info
 - Cisco-IOS-XR-ipv4-bgp-oper_bgp_instances_instance_instance-active_default-vrf_process-info
 - Cisco-IOS-XR-ipv4-io-oper_ipv4-network_nodes_node_statistics_traffic
 - Cisco-IOS-XR-ipv6-io-oper_ipv6-io_nodes_node_statistics_traffic
 - Cisco-IOS-XR-NCS-BDplatforms-npu-resources-oper_ofa_stats_nodes_node_hw-resources-datas_hw-resources-data
 - Cisco-IOS-XR-nto-misc-oper_memory-summary_nodes_node_summary
 - Cisco-IOS-XR-pfi-im-cmd-oper_interfaces_interface-briefs_interface-brief
 - Cisco-IOS-XR-pfi-im-cmd-oper_interfaces_interface-summary
 - Cisco-IOS-XR-pfi-im-cmd-oper_interfaces_interface-xr_interface
 - Cisco-IOS-XR-wdsysmon-fd-oper_system-monitoring_cpu-utilization

## Other details

Most of the datasets in this entry only has one inserted event. Some longer datasets may have more than one event. The data
collected from each router is stored in a folder of the same name under the dataset name generated for the specific duration of running a test. 
An **event file** is associated with each dataset that specifies the timestamp of the event(s). The event description is included in the **event file**.  
The collection sets from all devices (routers) during a specific time frame share the same event file. 
The file **merged.xlsx** consists of the rendered time-series put together from the different yang collections.
The **merged.xlsx** files do not include the features that remain constant during the collection time. 
The test datasets are composed of different number of features ranging from 300 to 20000 features/time-series. 

The following table provides general details of the datasets: 

| num | Dataset | duration (s) | traffic | event                        | event description                                        |
|--------|---------|--------------|---------|------------------------------|----------------------------------------------------------|
|1|S-200202_1940_bfd-2| 650          | AppMix  | break BFD                    | eth1/41 on spine4-3464                                   |
|2|S-190521_0316_netloop_dr0203-add-1| 5400         | FlowMix | Routing loops                | leaf8, dr02 and dr03                                     |
|3|S-200206_1416_iflap-1| 750          | AppMix  | disable interface            | HundredGigE0/0/0/12 on leaf4                             |
|4|S-200122_1624_blackhole_small| 1270         | AppMix  | blackhole                    | destroy 172.31.154.0/24 on leaf3                         |
|5|S-200124_0247_bfd_break| 850          | AppMix  | break BFD                    | eth1/41 on spine4-3464                                   |
|6|S-200121_0507_ecmp_disbalance| 1370         | AppMix  | ECMP                         | 14.32.97.18/32 on spine3                                 |
|7|S-200528_1445_bfd| 1060         | -       | BFD                          | HundredGigE0/0/0/22 on leaf7                             |
|8|S-200205_0030_evtmix-2| 750          | AppMix  | enable interface             | HundredGigE0/0/0/1 on leaf7                              |
|9|S-200205_0138_evtmix-1| 1806         | AppMix  | enable and disable interface | HundredGigE0/0/0/18 on leaf7                             |
|10|S-200527_1500_iface_shutdown| 1860         | -       | enable interface             | HundredGigE0/0/0/10 on leaf4                             |
|11|S-200202_2014_evtmix-1| 1270         | AppMix  | enable and disable interface | HundredGigE0/0/0/13 on leaf4                             |
|12|S-200206_1929_evtmix-2| 1050         | AppMix  | enable interface             | HundredGigE0/0/0/4 on leaf7                              |
|13|S-200204_2035_iflap-1| 750          | AppMix  | disable interface            | HundredGigE0/0/0/17 on leaf4                             |
|14|S-200124_0458_iflap| 1270         | AppMix  | disable interface            | HundredGigE0/0/0/31 on leaf4                             |
|15|S-200204_2142_blackhole-1| 900          | AppMix  | Blackhole                    | destroy 172.31.153.0/24 on leaf3                         |
|16|S-200202_2155_evtmix-2| 630          | AppMix  | enable interface             | HundredGigE0/0/0/13 on leaf4                             |
|17|S-200202_2228_evtmix-2| 750          | AppMix  | enable interface             | HundredGigE0/0/0/4 on leaf4                              |
|18|S-200205_0104_evtmix-1| 830         | AppMix  | enable interface             | HundredGigE0/0/0/0 on leaf7                              |        
|19|S-200204_2108_ecmp-2| 800          | AppMix  | ECMP                         | 2.2.2.2/32 on spine3                                     |
|20|S-200124_0247_bfd_restore| 1270         | AppMix  | restore BFD                  | eth1/41 on spine4-3464                                   |
|21|S-200205_0246_evtmix-2| 750          | AppMix  | ebnable interface            | HundredGigE0/0/0/14 on leaf7                             |
|22|S-200206_1235_ecmp-1| 950          | AppMix  | ECMP                         | 14.32.97.18/32 on spine3                                 |
|23|S-200204_1825_bfd-1| 750          | AppMix  | break BFD                    | eth1/41 on spine4-3464                                   |
|24|S-200121_0803_ecmp-1| 1170         | AppMix  | ECMP                         | 10.10.10.249/32, 14.32.97.18/32 and 2.2.2.2/32 on spine3 |
|25|S-200202_2228_evtmix-1| 750          | AppMix  | disable interface            | HundredGigE0/0/0/4 on leaf4                              |
|26|S-200205_0246_evtmix-1| 700          | AppMix  | disable interface            | HundredGigE0/0/0/14 on leaf7                             |
|27|S-200205_0138_evtmix-2| 1150         | AppMix  | enable interface             | HundredGigE0/0/0/18 on leaf7                             |
|28|S-200206_1416_iflap-2| 1000         | AppMix  | enable interface             | HundredGigE0/0/0/12 on leaf4                             |
|29|S-200204_2108_ecmp-1| 900          | AppMix  | ECMP                         | 14.32.97.18/32 on spine3                                 |
|30|S-200202_1907_blackhole-1| 900          | AppMix  | blackhole                    | destroy 172.31.153.0/24 on leaf3                         |
|31|S-200204_1859_ecmp-2| 750          | AppMix  | ECMP                         | 2.2.2.2/32 on spine3                                     |
|32|S-200121_1947_blackhole| 1370         | AppMix  | Blackhole                    | destroy 172.31.56.0/24 on leaf3                          |
|33|S-200204_2035_iflap-2| 750          | AppMix  | enable interface             | HundredGigE0/0/0/17 on leaf4                             |
|34|S-200204_1932_blackhole-1| 960          | AppMix  | Blackhole                    | destroy 172.31.53.0/24 on leaf3                          |
|35|S-200122_1729_iflap_ifdown| 640          | AppMix  | disable interface            | HundredGigE0/0/0/4 on leaf4                              |
|36|S-200121_0507_ecmp_balance| 900          | AppMix  | ECMP                         | 2.2.2.2/32 on spine3                                     |
|37|S-200122_1624_blackhole_big| 900          | AppMix  | Blackhole                    | destroy 172.31.154.0/24 on leaf3                         |
|37|S-200417_2255_blackhole| 1611         | -       | Blackhole                    | destroy 172.31.154.0/24 on leaf3                         |
|38|S-200206_1235_ecmp-2| 900          | AppMix  | ECMP                         | 2.2.2.2/32 on spine3                                     |
|39|S-200121_0731_iflap-ifdown| 970          | AppMix  | interface flapping           | HundredGigE0/0/0/18 on leaf4                             |
|40|S-200202_2335_evtmix-2| 750          | AppMix  | enable interface             | HundredGigE0/0/0/4 on leaf4                              |
|41|S-200204_1932_blackhole-2| 650          | AppMix  | Blackhole                    | destroy 172.31.53.0/24 on leaf3                          |
|42|S-200202_2014_evtmix-2| 800          | AppMix  | enable interface             | HundredGigE0/0/0/13 on leaf4                             |
|43|S-200202_2121_evtmix-1| 700          | AppMix  | disnable interface           | HundredGigE0/0/0/12 on leaf4                             |
|44|S-190521_0316_netloop_dr0203-del-1| 5400         | FlowMix | Routing loops                | leaf8, dr02 and dr03                                     |
|45|S-200202_2302_evtmix-1| 750          | AppMix  | disable interface            | HundredGigE0/0/0/18 on leaf4                             |
|46|S-200206_1450_ecmp-1| 950          | AppMix  | ECMP                         | 2.2.2.2/32 on spine3                                     |
|47|S-200206_1734_evtmix-2| 750          | AppMix  | enable interface             | HundredGigE0/0/0/10 on leaf7                             |
|48|S-200206_1734_evtmix-1| 800          | AppMix  | disable interface            | HundredGigE0/0/0/10 on leaf7                             |
|49|S-200202_2155_evtmix-1| 950          | AppMix  | disable interface            | HundredGigE0/0/0/13 on leaf4                             |
|50|S-200122_1802_ecmp_low_traffic-2| 800          | AppMix  | ECMP                         | destroy 172.31.154.0/24 on leaf3                         |
|51|S-200121_0731_iflap-ifup| 970          | AppMix  | interface                    | HundredGigE0/0/0/18 on leaf4                             |
|52|S-200206_1309_blackhole-1| 1240         | AppMix  | Blackhole                    | destroy 172.31.156.0/24 on leaf3                         |
|53|S-200121_0836_blackhole| 1370         | AppMix  | Blackhole                    | destroy 172.31.154.0/24 on leaf3                         |
|54|S-200206_1929_evtmix-1| 800          | AppMix  | disable interface            | HundredGigE0/0/0/4 on leaf7                              |
|55|S-200205_0104_evtmix-2| 740          | AppMix  | disable interface            | HundredGigE0/0/0/0 on leaf7                              |
|56|S-200202_2335_evtmix-1| 750          | AppMix  | disable interface            | HundredGigE0/0/0/4 on leaf4                              |
|57|S-200121_0803_ecmp| 1804         | AppMix  | ECMP                         | 10.10.10.249/32, 14.32.97.18/32 and 2.2.2.2/32 on spine3 |
|58|S-200202_2302_evtmix-2| 750          | AppMix  | enable interface             | HundredGigE0/0/0/18 on leaf4                             |
|59|S-200206_1450_ecmp-2| 900          | AppMix  | ECMP                         | loopback 2.2.2.2/32 on spine3                            |
|60|S-200204_2142_blackhole-2| 700          | AppMix  | Blackhole                    | destroy 172.31.54.0/24 on leaf3                          |
|61|S-200206_1852_evtmix-1| 800          | AppMix  | enable interface             | HundredGigE0/0/0/10 on leaf7                             |
|62|S-200206_1852_evtmix-2| 850          | AppMix  | disable interface            | HundredGigE0/0/0/10 on leaf7                             |
|63|S-200202_1940_bfd-1| 900          | AppMix  | enable BFD                   | eth1/41 on spine4-3464                                   |
|64|S-200202_2121_evtmix-2| 650          | AppMix  | enable interface             | HundredGigE0/0/0/12 on leaf4                             |
|65|S-200204_1859_ecmp-1| 950          | AppMix  | ECMP                         | 2.2.2.2/32 on spine3                                     |
|66|S-200122_1802_ecmp_low_traffic-1| 800          | AppMix  | ECMP                         | destroy 172.31.154.0/24 on leaf3                         |
|67|S-200205_0030_evtmix-1| 800          | AppMix  | disable interface            | HundredGigE0/0/0/1 on leaf7                              |
|68|S-200206_1523_blackhole-1| 950          | AppMix  | Blackhole                    | destroy 172.31.53.0/24 on leaf3                          |
|69|S-200202_2047_evtmix-1| 800          | AppMix  | disable interface            | HundredGigE0/0/0/10 on leaf4                             |
|70|S-200206_1626_evtmix-1| 800          | AppMix  | disable interface            | HundredGigE0/0/0/10 on leaf7                             |
|71|S-200202_2047_evtmix-2| 650          | AppMix  | enable interface             | HundredGigE0/0/0/10 on leaf4                             |
|72|S-200206_1343_bfd-1| 900          | AppMix  | break BFD                    | eth1/41 on spine4-3464                                   |
|73|S-200122_1729_iflap_ifup| 800          | AppMix  | enable interface             | HundredGigE0/0/0/4 on leaf4                              |
|74|S-200528_1055_netloop| 1080         | -       | Routing loop                 | leaf8, dr02 and dr03                                     |
|75|S-200527_1655_netloop| 1800         | AppMix  | Routing loop                 | leaf8, dr02 and dr03                                     |


## Datasets' usecase examples

The provided datasets can be used in various ways. To name but a few:

- **Research**: provide a reasonable set of large and small time-series (as opposed to flow data) datasets with variety of features for research purposes. Some research areas could be as follows: 
  - Change point detection and assessment of the network/device functionality state, ex. paper [here](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=bY0WnP8AAAAJ&citation_for_view=bY0WnP8AAAAJ:9yKSN-GCB0IC)
  - Applied mathematics in networking for modeling the traffic properties with small cadence (5- 10 seconds)
  - Behavioral network analysis for Rule-based system designs based on the interdependency of different counters 
  - Traffic classification and ML application to networking 
  - Feature selection problems such as application of natural language processing on hierarchical names of features resulted from the Yang model, ex. paper: [here](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=bY0WnP8AAAAJ&citation_for_view=bY0WnP8AAAAJ:d1gkVwhDpl0C)

- **Industry**: As meticulously studied datasets, the provided datasets' properties can set a reasonable expectation base-line 
for the  quality of data collected using Model Driven Telemetry.
