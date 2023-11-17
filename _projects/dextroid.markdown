---
layout: article
title: Dextroid-The Humanoid
description: Low cost 8-DOF Bipedal Robot
img: /assets/images/dextroid.jpg
importance: 1
select: true
tags:
    - Robotics
    - Humanoid
excerpt: An 8-DOF Bipedal Humanoid designed to be low-cost and enable fast prototyping, with easily replaceable off-the-shelf parts.
date: 2018-02-15
---

Dextroid is an 8-DOF Bipedal Humanoid developed by team of students from BITS Pilani, Hyderabad Campus. It was designed to be low-cost and enable fast prototyping, with easily replaceable off-the-shelf parts.

### Mechanical Design

TowerPro MG995 metal-gear servos were choosen to actuate the 8 Degrees of Freedom. These were attached for leg arrangement with off-the-shelf brackets. Acrylic sheets were used for the foot and the hip base. SolidWorks was used for initial design and test assembly.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/images/dextroid2.png' | relative_url }}" alt="" title="Dextroid"/>
    </div>
</div>
<div class="caption">
    Left: SolidWorks Render of the robot assembly. Right: Actual robot.
</div>


### Electronics

Arduino UNO was used as the microcontroller. The robot was powered by a lithium polymer battery (not attached). A DC-DC Buck Converter was used to step-down voltage for the servos/arduino.

### Demo Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/JOigEVpNYiw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>