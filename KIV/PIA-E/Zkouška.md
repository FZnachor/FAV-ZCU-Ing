# Výtah z poznámek PIA-E

## Transakce - Phantoms
- **Transakce**: Jednotka práce, která musí proběhnout celá nebo vůbec (ACID - Atomicity, Consistency, Isolation, Durability).
- **Problémy souběhu (Concurrency anomalies)**:
    - **Dirty reads**: Transakce čte data, která byla změněna jinou transakcí, ale ještě nebyla commitnuta. Pokud druhá transakce provede rollback, první transakce pracuje s neplatnými daty.
    - **Non-repeatable reads**: Transakce čte stejný řádek dvakrát, ale pokaždé dostane jiná data, protože jiná transakce mezitím data změnila a commitnula.
    - **Phantoms (fantomové čtení)**: Situace, kdy opakovaný dotaz v rámci jedné transakce vrátí jinou množinu řádků, protože jiná transakce mezitím vložila nebo smazala data vyhovující podmínce dotazu.
- **Izolační úrovně**:
    - **Read uncommitted**: Nejvyšší výkon, nejnižší konzistence (Dirty reads).
    - **Read committed**: Čtení jen commitovaných dat (řeší Dirty reads).
    - **Repeatable read**: Drží zámky na čtených záznamech (řeší Non-repeatable reads).
    - **Serializable**: Nejvyšší izolace, řeší i Phantoms (např. zamykáním rozsahu).
- **Řešení Phantoms**: Vyšší úroveň izolace transakcí (**Serializable**) nebo explicitní zamykání (např. `SELECT ... FOR UPDATE`).

## Objektově relační mapování (ORM)
- **Cíl**: Most mezi objektovým světem a relační databází (mapování třída → tabulka).
- **Výhody**: Odstínění od SQL, zvýšení produktivity, typová bezpečnost.
- **Nevýhody**: Režie, riziko výkonových problémů (N+1 SELECT problém), "leaky abstraction" (nelze zcela ignorovat DB).
- **Impedance mismatch**: Nesoulad mezi objektovým (dědičnost, asociace) a relačním modelem (tabulky, cizí klíče).
- **N+1 SELECT problém**: Načtení seznamu N entit a následné dotazování na jejich asociace v cyklu (1 dotaz pro seznam + N dotazů pro detaily). Řešení: `JOIN FETCH` nebo dávkové načítání.
- **Best practices**: Kolekce (\*-to-many) mapovat jako LAZY, \*-to-one přes JOIN (EAGER), neignorovat existenci relační DB.

## CSRF (Cross-Site Request Forgery)
- **Definice**: Útok, který donutí prohlížeč oběti provést nechtěnou akci na webu, kde je uživatel přihlášen. Využívá toho, že prohlížeč automaticky posílá cookies (session ID) s každým požadavkem na danou doménu.
- **Ochrana**:
    - **Synchronizer Token**: Unikátní token v každém formuláři/požadavku, který server ověřuje (stateful).
    - **Double Submit Cookie**: Token v cookie i v těle požadavku (stateless).
    - **SameSite Cookie**: Atribut cookie (`Strict` nebo `Lax`) omezující odesílání cookies při cross-site požadavcích.
    - Kontrola hlaviček `Origin` a `Referer`.

## XSS (Cross-Site Scripting)
- **Definice**: Injektování škodlivého skriptu do webové stránky, který se spustí v prohlížeči oběti.
- **Typy**: Stored (uložený v DB), Reflected (součást URL), DOM-based.
- **Prevence**:
    - **Sanitizace vstupu a výstupu** (escapování HTML znaků).
    - **Content Security Policy (CSP)**: Hlavička omezující zdroje, ze kterých lze načítat skripty.
    - `HttpOnly` cookies (nedostupné pro JavaScript).

## Autorizační mechanizmy na úrovni aplikační vrstvy
- Autorizace by měla probíhat v **aplikační vrstvě** (business logic), ne jen v UI (skrytí tlačítek nestačí) ani jen v kontroleru.
- Zajišťuje, že uživatel může vykonat konkrétní akci nebo číst data.
- Implementace: Kontrola práv uvnitř metod nebo pomocí **aspektů (AOP)** před voláním metody.
- Modely: **Role-based** (RBAC), **Capability-based**.
- **Identity hijack**: Útočník převezme session. Prevence: krátká platnost session, re-autentizace pro citlivé akce.

## Pojem Level of Assurance (LoA)
- Stupeň důvěry v to, že deklarovaná identita skutečně patří danému subjektu.
- Dle eIDAS:
    - **Low**: Samoregistrace bez ověření.
    - **Substantial**: Ověření identity při registraci, často také MFA.
    - **High**: Osobní ověření, certifikovaný HW token.

## Šifrování
- **HTTPS (TLS/SSL)**: Nezbytné pro veškerou komunikaci (ochrana proti odposlechu a MITM). Ověřuje identitu serveru pomocí certifikátu.
- **Hesla**: Hashovat pomocí silných algoritmů (**Argon2id**, Scrypt, Bcrypt) s použitím **salt** (unikátní náhodná hodnota proti rainbow tables) a případně **pepper** (tajný klíč aplikace, ochrana před únikem DB).

## Přihlašování - Autentizace vs Autorizace
- **Autentizace (Authentication)**: Ověření identity uživatele ("Kdo jsi?").
    - Metody: Jméno/heslo, certifikáty, tokeny, MFA, OAuth2/OpenID Connect.
