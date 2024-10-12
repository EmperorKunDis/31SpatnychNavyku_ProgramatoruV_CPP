Ahoj a vítejte na mém seznamu nováčkovských návyků v C++. C++ je neuvěřitelně složitý jazyk s bohatou historií, takže ať už jsi úplný nováček, který si na to musí dávat pozor, nebo chceš jenom trochu vylepšit svůj kód, pojďme na to. Nováčkovská věc číslo jedna: používání namespace standard. Lidi to většinou používají, aby ušetřili nějaké psaní, takže můžeš říct jen „string“ místo „std::string“. Pokud je to omezeno jen na jednu funkci, tak to možná není tak hrozné, ale...

Opravuju, obvykle se to používá na globální úrovni, a ještě horší je, když to uděláte v hlavičkovém souboru, protože tím nutíte všechny, kdo používají váš kód, udělat to samé. Takže prosím, nedělejte to v hlavičkovém souboru a raději používejte názvy, které skutečně používáte. Dále, používání standardního konce řádku, obzvlášť v cyklu. Asi jste chtěli jen vytisknout nový řádek, ale konec řádku dělá víc než to — také vyprázdní buffer, což zabere extra čas. Místo toho prostě použijte znak pro nový řádek. A nakonec, používání for cyklu podle indexu, když...

"Pro tento případ je lepší použít cyklus založený na rozsahu, protože mě vlastně vůbec nezajímá index. Když použiješ cyklus založený na rozsahu, index tam není, takže je menší šance na překlep nebo chybu o jedničku. Číslo čtyři: používat cyklus, když už existuje standardní algoritmus, který dělá to, co potřebuješ. Když chceš udělat něco jednoduchého, jako najít index prvního kladného čísla ve vektoru, je to tak jednoduché, že se rozhodneš to napsat sám. Místo toho zvaž, jestli už neexistuje nějaký algoritmus."

Tohle už dělá to, co se snažíš udělat. V tomhle případě můžeme použít standardní funkci `find_if`, abychom našli, kde je první kladný prvek číslo pět, když bys mohl použít standardní pole. C-style pole často "decay" na ukazatele a vyžadují, abys předal délku pole spolu s samotným polem. To je jen další příležitost udělat překlep. Místo toho použij standardní pole. Číslo šest: jakékoli použití `reinterpret_cast` – to je skoro jediné, co s objektem můžeš dělat.

Z reinterpret_cast dostaneš zpátky původní typ, skoro všechno ostatní je nedefinované chování a to samé platí i pro C-style casting. Omlouvám se, slavný algoritmus z Quake 3 na výpočet inverzního druhého odmocniny – reinterpretace bytů floatu jako longu je vlastně nedefinované chování. Vždycky můžeš reinterpret castnout adresu objektu na typ char, což ti umožní prozkoumat nebo vytisknout byty, které tvoří objekt, takže můžeš vidět, jak vypadá jeho paměťové rozložení. Ale co se týče C++, to už je jiná kapitola.

Použití reinterpret_castu tady není potřeba, bitcast interpretuje byty jednoho objektu jako jiný typ. V tomhle případě můžu převést jakýkoliv objekt na pole bytů stejné velikosti. Funkce číslo 7 odstraňuje const. Tato funkce přijímá mapu, která mapuje řetězce na počet jejich výskytů. Vezme dvě slova a vrátí ti to, které se vyskytuje častěji. První způsob, jak to můžeš zkusit implementovat, je vyhledat počty těch dvou slov a pak, pokud je první počet...

Větší než druhý, pak vrátit první slovo. Když se to pokusím zkompilovat, dostanu divnou chybovou hlášku, která mi říká, že metoda není označená jako const, a tak jsme skončili s tímto kódem. Vím, že mapu nemodifikuju správně. Správné řešení v tomhle případě není zbavit se const, ale místo toho použít metodu at. Ta je const verzí operátoru hranaté závorky a vyhodí výjimku, pokud slovo není v mapě. Ale mohl bys se ptát, proč prostě nepřidají const verzi, aby to takhle fungovalo.

Tohle nás přivádí k nováčkovské věci číslo osm – nevíme, že operátor hranatých závorek vkládá prvek do mapy, pokud tam už není. Správně, když se snažíme vyhledat tohle slovo v mapě, vlastně ho s počtem nula vložíme. Číslo devět – ignorování const správnosti. Tato funkce prochází vektorem a jednoduše vypisuje každý prvek, jeden prvek na řádek. Nemění vektor, takže bychom měli a měli bychom ho označit jako const. To je dvojnásobně důležité pro a.

