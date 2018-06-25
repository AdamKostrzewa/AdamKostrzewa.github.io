---
layout: post
title:  "[PL] Ile kosztuje produkcja układu scalonego? Czynniki ekonomiczne."
date:   2018-06-25 09:38:12 +0200
image: /download/dram_dies.jpg
categories: jekyll update
---


Artykuł jest kontynuacją pierwszej części opublikowanej na blogu - [Ile kosztuje produkcja układu scalonego? Czynniki techniczne](https://adamkostrzewa.github.io/jekyll/update/2018/06/14/hw-sram-dram.html)

Zgodnie z podstawami produkcji seryjnej wraz z rozwojem technologii produkcji i długości serii cena jednostkowa spada. Czyli cena DRAMu powinna się obniżać. Dlaczego tak jest? Po pierwsze produkcja staje się "bezpieczna". Firmy wiedzą że jest zbyt i rynek (technologia się "przyjeła"), rozbudowują sieci dystrybucji, pojawiają się usprawnienia maszyn i wdrażane jest doświadczenie produkcyjne. Czy jest tak zawsze?


**Krzemowe monopole**

Cena kości DDR4-2400 na początku tego roku wynosiła 192 USD gdy za tą samą pamięć przed dwoma laty (2016) płaciliśmy 81 USD. Poniżej wykres z serwisu [PCpartPicker](https://pcpartpicker.com/) który generuje automatycznie ceny dla modułów pamięci na podstawie danych dostępnych w Internecie. Jak widać tendencja jest wzrostowa i odwrotna do oczekiwań (a także teorii).

![DRAM prices](/download/dram-price.jpg)

Cena za moduł F4-2400C15D-16GVB G.SKILL Ripjaws 2x8GB DDR4 2400MHz 15-15-15-35, źródło [gamersnexus](https://www.gamersnexus.net/industry/3212-ram-price-investigation-ddr4-same-price-as-initial-launch).

Co stoi za takimi anomaliami? Jakie jest wyjaśnienie takiego dziwnego trendu rynkowego?

Dość proste. Jest tylko kilka firm (a nawet krajów na świecie) które mają zdolność produkcji i projektowania układów scalonych. Konsolidacja firm z rynku produkcji krzemu doprowadziła do tego że na świecie jest tylko sześć dużych firm produkujących pamięci z czego trzy firmy (Samsung, SK Hynix i Micron Group) miały w 2016 po konsolidacjach 90% procent rynku, patrz tabelka poniżej. W 2018 roku te sam trzy firmy posiadają już 96% rynku. Zauważmy że trzy pozostałe firmy, na podstawie danych z 2016 roku, mają razem 9% a cała reszta świata jakieś 1%. Reszta świata w tym ujęciu to głównie produkcja wojskowa.

![DRAM marketshare](/download/DRAM-marketshare.png)

Taka sytuacja stwarza niebezpieczeństwo monopolu już tylko przez sam podział rynku i daje duże możliwości zmowy cenowej - która nie musi nawet odbywać się w sposób bezpośredni. Na przykład firmy w reakcji na wzrost ceny konkurencji zwiększają swoją cenę zamiast ją zmniejszać. Jest w tym logika jeśli nie chce / nie mogę zwiększyć mocy przerobowych bądź zrozumiałem intencje konkurencji. Podobna sytuacja jest dobrze znana kierowcom. Gdy cena baryłki ropy rośnie błyskawicznie wszystkie stacje benzynowe podwyższają cenę. Gdy jednak cena baryłki spada, to cena obniżana jest dopiero wtedy  gdy konkurencja ją też obniży i tylko o tyle o ile obniży konkurencja. 
W ten sposób sprawdza się próg „wytrzymałości” portfela przeciętnego „Kowalskiego|”. Wiadomo bowiem dolny próg ceny wyznaczają koszty produkcji – poniżej jest strata. Górny limit nie istnieje – cena jest tak wysoka ile wstanie jest zapłacić klient. Jest to całkowicie sprzeczne z prawem zbytu i podaży ale zdarza się notorycznie. Przykłady?

Chiny są głównym światowym producentem elektroniki (ponad 50% produkcji) drugie miejsce to USA. Od 2005 regularnie rządy Chin i USA występują na drogę sądową przeciwko producentom DRAMu ze względu na praktyki monopolistyczne, kartelowe i zmowy cenowe. I tak na przykład:


* W 2005 Samsung zapłacił 300 mln. dolarów i przyznał się do zmowy 	cenowej na rynku pamięci. Rozprawa odbyła się w San Francisco w 	Kalifornii <http://www.theregister.co.uk/2005/10/13/samsung_pricing/>
 
* Ta sprawa ewidentnie nie dała Samsungowi do myślenia i w 2014 roku 	ponownie Samsung tym razem w towarzystwie innych graczy Microna, 	Hynixa, i kilku innych Elpida, Hitachi, Infineon, Mitsubishi, Mosel, 	Nanya, NEC, Toshiba, Winbond kara to 310 mln-ów (z czego Samsung 	zapłacił 110 mln) dolarów 	<https://www.gamersnexus.net/news/1348-dram-price-fixing-98-02>

* W 2018 chińskie biuro antykorupcyjne spotkało się z 	przedstawicielami Micron Technolog, detale rozmów są utajnione. 	Spotkanie to odbywa się po podobnym spotkaniu z Samsungiem i 	zbliżającym się pozwie grupowym, w którym twierdzi się, że 	dostawcy pamięci DRAM tworzą kartel w zakresie ustalania cen. 	Chińskie spotkanie z Samsungiem miło rzekomo być kompromisowym 	(https://press.trendforce.com/press/20180525-3108.html) jeśli 	chodzi o zakres cen pamięci DRAM i zwiększonie produkcji. 	Spotkanie firmy Micron z chińskimi agencjami rządowymi może 	przynieść podobne rezultaty. Chiny nie zwróciły jeszcze uwagi na 	SK Hynix, ale biorąc pod uwagę obecny klimat, możemy oczekiwać, 	że Chiny wcześniej czy później do nich dotrą. Źródło 	<https://www.gamersnexus.net/news-pc/3311-hw-news-china-vs-memory-makers-b450>

Wiadomo jednak co w tym samym czasie dzieje się w USA. W nowym postępowaniu sądowym zarzuca się Samsungowi, Hynixowi i Micronowi, którzy łącznie kontrolują 96 % rynku pamięci DRAM, zmowę kartelową w celu podniesienia cen pamięci DRAM za okres od 1 stycznia 2016 r. do 1 lutego 2018 r. W pozwie sądowym zauważono, że ceny RAM spadały od 2014-2015 r., kiedy to trzy przedsiębiorstwa działały niezależnie w celu zwiększenia pojemności pamięci DRAM. Nie na długo - następnie gwałtownie wzrosły, począwszy od 2016 r., kiedy to wszystkie trzy przedsiębiorstwa zdecydowały się ograniczyć wzrost cen pamięci DRAM, aby powstrzymać obniżanie marży.

Warto zauważyć że o ile zawyżanie cen kart graficznych przez użycie na rynku kryptowalut dotykało jedynie małego segmentu rynku komputerowego to monopol na DRAM dotyka każdego z nas! Nie ma telefonu, komputera a nawet lepszych telewizorów i routerów bez DRAMu.

Cały pozew jest dostępny pod adresem: <https://www.hbsslaw.com/uploads/case_downloads/dram2/2018-04-27_dram_class_action_complaint.pdf>

poniżej tłumaczenie fragmentu mojego autorstwa:

>  Na przykład 30 marca 2016 r. zapytano firmę Micron o to, czy angażuje się w cięcia w dostawach, a dyrektor generalny firmy, Mark Durcan, odpowiedział, że "byłoby nierozsądne, gdyby firma Micron jako pierwsza uruchomiła nowe moce produkcyjne". Ernie Maddock, dyrektor finansowy firmy Micron, potwierdził ponadto, że firma Micron nie będzie jednostronnie ograniczać produkcji: "To naprawdę nierozsądne posunięcie, aby jednostronnie ograniczać produkcję".

>  Jednocześnie firma Micron zapewniła konkurentów, że zaprzestanie prób przejęcia udziału w rynku od Samsunga i Hynix. 28 kwietnia 2016 roku Samsung odpowiedział na zaproszenie Microna do ograniczenia podaży, ogłaszając publicznie, że wzrost podaży pamięci DRAM okazał się ujemny. Po tych komunikatach, do 1 czerwca 2016 roku, ceny pamięci DRAM zmieniły kurs, zaczęły iść ostro w górę i trend ten utrzymał się przez cały okres określony w pozwie (czyli aż do dziś - przypis tłumacza) .

>  W tym okresie pozwani kontynuowali wysiłki w celu skoordynowania swoich decyzji dotyczących dostaw pamięci DRAM. Znajduje to odzwierciedlenie w publicznych komunikatach pozwanych, nakłaniających się wzajemnie do kontrolowania podaży w branży. Oskarżeni złożyli publiczne oświadczenia potwierdzające ich zaangażowanie na rzecz wspólnego planu ograniczenia dostaw i nie konkurowania o swój udział w rynku poprzez ekspansję dostaw. Na przykład, pozwani poinformowali pozostałych pozwanych w publicznych oświadczeniach, że utrzymają produkcje wafli krzemowych na stałym poziomie, aby ograniczyć wzrost podaży pamięci DRAM, w 2017 r. zwiększą jedynie podaż pamięci DRAM o 15-20 procent, nawet jeśli popyt na nie wzrośnie o 20-25 procent, oraz że powstrzymają się od przejmowania udziału w rynku. Oświadczeniom pozwanych towarzyszyło - potwierdzone w raportach i analizach branżowych - postępowanie, które wzmocniło zaangażowanie każdego z nich na rzecz wspólnego systemu podaży i dystrybucji. W wyniku skoordynowanych działań pozwanych mających na celu ograniczenie podaży i rezygnację ze zwiększenia udziału w rynku, pozwani byli w stanie stale podnosić ceny pamięci DRAM w okresie klasy i osiągać ogromne zyski, jak pokazano na poniższym wykresie.

Jak widać azjatyckie tygrysy zmieniły strategię i nawet się nie ukrywają z tajnymi negocjacjami w hotelach.

Po prostu wydają oficjalnie komunikaty i oświadczenia w myśl staropolskie zasady "Siara - i wszystko jasne!". A moduły pamięci DRAM to nie są to przypadki odosobnione.

W 2012 po 5 letnim dochodzeniu FBI udowodniło zmowę cenową a rynku ekranów LCD i udział w kartelu który powstał po fuzji AU Optronics Corporation (podmiotu należącego do BENQ) z Acer Display Technology i Unipac Optoelectronics. Rezultat to 500 mln dolarów grzywny dla podstatwowych oskarżonych a w całym procesie zasądzono 1,39 MILIARDA dolarów grzywny dla różnych firm i podmiotów. Spotkania kartelu odbywały się według dowodów FBI w hotelach na Tajwanie gdzie ustalono w sposób bezpośredni podział rynku światowego i ceny paneli LCD. Raport FBI dla zainteresowanych tematem jest dostępny pod adresem: <https://archives.fbi.gov/archives/sanfrancisco/press-releases/2012/taiwan-based-au-optronics-corporation-sentenced-to-pay-500-million-criminal-fine-for-role-in-lcd-price-fixing-conspiracy>

Przykłady można by mnożyć. Jak na razie niski poziom kar dla producentów DRAMu wydaje się być raczej zachętą do dalszego działania. Może posiadając tak długą i ciekawą historię kar sądowych Samsung zdecydował, że chce dobra dla ludzi na całym świecie i teraz nie będzie już łamał prawa. Sytuacja jest jednak niezwykle ciekawa biorąc pod uwagę korumpowanie przez Samsunga prezydenta Korei Południowej które doprowadziło do masowych demonstracji i impeachmentu. Wyczerpujący artykuł BBC na ten temat jest dostępny pod adresem: <https://www.bbc.com/news/business-39191196>.

**Inne czynniki ekonomiczne i linie obrony koncernów.**

Fabryka tak jak sieć komputerowa czy komunikacyjna jest zorientowana na średni popyt. Budowanie nowej fabryki lub przejścia na mniejszy proces produkcji krzemu (np. z 22nm na 10nm) to decyzja ekonomiczno-polityczna obliczona na lata która ma konkretne konsekwencje nie tylko dla firmy ale i dla całego rynku. Wprowadzenie nowej technologii produkcji (np. zmiana litografii) mogą zmniejszyć zdolność do dostarczania istniejących, popularnych modułów DRAM o takiej samej pojemności na koszt nowej produkcji. Firma nie jest w stanie utrzymać produkcji na obydwu liniach na tym samym poziomie ze względu na koszty bądź obawia się że jeśli będzie produkowała stare moduły DRAM to ich cena spadnie (bo zwiększy się podaż o nowe moduły) i mniej osób zdecyduje się na zmianę układów. To powoduje że o ile firma produkująca DRAM otwiera sobie nowy rynek to jednocześnie oddaje konkurencji stary tzn. często wycofuje się z produkcji w starej technologii. Wszystko jest dobrze jeśli nowa technologia jest przełomowa - gorzej jeśli zyski z niej są niewielkie bo np. producent systemu operacyjnego zwleka z wypuszczeniem sterowników.

Dlatego dla producentów układów scalonych ważne są informacje o stałych odbiorcach (długoterminowych trendach rynkowych) a poddawanie się chwilowym zmianom które mogą prowadzić do nadprodukcji albo niedoborów. Przykładem tego rodzaju sytuacji są kryptowaluty. Wysokie kursy np. Bitcoina, doprowadziły do dokapitalizowania "górników" którzy mogą sobie pozwolić na lepszy sprzęt np. procesory graficzne w ilościach hurtowych. Jednak nie dają oni producentom pewności, że popyt utrzyma się na stałym poziomie. Gwałtowny spadek ceny kryptowalut może doprowadzić do załamania popytu a fabryki zostają ze zwiększoną produkcją.

Dlatego też ceny pamięci GDDR5 do procesorów graficznych, wzrosła o 20 do 30 USD za średni jakości kartę z pojemnością 8 GB. Typowe (notowane wcześniej) wahania cen były zbliżone do 5 dolarów. I tutaj wracamy do monopoli. Pamięć DRAM do kart graficznych jak i wszystkich innych urządzeń pochodzi od tych samych trzech dostawców: Samsung, Micron i SK Hynix. Te same fabryki wytwarzają wszystkie komponenty, rozdzielając czas produkcji pomiędzy większą liczbę urządzeń. Firmy wyczuły koniunkturę i ograniczyły produkcję w innych segmentach by zaspokoić potrzeby "górników" - przynajmniej taka jest ich linia obrony. Rząd i oskarżyciele w USA widzą sprawę inaczej i uznają że Samsung, Micron i SK Hynix wykorzystały ten chwilowy trend do ograniczenia produkcji i zwiększenia marży o 250% o 350%.

Ceny RAMu wzrosły przez duży popyt na dyski SSD. Prawie każdy laptop jest obecnie dostarczany z dyskami SSD do podstawowego przechowywania danych. Na przykład firmy Apple lub Lenvo całkowicie lub prawie całkowicie przestawiły się na dyski SSD, a inne popularne notebooki w przystępnych cenach używają obecnie dysków SSD o pojemności 128-512 GB jako podstawowego nośnika danych. Jednak SSD podobnie jak procesory graficzne, korzystają z tych samych linii produkcyjnych co inne moduły DRAM. Patrz na sytuacje powyżej. Firmy Samsung, Micron i SK Hynix zamiast zwiększać produkcję zwiększają cenę tłumacząc że to chwilowy trend i one inaczej nie mogą.

*Klęski żywiołowe* Ten problem ostatnio nie występował, ale we wrześniu 2013 r. pożar w fabryce SK Hynix spowodował natychmiastowy skok cen pamięci DRAM i spadek cen akcji. Zmiany te były wówczas ogromne i zostały dobrze podsumowane w raporcie firmy ExtremeTech <https://www.extremetech.com/computing/166775-ram-pricewatch-memory-spikes-in-wake-of-hynix-fire-but-for-how-long>. Na szczęście niedobory udało się skorygować w ciągu kilku miesięcy. Innym przykładem jest powódź w Tajlandii i wahania cen napędów HDD <https://www.gamersnexus.net/news-pc/669-hdd-prices-remain-high-through-spring-wd>.

*Zmiany na rynku softwaru*. Nie tylko hardware może wymusić zmianę cen - giganci softwarowi też to potrafią. Do niedawna wypuszczenie każdej nowej wersji Windowsa wiązało się z wyższymi wymogami sprzętowymi np. oficjalne minimum dla Windows 10 to tylko 2 GB pamięci RAM, ale minimalne specyfikacje dla nowego oprogramowania i gier oczywiście rosną w miarę upływu czasu. To powoduje że wiele firm, instytucji a także zwykłych użytkowników kupuje jednocześnie (by nie powiedzieć "na hejnał") sprzęt tak by pasował do nowych specyfikacji. Efektem tego są tak zwane "fale popytowe".

Podobne fale pojawiają się przy zmianach standardów produkcji sprzętu np. płyt głównych. Pamięci DDR3 nie są kompatybilne z nowoczesnymi płytami głównymi lub procesorami, co powoduje zapotrzebowanie na nowe pamięci DDR4 - niezależnie od tego, czy klient tego chce, czy nie.

*Urządzenia przenośne* Mimo że smartfony nie posiadają dużo pamięci (np. 512 MB do 2 GB) to zwiększają popyt ze względu na długie (by nie powiedzieć astronomiczne) serie produkcyjne. W sierpniu 2013 roku Samsung Galaxy S4 wprowadził na rynek 2 GB pamięci RAM, a w ciągu sześciu miesięcy sprzedał 40 mln sztuk. Urządzenia iPhone 6 i 6+ zostały wprowadzone na rynek rok później i sprzedały łącznie ponad 220 mln sztuk. W pierwszym kwartale 2017 r. sprzedano 380 mln smartfonów. Dla porównania sprzedaż komputerów w pierwszym kwartale 2017 wyniosła 62,2 mln.

**Podsumowanie**

Czy postępowanie antymonopolowe przyniosą zamierzony skutek? Te pytanie pozostanie jeszcze przez jakiś czas bez odpowiedzi jednak już teraz można wyciągnąć pewne wnioski. Postępowania prowadzone są w krajach posiadających silny przemysł elektroniczny. Na terenie Unii Europejskiej te problemy przechodzą bez większego medialnego „echa”. Czy wolimy płacić więcej? A może całkowity brak przemysłu półprzewodnikowego nie jest rozwiązaniem? Może nawet mała produkcja, mimo że z minimalnym zyskiem bądź małej stracie, umożliwia szybsza reakcję i łatwiejszą kontrolę? Jak widać fakt że ktoś produkuje jakiś towar taniej i lepiej nie znaczy że stan ten będzie trwał wiecznie. Często po osiągnięciu przez producenta pozycji monopolistycznej obniża się jakość a zwiększa cena. W efekcie oddajemy z nawiązką zaoszczędzone wcześniej pieniądze. Ten efekt  zna chyba każdy kto grał w popularną grę planszową „Monopoly”. Ocenę sytuacji pozostawiam wam wszystkim.

