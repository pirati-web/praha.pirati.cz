---
date:         2017-10-10
category:     blog
tags:         informatika smart-cities
layout:       post
title:        "Předražený internet na Petříne"
image:        petrin-wifi.jpg
author:       Ondřej Profant
---

Piráti nesouhlasí se zakázkou za 2 292 992,- Kč bez DPH na pokrytí Petřínské lanovky internetem.

> "Tato zakázka není snahou o zabepečení internetu pro širokou veřejnost, nýbrž snahou utratit miliony korun u soukromého subjektu, jehož dřívější dodávky [byly pokutovány][UOHS] Úřadem pro hospodářskou soutěž (ÚHOS). Parametry zakázky nejsou přiměřené danému cíli, kterého se město snaží dosáhnout - tedy poskytnutí internetu široké veřejnosti v rekreačních prostorách parku. To je problém srovnatelný například s poskytováním internetových připojení v kavárnách nebo knihovnách. Namísto toho se nakupuje předimenzovaný hardware, který je vhodný pro obsluhu rozsáhlých sítí." říká Ondřej Profant, zastupitel a člen komise Smart Cities za Piráty.

Město také mohlo využít dotačního programu [WIFI4EU][], namísto toho chce investici pokrýt samo z vlastních zdrojů. Provoz této sítě má navíc stát daňové poplatníky dalších až 400 000 Kč každý rok. Vypadá to, že se rodí nová Praha bezdrátová, která stála 390 mil. Kč, ale nikdy nezačala ani nefungovat. Municipalita by měla vytvářet prostor pro budování infrastruktury, nikoli ji neefektivně budovat.

## Dynamický nákupní systém

Z projektu je zřejmé megalomanství magistrátu nebo v horšímm případě cílená preference konkrétních dodavatelů. Magistrát zavedl dynamický nákupní systém (DNS), kde jsou vysoké požadavky např. na předchozí zkušenost (3 zakázky za 40 000 000 Kč bez DPH). To je v mnoha případech správné (např. dodávka HW), avšak magistrát ignoruje malou míru reálné soutěže v tomto systému (zvláště u běžného HW). Což ukazuje i tato zakázka. Ondřej Profant k tomu dodává:

> "Přihlásil se jediný uchazeč - firma Simac Technik ČR a.s. To je velmi zvláštní, protože v Praze je množství provozovatelů připojení k internetu pomocí WIFI. Tito poskytovatelé téměř vždy poskytují i venkovní pokrytí. Viditelně pro ně podmínky DNS a zakázky byly nepřijatelné. Soutěži jistě také nepomohlo, že soutěž trvala pouze 10 pracovních dnů."

## Technické problémy zadávací dokumentace

Celé řešení je dimenzováno pro ohromný provoz s velkou spolehlivostí, což je pro veřejnou WIFI naprosto zbytečné. Požadované řešení spíš odpovídá budování datového centra či jiného zařízení, kde je kritcká vysoká dostupnost. Zde se bavíme o připojení jako doplňkové službě, kdy drobný výpadek či odstávka není žádný problém. Navíc jsou v daném místě dostupné veřejné LTE sítě, které nabízejí dostatečné řešení s náklady pár set tisíc korun i s provozem. Stejně tak vyšší latence je pochopitelná. Některé prvky jsou dokonce v kontextu řešení zcela nevyužitelné. Nestandartní a předimenzovaný hardware vyžaduje výrazně dražší údržbu než běžně používané zařízení.

Požadavky jsou vidtelně psány tak, aby zvítězilo řešení od firmy Cisco, což není poprvé. Již jsme na to upozorňovali u [datového centra][DC05].

Konkrétně špatně je např:

