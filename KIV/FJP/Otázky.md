# Otázky

#### 1. Charakterizujte křížový překladač
Křížový překladač (cross-compiler) je překladač, který běží na jedné platformě (hostitelské) a generuje spustitelný kód pro jinou platformu (cílovou). Příkladem může být překladač běžící na Windows, který generuje kód pro Linux, nebo překladač pro ARM procesor běžící na x86 architektuře. (Internet)

#### 2. Objasněte pojem silikonový překladač
Silikonové překladače navrhují specializované obvody pro logické programy.

#### 3. Co to jsou formátory textu? Uveďte příklad
Formátovače textu provádějí sazbu textu podle značek/otagování. Příkladem je LaTeX nebo Markdown procesor.

#### 4. Charakterizujte kaskádní překladač
Kaskádní překladač (cascading compiler) je typ překladače, který se skládá z několika fází, kde výstup jedné fáze slouží jako vstup pro fázi následující. Často se používá pro překlad z jednoho vysokoúrovňového jazyka do jiného, než se nakonec přeloží do strojového kódu. (Internet)

#### 5. Porovnejte výhody a nevýhody interpretačních a kompilačních překladačů
*   **Kompilační překladače:**
    *   **Výhody:** Rychlé vykonávání programu (kód je přeložen jednou a spouští se opakovaně), optimalizace kódu pro konkrétní architekturu.
    *   **Nevýhody:** Delší doba překladu, obtížnější ladění (chyby se objevují až po překladu), méně flexibilní pro interaktivní režim.
*   **Interpretační překladače:**
    *   **Výhody:** Snazší ladění (chyby se objevují okamžitě), často v interaktivním režimu, zvládá složitější konstrukce, rychlejší vývoj a prototypování.
    *   **Nevýhody:** Pomalejší vykonávání programu (kód se analyzuje a vykonává při každém spuštění), menší možnosti optimalizace.

#### 6. Jaký je rozdíl mezi fází a průchodem překladače
*   **Fáze překladače** je logická část procesu překladu, která provádí specifickou transformaci kódu (např. lexikální analýza, syntaktická analýza, sémantická analýza, generování mezikódu, optimalizace, generování cílového kódu).
*   **Průchod překladače** (pass) označuje jedno přečtení celého zdrojového kódu nebo jeho mezireprezentace. Víceprůchodový překladač čte kód nebo jeho reprezentaci vícekrát, což umožňuje složitější analýzy a optimalizace. Jednoprůchodový překladač zpracuje kód v jednom čtení.

#### 7. Charakterizujte vnitřní jazyky jednotlivých fází překladače
Vnitřní jazyky (mezijazyky) slouží jako společná reprezentace programu mezi jednotlivými fázemi překladače, zejména u vícevrstvých překladačů.
*   **Lexikální analýza:** Produkuje proud tokenů.
*   **Syntaktická analýza:** Produkuje derivační strom (parse tree) nebo abstraktní syntaktický strom (AST).
*   **Sémantická analýza:** Obohacuje AST a tabulku symbolů o sémantické informace.
*   **Generování mezikódu:** Produkuje mezikód, který je snazší pro optimalizaci a generování cílového kódu. Příklady:
    *   **Jazyk trojic (Triples):** Formát `operátor, operand, operand`. Odpovídá instrukcím vykonávaným v zásobníku.
    *   **Jazyk čtveřic (Quadruples):** Formát `operátor, operand, operand, výsledek/cíl skoku`. Podobné instrukcím CPU, snazší pro optimalizátor.

#### 8. Jaké jsou důvody pro použití víceprůchodového překladače
*   **Snazší zpracování více jazyků pro různé platformy:** Oddělení frontend, middle-end a backend s využitím společné vnitřní reprezentace programu.
*   **Možnost deklarace metod kdekoliv:** Některé jazyky (např. Java) umožňují deklaraci metod v libovolném pořadí, což vyžaduje více průchodů pro shromáždění všech informací.
*   **Lepší optimalizace:** Více průchodů umožňuje provádět složitější analýzy a optimalizace kódu, které by v jednom průchodu nebyly možné.
*   **Snazší návrh a kontrola správnosti:** Rozdělení překladače na více průchodů, kde každý dělá jednu věc, zjednodušuje návrh a údržbu.

#### 9. Zdůvodněte, proč se nepoužívají čistě interpretační překladače
Čistě interpretační překladače se nepoužívají pro produkční nasazení, protože jsou výrazně pomalejší než kompilované programy. Každá instrukce je analyzována a vykonána za běhu, což vede k velké režii. Kompilované programy jsou optimalizovány a vykonávány přímo strojovým kódem, což je mnohem efektivnější. (Internet)

#### 10. Co to jsou generátory překladačů, uveďte příklad
Generátory překladačů jsou nástroje, které automaticky generují části překladače (např. lexikální analyzátory nebo syntaktické analyzátory) z formálních specifikací.
*   **Příklady:**
    *   **AntLR, JavaCC:** Generátory pro rekurzivní sestup (LL parsery).
    *   **Yacc, Bison:** Generátory pro LR parsery.

#### 11. Nakreslete schéma překladače kompilačního typu
Nelze nakreslit, ale schéma překladače kompilačního typu typicky zahrnuje následující fáze v tomto pořadí:
1.  **Preprocesor** (volitelný): Zpracovává makra, vkládá soubory.
2.  **Lexikální analyzátor (Scanner):** Převádí zdrojový kód na proud tokenů.
3.  **Syntaktický analyzátor (Parser):** Kontroluje gramatiku a vytváří derivační strom (parse tree) nebo abstraktní syntaktický strom (AST).
4.  **Sémantický analyzátor:** Kontroluje sémantiku (typy, deklarace) a obohacuje AST/tabulku symbolů.
5.  **Generátor mezikódu:** Převádí AST na mezikód (např. trojice, čtveřice).
6.  **Optimalizátor kódu:** Vylepšuje mezikód pro efektivnější vykonávání.
7.  **Generátor cílového kódu:** Převádí mezikód na strojový kód nebo assembler.
8.  **Assembler:** Převádí assembler na objektový kód.
9.  **Linker:** Spojuje objektové soubory a knihovny do spustitelného programu.
10. **Loader:** Zavádí program do paměti a spouští ho.
**Tabulka symbolů** a **Správa chyb** jsou komponenty, které interagují se všemi fázemi.

#### 12. Jaké znáte vnitřní jazyky, které produkují jednotlivé fáze překladače
*   **Lexikální analýza:** Tokeny.
*   **Syntaktická analýza:** Derivační strom (Parse Tree) nebo Abstraktní syntaktický strom (AST).
*   **Sémantická analýza:** Obohacený Abstraktní syntaktický strom (AST) a Tabulka symbolů.
*   **Generování mezikódu:** Trojice, čtveřice, P-kód, bytecode.
*   **Generování cílového kódu:** Assembler, strojový kód.

#### 13. Popište vám známé principy optimalizace kódu
Optimalizace kódu se provádí na různých úrovních (AST, mezijazyk, cílový kód) a zahrnuje principy jako:
*   **Vkládání konstant (Constant Folding):** Vyhodnocení konstantních výrazů v době překladu (např. `2 + 3` se stane `5`).
*   **Propagace konstant (Constant Propagation):** Nahrazení proměnné konstantní hodnotou, pokud je známo, že se nemění.
*   **Zjednodušení algebry (Algebraic Simplification):** Zjednodušení výrazů (např. `x + 0` se stane `x`, `x * 1` se stane `x`).
*   **Eliminace mrtvého kódu (Dead Code Elimination):** Odstranění kódu, který nemá žádný vliv na výsledek programu.
*   **Inlining:** Nahrazení volání funkce jejím tělem, čímž se ušetří režie volání.
*   **Eliminace společného podvýrazu (Common Subexpression Elimination):** Identifikace a odstranění opakovaných výpočtů stejného výrazu.
*   **Optimalizace smyček:**
    *   **Code Motion:** Přesunutí kódu, který se nemění uvnitř smyčky, před smyčku.
    *   **Strength Reduction:** Nahrazení drahých operací (např. násobení) levnějšími (např. sčítání) uvnitř smyček.
    *   **Loop Unrolling/Splitting:** Rozbalení smyček pro snížení režie nebo rozdělení smyček pro lepší využití cache.
