# Zkouškové otázky

### 1. Vyjmenujte a stručně charakterizujte vybrané datové sady (jejich obsah) geoprostorových dat s celostátním pokrytím.

- **ZABAGED (Základní báze geografických dat)**
    - **Obsah**: vektorové prvky topografie (komunikace, vodní toky, vegetace, geodetické body)
    - **Účel**: obecné podkladové mapování a GIS analýzy; aktualizována ČÚZK
- **RÚIAN (Registr územní identifikace, adres a nemovitostí)**
    - **Obsah**: administrativní hranice, katastrální území, adresní místa, stavební objekty, parcely (převzaté z KN)
    - **Účel**: jednoznačná identifikace územních prvků a adresního místa
- **Ortofotomapy (letecké snímky)**
    - **Obsah**: barevná rastrová ortofota celého území státu v různých letech/rozlišeních
    - **Účel**: vizuální podklad, analýza pokrytí vegetace, změnové detekce

### 2. Popište základní charakteristiky Informačního systému katastru nemovitostí (ISKN) a jeho vazby na další externí systémy.

Charakteristika
- jednotný celek
- činnosti rozděleny do různých aplikací nad společnou databází
- společné technologické zázemí
- centrální správa a monitoring
- vznik v roce 2001 (migrace z KN2000)
- popisná (SPI) i prostorová (SGI) data v jedné databázi
	- prostorové rozšíření Oracle spatial
- data včetně kompletní historie
- vysoký stupeň bezpečnosti dat i systému
- jakákoliv změna dat svázána s řízením na katastrálním pracovišti
- informace pro externí zákazníky přes Internet
- jeden z největších a nejsložitějších IS ve státní správě (2 TB, 1100 tabulek)

Externí systémy
- Registr obyvatel (ROB)
	- ISEO – Evidence obyvatel – MV
- Registr osob (ROS)
- Registr územní identifikace, adres a nemovitostí (RÚIAN)
- Insolvenční rejstřík

### 3. Popište základní charakteristiky centrální databáze ISKN.

- Oracle 19
- centrální DB (v srpnu 2011 proběhla centralizace ISKN)
- do srpna 2011 na každém KP lokální databáze (celkem 107 databází)

Obecné rozdělení dat
- číselníky (např. katastrální území …)
- minulost (data, která již přestala platit)
- přítomnost (aktuální stav katastru)
- budoucnost (připravovaný stav, změny)
- další data (uživatelská data, …)

Infrastruktura
- 2 nezávislá datová centra v Praze
- 2 nezávislé optické trasy (různí poskytovatelé)
- vzdálenost datových center cca 18 a 20 km (podle trasy vláken)
- produkční systémy jsou provozovány v primární lokalitě
- aktivní-pasivní lokalita, clustery v rámci lokality
- v záložní lokalitě běží testovací prostředí (využití HW)
- data jsou synchronně kopírována do zálohy
- v případě havárie a přesunu do záložní lokality utlumení testovacích prostředí a start produkce

### 4. Popište základní charakteristiky Dálkového přístupu do katastru nemovitostí.

- spuštěn v roce 2004
- placená služba
- umožňuje registrovaným uživatelům on-line přístup k údajům katastru nemovitostí (KN)

Účty
- účty jsou zřizovány na základě žádost
- běžný (úplatný)
	- pro bezúplatný dálkový přístup
	- pro účely vydávání ověřených výstupů z KN
	- pro vyhotovitele a ověřovatele geometrických plánů
- interní

Sestavy
- výpis z KN
- přehled vlastnictví
- přehled vlastnictví s nemovitostmi
- evidence práv pro osobu
- kopie katastrální mapy
+ výstupy ze Sbírky listin opatřeny elektronickou značkou a časovým razítkem

### 5. Vyjmenujte způsoby, jakými je možné dostat data katastru nemovitostí do GIS.

- pomocí WMS, WMTS nebo WFS služby
- importem dat VFK z webu ČÚZK

