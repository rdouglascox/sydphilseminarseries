
# Sem 2, 2024

<ul>
{% for sem in site.data.sem2_2024 %}
    {% if sem.week %}
    <li>Week {{ sem.week }} </li>
    {% endif %}
    {% if sem.date %}
    <li>{{ sem.date }} </li>
    {% endif %}
    {% if sem.speaker %}
    <li>Speaker: {{ sem.speaker }}{% if sem.speaker %}, {{ sem.affiliation }} {% endif %} </li>
    {% else %} 
    <li>Speaker: TBA</li>  
    {% endif %}
    {% if sem.title %}
    <li>Title: {{ sem.title }} </li>
    {% endif %}
    {% if sem.abstract %}
    <li>Abstract: {{ sem.abstract }} </li>
    {% endif %}
    {% if sem.notes %}
    <li>Note: {{ sem.notes }} </li>
    {% endif %}

{% endfor %}
</ul>

Previous semesters: [Archive](archive.html)


