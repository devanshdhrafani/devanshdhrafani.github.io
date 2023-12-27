---
layout: article
title: MPC TrajOpt for Quadrotor Subcanopy Flight
img: /assets/images/projects/ocrlmpc/mpc-gif.gif
tags: 
    - Aerial
    - Robotics
select: true
excerpt: RRT + minimum snap trajectory and non-linear MPC controller with convex obstacle constraints for fast flight in forest subcanopy.
date: 2023-05-12
links:
    - code: https://github.com/rachelzh9/subcanopy_flight
    - video: https://youtu.be/LnCpOuqSb0I?feature=shared
---

Quadrotors are agile, able to traverse complex environments at high speeds, making them a valuable tool in many high-risk scenarios such as search and rescue and wildfire monitoring. In order to navigate cluttered environments such as dense forests, quadrotors need to be able to dynamically avoid obstacles as they are detected online. In this project, we tackle the problem of trajectory optimization for quadrotor subcanopy flight. We use a sampling-based global planner with minimum snap trajectory generation, and nonlinear model predictive control (MPC) with convex obstacle constraints to track the trajectory. We show successful real-time results in a realistic forest simulation. 

![MPC trajectory through forest](/assets/images/projects/ocrlmpc/quadrotor_forest_sim.png?style=centerme){:.image--xxl}

This was a course project for [Prof Zachary Manchester](https://www.ri.cmu.edu/ri-faculty/zachary-manchester/){:target="\_blank"}'s CMU course [16-745 Optimal Control and Reinforcement Learning](https://github.com/Optimal-Control-16-745/){:target="\_blank"}. My key contributions to this project are as follows:
- Developed and implemented a minimum snap trajectory and non-linear MPC control framework with convex obstacle constraints to enable safe navigation through dense forest sub-canopy during wildfire search and rescue operations.
- Integrated 2D RRT-planner ROS server to generate waypoints for the minimum snap trajectory generator.
- Formulated the MPC optimization problem with dynamics and constraints, utilizing the ACADOS solver for non-linear MPC. 

## System Architecture
We use a hierarchical approach with a high-level global planner and a low-level controller. Our system architecture is depicted in the figure below. We simulate active perception with an obstacle detector module that publishes all obstacles within a detection radius of the quadrotor. The global planner plans a smooth trajectory from the quadrotor’s start pose to its goal pose that is not guaranteed to be completely collision-free. The quadrotor must then do online tracking of the global trajectory while avoiding collisions with the perceived obstacles. To read more about the implementation details, please refer our report.

![System architecture](/assets/images/projects/ocrlmpc/system-architecture.png?style=centerme){:.image--xxxl}

## Model Predictive Control (MPC)
We use the ACADO Toolkit, a C++ library for automatic control and dynamic optimization, for a fast real-time MPC implementation. ACADO gives us a convenient way to represent standard optimal control problems and supports several types of constraints, such as control and state bounds, terminal constraints, and general nonlinear path constraints. It solves these nonlinear optimal control problems using Sequential Quadratic Programming (SQP) with multiple shooting transcription. Its QP backend uses an active set method, so obstacles far away do not influence computation. Furthermore, ACADO also supports fast C code generation, which makes it much easier to deploy our controllers in real-time and on hardware. The figure below describes our MPC formulation. The controller is ran at 100Hz and receives state feedback at the same rate. 

![MPC formulation](/assets/images/projects/ocrlmpc/mpc-formulation.png?style=centerme)

## Results
We test our system in a realistic forest environment in Gazebo. We use the quadrotor simulation package RotorS, which comes with several different quadrotor models, an autopilot state machine, and controllers. We extend the existing simulation by adding our own forest world, converting it to a simplified world where the trees are modelled by cylinders, and creating a custom MPC controller with obstacle constraints. Below is a video showing our system in action.

<div>{%- include extensions/youtube.html id='LnCpOuqSb0I' -%}</div>

## Conclusion
In conclusion, this work presents a successful implementation of autonomous UAV subcanopy navigation in simulation using a combination of RRT and MPC. The ACADO toolkit was utilized to perform the optimization process, and the three closest trees were represented as simple cylinder primitives. To improve the system, future work will focus on integrating perception capabilities for trees and developing more complex obstacle models. Additionally, the implementation of this navigation algorithm on real hardware is a necessary step towards practical applications in the field of autonomous aerial navigation. The results obtained in this study provide a solid foundation for further development towards achieving safe and efficient subcanopy navigation for UAVs. Through this project, I gained experience in implementing modern control theory for designing controllers which utilize the agile dynamics of quadrotors for fast navigation. I also gained familiarity with the ACADO toolkit, which is the tool of choice for trajectory optimization in many modern quadrotors. Integrating the controller in a ROS1 simulation stack was also a immense learning experience. 
