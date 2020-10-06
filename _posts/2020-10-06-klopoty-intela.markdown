---
layout: post
title:  "Kłopoty Intela i rewolucja TSMC"
date:   2020-10-06 08:38:12 +0200
image: /download/tekst_html_7a1fddc154f1a3fb.jpg
summary_large_image: /download/tekst_html_7a1fddc154f1a3fb.jpg
categories: jekyll update
---


Przygotowując artykuł na temat zakupu firmy ARM przez Nvidię zauważyłem, że brakuje wprowadzenia w temat struktury produkcji w przemyśle elektronicznym. Bez znajomości tego zagadnienia (a przynajmniej bez odwołań do pewnych terminów), trudno jest w poważny sposób przeanalizować tą transakcję (jak i wiele innych zależności na rynku elektroniki).

**Etapy produkcji produktu elektronicznego**

Inżynieria produkcji zajmuje się zasadami projektowania wyrobów i procesów, jak również podstawami sterowania, eksploatacji, organizacji i zarządzania procesami wytwarzania. W przypadku produktu elektronicznego (jak również wielu innych produktów składających się z części) możemy wyróżnić (w dużym uproszczeniu) następujące elementy procesu produkcji i dostaw prowadzące do gotowego produktu dostępnego w sklepie:

- Podwykonawcy dostarczający części (IP providers) do konkretnych komponentów z których wytwarzany jest potem końcowy produkt. Można porównać z dostawcą biblioteki/frameworka dla produkcji konkretnego programu

- Projekt (Design) - główny projektant produktu (np. procesora) który tworzy produkt na bazie istniejących komponentów (własnych i kupionych).

- Fabrication - firma wykonująca fizycznie konkretne podzespoły np. układy scalone na krzemie.

- Integration - firma integrująca konkretne podzespoły dla odbiorcy końcowego np. na PCB

- Sale - firma sprzedająca gotowy produkt

Jako przykład możemy przeanalizować produkcję smartfona (również w dużym uproszczeniu):

- Sale - mamy firmę Xiaomi która zamierza sprzedawać konkretny produkt np. smartfona. W tym celu dobiera komponenty (procesor, pamięć, kamera) dodatkowo projektuje bądź zleca zaprojektowanie płytki PCB i obudowy.

- Integration - to jest firma która fizycznie składa produkt. Dostaje od podwykonawców osobno PCB, chipy, SoCi etc. i integruje je razem w gotowy produkt. Chyba najlepszym znanym przykładem takiej firmy jest Foxconn.

- Design - to jest firma projektująca konkretny element e.g. procesor, pamięć aparat fotograficzny, SoC np. MediaTek projektuje procesory do telefonów komórkowych. Oczywiście projektowaniem zajmuje się też w jakimś zakresie Xiaomi dlatego często wyróżnia się high-level design (całego systemu) i low-level design.

- IP Provider - MediaTek może korzystać z “frameworków” by przyspieszyć pracę, poprawić jakość (specjalizacje podwykonawców) czy zachować zgodność z pewnym standardem np. może wykupić od firmy ARM licencję na wykorzystanie ich ISA przez co na przykład uzyskuje dostęp do całego ekosystemu oprogramowania - kompilatory, biblioteki systemy operacyjne etc.

- Fabrication - Ta firma wykonuje konkretny element na przykład jako układ scalony na krzemie na podstawie projektu. Jako przykład MediaTek zleca wykonanie procesora TSMC na krzemie na podstawie swojego designu będącego zmodyfikowanym procesorem na licencji ARMa.

Nic nie stoi na przeszkodzie by działalność jednej firmy obejmowała kilka różnych etapów produkcji np. firma projektująca procesory miała własną ISA i własną fabrykę do produkcji układów scalonych. Jak również by firma zamawiająca produkt zaprojektowała jego części np. Nvidia z kartami graficznymi. Nazywamy to integracją pionową, i opisze taki model w następnej sekcji.

