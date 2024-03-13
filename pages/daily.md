---
layout: page
title: Daily
description: daily 索引页
keywords: daily
comments: false
mermaid: false
menu: 句子
permalink: /daily/
---

> 零散的知识，简短的观点，作为片段汇集于此。


<a href="{{ site.url }}/daily/" style="color:#888;display:inline-block;margin:0 8px;">全部</a>{% for tag in taglist %}<a href="{{ site.url }}/daily/?tag={{ tag }}" style="color:#888;display:inline-block;margin:0 8px;">{{ tag }}</a>{% endfor %}

<ul class="listing">
{% for item in site.daily %}
{% if item.title != "Daily Template" %}
<li class="listing-item" tags="{% for tag in item.tags %}{{ tag }} {% endfor %}">
  <a href="{{ site.url }}{{ item.url }}">{{ item.title }}</a>
  {% for tag in item.tags %}
  <a style="font-size:12px;color:gray;font-style:italic;display:inline-block;margin:0 0 0 4px;padding:0 4px;background-color:lightgray;" href="{{ site.url }}/daily/?tag={{ tag }}" title="{{ tag }}">{{ tag }}</a>
  {% endfor %}
</li>
{% endif %}
{% endfor %}
</ul>

<script>
jQuery(function() {
    function getUrlParam(name) {
        var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)");
        var r = window.location.search.substr(1).match(reg);
        if (r != null) return r[2]; return null;
    }

    var tag = getUrlParam('tag');
    if (tag == undefined || tag === '') {
        return;
    }

    $(".listing-item").each(function() {
        if ($(this).attr('tags').indexOf(tag) < 0) {
            $(this).css('display', 'none');
        }
    });

});
</script>
