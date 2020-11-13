---
layout: default
title: Daily History
---

<ul class="posts-list">
    {% for daily in site.daily %}
        <li>
            <h3>
                <a href="{{ site.baseurl }}{{ daily.url }}">
                    {{ daily.title }}
                </a>
                <p class="post-excerpt">{{ daily.description | truncate: 160 }}</p>
            </h3>
        </li>
    {% endfor %}
</ul>