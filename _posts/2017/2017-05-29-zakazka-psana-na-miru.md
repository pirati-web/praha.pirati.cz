---
date:         2017-05-29
category:     blog
tags:         [IT]
layout:       post
title:        "Zakázka na datové centrum psaná na míru"
image:        posts/dc04.jpg
author:      Ondřej Profant
---

Pražský magistrát (MHMP) vypsal zakázku v hodnotě 38 000 000 Kč na vybavení datového centra, jejíž parametry jsou tak podivné, že vzbuzují pochybnosti o faktické otevřenosti soutěže. Hlavní problémy soutěže dle Pirátů:

* Uchazeči měli na podání nabídek pouze 11 pracovních dnů.
* Některé specifikace jsou převzaty z marketingových letáků konkrétních dodavatelů (Hewlett-Packard, Cisco).
* Předimenzované požadavky na server, které splňuje jen několik málo výrobků. Přitom by bylo vhodnější pořídit více serverů místo jednoho. 
* V rámci diskového pole je požadována podpora Dockeru, což je technologie, která se na MHMP nepoužívá ani ve strategických dokumentech není zavedena. Piráti sami tuto technologii používají, ale nemyslíme si, že je vhodná pro nasazení v rámci magistrátu.
* Konzervováni využívání technologií (např. VMware, Oracle), které lze nahradit otevřenými alternativami a snížit tak vendor lock-in a cenu.
* V případě takto odborné zakázky bychom doporučili postupovat formou soutěžního dialogu, aby se případné problematické části opravili a zakázka byla reálně otevřenou pro celou šíři možných dodavatelů.

### Průběh

První alarmující skutečností je termín vypsání veřejné zakázky. Ta byla vypsána 4. 4., s datem odevzdání do 20. 4. 2017, na podání nabídek měli tedy zájemci pouze 11 pracovních dní.[^3] Po urgencích ze stran dodavatelů dne 19. 4. (čili v předposlední den) prodloužil lhůtu na 26. 4. 2017 (do 13:00), tedy o 4 pracovní dny. Je patrné, že MHMP vůbec nepředpokládá, že by uchazeči na přípravu nabídky potřebovali čas – nejspíše proto, že všichni zúčasnění byli o zakázce informování předem. Je těžko uvěřitelné, že by uchazeč dokázal připravit nabídku takto rozsáhlé a technologicky náročné realizace obratem.

Datové centrum mělo bylo projednáno na komisí ICT Rady hl. m. Prahy dne 9. 5., avšak vedení města se neobtěžovalo k tomuto bodu jednání dodat podklady. Následně byla schůze komise pro nezájem (!) 2x přesunuta. Když se konečně komise 22. 5. sešla, tak jednala bez písemného podkladu. Ondřej Profant vznesl připomínky, ale zbytek komise neprojevil sebemenší vůli věc řešit. Ale tím pochybnosti zdaleka nekončí.

Je důležité si uvědomit, že se jedná pouze o první zakázku v dlouhém životním cyklu tohoto datového centra. Výrobce, který dodá tento základ, bude ještě velmi dlouho těžit z dodávek kompatibilních, nebo přímo identických zařízení při rozšiřování nebo nahrazování kapacit.

MHMP již velmi dlouho nepořizoval takto ucelené řešení. Potenciál uvázání se k jedinému dodavateli je v případě této zakázky výrazně vyšší než u ostatních datových center, která jsou v pokročilejší fázi svého životního cyklu. Hrozí tak klasický vendor lock-in.

### Síť

Síťová část zcela jednoznačně odkazuje na produkty Cisco, konkrétně Cisco ASA, Cisco ACI s Nexus řadou a Cisco Catalyst switch.[^4] Příkladem budiž požadavek na “Výkon aplikačního firewallu NGFW k hodnotě velikosti HTTP packetu 440B”, což je přímá citace z materiálů společnosti Cisco.[^5] Nebo “280 milionů kategorizovaných URL”, což je citace z popisu Cisco ASA 55xx.[^6]

### Servery

Požadavky na jednotlivé servery jsou jednoznačně předimenzované.[^7] Dnešním trendem je použít cluster více běžnějších serverů, které jsou lehce nahraditelné. Vysoké požadavky vedou k špatně nahraditelnému hardware. Přitom dnes je vše virtualizováno, čili nezáleží na tom, kolik fyzických serverů tam je.

Potenciálním problémem těchto monstrozních serverů je licencování aplikací. Například licenční podmínky společnosti Oracle vyžadují, aby byl vždy licencován celý fyzický hardware, i když se nevyužívá pouze k běhu aplikace Oracle. Schopnost členění stroje (multitenancy), který je v zadávacích podmínkách vyžadován, tedy nedává smysl – Praha by stejně musela platit licence za celý stroj.

Dalším problémem je nákup licencí VMware vSphere Enterprise Plus[^8], které by šly nahradit (komerčním) open source řešením, například oVirt (reps. Red Hat Enterpise Virtualization). Což by například vyřešilo problém, že pražský magistrát pravidelně nestíhá podporu přesoutěžit. Čili v době bez podpory by měl komunitní podporu (lepší než žádná) a po vysoutěžení by měl profesionální podporu - což dnes ale vůbec není běžné. Alternativně by bylo možné učinit přechod na jinou technologii mnohem snáze než z proprietálního řešení.[^9]

### Úložiště

Úložiště jednoznačně odkazuje na produkt HPE 3PAR 8440.[^10] Navíc je zde požadavek na integraci opět pouze s proprietárními hypervizory.
Integrace úložiště obsahuje pasáž: “Integrace minimálně s aplikacemi Oracle DB a MS SQL (vytváření aplikačně konzistentních snapshotů).”, čili prohlubuje vendor lock-in na databázi.

