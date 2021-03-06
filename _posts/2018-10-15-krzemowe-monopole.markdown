---
layout: post
title:  "Krzemowe Monopole"
date:   2018-10-15 13:46:12 +0200
image: /download/krzem-580x387.jpg
summary_large_image: /download/krzem-580x387.jpg
categories: jekyll update
---





Zgodnie z teorią produkcji seryjnej wraz z rozwojem technologii produkcji i długości serii cena jednostkowa spada. Czy jest tak zawsze? Dlaczego cena DRAM-u DDR4, zamiast obniżać się, wzrasta?

Co produkcja i sprzedaż układów scalonych mają wspólnego z bezpieczeństwem? Ceny procesorów i kości pamięci wpływają nawet na analizę ryzyka i rekomendacje dotyczące bezpieczeństwa danych rozwiązań. Im tańsza moc obliczeniowa, tym łatwiej atakować algorytmy kryptograficzne. Warto zatem zajrzeć nieco głębiej w problemy sprzętu, z którego korzystamy na co dzień w naszej pracy. Poza tym kto nie chciałby niższych cen RAMu i dysków SSD?

### **Krzemowe monopole**

Cena jednostkowa spada wraz z rozwojem technologii produkcji i długości serii. Po pierwsze produkcja staje się “bezpieczna”. Firmy wiedzą, że jest zbyt i rynek (technologia się “przyjęła”), rozbudowują sieci dystrybucji, pojawiają się usprawnienia maszyn i wdrażane jest doświadczenie produkcyjne. Czy jest tak zawsze?

