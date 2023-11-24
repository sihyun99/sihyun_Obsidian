---
layout: page
title: Home
id: home
permalink: /
---

# 방패맨의 기술 블로그

<template> 테스트 아아</template>
<p style="padding: 3em 1em; background: #f5f7ff; border-radius: 4px;">
  성장과 적응, 그리고 각종 IT 기술 정리 블로그,
  BackEnd개발자의 적응일기
</p>



<strong>최근 문서</strong>

<ul>
  {% assign recent_notes = site.notes | sort: "last_modified_at_timestamp" | reverse %}
  {% for note in recent_notes limit: 5 %}
    <li>
      {{ note.last_modified_at | date: "%Y-%m-%d" }} — <a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">{{ note.title }}</a>
    </li>
  {% endfor %}
</ul>

<style>
  .wrapper {
    max-width: 46em;
  }
</style>
