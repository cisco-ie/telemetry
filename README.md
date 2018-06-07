<p align="center">
    <a href="https://github.com/cisco-ie/telemetry" target="_blank"><img src="https://user-images.githubusercontent.com/6020066/29088554-449866a6-7c2e-11e7-9b92-8e2802619122.png"></a>
 </p>

> Open-source datasets for anyone interested in working with network anomaly based
machine learning, data science and research

## Objective
Our immediate goal is to share real-world datasets and documentation that are instrumental to develop, test and compare anomaly detection algorithms based on  machine learning (both supervised or unsupervised). 

Our longer term goal is to systematically extend this collection with more complex datasets, event occurrences, which drives towards more real-life situations and helps the community move towards a greater capability for automation, remediation, and behavior pattern recognition.


## Related repositories 
The datasets released in this website are also instrumental to reproduce results that are published in  [ACM SIGCOMM BigDama'18] and that are demonstrated at [IEEE INFOCOM'18] (see the Reference section below)

This repository only contains the dataset, whereas related repositories contain 
- our generic  DenStream implementation   https://github.com/anrputina/OutlierDenStream
- specific instruction and code to replicate the paper results   https://github.com/anrputina/OutlierDenStream-BigDama18


## Usage
Each datasets include the following:
- `.csv` Dataset
- **Header Definition File:** Provides a definition of each header
- **Case File:** Information reflecting the events, time of the events, and device(s) where event triggers are initiated



### Folders & Files
- `/topology_description_docs` - Information regarding the topology, all connections, cdp neighbors, and device types
    - `telemetry_topology_maps.pdf`
        - **Slide 1:** Logical topology map with links colored based on the numbe of ECMP links and speed
        - **Slide 2:** Actual connected topology
        - **Slide 3:** Device types in position
    - `CDP_ground_truth.pdf`: Device connections for the network under test

- | # | Traffic load | No. Anomalies | Duration | Description |
  | --- | --- | --- | --- | --- |
  | 0 | 0 | 0 | 1h | Baseline (no amolies) |
  | 1 | 500Gbps | 0 | 1h | Baseline (no anomalies) |
  | 2 | 1Tbps | 11 | 1h | BGP Clear | 
  | 3 | 1Tbps | 8 | 0.55h | BGP Clear | 
  | 4 | 1Tbps | 5 | 0.72h | Port Flap | 
  | 5 | 1Tbps | 12 | 2h | BGP Clear |
  | 6 | 0 | 12 | 2h | BGP Clear |
  | 7 | 0 | 130 | 72h | (VIRL) BGP Clear |
  | 8 | 0 | 238 | 262h | (VIRL) BGP Clear |

## References

[ACM SIGCOMM BigDama'18] Putina, Andrian and Rossi, Dario and Bifet, Albert and Barth, Steven and Pletcher, Drew and Precup, Cristina and Nivaggioli, Patrice,  Telemetry-based stream-learning of BGP anomalies ACM SIGCOMM Workshop on Big Data Analytics and Machine Learning for Data Communication Networks (Big-DAMA’18) aug. 2018

[IEEE INFOCOM'18] Putina, Andrian and Rossi, Dario and Bifet, Albert and Barth, Steven and Pletcher, Drew and Precup, Cristina and Nivaggioli, Patrice,  Unsupervised real-time detection of BGP anomalies leveraging high-rate and fine-grained telemetry data IEEE INFOCOM, Demo Session apr. 2018,

## License
[Community Data License Agreementeative - Permissive, Version 1.0 ](LICENSE) &copy; [Cisco Innovation Edge](https://github.com/cisco-ie/telemetry/blob/master/LICENSE)