Funkční parametr, aby volající věděl, že tuto funkci může použít, aniž by se mu změnil vektor. Číslo 10, nevědět o životnosti řetězcových literálů. Řetězcové literály jako tento jsou garantovány, že přežijí celou dobu běhu programu, takže je naprosto v pořádku je vracet, i když to vypadá jako reference na lokální proměnnou. Číslo 11, nepoužívat strukturované vazby. Tady máme mapu názvů barev a jejich hex hodnot. Pak prostě projdeme všechny páry a vytiskneme název a.

Hodnota hex by byla mnohem čitelnější, kdybychom tyto věci mohli nazývat jménem a hexem místo pair.first a pair.second. A přesně to nám umožňuje strukturované vazba. Chytíme pár jako referenci a strukturovaná vazba zavádí jméno a hex jako názvy pro první a druhý prvek páru. Strukturované vazby lze také použít s vlastními typy, pokud jsou členové veřejní. Názvy se přiřazují proměnným podle pořadí jejich deklarací. Číslo 12: použití více výstupních parametrů.

Když chceš vrátit víc věcí z funkce, radši si vytvoř základní strukturu a těm věcem dej jména. Pak můžeš vrátit ty víc hodnot tím, že vrátíš tu strukturu. Volající může dokonce udělat, že to vypadá, jako by se vrátilo víc hodnot, pomocí strukturovaného vázání. 13. Dělat práci během běhu programu, kterou by šlo udělat při kompilaci. Tady je funkce, která dává vzorec pro součet prvních n celých čísel. Někdy můžou být parametry známy při kompilaci a mohl bys to udělat.

Výpočet dopředu, dej vědět kompilátoru, že je úplně v pohodě to spočítat předem. Číslo 14 – zapomněl jsem označit destruktor jako virtuální. Když se odvozená třída smaže přes ukazatel na tuto základní třídu, destruktor odvozené třídy se neprovolá, zavolá se jen destruktor základní třídy. Tady mám třídu, která dědí ze základní třídy, která nemá virtuální destruktor. Tato funkce očekává ukazatel na základní třídu, používá nějakou základní funkcionalitu a pak se to smaže.

Když to bude hotové, stane se to automaticky, protože používám unikátní ukazatel, ale totéž platí, pokud vezmeš normální ukazatel a pak manuálně zavoláš delete. Pokud předáš ukazatel na instanci tohoto odvozeného typu, tak se na konci zavolá špatný destruktor. Aby se zajistilo, že se zavolá správný destruktor, i přes ukazatel na základní třídu, musíš označit funkci jako virtuální. Také je dobrá praxe explicitně označit destruktor odvozené třídy jako override.

Jsou inicializovány v pořadí, v jakém se objevují v inicializačním seznamu zleva doprava. To vypadá v pohodě, ale skutečné pořadí inicializace členů je podle toho, v jakém jsou deklarovány. Nejprve inicializujeme konec jako začátek plus velikost, ale ten m start je odpad, ještě nebyl inicializován. Samozřejmě to můžeme opravit tím, že deklarujeme začátek jako první. Nebo protože je start také parametrem funkce, mohli bychom prostě definovat proměnnou end v závislosti na parametru start, aniž bychom si uvědomovali, že je tu rozdíl.

Mezi výchozím a hodnotovým inicializováním jsou x a x2 výchozí inicializované, takže obsahují nějaký bordel, dokud do nich něco nedáš. y, y2 a y3 jsou hodnotově inicializované, takže je zaručeno, že budou mít hodnotu 0. z na druhou stranu není ani výchozí, ani hodnotově inicializované. To je deklarace funkce. I když to je trošku méně efektivní, skoro vždycky je dobrý nápad inicializovat svoje hodnoty. Stejně to platí, když máš agregát nebo pole. V prvních dvou případech n a m budou bordel a s bude prázdný řetězec.

V posledních třech případech jsou n a m nula a s je prázdný řetězec. Všimni si, že i při výchozím inicializování se prázdný řetězec stále inicializoval. To je proto, že při výchozím i hodnotovém inicializování, pokud definuješ výchozí konstruktor, bude zavolán. 17. Přehnané používání magických čísel. Zavedení základní konstanty do tvého kódu může udělat kód mnohem čitelnější. Kompilátor to stejně optimalizuje, tak mu dej dobrý název. 18. Pokus o přidání nebo odstranění prvků z kontejneru během procházení.

