---
title: People
permalink: /people/
---

{% assign people_sorted = site.people | sort: 'year' | reverse %}
{% assign role_array = "pi|postdoc|gradstudent|undergrad|researchstaff|visiting|others|alumni" | split: "|" %}

{% for role in role_array %}

{% assign people_in_role = people_sorted | where: 'position', role %}

<!-- {{ role }}
{{ people_in_role.size }} -->


<!-- Skip section if there's nobody -->
{% if people_in_role.size == 0 %}
  {% continue %}
{% endif %}

{% if role == 'others' %}
  {% continue %}
{% endif %}


{% if role != 'pi' %}
<hr>
{% endif %}


<div class="pos_header">
{% if role == 'postdoc' %}
<h3>Postdoctoral Scholars</h3>
 {% elsif role == 'pi' %}
<h3>Principal Investigator</h3>
 {% elsif role == 'gradstudent' %}
<h3>Graduate Students</h3>
 {% elsif role == 'undergrad' %}
<h3>Undergraduate Students</h3>
 {% elsif role == 'researchstaff' %}
<h3>Research Staff</h3>
 {% elsif role == 'visiting' %}
<h3>Visiting Scholars</h3>
 {% elsif role == 'others' %}
<h3>Honorary Members</h3>
 {% elsif role == 'alumni' %}
<h3>Alumni</h3>
{% endif %}
</div>

<div class="content list people">
  {% for profile in people_sorted %}
    {% if profile.position contains role %}
      <div class="list-item-people">
        <p class="list-post-title">
          <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail" src="{{site.baseurl}}/images/people/{{profile.avatar}}"></a>
          <a class="name" href="{{ site.baseurl }}{{ profile.url }}">{{ profile.name }}</a>
        </p>
      </div>    
    {% endif %}
  {% endfor %}
</div>

<!-- 
DO FOR ALUMNI
| Who are they | When were they here | Where they went |
| :------------- |:-------------| :-----------|
| Alum Ni | Student | Professor, Department, University | -->

{% endfor %}
