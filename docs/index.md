
# GRTK Introduction

GRTK is a dual-antenna high-precision differential positioning and directional module (Real Time Kinematics) independently developed by **Blicube**. A complete RTK system can be formed through two GRTK modules (one mobile terminal and one base station terminal).

The module is based on a new generation of high-performance GNSS SoC chip design,supports multi-system multi-frequency RTK positioning, supports dual-antenna high-precision orientation, and supports GPS&GLONASS&Beidou&Galileo&QZSS navigation and positioning. It is mainly for high-precision positioning and orientation requirements such as drones, robots and intelligent driving.

**<center><img src="media/grtk_1.1.png" width="50%"></center>**

<center>

Figure 1.1 Physical image of GRTK centimeter-level positioning and orientation system

<iframe width="560" height="315" src="https://www.youtube.com/embed/Gq83rHsXRVo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>



## Performance

| Item                           |                                                                        |
|--------------------------------|------------------------------------------------------------------------|
| Frequencies                    | BDS B1I/B2I1<br> GPS L1/L2 <br/>GLONASS L1/L2<br> Galileo E1/E5b<br> QZSS L1/L2 |
| Single Point Positioning (RMS) | Horizontal：1.5m<br> Vertical：2.5m                                      |
| DGPS (RMS)                     | Horizontal：0.4m<br> Vertical：0.8m                                      |
| RTK (RMS)                      | Horizontal：1cm+1ppm<br> Vertical：1.5cm+1ppm                            |
| Heading Accuracy (RMS)         | 0.2 degree/1 m baseline                                                |
| Velocity Accuracy (RMS)        | 0.03 m/s                                                               |
| Time Accuracy (RMS)            | 20 ns                                                                  |
| Time to First Fix (TTFF)       | Cold start < 25 s                                                      |
| Initialization Time            | < 5s (typical)                                                         |
| Reacquisition                  | < 1 s                                                                  |
| Correction                     | RTCM v2.3/3.0/3.2                                                      |
| Data Output                    | NMEA-0183                                                              |
| Update Rate                    | 20 Hz                                                                  |
| Inertial Navigation Accuracy   | < 5% of distance travelled during GPS denied conditions                |
| Working Temperature            | -20℃ to +85℃                                                           |
| Power Supply                   | 5v to 35v      
| Power Dissipation              | ~2.5W

## Physical size

<center>

**![](media/grtk_dia.png)**


Figure 1.2 Schematic diagram of physical size
</center>

## Test Video

-   Unmanned vehicle automatic route mission measurement.

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/vlFBtBZZLb4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

## User Manual

* [GRTK 用户手册](GRTK用户手册.md)
* [GRTK User Manual](GRTK_User_Manual.md)