No, občas je to prostě nutné, ale co tím myslím je, že nováčci to často dělají špatně. Snažíme se dát kopii vektoru na jeho konec, ale přidávání nebo odebírání prvku z vektoru může způsobit, že iterátory k vektoru se stanou neplatnými. Například `push_back` může vyžadovat, abychom vektor zvětšili a přesunuli všechny prvky na nové místo. Po přesunu obsahu vektoru na nové místo nemůžeš očekávat, že ukazatel na konec zůstane stejný. Narazíš na stejný problém. Ve skutečnosti je to asi jasnější, proč.

Narazil bys na tenhle problém, kdybys používal iterátory přímo. Tohle je případ, kdy použití indexu smyčky skutečně problém vyřeší. Je jedno, jestli se obsah tvého vektoru přesune někam jinam, prvek i je pořád prvek číslo 19. Rozumím ti, že se snažíš vrátit přesunutou lokální proměnnou. Vektor může být velký objekt a nechceš ho kopírovat, takže se pokusíš ho přesunout. Kdybys se jen pokusil vrátit v přímo, žádná kopie by nevznikla.

A žádnej přesun v téhle situaci, to je kvůli optimalizaci návratový hodnoty, ale co když kompilátor nemůže udělat optimalizaci návratový hodnoty ve všech případech? Přesun je zbytečnej. Kompilátor vždycky ví, že může přesunout lokální proměnnou, ale v některých případech to aktivně brání optimalizaci návratový hodnoty. Takže proto tohle je jedno z mála pravidel, kde můžu říct, že bys to prostě nikdy neměl dělat, což nás přivádí k číslu 20, myslet si, že přesun fakt něco přesouvá. Tady je implementace standardního přesunu.

Celá ta šablonová definice může být trochu moc najednou, takže se podívejme jen na případ s int. Funkce move bere odkaz na hodnotu typu int, staticky ho přetypovává na odkaz na r hodnotu a vrací ho. To samé se děje i při přetížení pro r hodnotu, jen se to staticky přetypovává na r hodnotu a vrací to. Přesnější název pro move by asi byl něco jako přetypování na r hodnotu. Číslo 21 si myslí, že pořadí vyhodnocení je zaručené zleva doprava. Tady je slavný příklad – máme řetězec.

To říká, ale slyšel jsem, že to funguje, i když v to nevěříš. Nejprve nahradíme prvních čtyři znaky prázdným řetězcem, pak najdeme „even“ a nahradíme to „only“. Pak najdeme „don't“ a odstraníme to. S tímto uvažováním bychom měli skončit s „slyšel jsem, že to funguje jen pokud v to věříš“. Ale před C++ 17 měl kompilátor vlastně povoleno počítat jakýkoli podvýraz v libovolném pořadí, takže teoreticky mohl nejprve najít místo „even“ a pak nahradit prvních čtyři znaky, což by udělalo to místo posunuté.

Čtyři, takže když k druhé výměně dojde, nahradí tyto čtyři znaky jenom a můžeš vidět, jak to pokračuje, nedostaneš výsledek, který jsi očekával. No, dobrou zprávou je, že od C++17 je tento příklad zaručený – pokud máš a.b, tak a se zaručeně vyhodnotí před b. I když v C++20 pořadí, ve kterém se vyhodnocují argumenty funkcí, stále není zaručeno zleva doprava. To by nebylo až tak důležité, kdyby a, b a c byly čisté funkce, ale pokud mají a, b a c vedlejší efekty, tak...

Pořadí, ve kterém je voláme, může mít fakt vliv. Používáme úplně zbytečné alokace na haldě, když by nám tady stačila alokace na zásobníku. Vytvoříme dva záznamy zákazníků na haldě, pak něco děláme a nakonec ty proměnné na konci funkce smažeme. Otázka, kterou si máme položit, je, jestli to opravdu muselo být na haldě. Je dost pravděpodobné, že by to bylo v pohodě i s alokací na zásobníku. Tak si řekněme, že ty objekty jsou prostě moc velké.

A fakt je, že je chceš mít na hromadě, což nás přivádí k číslu 23. Nepoužíváš unique pointer a shared pointer pro alokaci na hromadě? Co se stane, když se uprostřed vyhodí výjimka? Pak se ty delete nikdy neprovedou a paměť se propadne. Když chceš zajistit, že se nějaký zdroj uvolní, musíš ten úklidový kód dát do destruktora. Tak proč si neudělat třídu, která drží ukazatel, a v jejím destruktoru ten ukazatel uvolní? No, a přesně to dělá unique pointer.