- **Autorizace (Authorization)**: Ověření oprávnění k provedení akce ("Co můžeš dělat?").
    - Probíhá až po úspěšné autentizaci.
- **Session Management**: Server-side (session ID v cookie) vs. Client-side (JWT tokeny).

## Architektury - Monolit vs Microservice
- **Monolit**:
    - Jedna aplikace, jedna databáze, nasazováno jako celek.
    - Výhody: Jednoduchý vývoj a nasazení na začátku, snadné transakce, snadný debugging.
    - Nevýhody: Těžkopádné škálování, "dependency hell", pomalý build/start při velké velikosti, pevný technický stack.
- **Microservices**:
    - Sada malých, nezávislých služeb komunikujících po síti (každá má vlastní proces a často i DB).
    - Výhody: Nezávislé škálování a nasazování, možnost různých technologií, "do one thing well", odolnost (výpadek jedné služby nepoloží celek).
    - Nevýhody: Složitost distribuovaného systému (síťová latence, konzistence, distribuované transakce), náročnější provoz, monitoring a service discovery.

## Aspecty - Programování (AOP)
- **Cíl**: Oddělení průřezových zájmů (cross-cutting concerns) od business logiky (např. logování, transakce, bezpečnost).
- **Pojmy**:
    - **Aspect**: Modul zapouzdřující průřezovou logiku.
    - **Join Point**: Místo v programu, kde lze aspekt aplikovat (např. volání metody).
    - **Pointcut**: Definice, kde se má aspekt aplikovat (výběr Join Pointů, např. `execution(* Service.*(..))`).
    - **Advice**: Kód, který se provede (Before, After, Around).
    - **Weaving**: Propojení aspektu s kódem (compile-time, load-time, run-time).

## Služby - Service
- V kontextu SOA/Microservices: Samostatná komponenta s definovaným rozhraním (kontraktem).
- V kontextu vrstvené architektury: Vrstva business logiky (Service Layer), která zapouzdřuje operace nad doménou a řídí transakce.
- **Service Discovery**: Mechanismus, jak se služby v distribuovaném prostředí navzájem najdou (např. Eureka, Consul, Kubernetes DNS).

## HTTP vs HTTPS
- **HTTP**: Textový protokol, data přenášena otevřeně (čitelné pro útočníka na síti). Bezestavový protokol.
- **HTTPS**: HTTP zapouzdřené v TLS/SSL tunelu.
    - **Šifrování**: Data jsou nečitelná pro třetí strany.
    - **Integrita**: Data nebyla cestou změněna.
    - **Autentizace**: Ověření identity serveru (pomocí certifikátu vydaného CA).
- **Cookies**: Slouží k udržení stavu (např. session ID). Atributy: `Secure` (jen HTTPS), `HttpOnly` (ne JS), `SameSite` (CSRF ochrana).

## Webové služby - SOAP, WSDL, REST a další
- **SOAP**: Protokol založený na XML zprávách (Envelope, Header, Body). Přísný standard, podpora WS-* (Security, Transaction). Rozhraní popsáno pomocí **WSDL**. Vhodné pro enterprise integrace.
- **WSDL**: XML formát popisující rozhraní SOAP služby (typy, zprávy, operace, binding).
- **REST**: Architektonický styl (ne protokol) orientovaný na zdroje (Resources).
    - Využívá HTTP metody (GET, POST, PUT, DELETE) a stavové kódy.
    - Reprezentace často v JSON.
    - **Stateless**: Server neuchovává stav klienta mezi požadavky.
    - **HATEOAS**: Navigace v API pomocí hypertextových odkazů v odpovědích.

## GraphQL
- **Popis**: Dotazovací jazyk pro API a runtime pro jeho provádění. Alternativa k REST.
- **Vlastnosti**:
    - Klient si přesně řekne, jaká data chce (řeší **over-fetching** a **under-fetching**).
    - Silně typované schéma (Schema Definition Language).
    - Jeden endpoint (obvykle POST).
- **Operace**:
    - **Query**: Čtení dat (paralelní).
    - **Mutation**: Změna dat (sériové).
    - **Subscription**: Reálný čas (WebSocket).
- **Příklad schématu**:
    ```graphql
    type Query { me: User }
    type User { id: ID, name: String }
    ```
- **Příklad dotazu**:
    ```graphql
    query { me { name } }
    ```

## Problematika návrhu rozsáhlého IS
- **Distribuované systémy**: Problémy se síťovou latencí, dostupností služeb a konzistencí dat (CAP teorém).
- **Komunikace**:
    - **Synchronní** (REST/RPC): Blokující, těsná vazba, riziko kaskádových selhání.
    - **Asynchronní** (Messaging/Broker): Neblokující, volná vazba, vyšší odolnost, eventual consistency.
- **Škálovatelnost**: Horizontální (více instancí) vs. Vertikální (silnější HW).
- **Výkon a Perzistence**:
    - **Connection Pooling**: Znovupoužití otevřených připojení k DB pro snížení režie (handshake).
    - **Indexy**: Zrychlení čtení, zpomalení zápisu.
- **Konzistence**: V distribuovaném prostředí často "Eventual Consistency" místo striktní ACID transakce napříč službami.
- **Architektura**: Vrstvená (Layered), Clean Architecture (Dependency Rule: závislosti směrem dovnitř).
- **Kvalita SW**:
    - **Validace**: Děláme správnou věc?
    - **Verifikace**: Děláme věc správně? (Unit testy, Integrační testy, Funkční testy).
    - **Logování**: Application, Access, Audit logy.