*   **Propagace přiřazení/kopírování (Copy Propagation):** Nahrazení proměnné její kopií, pokud je to možné.

#### 14. Jaká vlastnost gramatiky podmiňuje nekonečnost generovaného jazyka?
Nekonečnost generovaného jazyka je podmíněna přítomností rekurzivních pravidel v gramatice. Pokud existuje neterminální symbol, který se může přepsat sám na sebe (přímo nebo nepřímo), pak gramatika může generovat nekonečně mnoho řetězců. (Internet)

#### 15. Popište gramatikou reálná čísla s desetinnou částí
```
<RealNumber> ::= <IntegerPart> "." <FractionalPart>
<IntegerPart> ::= <Digit> | <IntegerPart> <Digit>
<FractionalPart> ::= <Digit> | <FractionalPart> <Digit>
<Digit> ::= "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"
```
Tato gramatika popisuje reálná čísla s povinnou celou i desetinnou částí, oddělenou tečkou. Pro volitelné znaménko nebo exponent by bylo potřeba gramatiku rozšířit. (Internet)

#### 16. Jaký je nejvyšší možný počet stavů deterministického KA, má-li ekvivalentní nederm. KA 5 stavů
Nejvyšší možný počet stavů deterministického konečného automatu (DKA), který je ekvivalentní nedeterministickému konečnému automatu (NKA) s `n` stavy, je `2^n`. Pro NKA s 5 stavy je to `2^5 = 32` stavů. (Internet)

#### 17. Popište tvar identifikátoru levou lineární gramatikou
Identifikátor typicky začíná písmenem nebo podtržítkem, následovaným písmeny, číslicemi nebo podtržítky.
```
<ID> ::= <Letter> | <ID> <Letter> | <ID> <Digit> | <ID> "_"
<Letter> ::= "a" | "b" | ... | "z" | "A" | "B" | ... | "Z"
<Digit> ::= "0" | "1" | ... | "9"
```
(Internet)

#### 18. Zapište pravou lineární gramatiku čísla real v semilogaritmickém tvaru
Semilogaritmický tvar (např. `1.23e+45`) je pro čistě pravou lineární gramatiku poměrně složitý, protože pravé lineární gramatiky generují regulární jazyky, které nemají paměť pro počítání. Zde je zjednodušená pravá lineární gramatika pro číslo ve tvaru `C.C` nebo `C.CeE` kde `C` je číslice:
```
<S> ::= <Digit> <S1>
<S1> ::= "." <S2> | "e" <S3> | ε
<S2> ::= <Digit> <S2> | "e" <S3> | ε
<S3> ::= "+" <S4> | "-" <S4> | <Digit> <S4>
<S4> ::= <Digit> <S4> | ε
<Digit> ::= "0" | "1" | ... | "9"
```
(Internet)

#### 19. Zapište s co nejmenším počtem pravidel gramatiku popisující binární čísla s lichým počtem jedniček.
```
S ::= 0S | 1A
A ::= 0A | 1S | 1
```
Kde `S` je počáteční stav (lichý počet jedniček) a `A` je pomocný stav (sudý počet jedniček). (Internet)

#### 20. Uveďte obecný tvar překladových pravidel používaných v LEX
V LEXu (nebo Flexu) se překladová pravidla skládají z regulárního výrazu a akce, která se provede, když se regulární výraz shoduje se vstupem. Obecný tvar je:
```
regulární_výraz { akce_v_C_kódu }
```
Akce může zahrnovat vrácení tokenu, uložení lexému, inkrementaci počítadla atd.

#### 21. Jaký řetězec rozpoznává LEX, je-li překladové pravidlo dáno výrazem \+?[0-9][0-9]\*$
Tento regulární výraz rozpoznává:
*   Volitelné znaménko plus (`+?`).
*   Následované jednou číslicí (`[0-9]`).
*   Následované nulou nebo více číslicemi (`[0-9]*`).
*   Až do konce řetězce/tokenu (`$`).
Rozpoznává tedy celá kladná čísla, která mohou volitelně začínat znakem `+`. Např. `123`, `+45`, `0`, `+0`.

#### 22. Jak řeší lexik. analyzátory problém nalezení symbolu v případě, kdy je jeden symbol prefixem jiného?
Lexikální analyzátory tento problém řeší dvěma hlavními pravidly:
1.  **Pravidlo nejdelší shody (Longest Match Rule):** Vždy se vybere nejdelší možný lexém, který odpovídá některému regulárnímu výrazu. Například, pokud `if` i `identifier` jsou tokeny a vstup je `if_else`, bude rozpoznán jako `identifier` (`if_else`), nikoli jako `if` následovaný `_else`.
2.  **Pravidlo priority (Priority Rule):** Pokud se dva nebo více regulárních výrazů shodují se stejným nejdelším lexémem, vybere se ten, který je definován dříve (má vyšší prioritu) ve specifikaci lexikálního analyzátoru. Například, klíčová slova mají obvykle vyšší prioritu než obecné identifikátory.

#### 23. Jaký řetězec rozpoznává LEX, je-li překladové pravidlo dáno výrazem (např. \\\*?\[1-9]\* )?
Pravidlo `\*?[1-9]*` rozpoznává:
*   Volitelnou hvězdičku (`\*?`).
*   Následovanou nulou nebo více číslicemi od 1 do 9 (`[1-9]*`).
Příklady: `*123`, `456`, `*`, `1`.

#### 24. Popište princip způsobu zotavení ze syntaktické chyby v překladači PL/0
Překladač PL/0, jako mnoho jednoduchých překladačů, pravděpodobně používá metodu **panic mode** pro zotavení ze syntaktických chyb. Při detekci chyby se parser začne ignorovat vstupní tokeny, dokud nenarazí na tzv. synchronizační token (např. středník, klíčové slovo `END`, `BEGIN`), který pravděpodobně označuje konec nějaké syntaktické konstrukce. Poté se pokusí pokračovat v analýze od tohoto bodu. (Internet)

#### 25. Jaké vlastnosti musí splňovat jazyk analyzovatelný rekurzivním sestupem
Jazyk analyzovatelný rekurzivním sestupem (typicky LL(k) gramatiky) musí splňovat následující vlastnosti:
*   **Žádná levá rekurze:** Gramatika nesmí obsahovat pravidla jako `A -> Aα`, protože by vedla k nekonečné smyčce.
*   **Žádné společné prefixy (nebo vyřešené lookaheadem):** Pokud má neterminál více produkcí, jejich pravé strany nesmí začínat stejným symbolem (terminálem nebo neterminálem), pokud není možné rozhodnout o výběru produkce pomocí lookaheadu. To se řeší levou faktorizací.
*   **Správné zpracování epsilon pravidel:** Pravidla generující prázdný řetězec (`A -> ε`) musí být zpracována tak, aby nedocházelo ke konfliktům s `FIRST` a `FOLLOW` množinami.
*   **Gramatika musí být LL(k):** Pro daný počet `k` vstupních symbolů musí být možné jednoznačně vybrat pravidlo pro expanzi neterminálu.

