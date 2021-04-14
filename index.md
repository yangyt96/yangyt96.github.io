# Welcome to yangyt96 space

This is a working journal that I would like to share some problem that I have encountered and engineering contents that I have solved it.

## Blog post
{% for file in site.static_files %}
{% if file.extname == ".md" and file.basename != "index" %}

[{{ file.basename }}]({{site.baseurl}}{{file.path}})

{{ file.basename }}

{{ file.path }}

{{file.name}}


{% endif %}
{% endfor %}


{% for page in site.html_pages %}

{{page.title}}

{{page.url}}

{% endfor %}