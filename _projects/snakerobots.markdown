---
layout: article
title: Snake-like Robots for Search and Rescue
img: /assets/images/projects/snakerobots/poleclimb.gif
tags: 
    - Bio-Inspired
    - Embedded systems
    - Robotics
select: true
excerpt: ROS-based software stack to control Biorobotics lab Snake Robots; Firmware development for snake head perception module.
date: 2022-05-30
---

Natural calamities like earthquakes, cyclones, and tsunamis affect millions of people every year. Many casualties are caused in the aftermath of the disaster, when response efforts are inefficient to find and rescue the survivors. More people die of  entrapment after a building collapses than during the actual collapse. Snake Robots can play a pivotal role in the search and rescue operations, adeptly navigating confined spaces and disaster debris where humans struggle to reach. Their flexible, serpentine design enables them to slither through crevices, offering invaluable assistance in locating survivors and delivering crucial aid. Their slender form factor and ability to climb structures like trees/poles also make them useful for reconnaissance.

![Pole Climb](/assets/images/projects/snakerobots/poleclimb.gif?style=centerme)

As a visiting research scholar at the [Biorobotics Lab](https://biorobotics.ri.cmu.edu/index.php){:target="\_blank"}, I got the opportunity to work on modular snake-like robots with [Prof Howie Choset](https://www.cs.cmu.edu/~choset/){:target="\_blank"}. My key contributions to this project are:

- Pioneered the development of SnakeLib, a unified, easy-to-use ROS-based software library to control all the different snake-like robots at the Biorobotics lab. 
- Outlined the implementation and led a team of 4 in the development and testing of SnakeLib on Snake Robots.
- Programmed and integrated NanoPi firmware and hardware for the snake robot perception module.


## SnakeLib

In my initial days at the Biorobotics Lab, I was re-implementing existing gaits on the new snake robot (called ReU snake) at the lab. This involved reading papers and digging through deprecated code to figure out the nuances to correctly implementing the gaits on hardware. It was then that I realized the need of a modern, unified software and research tool for controlling these robots. 

After talking with many people who worked on the original snake-robot software, I came up with a plan to develop SnakeLib. ROS1 Noetic was chosen as the platform since it had wide support being the LTS release at that time. I wanted a simulation platform to test the gaits before deploying them to hardware. PyBullet was chosen for the simulation environment since it is lightweight and easily configurable. Below is the layout I created for SnakeLib's ROS architecture. 

![SnakeLib ROS Architecture](/assets/images/projects/snakerobots/snakelibros.png?style=centerme)

## Hardware demos

Here is a demo video showing the Biorobotics Lab's ReU snake running different gaits implemented in SnakeLib. Note that the robot is controlled via a wireless gamepad. At the end, you can see the snake robot climb up my leg!

<div>{%- include extensions/youtube.html id='d7W90u8xka8' -%}</div>

For more videos, [click here](https://www.youtube.com/playlist?list=PLRgXEcRAQzpb1k4Q2uOfEWpQCaI2rGA0p){:target="\_blank"}.


## Snake Head perception module

When navigating through tight spaces with no visual line of sight, a perception system is essential for robot operation. Developing an integrated perception module for a modular robot like the ReU snake is a challenging task because of the size constraints, limited compute and low communication bandwidth. In this project, I programmed the NanoPi Neo Core 2 firmware to interface with sensors and stream the data via ethernet to the base station. Here is an overview of the communication channels of the snake head perception module.

![ReU Snake Head Perception Module](/assets/images/projects/snakerobots/reusnakehead.png?style=centerme)

The perception head consists of 2 RGB cameras, 1 Thermal Array and an LED strip to provide illumination in confined, low-light spaces. All the sensors interface with a NanoPi Neo Core 2. Because the ReU snake modules communicate via ethernet, the NanoPi had to be programmed as a camera server to stream data to the base station. MJPG streamer was used to stream the RGB data. For the thermal array, a custom firmware was developed to interface with the I2C sensor and stream the data. 

## Conclusion

Snake-like robots are a fascinating and unconventional breed of locomoting robots. Their versatile design and high DOF enables them to navigate challenging terrains. When originally developing SnakeLib, my goal was to make a research tool which would utilize the full capability of these amazing limbless locomotors. Today, SnakeLib is actively used in the lab for all snake robot research. Throughout this project, I learned many skills. The biggest learning I had was about the importance of hardware testing for robots. Despite the considerable realism of current simulators, they fall short in accurately modeling the dynamics of real systems, particularly the intricate contact dynamics inherent in snake-like robots. Apart from sim-to-real gap, many issues come up with hardware: modules constantly breaking, loose connections, not enough power, etc. Rigorous testing of each gait on the hardware proved instrumental in fortifying the final software and refining the hardware, rendering it robust and reliable. Programming the snake head perception module firmware was also a great learning experience, since I got to dive deep into the workings of I2C and TCP protocols, while also doing a lot of electronics testing/integration.

![Snake Robot climbing up a giant spider robot](/assets/images/projects/snakerobots/snakespiderclimb.gif?style=centerme)