#### 26. Vysvětlete funkci procedury Test(s1,s2: symset; n: integer); v překladači PL/0
Procedura `Test` v překladači PL/0 je typicky používána pro zotavení ze syntaktických chyb. Jejím účelem je zajistit, aby aktuální token patřil do očekávané množiny tokenů.
*   `s1`: Množina tokenů, které jsou v daném kontextu povoleny.
*   `s2`: Množina tokenů, které slouží jako synchronizační body pro zotavení z chyby.
*   `n`: Kód chyby, který se vypíše, pokud aktuální token není v `s1`.
Pokud aktuální token není v `s1`, vypíše se chyba `n`. Poté se parser posouvá vpřed (ignoruje tokeny), dokud nenarazí na token, který je buď v `s1` nebo v `s2`. Tím se snaží obnovit syntaktickou analýzu. (Internet)

#### 27. Zapište gramatiku aritmetického výrazu s operátory + , \*, a závorkami (, ). Zapište levou derivaci věty i + i
Standardní gramatika pro aritmetické výrazy s respektováním priority operátorů:
```
E -> T { "+" T }
T -> F { "*" F }
F -> "(" E ")" | "i"
```
Kde `E` je výraz, `T` je term, `F` je faktor a `i` je identifikátor/číslo.

Levá derivace věty `i + i`:
1.  `E`
2.  `T { "+" T }` (použito `E -> T { "+" T }`)
3.  `F { "*" F } { "+" T }` (použito `T -> F { "*" F }`)
4.  `i { "+" T }` (použito `F -> "i"`)
5.  `i + T` (použito `{ "+" T }` a odstraněno `{ "*" F }` jako prázdné)
6.  `i + F { "*" F }` (použito `T -> F { "*" F }`)
7.  `i + i` (použito `F -> "i"` a odstraněno `{ "*" F }` jako prázdné)

#### 28. Popište princip metody rekurzivního sestupu
Metoda rekurzivního sestupu je shora dolů syntaktická analýza, která využívá princip "rozděl a panuj". Pro každý neterminální symbol v gramatice existuje procedura (funkce). Tyto procedury se vzájemně rekurzivně volají, aby odpovídaly struktuře gramatiky.
*   **Princip:**
    1.  Pro každý neterminální symbol `A` existuje procedura `parseA()`.
    2.  Když procedura `parseA()` začne, snaží se rozpoznat řetězec, který může být odvozen z `A`.
    3.  Pokud `A` má více produkcí (např. `A -> α | β`), procedura `parseA()` se rozhodne, kterou produkci použít, obvykle na základě aktuálního vstupního symbolu (lookahead).
    4.  Pokud produkce obsahuje terminální symbol, procedura ověří, zda se shoduje s aktuálním vstupním symbolem, a posune vstup.
    5.  Pokud produkce obsahuje neterminální symbol `B`, procedura zavolá `parseB()`.
*   Analýza probíhá zleva doprava a provádí nejlevější derivaci.

#### 29. Charakterizujte syntetizované atributy
Syntetizované atributy jsou atributy, jejichž hodnoty jsou spočteny z atributů potomků v derivačním stromě. Jejich vyhodnocování probíhá zdola nahoru (od listů ke kořeni). Příkladem je hodnota aritmetického výrazu, která se počítá z hodnot jeho operandů.

#### 30. Popište způsob vyhodnocování dědičných atributů
Dědičné atributy jsou atributy, jejichž hodnoty jsou získány z atributů rodiče nebo sourozenců v derivačním stromě. Jejich vyhodnocování probíhá shora dolů (od kořene k listům). Příkladem je typ proměnné, který je děděn z deklarace do místa použití.

#### 31. Charakterizujte derivační strom a syntaktický strom
*   **Derivační strom (Parse Tree):** Je to úplná reprezentace vstupu získaná parserem. Zobrazuje všechny kroky derivace podle gramatiky, včetně neterminálních symbolů a pomocných pravidel, které nemusí být sémanticky důležité. Zachovává nepodstatné uzly.
*   **Abstraktní syntaktický strom (AST):** Je to zjednodušená reprezentace programu, která obsahuje pouze důležité informace potřebné pro vykonávání programu. Odstraňuje syntaktické detaily, které nejsou sémanticky relevantní (např. závorky, klíčová slova jako `begin`/`end` pokud nejsou nutná pro strukturu).

#### 32. Popište zásady konstrukce postfixového výrazu z infixového
Konstrukce postfixového výrazu z infixového se obvykle provádí pomocí algoritmu Shunting-yard (nebo podobného algoritmu založeného na zásobníku).
*   **Zásady:**
    1.  **Operandy:** Operandy se okamžitě přidávají na výstup.
    2.  **Operátory:**
        *   Pokud je na vstupu operátor, porovná se s operátory na vrcholu zásobníku.
        *   Pokud je zásobník prázdný nebo na vrcholu je levá závorka, operátor se vloží na zásobník.
        *   Pokud má operátor na vstupu vyšší prioritu než operátor na vrcholu zásobníku, vloží se na zásobník.
        *   Pokud má operátor na vstupu nižší nebo stejnou prioritu (a je levopřidružený), operátory ze zásobníku s vyšší nebo stejnou prioritou se přesunou na výstup, dokud není splněna podmínka pro vložení operátoru na vstup.
    3.  **Závorky:**
        *   Levá závorka se vloží na zásobník.
        *   Pravá závorka způsobí, že se všechny operátory ze zásobníku přesunou na výstup, dokud se nenarazí na odpovídající levou závorku, která se pak ze zásobníku odstraní (ale nepřidá se na výstup).
    4.  **Konec výrazu:** Po zpracování celého infixového výrazu se všechny zbývající operátory ze zásobníku přesunou na výstup. (Internet)

#### 33. Zapište posloupnost postfixových instrukcí pro příkaz a10 = - (x20 + y30)/(x20 - y30)
1.  `x20`
2.  `y30`
3.  `+`
4.  `x20`
5.  `y30`
6.  `-`
7.  `/`
8.  `UMINUS` (unární minus)
9.  `a10`
10. `=` (přiřazení)

Výsledná posloupnost: `x20 y30 + x20 y30 - / UMINUS a10 =`

#### 34. Zapište výraz -2\*(x + y) ^ 3 pro případ 1) nejvyšší, 2) nejnižší precedence operátoru unárního minus a) v prefixové, b) v postfixové notaci
Předpokládané priority: `^` > `*` > `+` (binární)

**Případ 1: Unární minus má nejvyšší precedenci**
*   **a) Prefixová notace:** `* NEG 2 ^ + x y 3`
*   **b) Postfixová notace:** `2 NEG x y + 3 ^ *`

**Případ 2: Unární minus má nejnižší precedenci**
*   **a) Prefixová notace:** `NEG * 2 ^ + x y 3`
*   **b) Postfixová notace:** `2 x y + 3 ^ * NEG`
(Internet)

#### 35. Přeložte do posloupnosti postfix. instrukcí if (A10 < B 20) then C 30 = (A 10 + B 20 ) \* ( A10 - B20 );
Předpokládáme instrukce pro podmíněné skoky (`JUMPF` - skok, pokud je false, `JUMP` - nepodmíněný skok) a návěští (`L1`, `L2`).
1.  `A10`
2.  `B20`
3.  `<`
4.  `JUMPF L1` (Pokud A10 není menší než B20, skoč na L1)
5.  `A10`
6.  `B20`
7.  `+`
8.  `A10`
9.  `B20`
10. `-`
11. `*`
12. `C30`
13. `=`
14. `L1:` (Návěští pro konec `if` bloku)
(Internet)

