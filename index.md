### Sem 1, 2025

<ul>
{% for sem in site.data.sem2_2025 %}
    {% if sem.week %}
    <li><b>Week {{ sem.week }}
    {% endif %}
    {% if sem.date %}
    , {{ sem.date }}
    {% endif %}
    </b>
    </li> 
    {% if sem.speaker %}
    <ul>
    <li>Speaker: {{ sem.speaker }}{% if sem.affiliation %}, ({{ sem.affiliation }}) {% endif %} </li>
    {% if sem.title %}
    <li>Title: {{ sem.title }} </li>
    {% endif %}
    {% if sem.abstract %}
    <li>Abstract: {{ sem.abstract }} </li>
    {% endif %}
    {% if sem.notes %}
    <li>Note: {{ sem.notes }} </li>
    {% endif %}
    </ul>
    {% else %}  
    <ul>
    <li>Speaker: TBA</li>  
    </ul>
    {% endif %}
{% endfor %}
</ul>

### Previous Speakers 

{% for sem in site.data.previous reversed %}{% if sem.speaker %}{{ sem.speaker }}{% if sem.affiliation %} ({{ sem.affiliation }}){% endif %}{% endif %}, {% endfor %}...