W bardziej skomplikowanych systemach możemy mieć wiele części które same w sobie stanowią oddzielny produkt np. karty graficzne, procesory, aparaty fotograficzne, baterie etc.

Dla każdej z takich części powtarzają się zależności opisywane powyżej.

<img src="/download/tekst_html_7a1fddc154f1a3fb.png" style="width:6.5in;height:5.55556in" />

**Intel i integracja pionowa (wertykalna)**

W przemyśle elektronicznym do końca lat 80tych dominowała integracja pionowa (wertykalna) procesu produkcyjnego. Integracja pionowa jest to sposób zarządzania produkcją w której łańcuch dostaw przedsiębiorstwa niezbędnych do wykonania produktu jest własnością tego przedsiębiorstwa.

Prześledźmy to zatem na konkretnym i chyba najbardziej znanym przykładzie firmy Intel. Intel to firma założona przez byłych pracowników Fairchild Semiconductors Robert Noyce’a i Gordon Moore’a. Powodzenie Intela tak jak i Microsoftu na rynku elektroniki zaczęło się od firmy IBM, w latach 70tych. Obie firmy założone były praktycznie jednocześnie: Intel w roku 1968 a Microsoft w 1975 i są pochodną rewolucji technicznej jaką było wynalezienie [monolitycznego układu scalonego][monolitycznego-układu-scalonego] (patrz ramka). Ze względu na dynamiczny rozwój rynku PC, coraz większe wymagania klientów, a także fakt że koncern IBM totalnie zignorował ten segment sprzedaży komputerów osobistych, IBM zdecydował się na bezprecedensowe rozwiązanie (z ówczesnego punktu widzenia) - na zlecenie firmom trzecim produkcji komponentów do swoich produktów w tym dwóch najważniejszych tzn. systemu operacyjnego i procesora. Były nimi właśnie Microsoft i Intel.

--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------

> Monolityczny układ scalony to taki w którym wszystkie elementy (zarówno elementy czynne jak i bierne) wykonane są w monokrystalicznej strukturze półprzewodnika. Istnieją również hybrydowe układy scalone, czyli zminiaturyzowane układ elektroniczne zbudowany z pojedynczych urządzeń, takich jak urządzenia półprzewodnikowe (np. tranzystory, diody lub monolityczne układy scalone) i elementy bierne (np. rezystory, induktory, transformatory i kondensatory), połączone z podłożem lub płytką drukowaną (PCB). Wynalazcą scalonych układów hybrydowych był Jack Kilby pracujący w Texas Instruments, za co dostał nagrodę nobla w 2000 roku. Wynalazcą układów monolitycznych wspomniany Rober Noyce założyciel Intela. Oba odkrycia zostały niezależnie dokonane w tym samym roku 1958. Co ciekawe, oba odkrycia zostały niezależnie dokonane w tym samym roku 1958. W 1961 roku, Noyce otrzymał patent na układ scalony od amerykańskiego Urzędu Patentowego. Zapoczątkowało to długą walkę patentową pomiędzy Noyce'em i Jackiem Kilby. Układ scalony Kilby'ego był jednak wykonany z germanu, podczas gdy układ Noyce'a z krzemu, i to drugie rozwiązanie zdominowało rynek. Ostatecznie Kilby uzyskał nagrodę Nobla zaś Noyce zrobił karierę finansową jako szef Intela. Jest to ważne gdyż wyznaczyło profil firmy Intel do dziś a także na lata sposób produkcji produktów elektronicznych (do tzw. rewolucji “tajwańskiej” zapoczątkowanej przez TSMC, o czym będzie w drugiej części artykułu). Można zatem powiedzieć że Intel był jednym z pierwszych (jeśli nie pierwszym) fabów (fabryk produkujących układy scalone) na świecie. 

> <img src="/download/tekst_html_6f7120e42381534b.png" style="width:4.03125in;height:2.67708in" />

