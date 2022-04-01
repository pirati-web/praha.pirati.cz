---
layout: communal-elections
title: Volby do Zastupitelstva hl. města Prahy 2022
heroBgImg: pice.jpg
campaignGroupUid: volby-2022
campaignCategoryUid: 2022-komunalni
candidateListUid: 2022-komunalni
customizeHeader: true
---

{% capture mainContent %}
  <h1 class="head-alt-lg md:head-alt-xl text-center">Komunální volby 2022</h1>
{% endcapture %}

{% capture subContent %}
  <h2 class="head-xs md:head-base mt-2 text-center"><strong>Odvaha dělat, co je správné!</strong></h2>
{% endcapture %}

{% assign candidates = site.candidatelists | where: "uid", page.candidateListUid | first %}

{% include elections-header.html img=page.img bgImg=page.heroBgImg mainContent=mainContent subContent=subContent candidateListNumber=candidates.number %}

