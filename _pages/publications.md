---
layout: single
classes: wide
author_profile: True 
permalink: /publications/
title: "Publications"
excerpt: "List of Publications of Mohammad Sadegh Akhondzadeh"
toc: False
sidebar:
  nav: "publinav"
---


A complete list of my publications are available in my [Google Scholar profile](https://scholar.google.com/citations?user=zmlh-HMAAAAJ&hl=en), or in my [Reasearch Gate profile](https://www.researchgate.net/profile/Mohammad_Sadegh_Akhondzadeh).

{% assign cur_year = 2022 %}

{% for publication in site.data.papers %}
  {% if publication.issued.date-parts[0][0] != cur_year and publication.issued.date-parts[0][0] < cur_year %}
    {% assign cur_year = publication.issued.date-parts[0][0] %}
## {{ publication.issued.date-parts[0][0] }}
  {% endif %}
<p>
<div itemscope itemtype="http://schema.org/ScholarlyArticle">
  {% case publication.type %}
    {% when 'book' %}
     <span class="btn btn--primary btn--small" style="padding: 0.1em 0.5em;">Book</span>
    {% when 'article-journal' %}
     <span class="btn btn--warning btn--small" style="padding: 0.1em 0.5em;">Journal</span>
    {% when 'paper-conference' %}
     <span class="btn btn--info btn--small" style="padding: 0.1em 0.5em;">Conference</span>
     {% when 'paper-workshop' %}
     <span class="btn btn--success btn--small" style="padding: 0.1em 0.5em;">Workshop</span>
     {% when 'archival' %}
     <span class="btn btn--success btn--small" style="padding: 0.1em 0.5em;">Archival</span>
     {% when 'chapter' %}
     <span class="btn btn--success btn--small" style="padding: 0.1em 0.5em;">Book Chapter</span>
     {% when 'editorial' %}
     <span class="btn btn--primary btn--small" style="padding: 0.1em 0.5em;">Editorial</span>
     {% when 'preprint' %}
     <span class="btn btn--primary btn--small" style="padding: 0.1em 0.5em;">Pre Preint</span>
    {% else %}
     <span class="btn btn--danger btn--small" style="padding: 0.1em 0.5em;">Other</span>
  {% endcase %}
  
  {% for auth in publication.author %}<span style="font-size: 0.8em;" itemprop="author">{{ auth.given }} {{ auth.family }}{% if forloop.last == false %}, {% else %}.{% endif %}</span>{% endfor %}
  <br/>
  <em><span style="text-transform:uppercase" itemprop="name">{{ publication.title }}</span></em>.
  <div style="font-size: 0.7em; text-transform:uppercase" itemprop="isPartOf" itemscope itemtype="http://schema.org/Periodical">
    <span itemprop="name">{{ publication.container-title }}.</span>
  {% if publication.publisher %}
    <span>{{ publication.publisher }}.</span>
  {% endif %}
  {% if publication.collection-title %}
    <span>{{ publication.collection-title }}.</span>
  {% endif %}
  {% if publication.issue %}
    <span>Issue: {{ publication.issue }}.</span>
  {% endif %}
   {% if publication.volume %}
    <span>Volume: {{ publication.volume }}.</span>
  {% endif %}
  {% if publication.page %}
    <span>Pages: {{ publication.page }}.</span>
  {% endif %}
  </div>
  [<span style="padding: 0.1em 0.1em;"><i class="fas fa-link"></i></span><span style="padding: 0.1em 0.1em;"><a target="_blank" href="{{ publication.URL }}">DOI</a></span>]
  {% if publication.code %}
    [<span style="padding: 0.1em 0.1em;"><i class="fas fa-link"></i></span><span style="padding: 0.1em 0.1em;"><a target="_blank" href="{{ publication.code }}">Code</a></span>]
  {% endif %}
  
  {% if publication.preprint %}
    [<span style="padding: 0.1em 0.1em;"><i class="fas fa-file-pdf"></i></span><span style="padding: 0.1em 0.1em;"><a target="_blank"  href="{{ publication.URL }}">Pre-Print</a></span>]
  {% endif %}
</div>
</p>
{% endfor %}