> Na zdjęciu pierwszy układ scalony zaprojektowany przez Jacka Kilby’iego. 

--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------

Historia Microsoftu jest inna niż Intela gdyż IBM nie zażądał od Billa Gatesa udzielenia licencji na kod źródłowy innemu podwykonawcy. W ten sposób Microsoft uzyskał wyłączność na oprogramowanie do tego modelu komputera. Może stało się tak dlatego że oprogramowanie w latach 60tych i 70tych było traktowane jako mniej istotny dodatek do sprzętu. Może też dlatego, że uwaga IBMa zogniskowana była na produkcji sprzętu do przynoszących wtedy (i dzisiaj) duże zyski serwerach i komputerach mainframe.

Pomijając te spekulacje, ważne że w przypadku Intela było inaczej. IBM zażądał już na samym początku by firma udzieliła licencji na swoje produkty drugiemu podwykonawcy - najprawdopodobniej w celu dywersyfikacji łańcucha dostaw i zabezpieczenia się przed ewentualną zależnością/uzależnieniem od jednego podwykonawcy. W ten sposób zaczęła swoja karierę z architekturą x86 firma AMD (założona również przez byłego pracownika Fairchild Semiconductors w 1969 roku) która uzyskała licencję na procesory 8086, 8088 i najważniejszy 80286. 80286 jest najważniejszy gdyż to właśnie z tym procesorem są kompatybilne wstecznie produkty Intela (a przynajmniej od tej architektury zwykło się datować kompatybilność wsteczną x86).

Bazą rozwoju komputera osobistego, takiego z jakiego korzystamy dzisiaj, stał się więc ekosystem stworzony przez IBM polegający na ścisłej integracji oprogramowania (DOS/Windows) z architekturą x86 i procesorami produkowanymi przez AMD i Intela. Obie firmy AMD i Intel posiadały w tamtym czasie zdolności produkcji krzemu i wdrażały pionowy model integracji. Można w dużym uproszczeniu (metaforycznie) powiedzieć że mieliśmy do czynienia z hutami które produkowały samochody. Bądź firmami samochodowymi które odlewały własne części.

Kluczem do sukcesu Intela w produkcji procesorów była ścisła integracja pomiędzy procesem produkcji krzemu i projektowaniem urządzenia. Firma nazwała tą zależność modelem “Tick–tock”. Każdy "tick" oznaczał poprawę technologii produkcji krzemu ( czyli “kurczenie” procesu np z 32nm do 22nm, czasami wprowadzono też nowe instrukcje), a każdy "tock" który oznaczał nową mikroarchitekturę procesora. Odstęp pomiędzy tymi dwoma etapami cyklu (i nowymi produktami) wynosił mniej więcej 18 miesięcy.

Konkurencja pomiędzy Intelem i AMD trwa do dzisiaj i obie firmy przez długi czas inwestowały w architekturę i technologię do wytwarzania układów scalonych. Jednak AMD w 2008 odeszło od integracji pionowej na rzecz poziomej i podzieliło się na dwa przedsiębiorstwa (GlobalFoundries produkcja krzemu i AMD projektowanie procesorów i innych komponentów elektronicznych).

Intel zaś po dziś dzień posiada 15 fabów (fabryk produkujących układy scalone) z których tylko cztery położone są poza USA (dwa w Izraelu, jeden w Irlandii i jeden w Chinach). Intel z przyn historycznych posiada też ogromną ilość bibliotek i komponentów (własności intelektualnej) - własna ISA, elementy procesora etc.

Można zatem powiedzieć że to największy fab (a także jeden z ostatnich) wytwarzający własny produkt praktycznie od samego początku do końca bez udziału firm trzecich. Modelowy przykład integracji pionowej.