#### 36. Přeložte do postfixových instrukcí příkaz while x<y do x = (x+y) / (x-y); je-li x na adrese 100 a y na adrese 101
Předpokládáme instrukce pro podmíněné skoky (`JUMPF` - skok, pokud je false, `JUMP` - nepodmíněný skok) a návěští (`L1`, `L2`).
1.  `L1:` (Návěští pro začátek smyčky)
2.  `@100` (načti hodnotu x)
3.  `@101` (načti hodnotu y)
4.  `<`
5.  `JUMPF L2` (Pokud x není menší než y, skoč na L2 - konec smyčky)
6.  `@100`
7.  `@101`
8.  `+`
9.  `@100`
10. `@101`
11. `-`
12. `/`
13. `@100`
14. `=` (ulož výsledek na adresu x)
15. `JUMP L1` (Nepodmíněný skok zpět na začátek smyčky)
16. `L2:` (Návěští pro konec smyčky)
(Internet)

#### 37. Jaké informace jsou ukládány v tabulce symbolů překladače
Tabulka symbolů mapuje jméno symbolu na jeho deskriptor a je vytvářena a udržována během sémantické analýzy. Obsahuje následující informace:
*   **Druh záznamu:** Typ symbolu (proměnná, konstanta, procedura, funkce, třída, metoda, návěští atd.).
*   **Hladina (úroveň vnoření):** Úroveň zanoření, ve které byl symbol deklarován (pro správu viditelnosti).
*   **Adresa:** Adresa v paměti, adresa cíle skoku, nebo offset.
*   **Použití:** Zda byl symbol použit (pro detekci mrtvého kódu).
*   **Inicializace:** Zda byl symbol inicializován a jaká je jeho počáteční hodnota.
*   **Datový typ:** Typ dat, které symbol reprezentuje (např. int, float, string, boolean, vlastní typy).
*   **Formální parametr:** Zda je symbol formálním parametrem procedury/funkce.
*   **Formální parametry (pro procedury/funkce/metody):** Seznam typů a jmen parametrů.
*   **Způsob přístupu:** Jak se k symbolu přistupuje (hodnotou, odkazem).
*   **Hodnota:** U konstant je uložena přímo jejich hodnota.

#### 38. Vysvětlete, jakým mechanismem překladač zajišťuje respektování lokality identifikátorů v blokově strukturovaném jazyce
Překladač zajišťuje respektování lokality identifikátorů (rozsah viditelnosti, scope) v blokově strukturovaných jazycích pomocí **zásobníku tabulek symbolů**.
1.  **Vytvoření rozsahu:** Při vstupu do nového bloku (např. funkce, cyklus, `if` blok) se vytvoří nová tabulka symbolů (často implementovaná jako mapa) pro tento rozsah a ta se přidá na vrchol zásobníku tabulek symbolů.
2.  **Vložení symbolu:** Nově deklarované identifikátory se vkládají do tabulky symbolů na vrcholu zásobníku (aktuální rozsah).
3.  **Vyhledání symbolu:** Při použití identifikátoru se nejprve hledá v tabulce symbolů na vrcholu zásobníku. Pokud se tam nenajde, hledání pokračuje v tabulkách symbolů níže v zásobníku (v nadřazených rozsazích), dokud se symbol nenajde nebo se zásobník nevyprázdní. Tím se zajistí, že vnitřní identifikátory překryjí vnější.
4.  **Odstranění rozsahu:** Při opuštění bloku se tabulka symbolů pro tento rozsah odstraní z vrcholu zásobníku, čímž se identifikátory deklarované v tomto bloku stanou nedostupnými.

#### 39. Jaká je časová složitost práce s rozptýleně organizovanou tabulkou symbolů v závislosti na počtu symbolů v programu?
"Rozptýleně organizovaná" tabulka symbolů obvykle odkazuje na **hashovací tabulku**.
*   **Průměrná časová složitost:** O(1) pro vložení, vyhledání a smazání symbolu, za předpokladu dobré hashovací funkce a minimálních kolizí.
*   **Nejhorší časová složitost:** O(N) v případě špatné hashovací funkce, která vede k mnoha kolizím a degeneruje na lineární seznam, kde N je počet symbolů. (Internet)

#### 40. Jaká je závislost časové režie vyhledávání v netříděně uspořádané tabulce symbolů na počtu jmen v tabulce
V netříděně uspořádané tabulce symbolů (např. jednoduchý lineární seznam) je pro vyhledání symbolu nutné projít seznam prvek po prvku.
*   **Časová složitost:** O(N), kde N je počet jmen v tabulce. V nejhorším případě (symbol je na konci nebo chybí) je nutné projít celý seznam. (Internet)

#### 41. Popište způsob vytváření a práce s frekvenčně uspořádanou tabulkou symbolů
Frekvenčně uspořádaná tabulka symbolů je taková, kde jsou symboly uspořádány podle četnosti jejich použití (nejčastěji používané symboly jsou na začátku).
*   **Vytváření:** Během prvního průchodu překladače se shromažďují informace o četnosti použití každého symbolu. Po dokončení analýzy se tabulka symbolů seřadí podle těchto frekvencí.
*   **Práce:** Při vyhledávání symbolu se prochází tabulka od začátku. Díky uspořádání se očekává, že nejčastěji hledané symboly budou nalezeny rychleji, což snižuje průměrnou dobu vyhledávání. Nevýhodou je režie na udržování seřazení při vkládání nových symbolů nebo aktualizaci frekvencí. (Internet)

#### 42. K čemu slouží mapovací funkce pole a na jaké části se člení?
Mapovací funkce pole slouží k výpočtu paměťové adresy konkrétního prvku v poli na základě jeho indexů. Převádí logické indexy na fyzickou adresu v paměti.
Člení se na:
*   **Koeficienty mapovací funkce:** Tyto koeficienty závisí na rozměrech pole a velikosti prvků. Pro vícerozměrná pole určují, jak se indexy jednotlivých dimenzí převádějí na offset.
*   **Konstantní část mapovací funkce:** Zahrnuje základní adresu pole a případné posuny způsobené dolními mezemi indexů.
*   **Příklad pro jednorozměrné pole:** `adresa(A[i]) = základní_adresa + (i - dolní_mez) * velikost_prvku`.

#### 43. Co je obsahem deskriptoru třídy.
Deskriptor třídy je datová struktura, která se vytváří v tabulce symbolů během překladu a obsahuje metadata o třídě. Jeho obsahem je:
*   **Ukazatel na deskriptor rodiče:** Pro podporu dědičnosti a dohledávání zděděných členů.
*   **Seznam datových položek:** Popisuje členské proměnné třídy (jejich jméno, typ, pozice/offset vzhledem k bázi instance).
*   **Seznam metod:** Popisuje metody třídy (jejich jméno, vstupní bod, deskriptor, signatura).

#### 44. Popište, jak překladač realizuje volání statických metod v OO jazyce
Volání statických metod v objektově orientovaných jazycích je realizováno v době překladu.
1.  **Rozlišení:** Překladač rozpozná, že jde o statickou metodu (nevyžaduje instanci objektu).
2.  **Přímá adresa:** Adresa statické metody je známa v době překladu, protože není závislá na dynamickém typu objektu.
3.  **Přímý skok:** Překladač vygeneruje kód, který provede přímý skok na tuto pevnou adresu metody. Není potřeba žádné vyhledávání v tabulkách virtuálních metod. (Internet)

