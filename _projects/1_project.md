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
    Figure 1. System architecture of the OpenMCT-based UAV ground station.
</div>

---

### Implementation & My Contributions

Role: Primary Developer

I was primarily responsible for the development and integration of the OpenMCT-based UAV ground station, with technical guidance and feedback from other team members.

    Technologies: C++, Python, JavaScript, Node.js, OpenMCT, MAVSDK, MAVLink, MAVProxy, PX4 SITL, jMAVSim, CMake

1. MAVSDK Telemetry Integration
Adapted existing MAVSDK C++ example code to retrieve UAV flight telemetry from PX4 via the MAVLink protocol.
Integrated MAVProxy to forward MAVLink messages to both QGroundControl and the MAVSDK application.
Connected the MAVSDK application to the OpenMCT telemetry server through socket communication.

2. OpenMCT Customization and Plugin Integration
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
       style="height: 250px; width: 100%; object-fit: contain;" %}
  </div>

  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid
       loading="eager"
       path="assets/img/openmct_plugin.png"
       class="img-fluid rounded z-depth-1"
       style="height: 250px; width: 100%; object-fit: contain;" %}
  </div>
</div>

3. Simulation, Testing, and Troubleshooting

Established a simulation environment using PX4 SITL and jMAVSim to test the ground station integration.

Verified telemetry data visualization in OpenMCT using simulated UAV flight data.

Investigated and resolved development environment, library dependency, and compilation issues during MAVSDK integration.

Documented environment configuration, integration procedures, and troubleshooting results for future development.



<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/GS.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    This image can also have a caption. It's like magic.
</div>

You can also put regular text between your rows of images, even citations {% cite einstein1950meaning %}.
Say you wanted to write a bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, _bled_ for your project, and then... you reveal its glory in the next row of images.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}

```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %}
