---
layout: page
title: ALFA -APTRI Labs Floor Assistant
description: An open-source internet controlled mobile robot.
img: /assets/img/alfa3.jpg
importance: 2
projectlink: https://github.com/YugAjmera/ALFA
---

This was an internship project done at [Adani Power](https://www.adanipower.com/)'s training and research institute [APTRI](https://www.aptri.org/). ALFA is an open-source internet controlled mobile robot. We designed, fabricated and tested the prototype in 2 months of the summer internship.

### Parts used:
- Raspberry Pi 3B+ (main controller)
- Pi cam (for camera feed)
- Power bank 10000 mAh (to power raspi)
- 4 x Motors (we have used 300RPM)
- L298N
- Lipo battery 4200 mAh (to power L298N)
- Jumper Wires
- Breadboard

### Robot structure
A basic chassis was designed on Solidworks 2017. Once the chassis design was finalised, the ANSYS Student 19.2 software was used to do the structural analysis of the robot. This analysis helped in identifying the major stress points and these were optimized them by making necessary changes to the robot.

The major components of the chassis were identified as follows:
1. Base plates (25cm x 25cm) - 2
2. Support Rod Mounts - 8
3. Support Rods - 4
4. Motor Mounts - 4

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/alfa/printer.gif' | relative_url }}" alt="" title="3D Printer"/>
    </div>
</div>
<br/>


Wooden based plates were used to aid in mounting the other components whereas the support rods mounts, support rods and motor mounts were all 3D Printed using the J-Group Robotics [Dimension Dual Delta](https://www.jgrouprobotics.com/dimension-dual-delta) 3D Printer.
<br/>

### Assembly
The mounts were fixed to the base plates using screws.
<br/>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/alfa/1.png' | relative_url }}" alt="" title="Assembly"/>
    </div>
</div>
<br/>

<br/>

### Final Prototype

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/alfa/alfaFinal.jpg' | relative_url }}" alt="" title="Working"/>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/alfa/bits.jpg' | relative_url }}" alt="" title="Team"/>
    </div>
</div>
<div class="caption">
    Left: Final Robot assembly. Right: Team photo with robot.
</div>

Find the Code, CAD Files and other details on [GitHub](https://github.com/YugAjmera/ALFA).