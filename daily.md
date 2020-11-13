---
layout: default
title: Daily History
---

<ul class="posts-list">
    {% for daily in site.daily %}
        <h2>
            <a href="{{ daily.url }}">
                {{ daily.title }}
            </a>
        </h2>
        <!-- <p>{{ daily.content | markdownify }}</p> -->
    {% endfor %}
</ul>