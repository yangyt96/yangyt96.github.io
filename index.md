# Welcome to yangyt96 space

This is a working journal that I would like to share some problem that I have encountered and engineering contents that I have solved it.

## Blog post
{% for file in site.static_files %}
{% if file.extname == ".md" && file.basename != "index" %}
[{{ file.basename }}]({{site.baseurl}}/{{file.basename}}.html)

file.path

file.name


{% endif %}
{% endfor %}

<!-- - [Petalinux on Windows 10 with WSL](./blog/2021/petalinux-on-windows-10-with-wsl.md) -->