#### 45. Popište, jak překladač realizuje vyvolání dynamických (virtuálních) metod v OO jazyce
Vyvolání dynamických (virtuálních) metod (polymorfní chování) je realizováno za běhu programu, protože adresa volané metody závisí na skutečném (dynamickém) typu objektu, nikoli na typu reference.
1.  **CIR objekty:** Každá instance objektu (CIR - Class Instance Record) obsahuje odkaz na deskriptor své třídy a/nebo na tabulku virtuálních metod (TVM) své třídy.
2.  **Tabulka virtuálních metod (TVM):** Každá třída má svou TVM, která je vytvořena v době překladu. TVM obsahuje seznam ukazatelů na implementace všech virtuálních metod, které třída a její předci definují. Metody jsou v TVM uspořádány na fixních pozicích (offsetech).
3.  **Vyhledání metody:** Při volání virtuální metody překladač vygeneruje kód, který:
    *   Získá ukazatel na TVM z instance objektu.
    *   Použije známý offset metody v TVM (stejný pro všechny třídy v hierarchii pro danou metodu) k nalezení adresy konkrétní implementace metody.
    *   Provede nepřímý skok na tuto adresu.

#### 46. Kdy překladač vytváří CIR (class instance rekord) a jaké informace v něm ukládá
Překladač vytváří CIR (Class Instance Record) v době běhu programu, když je vytvořena nová instance objektu (např. operátorem `new`). CIR je reprezentace objektu v paměti.
Ukládá v něm:
*   **Atributy s pevnou pozicí vůči bázi:** Hodnoty členských proměnných instance.
*   **Označení třídy jako číslo:** Identifikátor třídy, ke které instance patří.
*   **Odkaz na tabulku skoků (TVM):** Ukazatel na tabulku virtuálních metod dané třídy, pro podporu polymorfismu.
CIR objekty jsou obvykle uloženy v dynamické paměti (na haldě).

#### 47. Co je obsahem TVM (tabulka virtuálních metod) a kdy se TVM vytváří
TVM (Tabulka virtuálních metod, Dispatch table) je datová struktura, která se vytváří v době překladu (jedna pro každou třídu).
Obsahem TVM je:
*   **Seznam ukazatelů na metody:** Obsahuje adresy implementací všech virtuálních metod, které třída a její předci definují.
*   **Fixní pozice:** Metody jsou v TVM uspořádány na fixních pozicích (offsetech). Pokud potomek překryje metodu předka, adresa nové implementace je na stejném offsetu v TVM potomka.
TVM je klíčová pro realizaci polymorfismu a dynamické dispečování metod.

#### 48. Popište význam částí dynamické adresy (adresové dvojice)
Dynamická adresa (adresová dvojice) se v kontextu blokově strukturovaných jazyků s vnořenými procedurami obvykle skládá ze dvou částí:
1.  **Úroveň zanoření (Level):** Určuje lexikální úroveň zanoření, ve které byl identifikátor deklarován.
2.  **Offset:** Určuje posun (offset) od báze aktivačního záznamu dané úrovně zanoření, kde je hodnota identifikátoru uložena.
Tato dvojice (level, offset) umožňuje překladači generovat kód pro přístup k proměnným v různých lexikálních úrovních. (Internet)

#### 49. Formulujte podmínku, kterou musí splňovat program, aby statický řetězec výpočtového zásobníku stále splýval s dynamickým řetězcem
Statický řetězec výpočtového zásobníku splývá s dynamickým řetězcem, pokud program neobsahuje vnořené procedury/funkce nebo pokud jsou všechny volané procedury/funkce deklarovány na globální úrovni. V takovém případě je lexikální nadřazenost vždy stejná jako volající nadřazenost. (Internet)

#### 50. Popište způsob vytváření řetězce statických ukazatelů.
Řetězec statických ukazatelů (static chain) se vytváří pro přístup k nelokálním proměnným v lexikálně nadřazených (vnořených) rozsazích.
*   **Způsob vytváření:** Každý aktivační záznam procedury/funkce obsahuje tzv. **statický ukazatel**. Tento ukazatel směřuje na bázi aktivačního záznamu lexikálně bezprostředně nadřazené procedury/funkce.
*   **Použití:** Při volání procedury se do jejího aktivačního záznamu uloží statický ukazatel, který odkazuje na aktivační záznam lexikálně nadřazené procedury. Pro přístup k proměnné v lexikálně vzdálenějším rozsahu se prochází tento řetězec statických ukazatelů.

#### 51. Popište způsob vytváření řetězce dynamických ukazatelů.
Řetězec dynamických ukazatelů (dynamic chain) se vytváří pro správu toku řízení a návratu z procedur/funkcí.
*   **Způsob vytváření:** Každý aktivační záznam procedury/funkce obsahuje tzv. **dynamický ukazatel**. Tento ukazatel směřuje na bázi aktivačního záznamu volající procedury/funkce.
*   **Použití:** Při návratu z procedury se pomocí dynamického ukazatele obnoví stav volající procedury (např. ukazatel na vrchol zásobníku, ukazatel na instrukci, kam se má vrátit).

#### 52. Jakými vlastnostmi jazyka je podmíněno statické přidělování paměti
Statické přidělování paměti (tj. přidělování paměti v době překladu) je podmíněno následujícími vlastnostmi jazyka:
*   **Pevná velikost dat:** Všechny datové struktury (proměnné, pole) musí mít velikost známou v době překladu.
*   **Žádná rekurze:** Jazyk nesmí podporovat rekurzivní volání procedur/funkcí, protože by to vyžadovalo dynamické přidělování aktivačních záznamů na zásobníku.
*   **Žádné dynamické datové struktury:** Jazyk nesmí podporovat dynamickou alokaci paměti (např. na haldě) pro proměnné, jejichž velikost se mění za běhu.
Statické přidělování se používá pro konstanty, globální proměnné a statické proměnné, které existují po celou dobu běhu programu.

#### 55. Uveďte, jaké údaje ukládá překladač v aktivačním záznamu
Aktivační záznam (activation record) je datová struktura, která se vytváří na zásobníku při každém volání procedury/funkce. Ukládá následující údaje:
*   **Návratová adresa:** Adresa instrukce, kam se má program vrátit po dokončení procedury.
*   **Dynamický ukazatel:** Ukazatel na aktivační záznam volající procedury.
*   **Statický ukazatel:** Ukazatel na aktivační záznam lexikálně nadřazené procedury (pro přístup k nelokálním proměnným).
*   **Parametry:** Hodnoty nebo adresy formálních parametrů předaných proceduře.
*   **Lokální proměnné:** Paměť pro lokální proměnné deklarované v proceduře.
*   **Dočasné proměnné:** Paměť pro mezivýsledky výpočtů.
*   **Uložené registry:** Hodnoty registrů CPU, které musí být obnoveny po návratu z procedury.

#### 56. Uveďte datové struktury, které jsou použitelné k přidělování paměti pro
*   **a) rekurzivně volané procedury a funkce:** **Zásobník (Stack)** – každý aktivační záznam se přidá na vrchol zásobníku při volání a odebere při návratu.
*   **b) dynamické proměnné:** **Halda (Heap)** – paměť se alokuje a uvolňuje dynamicky za běhu programu.
*   **c) dynamické typy:** **Halda (Heap)** – paměť pro instance objektů nebo dynamicky alokované datové struktury.
*   **d) paralelně proveditelné programové jednotky:** Každá programová jednotka (vlákno, proces) má obvykle svůj vlastní **zásobník (Stack)**. Sdílené dynamické proměnné a objekty jsou alokovány na **haldě (Heap)**, která je sdílena mezi jednotkami. (Internet)

