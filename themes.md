---
layout: default
title: Jekyll Themes
---

<ul class="posts-list">
    {% for themes in site.themes %}
        <li>
            <h3>
                <a href="{{ site.baseurl }}{{ themes.url }}">
                    {{ themes.title }}
                </a>
                <p class="post-excerpt">{{ themes.description | truncate: 160 }}</p>
            </h3>
        </li>
    {% endfor %}
</ul>