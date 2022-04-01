---
layout: communal-elections
title: Volby do Zastupitelstva hl. města Prahy 2018
heroBgImg: pice.jpg
campaignGroupUid: volby-2018
campaignCategoryUid: 2018-komunalni
candidateListUid: 2018-komunalni
customizeHeader: true
---

{% capture mainContent %}
  <h1 class="head-alt-lg md:head-alt-xl text-center">Komunální volby 2018</h1>
{% endcapture %}

{% capture subContent %}
  <h2 class="head-xs md:head-base mt-2 text-center">Na prahu změny!</strong></h2>
{% endcapture %}

{% assign candidates = site.candidatelists | where: "uid", page.candidateListUid | first %}

{% include elections-header.html img=page.img bgImg=page.heroBgImg mainContent=mainContent subContent=subContent candidateListNumber=candidates.number %}