Cena kości DDR4-2400 na początku tego roku wynosiła 192 USD, gdy za tę samą pamięć przed dwoma laty (2016) płaciliśmy 81 USD. Poniżej wykres z serwisu [PCpartPicker](https://pcpartpicker.com/), który generuje automatycznie ceny dla modułów pamięci na podstawie danych dostępnych w internecie. Jak widać, tendencja jest wzrostowa i odwrotna do oczekiwań (a także teorii).

![img](/download/dram-price.jpg)

Cena za moduł F4-2400C15D-16GVB G.SKILL Ripjaws 2x8GB DDR4 2400MHz 15-15-15-35, źródło: [gamersnexus](https://www.gamersnexus.net/industry/3212-ram-price-investigation-ddr4-same-price-as-initial-launch)

Co stoi za takimi anomaliami? Jakie jest wyjaśnienie takiego dziwnego trendu rynkowego?

Dość proste. Jest tylko kilka firm, które mają zdolność produkcji seryjnej i projektowania układów scalonych. Konsolidacja firm z rynku produkcji krzemu doprowadziła do tego, że na świecie jest tylko sześć dużych firm produkujących pamięci, z czego trzy firmy (Samsung, SK Hynix i Micron Group) miały w 2016 po konsolidacjach 90% procent rynku, patrz tabelka poniżej. W 2018 roku te same trzy firmy posiadają już 96% rynku. Zauważmy, że trzy pozostałe firmy, na podstawie danych z 2016 roku, mają razem 9% rynku, a cała reszta świata pozostały 1%.

![img](/download/DRAM-marketshare.png)



Ranking firm produkujących pamięci DDR źródło DRAMeXchange

Taka sytuacja stwarza niebezpieczeństwo monopolu przez sam podział rynku i daje duże możliwości zmowy cenowej, która nie musi się odbywać w sposób bezpośredni. Firmy w reakcji na wzrost ceny konkurencji mogą zwyczajnie zwiększać swoją cenę, zamiast ją zmniejszać. Podobna sytuacja jest dobrze znana kierowcom. Gdy cena baryłki ropy rośnie, błyskawicznie wszystkie stacje benzynowe podwyższają cenę. Gdy jednak cena baryłki spada, to cena obniżana jest dopiero wtedy, gdy konkurencja ją też obniży i tylko o tyle, o ile obniży konkurencja. W ten sposób sprawdza się próg „wytrzymałości” portfela przeciętnego Kowalskiego. Wiadomo bowiem, że dolny próg ceny wyznaczają koszty produkcji – poniżej jest strata. Górny limit nie istnieje – cena jest tak wysoka, ile w stanie jest zapłacić klient. Jest to całkowicie sprzeczne z prawem zbytu i podaży, ale zdarza się notorycznie. Czasem (a nawet często) jest to działanie celowe, mające cechy zmowy cenowej. Przykłady?

Chiny (i Tajwan) są głównym światowym producentem elektroniki (w odniesieniu do układów scalonych), drugie miejsce zajmuje USA. Od 2005 regularnie rządy Chin i USA występują na drogę sądową przeciwko producentom DRAM-u ze względu na praktyki monopolistyczne, kartelowe i zmowy cenowe. I tak na przykład:

- W 2005 Samsung zapłacił 300 mln dolarów i przyznał się do zmowy cenowej na rynku pamięci. Rozprawa odbyła się w San Francisco w Kalifornii ([źródło](http://www.theregister.co.uk/2005/10/13/samsung_pricing/)).
- W 2014 roku ponownie Samsung – tym razem w towarzystwie innych producentów, takich jak Micron, Hynix, Elpida, Hitachi, Infineon, Mitsubishi, Mosel, Nanya, NEC, Toshiba, Winbond – został skazany za zmowę monopolową. Kara wyniosła 310 mln dolarów, z czego Samsung zapłacił 110 mln ([źródło](https://www.gamersnexus.net/news/1348-dram-price-fixing-98-02)).
- W 2018 chińskie biuro antykorupcyjne spotkało się z przedstawicielami Micron Technology, detale rozmów są utajnione. Spotkanie to odbywa się po podobnym spotkaniu z Samsungiem i zbliżającym się pozwie grupowym, w którym według chińskich urzędników dostawcy pamięci DRAM tworzą kartel w zakresie ustalania cen. Chińskie spotkanie z Samsungiem miało rzekomo być kompromisowym ([źródło](https://press.trendforce.com/press/20180525-3108.html)), jeśli chodzi o zakres cen pamięci DRAM i zwiększanie produkcji. Spotkanie firmy Micron z chińskimi agencjami rządowymi może przynieść podobne rezultaty. Chiny nie zwróciły jeszcze uwagi na SK Hynix, ale biorąc pod uwagę obecną sytuację, możemy oczekiwać, że Chiny wcześniej czy później zainteresują się i tą firmą ([źródło](https://www.gamersnexus.net/news-pc/3311-hw-news-china-vs-memory-makers-b450%20Wiadomo)).

Równolegle w USA, w nowym postępowaniu sądowym zarzuca się Samsungowi, Hynixowi i Micronowi, którzy łącznie kontrolują 96% rynku pamięci DRAM, zmowę kartelową w celu podniesienia cen pamięci DRAM za okres od 1 stycznia 2016 r. do 1 lutego 2018 r. W pozwie sądowym zauważono, że ceny RAM spadały od 2014-2015 r., kiedy to trzy przedsiębiorstwa działały niezależnie w celu zwiększenia pojemności pamięci DRAM. Nie na długo – następnie ceny gwałtownie wzrosły, począwszy od 2016 r., kiedy to wszystkie trzy przedsiębiorstwa zdecydowały się ograniczyć wzrost cen pamięci DRAM, aby powstrzymać obniżanie marży.

![img](https://zaufanatrzeciastrona.pl/wp-content/uploads/2018/07/krzem-580x387.jpg)

Warto zauważyć, że o ile zawyżanie cen kart graficznych przez użycie na rynku kryptowalut dotyka jedynie małego segmentu rynku komputerowego, to monopol na DRAM dotyka każdego z nas! Nie ma telefonu, komputera, a nawet lepszych telewizorów i routerów bez DRAM-u.

Cały pozew jest dostępny pod adresem: <https://www.hbsslaw.com/uploads/case_downloads/dram2/2018-04-27_dram_class_action_complaint.pdf>. Poniżej tłumaczenie (własne) fragmentu:

> Na przykład 30 marca 2016 r. zapytano firmę Micron o to, czy angażuje się w cięcia w dostawach, a dyrektor generalny firmy, Mark Durcan, odpowiedział, że “byłoby nierozsądne, gdyby firma Micron jako pierwsza uruchomiła nowe moce produkcyjne”. Ernie Maddock, dyrektor finansowy firmy Micron, potwierdził ponadto, że firma Micron nie będzie jednostronnie ograniczać produkcji: “To naprawdę nierozsądne posunięcie, aby jednostronnie ograniczać produkcję”.
>
> Jednocześnie firma Micron zapewniła konkurentów, że zaprzestanie prób przejęcia udziału w rynku od Samsunga i Hynix. 28 kwietnia 2016 roku Samsung odpowiedział na zaproszenie Microna do ograniczenia podaży, ogłaszając publicznie, że podaż pamięci DRAM spadła. Po tych komunikatach, do 1 czerwca 2016 roku, ceny pamięci DRAM zmieniły kurs, zaczęły iść ostro w górę i trend ten utrzymał się przez cały okres określony w pozwie (czyli aż do dziś – przypis tłumacza) .
>
> W tym okresie pozwani kontynuowali wysiłki w celu skoordynowania swoich decyzji dotyczących dostaw pamięci DRAM. Znajduje to odzwierciedlenie w publicznych komunikatach pozwanych, nakłaniających się wzajemnie do kontrolowania podaży w branży. Oskarżeni złożyli publiczne oświadczenia potwierdzające ich zaangażowanie na rzecz wspólnego planu ograniczenia dostaw i nie konkurowania o swój udział w rynku poprzez ekspansję dostaw. Na przykład, pozwani poinformowali pozostałych pozwanych w publicznych oświadczeniach, że utrzymają produkcje wafli krzemowych na stałym poziomie, aby ograniczyć wzrost podaży pamięci DRAM, w 2017 r. zwiększą jedynie podaż pamięci DRAM o 15-20 procent, nawet jeśli popyt na nie wzrośnie o 20-25 procent, oraz że powstrzymają się od przejmowania udziału w rynku. Oświadczeniom pozwanych towarzyszyło – potwierdzone w raportach i analizach branżowych – postępowanie, które wzmocniło zaangażowanie każdego z nich na rzecz wspólnego systemu podaży i dystrybucji. W wyniku skoordynowanych działań pozwanych mających na celu ograniczenie podaży i rezygnację ze zwiększenia udziału w rynku, pozwani byli w stanie stale podnosić ceny pamięci DRAM w okresie klasy i osiągać ogromne zyski, jak pokazano na poniższym wykresie.

Jak widać azjatyckie tygrysy zmieniły strategię i nawet się nie ukrywają z tajnymi negocjacjami w hotelach. Potwierdza to [raport Bloomberga](https://www.bloomberg.com/news/articles/2018-09-20/samsung-is-said-to-plan-lower-chip-growth-to-maintain-prices) z 20 września 2018, którego autorzy – powołując się na źródła – piszą otwarcie o zaniżaniu przez Samsunga produkcji DRAM-u w 2018 i podobnych planach na 2019 w celu zwiększenia ceny rynkowej pamięci, mimo grożących mu procesów. Przykłady można by mnożyć. Jak na razie niski poziom kar dla producentów DRAM-u wydaje się być raczej zachętą do dalszego działania. Sytuacja jest jednak niezwykle ciekawa, biorąc pod uwagę np. wpływy Samsunga w Korei Południowej, które mogą zapewniać szeroko rozumianą „bezkarność” i amortyzację kar poprzez państwowe subwencje i dotacje.  Ta „uprzywilejowana” pozycja koncernu w rodzimym kraju [już raz doprowadziła](https://www.bbc.com/news/business-39191196) do masowych demonstracji przeciw korupcji i impeachmentu prezydenta.

### **Inne czynniki ekonomiczne**

Fabryka, tak jak sieć komputerowa czy komunikacyjna, jest zorientowana na średni popyt. Budowanie nowej fabryki lub przejście na nowszy proces litograficzny (np. z 22nm na 10nm) to decyzja ekonomiczno-polityczna obliczona na lata, która ma konkretne konsekwencje nie tylko dla firmy, ale i dla całego rynku. Wprowadzenie nowej technologii produkcji (np. zmiana litografii) może zmniejszyć zdolność do dostarczania istniejących, popularnych modułów DRAM o takiej samej pojemności na koszt nowej produkcji. Firma nie jest w stanie utrzymać produkcji na obydwu liniach na tym samym poziomie ze względu na koszty bądź obawia się, że jeśli będzie produkowała stare moduły DRAM, to ich cena spadnie (bo zwiększy się podaż o nowe moduły) i mniej osób zdecyduje się na zmianę układów. To powoduje, że o ile firma produkująca DRAM otwiera sobie nowy rynek, to jednocześnie oddaje konkurencji stary, tzn. często wycofuje się z produkcji w starej technologii. Wszystko jest dobrze, jeśli nowa technologia jest przełomowa – gorzej, jeśli zyski z niej są niewielkie.

Przykładem takiej sytuacji są niedawne działania Intela. Niedobory produkcyjne zmusiły firmę do kreatywnego podejścia do problemu produkcji i podjęcia nietypowych kroków. Tradycyjnie ([model tick-tock](https://en.wikipedia.org/wiki/Tick%E2%80%93tock_model)) Intel starał się wyprzedzić innych producentów poprzez konsekwentne wprowadzanie nowszych procesów produkcyjnych (m.in. litograficznych). Dlatego oczekiwano, że po procesie litograficznym 14nm nastąpi 10nm. Jednak linie w technologii 10nm nie są gotowe (dochodzi do opóźnień) i 10nm ruszy dopiero w czwartym kwartale przyszłego roku. Jak donosi [TomsHardware](https://www.tomshardware.com/news/intel-14nm-shortage-h310c,37819.html),  firma przeprojektowała swój nowy chipset H310C z 14nm na 22nm. Oznacza to, że gigant produkujący układy scalone cofnął się o krok do starszego procesu produkcji chipsetu H310C, ponieważ boryka się z ciągłym brakiem procesorów w 14nm. Intel zazwyczaj produkuje chipsety w niższej litografii niż procesory z bieżącej generacji. Jednak opóźniona produkcja 10nm doprowadziła do tego, że zarówno chipsety, jak i chipy, produkowane są w 14nm, tworząc wąskie gardło.

Dla producentów układów scalonych ważne są informacje o stałych odbiorcach (długoterminowych trendach rynkowych) i nie poddawanie się chwilowym zmianom, które mogą prowadzić do nadprodukcji albo niedoborów.  Taka sytuacja miała miejsce w przypadku kryptowalut. Wysokie kursy bitcoina doprowadziły do dokapitalizowania “górników”, którzy mogą sobie pozwolić na lepszy sprzęt, np. procesory graficzne w ilościach hurtowych. Jednak nie dają oni producentom pewności, że popyt utrzyma się na stałym poziomie. Gwałtowny spadek ceny kryptowalut może doprowadzić do załamania popytu, a fabryki zostaną ze zwiększoną produkcją. Popyt motywowany przez kryptowaluty doprowadził do tego, że ceny pamięci GDDR5 do procesorów graficznych wzrosły o 20 do 30 USD za średniej jakości kartę z pojemnością 8 GB. Typowe (notowane wcześniej) wahania cen były zbliżone do 5 dolarów. I tutaj wracamy do monopoli. Pamięć DRAM do kart graficznych, jak i wszystkich innych urządzeń, pochodzi od tych samych trzech dostawców: Samsunga, Microna i SK Hynixa. Te same fabryki wytwarzają wszystkie komponenty, rozdzielając czas produkcji pomiędzy większą liczbę urządzeń. Firmy wykorzystały koniunkturę i ograniczyły produkcję w innych segmentach, by zaspokoić potrzeby “górników” – przynajmniej taka jest ich linia obrony. Rząd i oskarżyciele w USA widzą sprawę inaczej i uznają, że Samsung, Micron i SK Hynix wykorzystały ten chwilowy trend do ograniczenia produkcji i zwiększenia marży o 250-350%.

Ceny RAM-u wzrosły też przez duży popyt na dyski SSD. Prawie każdy laptop jest obecnie dostarczany z dyskami SSD, a  SSD o pojemności 128-512 GB są już używane jako podstawowy nośnik danych. Jednak SSD, podobnie jak procesory graficzne, korzystają z tych samych linii produkcyjnych co inne moduły DRAM. patrz na sytuacje powyżej. Firmy Samsung, Micron i SK Hynix, zamiast zwiększać produkcję, zwiększają cenę, tłumacząc że to chwilowy trend i ze względu na dobro akcjonariuszy nie mogą się mu poddawać. Teoretycznie mają do tego prawo, jednak oskarżyciele z Chin i USA są innego zdania co do motywacji wielkich korporacji.

### **Podsumowanie**

Czy postępowanie antymonopolowe przyniosą zamierzony skutek? To pytanie pozostanie jeszcze przez jakiś czas bez odpowiedzi, jednak już teraz można wyciągnąć pewne wnioski. Postępowania prowadzone są w krajach posiadających silny przemysł elektroniczny. Na terenie Unii Europejskiej te problemy przechodzą bez większego medialnego „echa”. Czy wolimy płacić więcej? A może całkowity brak przemysłu półprzewodnikowego nie jest rozwiązaniem? Może nawet mała produkcja, mimo że z minimalnym zyskiem bądź małą stratą, umożliwia szybszą reakcję na trendy rynkowe i łatwiejszą kontrolę importowanych towarów? Jak widać fakt, że ktoś produkuje jakiś towar taniej i lepiej, nie znaczy, że stan ten będzie trwał wiecznie. Często po osiągnięciu przez producenta pozycji monopolistycznej obniża się jakość, a zwiększa cena. W efekcie oddajemy z nawiązką zaoszczędzone wcześniej pieniądze. Ten efekt zna chyba każdy, kto grał w popularną grę planszową „Monopoly”. Ocenę sytuacji pozostawiam Wam wszystkim i zachęcam do dyskusji.

*Artykuł był opublikowany również w serwisie [ZaufanaTrzeciaStrona](https://zaufanatrzeciastrona.pl/post/krzemowe-monopole-czyli-dlaczego-moc-obliczeniowa-nie-tanieje-tak-szybko/).*