Złośliwi twierdzą nawet, że Intel od zawsze był lepszy w tym produkcji układów scalonych (założył go w końcu fizyk i chemik) niż architektury procesorów i jego architektury nigdy nie były zbyt nowatorskie. Nikt o tym jednak nie wiedział bo gdy tylko pojawiała się konkurencja to Intel przechodził na nowy cykl produkcji krzemu (litograficzny np. z 32nm na 22nm) automatycznie poprawiając osiągi. Nawet jeśli to teoria nieprawdziwa, to wydaje się być bardzo ciekawą patrząc na próbę (dodajmy że nieudaną) “przeskoczenia” na 10nm w momencie gdy pojawiły się problemy z AMD.

**Integracja Pozioma (horyzontalna)**

Integracja pionowa to nie jedyny sposób organizacji produkcji elektroniki. Możemy się również spotkać z sytuacją w której kto inny dostarcza biblioteki i komponenty (czyli własność intelektualną) kto inny projektuje produkt końcowy a kto inny wykonuje układ scalony w krzemie. Taki sposób organizacji produkcji nazywamy integracją poziomą. Umożliwia pojawienie się wąsko wyspecjalizowanych jednostek i ma na celu sprzedanie danego produktu na jak największej ilości rynków. Jeśli fab Intela produkuje układy scalone tylko dla Intela (bądź poprzez Intela) to niezależny fab (TSMC) produkuje dla każdego kto jest zainteresowany np. Apple, AMD, Nvidia etc. W skrócie zatem, uzyskuje się w ten sposób korzyść skali (osiąganą poprzez wyższą sprzedaż tego samego produktu) jaki i korzyść zakresu (osiąganą poprzez specjalizację i poprzez dzielenie wspólnych dla różnych produktów surowców czy komponentów).

Podsumowując Intel musi prowadzić prace w zakresie 1) technologii produkcji układów scalonych i 2) projektowania urządzeń elektronicznych np. procesorów.

Konkurencja robi to inaczej. Nvidia, AMD albo ARM tylko projektują urządzenia elektroniczne a TSMC/GlobalFoundries tylko wytwarza układy scalone.

Jednak nie wolno zapomnieć o tym, że to integracja pionowa a nie pozioma, umożliwia daleko idącą optymalizację produktu. Jeśli wiemy w jaki sposób coś jest wytwarzane albo wykorzystywane możemy dobierać rozwiązania techniczne tak by poprawiały wydajność bądź ograniczyły koszty produkcji. Mamy więc zatem klasyczną zależność “coś za coś”.

**TSMC i rewolucja lat 90tych **

W panteonie sławy elektroniki cyfrowej na pewno będzie miejsce dla ludzi takich jak wspomniani Robert Noyce, Gordon Moore czy Jack Kilby. Jednak jest też jedna osoba o której niewiele się mówi a zasługuje, przynajmniej moim zdaniem, na uwagę. Jest nią Morris Chang, były pracownik Texas Instruments, który na zlecenie rządu tajwańskiego doprowadził do rewolucji procesów produkcyjnych na rynku elektroniki. W rezultacie integracja pionowa została zdetronizowana na rzecz integracji poziomej która dominuje obecnie.

Dlaczego potrzebna była taka rewolucja? Najlepiej chyba opowie o tym sam Chang.

Poniżej fragment wywiadu z nim dla [Muzeum Historii Komputerów][muzeum-historii-komputerów]:

*“Kiedy byłem w TI i General Instrument, widziałem wielu projektantów układów scalonych chcących odejść i założyć własną firmę. Jednak największą przeszkodą, która powstrzymywała ich przed odejściem,było to, że nie byli w stanie zebrać wystarczająco dużo kapitału na rozpoczęcie produkcji. W tamtych czasach uważano, że każda firma potrzebuje zdolności do fizycznej produkcji układów scalonych, możliwości produkcji chipów na waflach krzemowych, a to była najbardziej kapitałochłonna część firmy produkującej półprzewodniki i układy scalone. A ja widziałem tych wszystkich ludzi, którzy chcieli odejść ale zatrzymał ich brak możliwości zebrania kapitału na budowę fabryki układów scalonych (fabów). Pomyślałem więc, że może TSMC, fab niezależnie działający, mógłby temu zaradzić. I dzięki temu ci projektanci założą własne firmy i staną się naszymi klientami tworząc dla nas stabilny i rosnący rynek.”*

