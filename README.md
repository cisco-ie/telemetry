<p align="center">
    <a href="https://github.com/cisco-ie/telemetry" target="_blank"><img src="https://user-images.githubusercontent.com/6020066/29088554-449866a6-7c2e-11e7-9b92-8e2802619122.png"></a>
 </p>

> Open-source datasets for anyone interested in working with telemetry-based network anomaly detection,
machine learning, data science and research

## Objective
Our goal is to empower the scientific and research community with datasets gathered from running equipment in real operational environments.  

As a first step, we release dataset, ground truth and documentation concerning synthetically injected BGP faults in a Content Service Provider (CSP) network, with and without aggregated traffic of up to  1 Tbps.
Given the presence of manually verified ground truth, these datasetes are geared to both supervised as well as unsupervised learning algorithms.

More complex datasets will also be provided where any number and differing type of 
event occurrences, which drives towards more real-life situations and helps us move towards
a greater capability for automation, remediation, and behavioral pattern recognition.

## Usage
Each datasets include the following:
- `.csv` Dataset
- **Header Definition File:** Provides a definition of each header
- **Case File:** Information reflecting the events, time of the events, and device(s) where event triggers are initiated

### Folders & Files
- `/portflap` - Relevant datasets and log files
- `/bgpclear` - Relevant dataset and log files
- `/ground_truth_docs` - Information regarding the topology, all connections, cdp neighbors, and device types
    - `telemetry_topology_maps.pdf`
        - **Slide 1:** Logical topology map with links colored based on the numbe of ECMP links and speed
        - **Slide 2:** Actual connected topology
        - **Slide 3:** Device types in position
    - `CDP_ground_truth.pdf`: Device connections for the network under test
- `baseline` - Baseline datasets containting no anomalies for initial modeling of the expected normal behavior of the network under test 

## Road Map
- Host/Application Metrics

## License
[Community Data License Agreementeative - Permissive, Version 1.0 ](LICENSE) &copy; [Cisco Innovation Edge](https://github.com/cisco-ie/telemetry/blob/master/LICENSE)
