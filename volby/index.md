---
layout: elections-2020
title: Volby do zastupitelstva hl. m. Prahy 2022
campaignGroupUid: volby-2022
campaignCategoryUid: 2022-krajske
candidateListUid: 2022-krajske
hideCandidateSocialProfiles: true
heroBgImg: kampan20/zahajenikampan.jpg
---

{% assign candidates = site.candidatelists | where: "uid", page.candidateListUid | first %}

{% capture mainContent %}
  <h1 class="head-alt-lg md:head-alt-xl text-center">Krajské volby 2022</h1>
{% endcapture %}

{% capture subContent %}
  <h2 class="head-xs md:head-base mt-2 text-center">Šance <strong>změnit budoucnost</strong></h2>
{% endcapture %}