#### 57. Popište způsob a důvod použití displeje.
Displej je technika pro efektivní přístup k nelokálním proměnným v lexikálně vnořených procedurách.
*   **Způsob použití:** Displej je pole ukazatelů, kde `display[i]` obsahuje ukazatel na bázi aktivačního záznamu procedury na lexikální úrovni `i`. Místo procházení statického řetězce se pro přístup k proměnné na úrovni `i` použije přímý přístup přes `display[i]`.
*   **Důvod použití:** Zrychlení přístupu k nelokálním proměnným. Procházení statického řetězce může být pomalé, pokud je úroveň zanoření velká. Displej umožňuje přístup v konstantním čase. (Internet)

#### 58. Jaká omezení budou důsledkem přístupu do výpočtového zásobníku pomocí displeje, který je realizován jako array[1..3] of adresa_v_zásobníku
Pokud je displej realizován jako pole s pevnou velikostí `array[1..3]`, bude to mít následující omezení:
*   **Omezení hloubky zanoření:** Programy budou moci používat maximálně 3 úrovně lexikálního zanoření procedur/funkcí. Jakákoli procedura deklarovaná na úrovni 4 nebo hlubší by nemohla být správně obsloužena displejem.
*   **Nepružnost:** Pevná velikost displeje omezuje flexibilitu jazyka a může vést k chybám při překladu programů s hlubším zanořením. (Internet)

#### 59. Jaké informace jsou předávány při volání podprogramu, je-li formálním parametrem procedura
Při předávání procedury jako formálního parametru je nutné předat dvě klíčové informace:
*   **a) V případě jazyků nedovolujících vnořování podprogramů:**
    *   Stačí předat pouze **adresu vstupního bodu** procedury. Prostředí (rozsah viditelnosti) je globální a je vždy stejné.
*   **b) V případě jazyků dovolujících vnořování podprogramů:**
    *   Je nutné předat **adresu vstupního bodu** procedury.
    *   Dále je nutné předat **ukazatel na aktivační záznam lexikálně nadřazeného rozsahu** (tzv. **statický ukazatel** nebo **closure**). To zajišťuje, že procedura bude mít přístup k proměnným z prostředí, ve kterém byla definována, nikoli z prostředí, ve kterém byla volána.

#### 60. K jakému účelu slouží tzv. kaktusový zásobník?
Kaktusový zásobník (cactus stack) je datová struktura používaná v některých programovacích jazycích (např. Lisp, Smalltalk) a operačních systémech pro správu zásobníků v prostředích s paralelním vykonáváním nebo korutinami. Namísto jediného lineárního zásobníku umožňuje, aby se zásobníky větvily, což odráží dynamickou povahu volání procedur v takových systémech. Každá větev představuje samostatný tok řízení. (Internet)

#### 61. Popište paměťové prostředí Javy.
Paměťové prostředí Javy je spravováno Java Virtual Machine (JVM) a je rozděleno do několika oblastí:
*   **Heap (Halda):** Sdílená paměť pro všechny vlákna, kde jsou alokovány všechny objekty a pole. Je spravována Garbage Collectorem.
*   **Stack (Zásobník):** Každé vlákno má svůj vlastní zásobník. Zde se ukládají lokální proměnné primitivních typů, reference na objekty na haldě a aktivační záznamy (stack frames) pro volání metod.
*   **Method Area (Metodická oblast):** Sdílená paměť, která ukládá metadata tříd (bytecode, konstantní pool, informace o polích a metodách).
*   **PC Registers (Program Counter Registry):** Každé vlákno má svůj PC registr, který uchovává adresu instrukce, která má být vykonána.
*   **Native Method Stack (Zásobník nativních metod):** Pro metody napsané v jiných jazycích (např. C/C++) a volané přes JNI. (Internet)

#### 62. Popište obecně základní cyklus interpretu
Základní cyklus interpretu se opakuje pro každou instrukci programu a zahrnuje následující kroky:
1.  **Načtení (Fetch):** Interpret načte další instrukci ze vstupního programu.
2.  **Dekódování (Decode):** Interpret analyzuje instrukci, aby zjistil, co má dělat (jaká operace, jaké operandy).
3.  **Vykonání (Execute):** Interpret provede operaci specifikovanou instrukcí. To může zahrnovat manipulaci s daty, volání funkcí, změnu toku řízení atd.
4.  **Aktualizace (Update):** Interpret aktualizuje svůj vnitřní stav (např. programový čítač) pro další cyklus.
Tento cyklus se opakuje, dokud není program dokončen nebo dokud nenastane chyba.

#### 63. S pomocí algoritmu generování z přednášek rozepište zadaný příklad pro generování z čtveřic
Pro rozepsání příkladu generování z čtveřic je potřeba konkrétní zadaný příklad čtveřic. Bez něj nelze algoritmus aplikovat.

#### 64. S pomocí algoritmu generování z přednášek rozepište zadaný příklad pro generování z trojic
Pro rozepsání příkladu generování z trojic je potřeba konkrétní zadaný příklad trojic. Bez něj nelze algoritmus aplikovat.

#### 65. Uveďte příklad víceznačné gramatiky. Tuto víceznačnost dokažte.
**Příklad víceznačné gramatiky:**
```
E -> E + E | E * E | id
```
**Důkaz víceznačnosti pro řetězec `id + id * id`:**
Lze vytvořit dva různé derivační stromy (nebo dvě různé levé/pravé derivace):

**Derivační strom 1 (id + (id \* id) - \* má vyšší prioritu):**
```
      E
     /|\
    E + E
   /    /|\
  id   E * E
      /   \
     id   id
```
**Derivační strom 2 ((id + id) \* id - + má vyšší prioritu):**
```
      E
     /|\
    E * E
   /|\   \
  E + E   id
 /   \
id   id
```
Protože pro stejný vstupní řetězec existují dva různé derivační stromy, je gramatika víceznačná.

#### 66. Kdy označujeme větu jazyka jako víceznačnou?
Větu jazyka označujeme jako víceznačnou, pokud v gramatice existují alespoň dva různé derivační stromy k jejímu odvození.

#### 67. Může pro víceznačnou gramatiku existovat ekvivalentní gramatika jednoznačná?
Ano, pro víceznačnou gramatiku může (a nemusí) existovat ekvivalentní jednoznačná gramatika. Často je možné gramatiku upravit (např. zavedením priorit operátorů a asociativity), aby se stala jednoznačnou, aniž by se změnil generovaný jazyk. Existují však i inherentně víceznačné jazyky, pro které nelze nalézt jednoznačnou bezkontextovou gramatiku.

#### 68. Operátor umocnění je ve Fortranu pravoasociativní. Zapište G pro aritmetický výraz respektující tuto vlastnost
Pro pravoasociativní operátor umocnění (`^`) se gramatika obvykle zapisuje s pravou rekurzí:
```
E -> T { "+" T }
T -> F { "*" F }
F -> G { "^" F } | "(" E ")" | "id"
G -> "(" E ")" | "id"
```
Kde `E` je výraz, `T` je term, `F` je faktor s umocňováním a `G` je základ umocňování.
(Internet)

#### 69. Popište formálně zásobníkový automat a význam jeho částí
Formálně je zásobníkový automat (Pushdown Automaton, PDA) definován jako sedmice `(Q, Σ, Γ, δ, q0, Z0, F)`, kde:
*   `Q`: Konečná množina stavů.
*   `Σ`: Konečná vstupní abeceda.
*   `Γ`: Konečná zásobníková abeceda.
*   `δ`: Přechodová funkce, `Q × (Σ ∪ {ε}) × Γ → P(Q × Γ*)`. Definuje, jak se automat mění stav, spotřebovává vstupní symbol a modifikuje zásobník.
*   `q0`: Počáteční stav (`q0 ∈ Q`).
*   `Z0`: Počáteční symbol na zásobníku (`Z0 ∈ Γ`).
*   `F`: Množina koncových (akceptujících) stavů (`F ⊆ Q`). (Alternativně se akceptuje prázdným zásobníkem).