Chang zauważył że pionowa integracja doprowadziła do monopoli kapitałowych na rynku elektroniki i zaproponował model poziomy. TSMC otworzyło rynek na niezależne firmy które specjalizowały się tylko w projektowaniu układów scalonych pozwalając na łatwą sprzedaż, zakup i montażu komponentów i podsystemów. Jak widać coś co teraz wydaje się być rzeczywistością wtedy nią nie było.

W latach 80tych mali projektanci i podwykonawcy byli zdani na łaskę i niełaskę dużych firm typu Intel zwanych wtedy (i teraz) Integrated Device Manufacturers. Od IDMów dostawali zazwyczaj te moce przerobowe których akurat IDM w danej chwili nie potrzebował. IDMy korzystały również z przewagi kapitałowej by opóźniać/ograniczać lub nawet blokować produkcję innych odbiorców według własnego uznania, a nawet kopiując pomysły i rozwiązania mniejszych podwykonawców.

Na tym tle TSMC zaoferowało ciekawą alternatywę. Firma była skoncentrowana wyłącznie na produkcji krzemu i nie posiadała własnego działu projektowego urządzeń elektronicznych. Głównym problemem były jej możliwości produkcyjne i przestarzałą technologia produkcji krzemu (wysokie procesy litograficzne). W porównaniu do takich gigantów jak Intel, moce przerobowe i jakość TSMC na starcie pozostawiały dużo do życzenia. Jednak ten nowy model biznesowy się przyjął tworząc cały szereg firm typu fabeless. Zaczynając od prostych układów scalonych inwestowano w badania i rozwój, powiększając zasięg i zakres rynku. Po 10 latach TSMC nie odstawało już tak bardzo od czołówki a po 20 latach się z nią zrównało choć Intel był wciąż na prowadzeniu. Teraz po trzydziestu latach pojawiają się już pytania o to kto tak naprawdę jest na prowadzeniu Intel czy TSMC.

Jest to też odpowiedź na pytanie ile czasu i jakich warunków potrzeba by np. w Polsce powstała taka gałąź przemysłu ciężkiego. Odpowiedź to: mniej więcej 30-40 lat, przy czym pierwsze 20 lat firma potrzebuje stabilnej sytuacji politycznej i “opieki” ze strony rządowej nie defraudując przy tym pieniędzy a inwestując zyski w badania i rozwój. Tak przynajmniej wynika z tajwańskich doświadczeń które co najważniejsze pokazują że się tak da!

Tak jak IBM dał impuls do rozwoju AMD, Intela czy Microsoftu tak TSMC pozwoliło na rozwój Nvidii i 3dfx na początku lat 90tych (prawie wszystkie karty graficzne były wtedy produkowane przez TSMC) jak i brytyjskiego ARMa, Mediatek i wielu innych.

**Konsekwencje dla rynku i nas wszystkich**

Pojawienie się TSMC doprowadziło do rewolucyjnych zmian na rynku elektroniki i w rezultacie do zagrożenia pozycji rynkowej Intela.