1. Požadavek na USB A u routerů: pravděpodobně se jedná o možnost připojení záložního LTE připojení. Nicméně USB A dongle není rozumná záloha pro takovouto soustavu. Nejspíše nejjednodušší by bylo nechat připojení bez zálohy. Pokud zálohu, tak sofistikovanější. A v zadávací dokumentaci by mělo být co je požadováno. Nikoliv port navíc, který nedává v kontextu smysl.
2. Požadavek na firewall s propustností 4Gb za sekundu, když připojení lokálně bude 1Gb za sekundu a velmi pravděpodobně samotné spojení dál bude ještě pomalejší, opět nedává jiný smysl, než prodražení zakázky.
3. Požadvek na IPv4 multicast je technologie, pro kterou není na Petříně využití a opět je v zadávací dokumentaci.
4. Požadavek na "Nástroj pro kontrolu SLA" se používá v datových centrech, pro zaručení dostupnosti typu 99.99%, avšak to opět není úplně nutné pro Petřín, kde nezáleží na mikrovýpadcích a lze pouzít jiné systémy kontroly.
5. Požadavek na 4000 virtuálních sití (VLAN), což zde nebude potřeba. Velmi pravděpodobně bude potřeba jednotek VLAN, což zvládá kdekterý wifi kontroler.
6. 200 000 záznamů v routovací tabulce je opět nesmysl. Routování zde bude probíhat velmi jednoduše, protože všechen provoz bude směřován do veřejného internetu. Opět se jedná o řešení, které se používá při propojování spíše metropolitních sití.
7. Pro relativně běžnou nekritickou věc je potřeba přehršel certifikátů pro pracovníky, což samozřejmě značně prodražuje řešení.

## Dlouhodobé problémy

Takto špatné zadání však není ojedinělé. Předimenzované technické parametry, které vedou k absenci reálné soutěže jsou v prostředí Prahy na denním pořádku. Obdobnou zakázku v současnosti vypisuje i dopravní podnik.

Problémem je, že magistrát ani další instituce města nemají žádnou sebereflexi. Obdobné zakázky vznikají pořád. Občas jsou pod tlakem veřejné kritiky staženy, avšak nic to nemění na faktu, že vznikají. Což je dánou buď neodborností, anebo snahou zakázky prodražit, či přihrát konkrétnímu dodavateli. Namísto snahy o nápravu jsou nám předkládány pseudoargumenty, např:

- "Nejedná se o připojení lanovky, ale celého petřínského vrchu": přímo ve stručném popisu zakázky se hovoří o: "Dodávka přístupových prvků WiFi, jejich instalace a propojení tak, aby pokryly stanovené prostory (pokrytí trasy pozemní lanové dráhy Újezd – Nebozízek – Petřín a prostor ve stanicích Újezd a Petřín lanové dráhy).", v příloze 2 je dokonce přiložena mapa konkrétních bodů výhradně po trase lanovky
- "Bezpečnost": pokud v argumentaci neví kudy kam, tak je vždy jednoduché svést všechno na bezpečnost. Ale zde máme standardní instalaci internetového připojení do veřejného prostoru jako v kdejaké kavárně, benzínce či nákupním centru. Bezpečnost je běžnou součástí projektu, nesmí být zcela ignorována, ale je srovnatelná se všemi dalšími instalacemi veřejného internetu.


## Zdroje

- [Veřejná zakázka](https://www.tenderarena.cz/profil/zakazka/detail.jsf?id=97581)
- [Usnesení rady R-2379 o výběru jediného uchazeče](http://zastupitelstvo.praha.eu)
- [Pravomocná rozhodnutí UOHS ve věci SIMAC/ČD-T/ČD][UOHS]
- [Zakázka na datové centrum psaná na míru][DC05]
- [Dotační program WIFI4EU][WIFI4EU]
- [Praha bezdrátová][praha-bezdratova]
- [Provozní náklady dle ředitele OICT](https://zpravy.aktualne.cz/regiony/praha/wi-fi-za-2-3-milionu-neni-jen-pro-lanovku-chceme-pokryt-cely/r~fab06f5cadc911e7a7000025900fea04/)

[UOHS]: https://www.uohs.cz/cs/verejne-zakazky/aktuality-z-verejnych-zakazek/2122-ceske-drahy-chybovaly-v-zakazce-na-vybaveni-railjetu-wi-fi-technologii.html
[DC05]: https://praha.pirati.cz/zakazka-psana-na-miru.html
[WIFI4EU]: https://ec.europa.eu/digital-single-market/en/wifi4eu-bezplatne-wifi-pripojeni-pro-obyvatele-eu
[praha-bezdratova]: https://technet.idnes.cz/konec-bezdratoveho-internetu-v-praze-dwv-/sw_internet.aspx?c=A120522_160155_sw_internet_vse
