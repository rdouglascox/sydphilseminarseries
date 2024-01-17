
### Sem 2, 2024

<ul>
{% for sem in site.data.sem1_2024 %}
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