#### 70. Popište přechodovou funkci zásobníkového automatu akceptujícího s prázdným zásobníkem, který je ekvivalentní gramatice G [S]: S -> ( S ) | S ( ) | e
Tato gramatika generuje jazyk správně uzávorkovaných výrazů. Pro akceptaci prázdným zásobníkem (s jedním stavem `q`):
*   `δ(q, ε, S) = {(q, (S)), (q, S()), (q, ε)}` (Pro expanzi S podle pravidel gramatiky)
*   `δ(q, (, () = {(q, ε)}` (Pokud je na vstupu `(` a na vrcholu zásobníku `(`, shodují se a odstraní se)
*   `δ(q, ), )) = {(q, ε)}` (Pokud je na vstupu `)` a na vrcholu zásobníku `)`, shodují se a odstraní se)
Počáteční symbol na zásobníku je `S`. (Internet)

#### 71. Jaký jazyk popisuje gramatika G [S]: S -> ( S ) | S ( ) | e
Tato gramatika popisuje jazyk **správně uzávorkovaných výrazů** (např. `()`, `(())`, `()()`, `(()())`).

#### 72. Jaký jazyk popisuje gramatika G [S]: S -> a S a | b S b | e
Tato gramatika popisuje jazyk **palindromů sudé délky** nad abecedou `{a, b}`. Řetězce, které se čtou stejně zepředu i zezadu, a mají sudý počet symbolů (např. `aa`, `bb`, `abba`, `baab`).

#### 73. Navrhněte gramatiku jazyka, jehož věty mají tvar w wreverzní, kde w∈{0,1}\*
Gramatika pro jazyk `w w^R` (kde `w^R` je reverzní `w`):
```
S -> 0 S 0 | 1 S 1 | ε
```
Tato gramatika generuje palindromy sudé délky nad abecedou `{0, 1}`. (Internet)

#### 74. Proveďte zadanou úpravu na zadané gramatice
Pro provedení úpravy je nutné zadat konkrétní gramatiku a konkrétní požadovanou úpravu (např. odstranění levé rekurze, faktorizace, odstranění epsilon pravidel).

#### 75. Charakterizujte vztah mezi jazyky s LL(0) gramatikou a regulárními jazyky
LL(0) gramatiky jsou velmi omezené. Mohou generovat pouze jazyky, kde je každá produkce jednoznačně určena bez jakéhokoli pohledu vpřed (lookahead). To znamená, že pro každý neterminál musí mít každá jeho produkce jedinečný první symbol. Jazyky generované LL(0) gramatikami jsou podmnožinou regulárních jazyků. V podstatě se jedná o velmi jednoduché regulární jazyky, kde je rozhodování o produkci triviální. (Internet)

#### 76. Uveďte formální definici LL(1) gramatiky
Bezkontextová gramatika `G` je LL(1), pokud splňuje následující podmínky:
1.  **Žádná levá rekurze:** `G` neobsahuje levou rekurzi.
2.  **Jednoznačnost výběru produkce:** Pro jakékoli dvě různé produkce `A -> α` a `A -> β` pro stejný neterminál `A` platí:
    `FIRST(α FOLLOW(A)) ∩ FIRST(β FOLLOW(A)) = ∅`
    Kde `FIRST(X)` je množina terminálů, kterými může začínat řetězec odvozený z `X`, a `FOLLOW(A)` je množina terminálů, které mohou následovat za `A` v jakékoli větné formě.
    Zjednodušeně:
    *   `FIRST(α) ∩ FIRST(β) = ∅`
    *   Pokud `ε ∈ FIRST(α)`, pak `FOLLOW(A) ∩ FIRST(β) = ∅`
    *   Pokud `ε ∈ FIRST(β)`, pak `FOLLOW(A) ∩ FIRST(α) = ∅`

#### 77. Zdůvodněte, proč je každá LL(1) gramatika silná
Každá LL(1) gramatika je silná, protože rozhodování o výběru produkce pro neterminál `A` je založeno pouze na aktuálním neterminálu na vrcholu zásobníku a na jednom symbolu z vstupního řetězce (lookahead). Tato informace je dostatečná pro jednoznačné určení produkce, což je definice silné LL(k) gramatiky pro k=1. (Internet)

#### 78. Uveďte nutnou a postačující podmínku pro to, aby gramatika byla silná LL(k)
Nutná a postačující podmínka pro to, aby gramatika byla silná LL(k), je, že pro jakékoli dvě různé produkce `A -> α` a `A -> β` pro stejný neterminál `A` platí:
`FIRST_k(α FOLLOW_k(A)) ∩ FIRST_k(β FOLLOW_k(A)) = ∅`
Kde `FIRST_k(X)` je množina všech řetězců délky `k` (nebo kratších, pokud `X` generuje kratší řetězce), kterými může začínat řetězec odvozený z `X`, a `FOLLOW_k(A)` je množina všech řetězců délky `k`, které mohou následovat za `A`. (Internet)

#### 79. K čemu slouží úprava gramatiky zvaná "pohlcení terminálu"? Uveďte příklad.
Termín "pohlcení terminálu" není standardní, ale pravděpodobně odkazuje na **levou faktorizaci (left factoring)**. Tato úprava slouží k odstranění společných prefixů z pravých stran produkcí pro stejný neterminál, což je nezbytné pro LL(k) parsery.
*   **Příklad:**
    Původní gramatika:
    `A -> αβ | αγ`
    Po levé faktorizaci:
    `A -> αA'`
    `A' -> β | γ`
Tím se umožní parseru rozhodnout o výběru produkce až po přečtení společného prefixu `α`. (Internet)

#### 80. Uveďte příklady algoritmicky nerozhodnutelných problémů z teorie formálních jazyků
Algoritmicky nerozhodnutelné problémy jsou ty, pro které neexistuje žádný algoritmus, který by vždy správně a v konečném čase poskytl odpověď. Příklady z teorie formálních jazyků:
*   **Problém zastavení (Halting Problem):** Zda daný program zastaví pro daný vstup.
*   **Ekvivalence dvou bezkontextových gramatik:** Zda dvě bezkontextové gramatiky generují stejný jazyk.
*   **Víceznačnost bezkontextové gramatiky:** Zda je daná bezkontextová gramatika víceznačná.
*   **Zda bezkontextová gramatika generuje všechny řetězce (Σ\*):** Zda jazyk generovaný CFG je roven množině všech možných řetězců. (Internet)

#### 81. Existuje pro libovolnou gramatiku typu 2 algoritmus pro
*   **a) převod na ekvivalentní nelevorekurzivní gramatiku?** **Ano.** Existuje algoritmus pro eliminaci levé rekurze z libovolné bezkontextové gramatiky.
*   **b) převod na ekvivalentní LL(k) gramatiku?** **Ne.** Ne všechny bezkontextové gramatiky lze převést na ekvivalentní LL(k) gramatiku. LL(k) gramatiky jsou podmnožinou bezkontextových gramatik.
*   **c) převod na ekvivalentní LR(k) gramatiku?** **Ano, ale s výhradami.** Všechny bezkontextové jazyky lze parsovat LR(k) parserem, ale ne všechny bezkontextové gramatiky jsou LR(k). Existuje algoritmus pro převod bezkontextové gramatiky na ekvivalentní LR(k) gramatiku, pokud jazyk, který generuje, je LR(k).
*   **d) výpočet množin LR(0) položek?** **Ano.** Existuje algoritmus pro výpočet kanonické kolekce LR(0) položek pro libovolnou bezkontextovou gramatiku.

