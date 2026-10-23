---
layout: page
title: NCKU UAV Ground Station
description: UAV Telemetry and Ground Control System
img: assets/img/OpenMCT.jpg
importance: 1
category: work
related_publications: false
---

### Overview

Our team previously used QGroundControl (QGC) for UAV operations. However, analyzing specific flight parameters often required retrieving recorded data from onboard storage after each flight. Customizing QGroundControl to meet our team's telemetry visualization requirements was also considered time-consuming.

To address these limitations, we adopted NASA's open-source Open Mission Control Technologies (OpenMCT) framework to develop a customizable ground station. By integrating UAV telemetry data with OpenMCT, the system was designed to provide real-time visualization of flight parameters, enabling more efficient flight monitoring and data analysis.

 ---
### Development Environment
    Ground Station Framework: NASA OpenMCT
    Programming Languages: C++, Python, JavaScript
    Runtime Environment: Node.js
    Communication: MAVLink, MAVSDK, UDP
    Simulation: PX4 SITL, jMAVSim
    Build Tools: CMake, Git
    
##### For detailed environment setup, build procedures, and troubleshooting records, refer to the [Technical Documentation](https://hackmd.io/@ncku-uav/BkuQc-tPc).

---

### Systemm Architecture
The ground station integrates PX4, MAVSDK, and NASA
OpenMCT to enable real-time UAV telemetry visualization.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/openmct_arch.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    System architecture of the OpenMCT-based UAV ground station.
</div>

---

### Implementation & My Contributions

Role: Primary Developer

I was primarily responsible for the development and integration of the OpenMCT-based UAV ground station, with technical guidance and feedback from other team members.

    Technologies: C++, Python, JavaScript, Node.js, OpenMCT, MAVSDK, MAVLink, MAVProxy, PX4 SITL, jMAVSim, CMake

##### MAVSDK Telemetry Integration
Adapted existing MAVSDK C++ example code to retrieve UAV flight telemetry from PX4 via the MAVLink protocol.
Integrated MAVProxy to forward MAVLink messages to both QGroundControl and the MAVSDK application.
Connected the MAVSDK application to the OpenMCT telemetry server through socket communication.

##### OpenMCT Customization and Plugin Integration
Extended telemetry parameter definitions using a Python-based telemetry object generator.
Configured JavaScript and JSON files to define telemetry identifiers, display names, and data types.
Registered aircraft-specific plugins and real-time/historical telemetry providers within OpenMCT.
Modified the Node.js telemetry server to incorporate the additional aircraft telemetry modules.

<div class="row align-items-center">
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid
       loading="eager"
       path="assets/img/openmct_tele.png"
       class="img-fluid rounded z-depth-1"
       style="height: 125px; width: 50%; object-fit: contain;" %}
  </div>

  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid
       loading="eager"
       path="assets/img/openmct_plugin.png"
       class="img-fluid rounded z-depth-1"
       style="height: 125px; width: 50%; object-fit: contain;" %}
  </div>
</div>

##### Simulation, Testing, and Troubleshooting
Established a simulation environment using PX4 SITL and jMAVSim to verify the integration between MAVSDK and OpenMCT.
During development, encountered telemetry visualization issues where flight data was successfully received in the terminal but could not be displayed in OpenMCT. Investigated integration issues and performed debugging to establish a functional telemetry visualization system.
Documented environment configurations, integration procedures, and troubleshooting experiences for future development.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/openmct_error.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    OpenMCT telemetry visualization failure despite successful telemetry reception from the PX4 simulator, as verified through terminal output.
</div>

---

##### Results & Demonstration

The OpenMCT-based UAV ground station was successfully integrated and validated through both Software-in-the-Loop (SITL) simulation and real-world flight testing.

During SITL testing, OpenMCT and QGroundControl operated simultaneously, successfully displaying flight telemetry parameters such as roll angle and latitude.

The system was also tested during actual UAV flights, where both OpenMCT and QGroundControl successfully received and displayed flight telemetry data, demonstrating the functionality of the integrated ground station under real-world operating conditions.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/openmct_result.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Simulation testing: Roll angle telemetry visualization using PX4 SITL and jMAVSim
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/openmct_result2.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    SITL validation: Simultaneous operation of QGroundControl and OpenMCT with latitude telemetry visualization
</div>

---

##### Future Work

The current ground station operates in a local environment, requiring users to access OpenMCT through the host computer.

Future development could focus on deploying the telemetry server to a remotely accessible environment, enabling users to monitor UAV flight data from multiple computers over a network.

This extension would improve system accessibility and support collaborative flight monitoring without requiring direct access to the ground station computer.