### 6. Co je a k čemu slouží VFK?

- Výměnný formát KN
- textový soubor, který přenáší údaje evidované v ISKN
- určen k vzájemnému předávání dat mezi systémem ISKN a jinými systémy zpracování dat

Typy exportů
1. **Stavové exporty** obsahují stav dat k určitému datu, vždy pouze platné záznamy
2. **Exporty změn** obsahují pouze změny dat za určité období

### 7. Popište základní schéma e-governmentu ČR.

Informační systém základních registrů
- získání údajů občana

Identita občana
- poskytovatel služeb požaduje ověření
- ověření přes poskytovatele ověření

Poskytovatel služeb
- ČÚZK
- IS datových schránek
- ePortál ČSSZ
- Moje daně
- Portál občana

Poskytovatel ověření
- mobilní klíč eGovernmentu
- eObčanka
- MojeID
- Bankovní identita

### 8. Vyjmenujte a stručně popište Systém základních registrů podle zákona č. 111/2009 Sb. o základních registrech.

- spuštěn 1. 7. 2012

**Informační systém základních registrů (ISZR)**
- napojen na všechny 4 následující registry

**Registr obyvatel (ROB)**
- správce – Digitální a informační agentura (DIA)
- referenční údaje o
	- občanech ČR
	- cizincích žijících v ČR
	- jiných fyzických osobách s právy a povinnostmi v ČR

**Registr osob (ROS)**
- správce – Digitální a informační agentura (DIA)
- referenční údaje o
	- právnických osobách
	- podnikajících fyzických osobách
	- orgánech veřejné moci

**Registr územní identifikace, adres a nemovitostí (RÚIAN)**
- správce – Český úřad zeměměřický a katastrální (ČÚZK)

**Registr práv a povinností (RPP)**
- správce – Digitální a informační agentura (DIA)
- kdykoliv někdo požádá o čtení či editaci údaje ze základních registrů, systém pomocí RPP posuzuje, zda je to v souladu se zákonem

### 9. Popište smysl a účel základních registrů.

- bezpečná datová báze sjednocující dříve roztříštěná data vedená různými úřady
- jedinečný (referenční) zdroj údajů využívaných při práci ve veřejné správě
- právně závazné referenční údaje o definovaných subjektech
- zjednodušení ohlašovací povinnosti, atd.
	- typicky: změna adresy trvalého bydliště

### 10. Popište ORG - převodník identifikátorů a vazbu mezi ZIFO a AIFO.

- správce – Úřad pro ochranu osobních údajů (ÚOOU)
- zajištění ochrany osobních údajů v celém systému základních registrů
- **náhrada používání rodného čísla fyzické osoby (FO)** systémem bezvýznamových identifikátorů
- **ZIFO** – zdrojový identifikátor FO
	- náhodně generovaný
- **AIFO** – agendový identifikátor FO
	- různý pro různé agendy, odvozen od ZIFO
- **IS ORG** – ukládá vazby AIFO a ZIFO
	- dokáže převést AIFO jedné agendy na AIFO jiné agendy

### 11. Vyjmenujte způsoby, jakými je možné dostat se k datům základních registrů.

- prostřednictvím **CzechPoint**
- prostřednictvím **Datových schránek**
- prostřednictvím **Agendových informačních systémů (AIS)** – které jsou propojeny se ZR
	- **Centrální AIS** (jejich prostřednictvím jsou editovány údaje v ZR)
	- **Lokální AIS** (vlastní IS jednotlivých orgánů veřejné moci, které musí mít technický certifikát napojení na ISZR)

### 12. Popište základní charakteristiky Národní infrastruktury pro prostorové informace (NIPI).