#### 82. Zdůvodněte proč LR(k) gramatiky popisují obsáhlejší třídu jazyků než LL(k)
LR(k) gramatiky popisují obsáhlejší třídu jazyků než LL(k) gramatiky z několika důvodů:
*   **Zpracování levé rekurze:** LR parsery dokáží přímo zpracovávat levou rekurzi, zatímco LL parsery ji vyžadují eliminovat.
*   **Zpracování společných prefixů:** LR parsery dokáží zpracovat gramatiky se společnými prefixy bez nutnosti levé faktorizace.
*   **Rozhodování "zdola nahoru":** LR parsery rozhodují o redukci až poté, co viděly celou pravou stranu produkce (handle), což jim dává více kontextu než LL parserům, které rozhodují "shora dolů" na základě omezeného lookaheadu.
*   **Více kontextu:** LR parsery efektivněji využívají kontext z již zpracované části vstupu (zásobníku).

#### 83. Porovnejte počet stavů charakteristického automatu (tj. rozsáhlost souboru množin položek) LR(0), LALR(k) a LR(k).
*   **LR(k):** Generuje největší počet stavů. Každá LR(k) položka obsahuje lookahead, a pokud se lookahead liší, vytváří se nový stav, i když jádro položky je stejné.
*   **LR(0) / SLR(k):** Generují nejmenší počet stavů. LR(0) položky neobsahují lookahead. SLR(k) používá stejné jádro stavů jako LR(0), ale rozhoduje o redukci na základě FOLLOW množin.
*   **LALR(k):** Generuje stejný počet stavů jako LR(0) (nebo SLR(k)). LALR(k) vzniká sloučením LR(k) stavů, které mají stejné jádro LR(0) položek, a sjednocením jejich lookahead množin. Tím se snižuje počet stavů oproti LR(k), ale zachovává se většina jeho síly.
Vztah je: `Počet_stavů(LR(0)) = Počet_stavů(SLR(k)) = Počet_stavů(LALR(k)) <= Počet_stavů(LR(k))`

#### 84. Jaké podmínky musí splňovat množiny LR(0) položek, aby gramatika byla SLR(1)?
Gramatika je SLR(1), pokud pro každou množinu LR(0) položek `I` platí, že:
1.  **Žádný konflikt přesun-redukce:** Pokud `I` obsahuje položku `A -> α . t β` (kde `t` je terminál) a položku `B -> γ .` (redukční položka), pak `t` nesmí být v `FOLLOW(B)`.
2.  **Žádný konflikt redukce-redukce:** Pokud `I` obsahuje dvě redukční položky `A -> α .` a `B -> γ .`, pak `FOLLOW(A)` a `FOLLOW(B)` musí být disjunktní (`FOLLOW(A) ∩ FOLLOW(B) = ∅`).

#### 85. Popište tvar LR(0) položky a význam jejích jednotlivých částí
Tvar LR(0) položky je: `A -> α . β`
*   `A -> αβ`: Je to produkční pravidlo gramatiky.
*   `.` (tečka): Označuje pozici v pravé straně produkce, která odděluje již zpracovanou část (`α`) od části, která se ještě očekává (`β`).
*   `α`: Řetězec symbolů (terminálů nebo neterminálů), které již byly rozpoznány a jsou na zásobníku.
*   `β`: Řetězec symbolů, které se ještě očekávají na vstupu, aby se dokončila shoda s pravou stranou produkce.
LR(0) položka neobsahuje žádnou informaci o lookaheadu.

#### 86. Popište tvar LR(k) položky a význam jejích jednotlivých částí
Tvar LR(k) položky je: `A -> α . β, w`
*   `A -> α . β`: Stejné jako u LR(0) položky, označuje produkční pravidlo a pozici tečky.
*   `w`: Je to lookahead řetězec délky `k`. Reprezentuje množinu terminálních řetězců délky `k`, které mohou následovat za `A`, pokud se produkce `A -> αβ` zredukuje. Tato lookahead informace pomáhá parseru rozhodovat o akcích přesun/redukce a redukce/redukce.

#### 87. Definujte překladovou gramatiku
Překladová gramatika (Translation Grammar) je rozšíření bezkontextové gramatiky, která kromě generování řetězců umožňuje i generování výstupu (překladu). Formálně se definuje jako `PG = { N, T ∪ D, P, S }`, kde:
*   `N`: Množina neterminálních symbolů.
*   `T`: Množina vstupních terminálních symbolů.
*   `D`: Množina výstupních terminálních symbolů (disjunktní s `T`).
*   `P`: Množina přepisovacích pravidel, která mohou obsahovat symboly z `T`, `N` a `D`.
*   `S`: Počáteční symbol.
Pravidla specifikují, jak se vstupní řetězec transformuje na výstupní řetězec.

#### 88. Definujte překladový automat
Překladový automat (Transducer) je typ automatu, který kromě akceptace vstupního řetězce generuje i výstupní řetězec. Na rozdíl od akceptujícího automatu, který pouze rozhoduje, zda vstup patří do jazyka, překladový automat transformuje vstup na výstup. Může být implementován jako konečný automat s výstupem (např. Mooreův nebo Mealyho automat) nebo jako zásobníkový automat s výstupem. (Internet)

#### 89. Charakterizujte L-atributovanou gramatiku
L-atributovaná gramatika je typ atributované gramatiky, ve které mohou být dědičné atributy vyhodnocovány během jediného průchodu shora dolů (zleva doprava) derivačním stromem. To znamená, že hodnota dědičného atributu uzlu může záviset na:
*   Atributech jeho rodiče.
*   Syntetizovaných nebo dědičných atributech jeho levých sourozenců.
*   Syntetizovaných atributech jeho vlastních potomků.
L-atributované gramatiky jsou vhodné pro jednoprůchodové parsery, jako je rekurzivní sestup. (Internet)

#### 90. Charakterizujte S-atributovanou gramatiku
S-atributovaná gramatika je typ atributované gramatiky, ve které se používají **pouze syntetizované atributy**. To znamená, že hodnota atributu uzlu může záviset pouze na atributech jeho potomků. Syntetizované atributy se vyhodnocují zdola nahoru (od listů ke kořeni) derivačním stromem. S-atributované gramatiky jsou vhodné pro parsery zdola nahoru, jako jsou LR parsery. (Internet)

#### 91. Jakou metodu syntaktické analýzy používá YACC
YACC (Yet Another Compiler Compiler) používá metodu syntaktické analýzy **LALR(1)** (Look-Ahead LR s jedním symbolem pohledu vpřed). LALR(1) je výkonná metoda zdola nahoru, která je schopna parsovat širokou třídu bezkontextových gramatik.

#### 92. Jakým způsobem řeší YACC konflikty redukce-redukce
YACC řeší konflikty (shift-reduce a reduce-reduce) pomocí předdefinovaných pravidel a pravidel definovaných uživatelem:
*   **Konflikt přesun-redukce (Shift-Reduce):** YACC standardně preferuje **přesun (shift)** před redukcí. To je obvykle správné pro většinu programovacích jazyků (např. pro operátory s asociativitou).
*   **Konflikt redukce-redukce (Reduce-Reduce):** YACC standardně preferuje **redukci podle pravidla, které se objevilo dříve** ve specifikaci gramatiky (tj. pravidlo s nižším číslem). Uživatel může také explicitně definovat priority a asociativitu operátorů, aby YACC tyto konflikty vyřešil podle sémantiky jazyka. (Internet)