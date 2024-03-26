---
layout: communal-elections
title: Volby do Senátu 2024
campaignGroupUid: volby-2024
campaignCategoryUid: 2024-senat
candidateListUid: 2024-senat
customizeHeader: true
---

{% capture mainContent %}
  <h1 class="head-alt-lg md:head-alt-xl text-center">Volby do Senátu 2024</h1>
{% endcapture %}

{% capture subContent %}
<h2 class="head-xs md:head-base mt-2 text-center"><strong>Máme odvahu řídit Prahu správně!</strong></h2>  
<h2 class="head-xs md:head-base mt-2 text-center">TEXT</h2>

{% endcapture %}

{% assign candidates = site.candidatelists | where: "uid", page.candidateListUid | first %}

{% include elections-header.html img=page.img bgImg=page.heroBgImg mainContent=mainContent subContent=subContent candidateListNumber=candidates.number %}