- **Cíl:** Zajistit zásady pořizování, sdílení a poskytování prostorových dat a služeb nad nimi pro potřeby veřejné správy a dalších uživatelů (přes věcný záměr zákona o NIPI).
- **Strategické řízení:** Vymezeno vládní strategií (GeoInfoStrategie) s koordinací ze strany Digitální a informační agentury (DIA).
- **Rozsah využití:** Prostorová data jsou používána napříč agendami veřejné správy — doprava, regionální rozvoj, ochrana ŽP, územní plánování, stavebnictví, lesnictví, správa majetku, ochrana kulturního dědictví aj.
- **Efektivní budování:** Zaměřeno na definici centrálních prvků infrastruktury a sdílených služeb, typové funkcionality informačních systémů spravujících prostorová data OVM a identifikaci klíčových konzumentů (externích i interních).
    - **Externí konzumenti:** fyzické osoby, právnické osoby, odborná veřejnost.
    - **Interní konzumenti:** zaměstnanci vykonávající agendy/činnosti, politici apod.

### 13. Popište obsah základního registru RÚIAN a způsob aktualizace tohoto registru.

**Registr územní identifikace, adres a nemovitostí**
- obsahem jsou **popisné** a **lokalizační údaje** o
	- územních prvcích
	- územně evidenčních jednotkách
	- účelových územních prvcích
	- **adresách**
	- vzájemných vazbách
- v ostatních registrech se vedou **odkazy** na **adresní místa** vedená v RÚIAN
- RÚIAN je **veřejným seznamem**
	- data k dispozici v **aplikaci VDP**
	- data **zákonem určena k vytěžování**
- vedeny závazné informace o **územní identifikaci** a o **adresách**

Editace údajů RÚIAN pomocí dvou AIS
- Informační systém územní identifikace (ISÚI)
	- obce
	- stavební úřady
	- Český statistický úřad (ČSÚ)
	- Český úřad zeměměřický a katastrální (ČÚZK)
	- editoři ÚÚP
- Informační systém katastru nemovitostí (ISKN)

### 14. Vyjmenujte způsoby, jakými je možné dostat data RÚIAN do GIS.

- pomocí WMS služby
- importem dat VFR z webu ČÚZK

### 15. Popište základní obsah Digitální technické mapy krajů (DTM).

- základní prostorová situace (ZPS)
	- vybrané přírodní, stavební a technické objekty a zařízení
- dopravní a technická infrastruktura (DTI)
	- údaje o dopravní a technické infrastruktuře
	- záměry na provedení změn dopravní a technické infrastruktury

### 16. Jaké jsou hlavní cíle budování a využití DMVS/DTM?

- podpora agend **stavebního řízení** a **územního plánování**
	- projekční a investiční příprava staveb
	- povolování staveb
	- stanovení okruhu vyjadřujících se subjektů (existence/připojení)
- zjednodušení **správy majetku**
	- veřejný majetek (silnice, vodovody, kanalizace, osvětlení, ...)
	- sítě technické a dopravní infrastruktury (vlastníci, provozovatelé)
- rozvoj infrastruktury včetně **vysokorychlostních sítí**
- **zdroj údajů** pro INSPIRE, RÚIAN a z něj do KN

### 17. Jaké jsou hlavní komponenty Digitální mapy veřejné správy (DMVS)?

- **ortofotomapy**  –  centrální řešení (ČÚZK/ZÚ)
- **katastrální mapy**  –  centrální řešení (ČÚZK)
- **krajské DTM**  –  decentralizované řešení (kraje)

### 18. Nakreslete schéma zobrazující vztah mezi e-governmentem ČR, základními registry, IS DMVS a IS DTM.

![](_assets/dmvs.webp)

### 19. Co je to digitální dvojče (digital twin) a k čemu se používá?

**Digitální vystavěné prostředí**
- **digitální dvojče** / digital twin
- (BIM ≠ Digitální dvojče)
- 3D model města

Příklady užití
- bezpečnost, krizové řízení, obrana
- územní rozvoj, plánování investic
- projektování a výstavba
- správa, provoz a údržba staveb
- hospodaření se zdroji, udržitelný rozvoj
- rozvoj uplatnění umělé inteligence
- nasazení IoT