Jak już wspomniałem TSMC utorowało drogę dla firm które koncentrują się tylko na projektowaniu układów elektronicznych (fabeless) np. Nvidia i ARM. Niektórzy nawet spekulują, że gdyby TSMC powstało wcześniej to i wcześniej mielibyśmy akceleratory graficzne, gdyż rozwój elektroniki nie był w interesie IDMów (działających w myśl zasady skoro jest popyt i nie ma konkurencji to po co badania i rozwój?). Wpływy z tych projektów umożliwiły dalszy rozwój TSMC a także wzbudziły zainteresowania tym segmentem rynku (czyli segmentem niezależnych fabów) innych inwestorów. W 2008 AMD zdecydowało się na podział na dwie firmy. Część zajmująca się produkcją krzemu przeszła na własny rozrachunek i występuje pod nazwą GlobalFoundries i działa na tym samym modelu biznesowym co TSMC. Część o nazwie AMD jest fabeless i zajmuje się min. projektowaniem procesorów opartych o architekturę x86. Innym przykładem jest Samsung. W rezultacie nastąpił gwałtowny rozwój elektroniki gdyż okazało się że można produkować wyspecjalizowane chipy do konkretnych zadań np. karty graficzne etc. i nie trzeba do wszystkiego stosować “uniwersalnych” procesorów. Pochodną tego trendu jest internet rzeczy (ang. internet-of-things).

A co się działo z Intelem? Intel cieszył się od 2008 (czyli od wprowadzenia procesorów z serii i-Core) niekwestionowaną pozycją lidera na rynku procesorów wysoko wydajnościowych uzyskaną dzięki integracji designu z możliwością produkcji krzemu. W związku z tym nie robił nic. I szybko pojawiły się problemy. Pierwszą porażką był rynek mobilny. Zamiast produkować chipy oparte na architekturze ARM bądź zaprojektować od podstaw nową architekturę pod procesor mobilny, Intel postanowił usprawnić własne procesory na bazie architektury x86. Jednak okazało się że różnice w wymaganiach i założeniach projektowych były zbyt duże. W czasie gdy x86 było “dostosowywane” do wymogów rynku ARM wyszedł na prowadzenie i zdobył pozycję niekwestionowanego lidera. Potem było już za późno.

Kolejną porażką Intela były karty graficzne. Tutaj postanowiono pójść tą samą drogą co zawsze. Zamiast tworzyć nowy, dedykowany produkt od podstaw (jak powinno się już stać w przypadku procesora do urządzeń mobilnych), zdecydowano że stworzy się procesor graficzny na bazie x86. W końcu optymalizacja wynikająca z integracji designu z produkcja chipa (model tick-tock) daje tak wiele korzyści że nawet jeśli nie będzie to procesor w pełni dedykowany to i tak wygra z dedykowanymi robionymi na przestarzałych procesach litograficznych TSMC, prawda?

Architekturę Larrabee można by uznać za hybrydę pomiędzy wielordzeniowym CPU i GPU. Spójna hierarchia pamięci podręcznej i kompatybilność z architekturą x86 przypominają jednostkę centralną, podczas gdy jednostki wektorowe SIMD i akceleracja do próbkowania tekstur są podobne do procesorów graficznych. Uważano zatem że posiadając niższe (lepsze) procesy produkcji krzemu taka jednostka hybrydowa będzie i tak wygrywa z dedykowanymi jednostkami Nvidi. Jednak życie szybko zweryfikowało te założenia. Chip miał zostać wprowadzony na rynek w 2010 r. jako rdzeń dla kart graficznych 3D, ale plany te zostały anulowane ze względu na opóźnienia i rozczarowujące dane dotyczące wydajności.

W związku z tym Intel postanowił się wycofać do swojego “bastionu” czyli segmentów procesorów wysoko wydajnościowych (dla serwerów i komputerów mainframe) a także procesorów do komputerów osobistych. Ten pierwszy (serwery i mainframe) jeszcze się trzyma - być może jednak już niedługo będzie inaczej po fuzji ARMa z Nvidia (o tym w następnym artykule). Ten drugi ma się już dużo gorzej.

