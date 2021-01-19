---
layout: page
title: Projects
permalink: /projects/
description: Here are some of the projects that I completed during my undergrad.
nav: true
---

### Robotics Projects

* **Dextroid-The Humanoid :** A low cost 8 DOF Bipedal Humanoid. ([link]({{ site.baseurl }}/projects/dextroid/))
* **ALFA :** An open-source floor assistant mobile robot developed at APTRI Labs, Ahmedabad. ([link]({{ site.baseurl }}/projects/alfa/))
* **diff_drive_bot :** ROS Package for implementing **slam_gmapping** and **ROS Navigation Stack** on a custom 2 wheeled Differential Drive Robot. ([code](https://github.com/devanshdhrafani/diff_drive_bot){:target="\_blank"})
* **mobile-robot-controller :** ROS Package for controlling mobile robots. Implements **HybridAutomata** with Go to Goal, Obstacle Avoidance, and Follow Wall behaviours governed by **Sliding Mode Switch**. ([code](https://github.com/devanshdhrafani/mobile-robot-controller){:target="\_blank"})
* **Quadrotor :** Successfully assembled, tuned and tested a quadrotor with KK2 1.5 flight controller.
* **Heatbuzzer :** Built a temperature monitoring device using DS18B20 Temperature sensor, Arduino Nano and 16x2 LCD screen. 
* **Obstacle Avoiding Bot :** Built an obstacle avoiding mobile robot using Ultrasound Sensor, Servo, and Arduino UNO.  

### Other Projects

* **EXPEVER :** Expert EV/HEV Prime-mover Selection System (EXPEVER) is an intelligent selection system for EV/HEV prime-mover parts. ([report]({{ site.baseurl }}/projects/expever/))
* **Solar Electricity Generation forecasting :** Implementing Machine Learning models for Solar Electricity Generation forecasting problems with weather parameters as inputs. ([report]({{ site.baseurl }}/projects/solar/))
* **Coefficient of Drag using Accelerometer Drop Test :** Researched on a drop-test method for finding Coefficient of Drag for a model airplane. ([link]({{ site.baseurl }}/projects/drag/))
* **Fabrication of Microfluidic Electrochemical Sensors :** Developed a novel method for fabrication of PoC Electrochemical Sensors at MEMS Lab, BITS Hyderabad. ([report]({{ site.baseurl }}/projects/mems/))

<!--ul class="posts">
	<li>
		<a href="{{ site.baseurl }}/projects/dextroid/" style="text-decoration:none;">
		<img src="../assets/img/dextroid2.png" alt="Dextroid -The Humanoid" style="float:left;width:120px;height:80px;border-color: white">
    <p> 
				<b>
				   &nbsp;&nbsp; Dextroid -The Humanoid
				</b>
			</p>
		</a>
	</li>
	<br/>
  <br/>
	<li>
		<a href="{{ site.baseurl }}/projects/alfa/" style="text-decoration:none;">
		<img src="../assets/img/alfa3.jpg" alt="ALFA" style="float:left;width:120px;height:80px;border-color: white">
			<p>
				<b>
			  	&nbsp;&nbsp; ALFA -APTRI Labs Floor Assistant
				</b>
			</p>
		</a>
	</li>	
	<br/>
  <br/>
</ul-->
	
<!--div class="projects grid">

  {% assign sorted_projects = site.projects | sort: "importance" %}
  {% for project in sorted_projects %}
  <div class="grid-item">
    {% if project.redirect %}
    <a href="{{ project.redirect }}" target="_blank">
    {% else %}
    <a href="{{ project.url | relative_url }}">
    {% endif %}
      <div class="card hoverable">
        {% if project.img %}
        <img src="{{ project.img | relative_url }}" alt="project thumbnail">
        {% endif %}
        <div class="card-body">
          <h2 class="card-title text-lowercase">{{ project.title }}</h2>
          <p class="card-text">{{ project.description }}</p>
          <div class="row ml-1 mr-1 p-0">
            {% if project.github %}
            <div class="github-icon">
              <div class="icon" data-toggle="tooltip" title="Code Repository">
                <a href="{{ project.github }}" target="_blank"><i class="fab fa-github gh-icon"></i></a>
              </div>
              {% if project.github_stars %}
              <span class="stars" data-toggle="tooltip" title="GitHub Stars">
                <i class="fas fa-star"></i>
                <span id="{{ project.github_stars }}-stars"></span>
              </span>
              {% endif %}
            </div>
            {% endif %}
          </div>
        </div>
      </div>
    </a>
  </div>
{% endfor %}

</div-->