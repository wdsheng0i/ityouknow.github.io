---
layout: page
title: jvm  
titlebar: jvm
subtitle: <span class="mega-octicon octicon-clippy"></span> &nbsp;&nbsp; Java 人的精神家园。>&nbsp;&nbsp;>&nbsp;&nbsp;<a href ="http://www.justdojava.com/" target="_blank" ><font color="#EB9439">点我直达 justdojava</font></a>
menu: jvm
css: ['blog-page.css']
permalink: /jvm
---

<div class="row">

    <div class="col-md-12">

        <ul id="posts-list">
            {% for post in site.posts %}
                {% if post.category=='jvm' or post.keywords contains 'jvm' %}
                <li class="posts-list-item">
                    <div class="posts-content">
                        <span class="posts-list-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
                        <a class="posts-list-name bubble-float-left" href="{{ post.url }}">{{ post.title }}</a>
                        <span class='circle'></span>
                    </div>
                </li>
                {% endif %}
            {% endfor %}
        </ul> 

        <!-- Pagination -->
        {% include pagination.html %}

        <!-- Comments -->
       <div class="comment">
         {% include comments.html %}
       </div>
    </div>

</div>
<script>
    $(document).ready(function(){

        // Enable bootstrap tooltip
        $("body").tooltip({ selector: '[data-toggle=tooltip]' });

    });
</script>