Můžeš mu dát ukazatel alokovaný na haldě, a když vyjde z rozsahu, tak se sám smaže. Sdílený ukazatel na druhou stranu používá systém počítání referencí, což je něco podobného, co máš třeba v jazyce Python. Když počet referencí klesne na nulu, jakmile poslední sdílený ukazatel vyjde z rozsahu, je ten sdílený ukazatel zodpovědný za smazání. Tenhle systém je mnohem nákladnější, protože zvyšování a snižování referencí musí probíhat atomově. A to nás přivádí k číslu 24 – přímo konstrukce unikátního nebo sdíleného ukazatele.

Místo toho, abyste používali make unique nebo make shared, použijte make unique a make shared, které předají vaše argumenty přímo konstruktoru vašeho objektu. Jakékoliv použití new nebo delete nemá smysl přepisovat funkce, které už tady existují. Snažím se spravovat paměť nějakého zdroje a pak ho smazat, když je hotový, což už dělá unikátní ukazatel. Nesnažte se spojovat účel vaší třídy s myšlenkou vlastnictví objektu, to je úplně jiná věc – unikátní ukazatel a sdílený ukazatel.

Společně pokrývají prakticky všechny platné použití nového nebo smazání čísla 26. Jakýkoli pokus o manuální správu zdrojů je v podstatě stejný příběh jako u new a delete. Pokud se ocitnete v situaci, kdy ručně uvolňujete, zavíráte nebo uvolňujete jakýkoli zdroj, podívejte se, jestli neexistuje třída, která to dělá automaticky. Mimochodem, ta myšlenka, že se zdroje automaticky zavírají v destruktoru, se nazývá RAII, což znamená, že získání zdroje je inicializace, ale ve skutečnosti to má více společného s tím, že se zajišťuje, že zdroje jsou.

Uvolněno po zničení číslo 27, že raw pointery jsou nějak špatné. Tady je základní max funkce, ta jenom čte z pointerů a vůbec ji nezajímá, kdo je zodpovědný za jejich uvolnění. Pokud tvoje funkce nemá nic společného s vlastnictvím dotyčných objektů, není potřeba používat smart pointery. Zvykem je, že raw pointery nevlastní to, na co ukazují, a to se nesmí plést s const-ness pointeru. Tato add funkce přidává zdroj do.

Cílová adresa, ale tahle funkce neřídí životnost žádného z ukazatelů. Samozřejmě, pokud spolupracujete s C kódem, tenhle kód nebude dodržovat tuto konvenci. C funkce vám může vrátit paměť alokovanou na haldě, kterou očekává, že odstraníte. Buďte opatrní, pokud máte ukazatel vytvořený s maloc, musíte ho uvolnit pomocí free, nemůžete jen tak nechat unique_ptr, aby se to pokusil smazat pomocí vestavěného delete. Můžete ale stále použít unique_ptr, jen si musíte definovat vlastní.

"Deleter, který používá volné číslo 28, vrací sdílený ukazatel, když si nejsi jistý, že objekt bude sdílený. Pokud má volající unikátní ukazatel, je levné a snadné ho převést na sdílený ukazatel, pokud to opravdu potřebují. Mohli by dokonce přímo přiřadit návratovou hodnotu unikátního ukazatele ke sdílenému ukazateli. Ale pokud jim rovnou vrátíš sdílený ukazatel, škoda už bude napáchána, pokud vlastně chtěli jen unikátní ukazatel číslo 29, přičemž si myslí, že to je sdílený ukazatel."

Je vlákno bezpečný, část s počítáním referencí u sdíleného ukazatele je vlákno bezpečná. Tady vytvářím sdílený zdroj a předávám ho dvěma pracovním vláknům, protože počítání referencí je vlákno bezpečné, nehrozí, že by objekt nebyl smazán nebo byl smazán dvakrát. Avšak jen ta část s počítáním referencí je atomická. Tady, kde přistupujeme k proměnné x a zdroji, atomické není a nejsou tu žádné zámky. To je prostě obyčejná datová závada, kdy se dvě vlákna snaží měnit stejnou paměť.

Pokud chceš opravit závod dat, musíš to udělat stejně jako bys opravil jakýkoliv jiný závod dat. A není dobré zaměňovat konstantní ukazatel s ukazatelem na konstantu. Rozdíl mezi konstantním ukazatelem a ukazatelem na konstantu je docela jednoduchý, ale spousta nováčků si s tím neví rady. Pravidlo je, že "const" se vztahuje na to, co je hned nalevo od něj, pokud to není to nejlevější, pak se vztahuje na to, co je napravo. Takže tady se "const" vztahuje na int, ne.

K pointeru zde cons platí pro int ne na pointer a zde con dodává na ukazatel nikoli na int číslo 31 ignorování varování kompilátoru jejich ignorování nebo jejich časté vypínání vede k nedefinovanému chování doufám, že se vám můj seznam nováčků líbil c++.
