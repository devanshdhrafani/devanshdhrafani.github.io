---
layout: page
title: Projects
permalink: /projects/
description: 
nav: true
---

### Robotics Projects

<ul class="posts">
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
  <li>
		<a href="{{ site.baseurl }}/projects/3_project/" style="text-decoration:none;">
		<img src="../assets/img/hive-1.jpg" alt="HIVE" style="float:left;width:100px;height:60px;border-color: white" border="8">
			<p>
				<b>
				HIVE: An effort to make multi robot system showcasing Swarm Intelligence.
				</b>
			</p>
		</a>
	</li>
</ul>
	
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
