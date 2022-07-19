---
layout: communal-elections
title: Volby do Zastupitelstva hl. města Prahy 2022
campaignGroupUid: volby-2022
campaignCategoryUid: 2022-komunalni
candidateListUid: 2022-komunalni
customizeHeader: true
---

{% capture mainContent %}
  <h1 class="head-alt-lg md:head-alt-xl text-center">Komunální volby 2022</h1>
{% endcapture %}

{% capture subContent %}
<h2 class="head-xs md:head-base mt-2 text-center"><strong>Máme odvahu řídit Prahu správně!</strong></h2>  
<h2 class="head-xs md:head-base mt-2 text-center"><strong>Díky důvěře Pražanů a stabilitě v koalici jsme mohli naše město 4 roky vést a měnit jej k lepšímu a také ho provést dvěma bezprecedentními krizemi. Praha za naší vlády prochází rekordním rozvojem. Zahájili jsme stavbu metra D, první nové linky po 40 letech. Loni se povolila stavba 9.700 nových bytů, což je rekord od roku 1989. Nebývalým tempem se prodlužují tramvajové trati. Otevřeli jsme rekordní množství nových P+R parkovišť. Za našich předchůdců mosty chátraly a padaly, my máme odvahu jít do velkých rekonstrukcí, bez kterých by spadly další. A nadto stavíme i nová přemostění řeky. Plán na výsadbu milionu nových stromů plníme přesně jak jsme slíbili.</strong></h2>

{% endcapture %}

{% assign candidates = site.candidatelists | where: "uid", page.candidateListUid | first %}

{% include elections-header.html img=page.img bgImg=page.heroBgImg mainContent=mainContent subContent=subContent candidateListNumber=candidates.number %}

