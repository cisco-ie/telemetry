<p align="center">
    <a href="https://github.com/cisco-ie/telemetry" target="_blank"><img src="https://user-images.githubusercontent.com/6020066/29088554-449866a6-7c2e-11e7-9b92-8e2802619122.png"></a>
 </p>

<p align="center">
    <a href="https://github.com/cisco-ie/telemetry/blob/master/LICENSE"><img src="https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg?style=flat-square" alt="CC License"></a>
</p>

> Open-source datasets for anyone interested in working with network anomaly based
machine learning, data science and research

## Port State Changes
This data set covers three different types of port state changes that can and are seen in a network. 
These three types are an optical transceiver pulled from a network port on a given device and then
once the event stabalizes, the transceiver is reinserted.  

The second type of port state change is an admin state change from up to down, a port shutdown. 
As with the first port state change, once the network event stabilizes the state of the port
is changed back to up.

The third port state change is a change in link state, in this case a loss of light to the 
transceiver.  This is achieved by removing the fiber optics cable from the transceiver.  Once
this network event stabilizes, the fiber optic cable is plugged in and and link will be established.



## Points of Focus

For the above scenarios, two events were completed allowing you to see the how the event 
is reflected when it happens on a local port, or when it happens on a remote port of the neighbor box. 
For the transceiver removal, we removed the transceiver on Spine 2 which will allow you to see the signature of 
the event trigger and the subsequent event bloom where the trigger happens on Spine 2.    

### Logfiles

Logfiles for the duration of the events for all devices in the fabric are found under /portflap/logs


## License
[Creative Commons Attribution-NonCommercial 4.0](LICENSE) &copy; [Cisco Innovation Edge](https://github.com/cisco-ie/telemetry/blob/master/LICENSE)
