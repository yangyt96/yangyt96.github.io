# Welcome to yangyt96 space

This is a working journal that I would like to share some problem that I have encountered and engineering contents that I have solved it.

## Blog post
{% for page in site.html_pages %}
{% if page.url != "/" %}

[{{page.title}}]({{site.baseurl}}{{page.url}})

{% endif %}
{% endfor %}

{% post_url 2021-04-15-test %}