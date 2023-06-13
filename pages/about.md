---
layout: page
title: About
permalink: /about/
weight: 3
---

# **About Me**

안녕하세요 :slightly_smiling_face:  **{{ site.author.name }}** 입니다.<br>
어쩌구저쩌고 샬라샬라

<div class="row">
{% include about/skills.html title="Programming Skills" source=site.data.programming-skills %}
{% include about/skills.html title="Other Skills" source=site.data.other-skills %}
</div>

<div class="row">
{% include about/timeline.html %}
</div>