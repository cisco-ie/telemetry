<p align="center">
    <a href="https://github.com/cisco-ie/telemetry" target="_blank"><img src="https://user-images.githubusercontent.com/6020066/29088554-449866a6-7c2e-11e7-9b92-8e2802619122.png"></a>
 </p>

> Open-source datasets for anyone interested in working with network anomaly based
machine learning, data science and research

> Baseline Data Sets

We have provided two baseline data sets that containt no anomalies or negative behavior. These files are here to be used a baseline dataset to model and understand the normal behavior of the environment.

The first dataset, baseline_no_anamaly.csv.gz, has an hour long run time in which no anomalies were injected and no application traffic is running.  The only traffic that will be seen on this data sets is associated with streaming telemetry as well as control and singling traffic for the various protocols in the network.

The second dataset, baseline_no_anomaly_500Gbps.csv.gz, has an hour long run time with no anomalies with application traffic running bidirectionally across the fabric at an aggregate rate of 500Gbps.


### Files ###

baseline_header.txt                     header of .csv files with column numbers
baseline_header_definitions.docx        definitions of each header column
baseline_header_definitions.pdf
baseline_no_anomaly.csv.gz              network data without anomalies
baseline_no_anomaly_500Gbps.csv.gz      hour long run of network data without anomalies
   
