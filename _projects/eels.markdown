---
layout: article
title: NASA-JPL Exobiology Extant Life Surveyor
img: /assets/images/projects/eels/eels-artistic.jpeg
tags: 
    - Bio-Inspired
    - Robotics
select: true
excerpt: Constrained optimization for gait generation in autonomous, self-propelled snake robot to travese icy crust of Saturn's moon Enceladus.
date: 2022-11-30
links:
    - video: https://youtu.be/-olZOWhfZ0g?feature=shared
---
The Cassini space-probe data indicates that Saturn's moon Enceladus has a liquid ocean under its icy crust. The plumes erupting from its surface are conduits directly to liquid water, potentially making this the easiest path to a habitable liquid ocean. The Exobiology Extant Life Surveyor (EELS) is a one-of-a-kind self-propelled, snake-like robot developed by the Jet Propulsion Laboratory (JPL) for autonomous exploration of the narrow, geyser-spewing vents and crevasses in the icy crust of Enceladus. The crevasse envelopes have driven every aspect of the EELS architecture to make it adaptable to the challenges it may face on the journey from surface to ocean and collect scientific data to assess habitability and evidence for life. The unique architecture of EELS introduces opportunities to design tailored surface mobility gaits inspired by biological snakes. 

![EELS Artistic Render](/assets/images/projects/eels/eels-artistic.jpeg?style=centerme){:.image--xxl}

As a part of the [Biorobotics Lab](https://biorobotics.ri.cmu.edu/index.php){:target="\_blank"} advised by [Prof Howie Choset](https://www.cs.cmu.edu/~choset/){:target="\_blank"} and in collaboration with the [NASA Jet Propulsion Laboratory (JPL)](https://www.jpl.nasa.gov){:target="\_blank"}, I contributed to the [EELS](https://www.jpl.nasa.gov/robotics-at-jpl/eels){:target="\_blank"} project by designing surface gaits for the snake-like robot. My key contributions to this project are as follows:
- Collaborated closely with the JPL EELS Autonomy team to design kinematic shaped-based gaits for the EELS snake robot, integrating newly designed gaits into the existing ROS/C++ software stack, enhancing its locomotion capabilities. 
- Researched constrained optimization techniques to develop a curve-fitting pipeline for generating gaits tailored to the EELS joint configuration. 

## Curve-Fitting pipeline
Biological snakes traverse challenging terrains by limbless locomotion, utilizing the ability to change their backbone shape to gain and lose traction on the surface to locomote on the surface. By thinking of gaits as following a backbone in 3D space instead of joint space, we can simplify the problem of gait generation while keeping the intuition from biological snakes. The gait generation problem is then reduced to finding the appropriate joint angles for the N-DOF robot which fits the desired reference backbone curve. Below is the overview of the gait-generation pipeline for the EELS robot. For the curve-fitting, we utilize a constrained optimization-based method. The objective function is the sum of squared distance between the joint links and the corresponding nearest points on the reference curve. We constrain this problem with the joint limits and also restrict the change in joint angles with to fixed value to produce smooth joint position commands.

![EELS Artistic Render](/assets/images/projects/eels/curve-fitting-pipeline.png?style=centerme){:.image--xxl}

## Results
We tested the curve-fitting pipeline to generate a sidewinding gait for the EELS robot by fitting the snake robot to a sidewinding backbone curve. The resulting gait was tested on a PyBullet simulation of the EELS robot. The following video shows the various steps of the pipeline described above. Please note that a moving average filter was applied on the resulting joint-angles to produce smooth joint changes for deployment on the robot. 

<div>{%- include extensions/youtube.html id='-olZOWhfZ0g' -%}</div>

## Conclusion
The Exobiology Extant Life Surveyor (EELS) project introduces a pioneering snake-like robot for exploring the icy crust of Saturn's moon, Enceladus. My contributions focused on designing surface gaits, enhancing the EELS robot's adaptability to challenging terrains. The curve-fitting pipeline employing constrained optimization enables the robot to mimic biological snakes' locomotion by dynamically adjusting joint angles to a specified curve. Successful testing yielded a sidewinding gait, demonstrating the robot's agility in navigating complex surfaces. This project has been an enriching learning journey, with the pivotal experience being the collaboration with the EELS Autonomy team at JPL. Being able to present weekly updates and receive feedback from some of the best minds in robotics was a transformative experience. The Exobiology Extant Life Surveyor  stands poised to revolutionize our understanding of extraterrestrial environments and inspire future scientific endeavors in the exploration of celestial bodies beyond our own. 


**Disclaimer**: Please note that all images and videos showcased on this page are the exclusive property of CMU Biorobotics and NASA Jet Propulsion Lab (JPL). Any unauthorized use, reproduction, or distribution of these visual assets is strictly prohibited without the explicit consent of the above.
{:.warning}