W międzyczasie pojawiło się bowiem AMD z Ryzenami wykonywanymi przez TSMC i GlobalFoundries które w międzyczasie nadgniły zaległości związane z technologią produkcji krzemu. Gdy w 2017 AMD wprowadziło na rynek nowoczesne (pod względem architektury) procesory, Intel mógł tylko odpowiedzieć poprawioną wersją architektury Skylake(która miała już trzy lata). Dlaczego? Ponieważ to był rok na “tick” a nie “tock”. Jak zwykle radą na kłopoty miał być skok na niższy proces litograficzny i właśnie ten etap cyklu był przewidziany na rok 2017. To czego nie przewidzieli planiści i zarząd Intela był koniec prawa Moore'a.

["To koniec. W tym roku stało się to naprawdę jasne," napisał Charles Leiserson]["to-koniec.-w-tym-roku-stało-się-to-naprawdę-jasne,"-napisał-charles-leiserson] pracujący na MIT pionier obliczeń równoległych. Najnowocześniejszy zakład produkcyjny firmy Intel, który miał produkować chipy w procesie 10 nanometrów już od 2017, zaczął dostarczać takie układy dopiero w 2019 roku, pięć lat po poprzedniej generacji chipów o 14 nanometrach i z dwuletnim opóźnieniem w stosunku do modelu “tick-tock”. Na początku 2019 roku, dyrektor generalny Nvidii, publicznie zgodził się z tą tezą. Pojawiają się pytania czy np. proces 5nm będzie w ogóle możliwy/ opłacalny dla Intela? W dniu 27 sierpnia 2018 r. GlobalFoundries ogłosiło na przykład że anulowało proces 7LP. Jako przyczynę podano zmiany strategii polegającej na skoncentrowaniu się na wyspecjalizowanych procesach zamiast na osiąganiu najlepszych wyników w procesie produkcji krzemu. Warto tutaj zauważyć że TSMC i Intel operują innymi technologiami więc proste porównanie procesu 5nm TSMC z 5nm Intela nie jest możliwe. TSMC drukuje bowiem bez przeplotu co daje w rezultacie mniejszą gęstość tranzystorów. W dużym uproszczeniu 7nm Intela to 5nm TSMC.

Wracając do Intela, gdy okazało się że proces litograficzny 10nm będzie opóźniony, nie było żadnej alternatywy, żadnej architektury która mogłaby zastąpić tą istniejącą. I tak zaczęły się kłopoty tej firmy. Przyszłość pokaże czy firma przezwycięży je jak Microsoft swoje.

**Uwagi do tekstu**

Podczas pisania tekstu pewną trudność sprawia fakt, że są problemy ze znalezieniem polskiej terminologii fachowej w zakresie technologii/inżynierii produkcji krzemu.

Łatwo sprawdzić szukając nawet na wikipedii, że terminy takie jak

- [fabless company][fabless-company]

- [Integrated Device Manufacturer][integrated-device-manufacturer]

- czy [fab albo foundry][fab-albo-foundry]

które wydają się być pojęciami zupełnie podstawowymi, niezbędnymi do zrozumienia procesu wytwarzania układów scalonych nie mają polskich haseł. Dlatego w tekście posługiwałem się albo terminami które udało się mi znaleźć w dostępnych źródłach albo własnymi tłumaczeniami.

Oczywiście będę wdzięczny za wszystkie uwagi. Jeśli jakiś termin jest użyty nie poprawnie, proszę o komentarz najlepiej ze źródłem bym mógł poprawić tekst.

[monolitycznego-układu-scalonego]: https://pl.wikipedia.org/wiki/Uk%C5%82ad_scalony
[muzeum-historii-komputerów]: https://www.semi.org/en/Oral-History-Interview-Morris-Chang
["to-koniec.-w-tym-roku-stało-się-to-naprawdę-jasne,"-napisał-charles-leiserson]: https://www.technologyreview.com/2020/02/24/905789/were-not-prepared-for-the-end-of-moores-law/
[fabless-company]: https://de.wikipedia.org/wiki/Fabless
[integrated-device-manufacturer]: https://en.wikipedia.org/wiki/Integrated_device_manufacturer
[fab-albo-foundry]: https://de.wikipedia.org/wiki/Foundry