Velmi zajímavý je též požadavek na podporu Dockeru/Flockeru. Vzhledem k tomu, že tato technologie se vyznačuje tím, že vše definuje softwarově, není ze strany úložiště potřeba žádná další podpora. Požadovaná funkce je velice progresivní technologií odbourávání virtualizační vrstvy (přitom v dodávce je požadavek na VMware pro virtualizaci) ve prospěch jednoduššího systému pro paralelní provoz aplikací výhradně na platformě Linux.

Ovšem vzhledem k tomu, že součástí dodávky není žádný nástroj pro orchestraci flotily serverů určených k provozu kontejnerů a samotných kontejnerů, tedy například Red Hat Open Shift, nezbývá nám, než se domnívat, že byl tento požadavek v zadání uveden pouze z důvodu ještě více pojistit vítězství konkrétního dodavatele, přesněji HPE, které poskytuje u svých diskových polí 3PAR tuto technologii.[^11]

Představa, že by se MHMP zmohl na nasazení technologie kontejnerů do konce této dekády se nám, vzhledem k aktuálním obtížím, jeví jako naprosto naivní, ba dokonce směšná a v rámci strategie se zatím v žádném materiálu magistrátu o Dockeru nemluvilo.

### Tržní prostředí

Bohužel větší srozumitelnosti a otevřenosti obdobných zakázek nepomáhá ani trh. Každý výrobce vymýšlí nové způsoby jak se odlišit, namísto spolupráce na všeobecných standardech. Věci, které je leckdy rozumné dělat softwarově, řeší uzavřeně hardwarově. Kvůli tomu je velmi těžké obdobné zakázky vypsat správně.

Dalším problémem jsou oficiální ceníky, které vždy uvádí značně nadsazenou cenu. Vždy je však přítomna nějaká sleva (běžně v řádu desítek procent) a výrobce ji využívá mimo jiné i pro zvýhodnění partnerů, kteří si tu kterou zakázku registrují jako první. Taková veřejná zakázka vypadá obvykle tak, že se výrobce a zákazník předem dohodnou na dodávce. Výrobce následně vybere 3 své partnery, z toho 2 jako takzvané „křoví“. O tom, který ve výběrovém řízení na cenu zvítězí, pak nerozhoduje ani kvalita, ani cena jeho práce, ale sleva od původního výrobce. Nicméně to, že oficiální ceny ani náznakem neodpovídají cenám reálným jistě, nepodporuje kvalitní tržní prostředí.

### Výsledek

Byly podány 4 nabídky:

|IČO     | Název               | Nabídková cena (bez DPH)|
|--------|---------------------|------------------------:|
|60779420| SÍŤ, spol. s r.o.   |             34 381 818,9|
|25715909| AMI Praha a.s.      |             37 987 456,0|
|48113336|ELSO PHILIPS SERVICE, spol. s r.o.|37 282 300,0|
|16188781| Com-Sys TRADE spol.s r.o.|        37 645 300,0| 
 
Neznáme jejich přesný obsah. Nicméně je vidět, že 3 nabídky se umístily nápadně blízko vedle sebe. Čtvrtá nabídka podle našich informací nesplňuje zadání (právě ta diskriminační kriteria psaná pro jednoho výrobce). 

### Disclaimer

Jsme si vědomi, že mnoho věcí může být v nějakém kontextu opodstatněno. V zadávací dokumentaci je více zvláštních věcí. Např. požadavek na rozlišení 1600x1200 u grafické konzole, avšak takovými věcmi se nezabýváme. Popřípadě vysoce odborné věci. Řešíme nejviditelnější případy, kdy je jasné, že je zakázka psána na míru. Pokud si jí podrobně přečtete, tak zjistíte, že je tam jistě mnoho dalších zvláštních věcí.

---

[^1]: Viz https://www.tenderarena.cz/profil/zakazka/detail.jsf?id=87558
[^2]: Označovaného DC04
[^3]: V termínu jsou velikonoční svátky, pracovní dny: 4.-7. (4), 10-13 (4) a 18-20 (3), 4+4+3=11
[^4]: "NextGen IPS" a "NextGen FW"
[^5]: Viz https://www.slideshare.net/CiscoPublicSector/cisco-firepower-nextgeneration-firewall-solutions
[^6]: Viz http://www.brinel.ro/Cisco-securitatea_retelei/Cisco_ASA_5500-X_Series_with_FirePOWER_Services.sflb.ashx "Number of URLs categorized More than 280 million"
[^7]: V části “1. Výpočetní infrastruktura pro kritické aplikace” je požadován stroj s až 80 CPU jádry, 4TB ram s možností multitenancy. Navíc je požadován takový výkon, na který dosáhne jen 144 strojů ze 44 tisíc hodnocených webem spec.org (SPECint®_rate2006 alespoň 4260 bodů).
[^8]: Část 5. Softwarové licence
[^9]: Opensource na opensource se zpravidla migruje výrazně snáze než proprietární řešení (minimálně s prvky vendor lock-inu) na opensource.
[^10]: Řadiče musí být osazeny dostatečně dimenzovanými zdroji (min. 12 samostatných CPU jader a min. 96 GB RAM na řadič)”  - Požadovaná hodnota 12 CPU jader, snížených na 10 CPU jader při užití na specializovaného obvodu  ukazuje na HP 3Par 8440. Počet jader v CPU diskového pole nemá přímou souvislost s výkonem pole který je dodán připojeným serverům. 
[^11]: Viz http://www.techazine.com/2016/06/16/hpe-introduces-native-docker-drivers-for-3par-and-storevirtual/