### 20. Jmenujte a popište hlavní typy heterogenity prostorových dat.

1. **Syntaktická** – rozdíl **v jazyce pro popis objektu**, rozdílný datový formát
2. **Strukturální** – rozdíl **v typech objektů**, struktuře prvků nebo datových typech
3. **Sémantická** – stejný prvek reálného světa je **pojmenován různými termíny** nebo naopak

### 21. Uveďte hlavní příčiny heterogenity prostorových dat.

- způsob sběru a zpracování dat
- datové modely, datové formáty, dimenze dat
- sémantika, terminologie, taxonomie, klasifikace
- měřítko, podrobnost a přesnost dat
- územní pokrytí
- souřadnicové systémy, použité jednotky

### 22. Popište proces harmonizace prostorových dat.

- proces **sjednocování a standardizace dat**, která mají geografickou polohu, **aby byla** snadno a efektivně **kombinovatelná z různých zdrojů a systémů**
- cílem je zajistit, aby data byla vzájemně kompatibilní a použitelná napříč různými aplikacemi a platformami, což usnadňuje sdílení a výměnu informací

### 23. Co je to interoperabilita prostorových dat?

- **schopnost** různých systémů a aplikací **vzájemně komunikovat**, sdílet a používat data bez nutnosti složitých úprav nebo znalosti specifických vlastností daného systému
- snadné a efektivní **kombinování a společné používání dat z různých zdrojů**

### 24. Popište hlavní aspekty interoperability.

- **Technická interoperabilita**
	- různé systémy dokážou číst a interpretovat stejná data
	- nezáleží na způsobu uložení nebo na použité technologii
- **Sémantická interoperabilita**
	- data chápána stejně různými systémy
	- význam prvků a atributů je stejný
- **Organizační interoperabilita**
	- organizace a instituce spolupracují a sdílejí data dle dohodnutých standardů a postupů

### 25. Uveďte příklady harmonizace prostorových dat.

- **Sjednocení souřadnicových systémů**
	- převod dat do jednoho společného souřadnicového systému
- **Standardizace datových modelů**
	- sjednocení struktury a obsahu prostorových dat, aby byla data kompatibilní
- **Definice společných pravidel pro popis dat (metadat)**
	- společný popis dat a jejich vlastností, aby byla snadno vyhledatelná a použitelná

### 26. Co je to INSPIRE? Na jakých hlavních principech stojí?

**IN**frastructure for **SP**atial **I**nfo**R**mation in **E**urope
- iniciativa (směrnice) Evropské komise
- vytvoření mezinárodní infrastruktury prostorových dat (SDI)
- výsledný systém decentralizovaný na národní úrovni a volitelně pak až na jednotlivé poskytovatele dat

**Základní principy**
- data shromažďována **pouze na jednom místě**, kde je to nejvíce efektivní
- možnost **kombinace** různých zdrojů prostorových dat v rámci celé Evropy a jejich sdílení s dalšími uživateli a aplikacemi
- možnost **sdílení** prostorových dat, která jsou vytvořena v rámci jedné úrovně státní správy, na jejích dalších úrovních
- **geografická data** potřebná pro rozhodování státní správy by měla být **snadno dostupná** a za jasných podmínek
- **snadné vyhledání dostupných dat** a jejich vhodnosti

### 27. Uveďte příklady služeb vyžadovaných prováděcími pravidly pro služby INSPIRE.

**Vyhledávací služba** (Discovery service)
- typ webové služby, která umožňuje vyhledání metadat (v XML)

**Prohlížecí služba** (View service)
- typ webové služby, která zpřístupňuje prostorová data v podobě rastru

**Služba stahování dat** (Download service)
- typ webové služby, která zpřístupňuje prostorová data ve formátu INSPIRE
- služba stahování celých předpřipravených datových sad nebo jejich částí
- služba stahování s přímým přístupem (WFS)

**Transformační služba** (Coord. transf. service)
