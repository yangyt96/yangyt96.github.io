# Welcome to yangyt96 space

<!-- This is a working journal that I would like to share some problem that I have encountered and engineering contents that I have solved it. -->


<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>