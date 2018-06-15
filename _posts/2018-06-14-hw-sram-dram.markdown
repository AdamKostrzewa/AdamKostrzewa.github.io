---
layout: post
title:  "Ile kosztuje produkcja układu scalonego? Czynniki techniczne."
date:   2018-06-14 09:38:12 +0200
image: /download/dram_dies.jpg
categories: jekyll update
---

Często proste pytania nie są tak proste i oczywiste jak nam się wydaje.
Na przykład takim pytaniem jest "Powiedz ile tak naprawdę kosztuje wykonanie układu scalonego w krzemie?" Teoretycznie sprawa prosta ale w praktyce nie do końca.
Przyczyny są dwie - techniczna i ekonomiczna.  Oczywiście na cenę produkcji układu wpływają takie czynniki jak materiały (krzem, odczynniki), technologia (wielkość układu, ilość elementów, rodzaje elementów etc.) i produkcja (maszyny, ilość błędów tzw. yield).
Są jednak i czynniki ekonomiczne. Dostęp do fabryki (czy firma jest fabless), sytuacja na rynku (np. nadprodukcja) czy nawet polityczne (monopole i cła). Dlatego to proste pytanie można porównać do pytania "Ile kosztuje litr benzyny?" - wszyscy wiemy że jest duża różnica pomiędzy kosztem wydobycia a ceną końcową na stacji która się zmienia z tygodnia na tydzień.

Omówienie tych problemów przedstawie na podstawie ceny produkcji pamięci komputerowej, konkretnie RAMu, i podzieliłem je na dwie części. W pierwszej (poniżej) skrót czynników technicznych. Jest on napisany dla osób mniej zainteresowanych sprzętem i / lub o specjalizacji softwarowej. W drugiej (wkrótce na blogu) dokładniejsze wyjaśnienie czynników ekonomicznych. Jeśli jesteście zainteresowani szczegółami piszcie i komentujcie! Postaram się  uwzględnić wszystkie komentarze i pytania.

**SRAM vs DRAM - powtórka z teorii**

Hierarchia pamięci to pojęcie powszechnie znane - pamięci jest kilka poziomów 
a im szybsza tym jest jej mniej. Dlaczego tak jest? Dlaczego *cache* jest tańszy niż DRAM?
Cache jest wykonany jako SRAM (ang. static random-access memory -  statyczna pamięć o dostępie swobodnym). Jak przedstawiono na obrazku poniżej. 

![DRAM and SRAM cells](/download/test.jpg)

Nawet bez znajomości elektroniki widać że SRAM i DRAM mają różną ilość elementów. Każdy bit cachu jest wykonany zazwyczaj z sześciu tranzystorów (teoretycznie możliwy ale nie często spotykany również wariant z czterema tranzystorami).  W DRAMie (ang. dynamic random-access memory) -  dynamicznej pamięci o dostępie swobodnym - każdy bit jest wykonany z jednego tranzystora i jednego kondensatora. Czyli ta same funkcja logiczna - przechowanie jednego bitu informacji -  jest wykonana fizycznie na dwa całkowicie odmienne sposoby - różne układy. Każde podejście ma swoje wady i zalety.
Zaletą SRAMu jest fakt że dane  mogą być odczytane w każdej chwili - bez konieczności odświeżania ale za to z koniecznością ciągłego zasilania układu. W DRAMie  niezbędne jest okresowe odświeżanie ze względu na rozładowywanie się kondensatorów. To powoduje że częstotliwość odczytu (a więc prędkość) jest ograniczona i niższa niż w przypadku SRAMu. Jednak DRAM jest wykonany z dwóch elementów a SRAM sześciu. To powoduję  że komórka pamięci (element przechowujący jeden bit) jest zdecydowanie mniejsza niż w przypadku SRAMu. 
Tutaj aby być uczciwym należy dodać że DRAM wymaga kontrolera który przeprowadzałby odświeżanie. Proces ten wymaga dodatkowych sygnałów i w związku z tym potrzebna jest odpowiednia ilość komórek pamięci by zamortyzowały koszty produkcji dodatkowego układu. Dlatego małe bufory (np. w sieciach) wykonywane są głównie w SRAMie a pamięci główne w DRAMie


**Ekonomia DRAMu**  
Jak zatem techniczne wykonanie komórki pamięci (czyli jednego bitu) przekłada się na cenę układu krzemowego?
Po pierwsze koszty techniczne można podzielić na jednorazowe (ang. non-recurrent) i powracające (ang. recurrent). Do tych pierwszych należą koszty licencji, czas pracy niezbędny do zaprojektowania układu czy generacja maski.
Koszty powracające to fizyczne wykonanie układu (powracające bo każdy nowy układ będzie miał konkretny koszt). Tutaj jest to przetwarzanie krzemu, testowanie, pakowanie etc.

Zajmijmy się zatem kosztem fizycznego wykonania chipu.
W dużym uproszczeniu produkcję chipów na waflu krzemowym można porównać do druku strony.
Mimo że druk jednej strony (np. kolorowej) może być droższy niż innej to drukarnia zazwyczaj stosuje uśrednioną stawkę. Podobnie jest z krzemem. Koszt wykonania wafla jest *mniej więcej * ten sam bez względu na ilość elementów.
Dlatego jeśli na tej samej powierzchni chipu (krzemu) mieści się więcej komórek w przypadku 
DRAMu niż SRAMu to DRAM jest tańszy tzn. albo obniżamy cenę albo zwiększamy pojemność. 

Po drugie ze względu na sposób produkcji inglot krzemowy (czyli kawałek krzemu na którym będzie trawiony czip) jest okrągły. Układy scalone ze względu na sposób produkcji i użytkowania prostokątne. Czyli sprawa jest prosta - im mniejsza powierzchnia układu tym większa rozdzielczość i mniejsze straty na krawędziach - jak na obrazku poniżej. 

![DRAM and SRAM surface](/download/better_surface.jpg)

Dodatkowo przy produkcji jakość maszyn i technologia wpływa na jakość wykonania. Ze względu na  
strukturę krzemu bądź zanieczyszczenia w powietrzu (słynne cleanroomy) zazwyczaj przy produkcji ilość układów scalonych na waflu ma błędy. Im lepsza fabryka (silicon foundry) i maszyny tym jest ich mniej ale praktycznie zawsze występują. Starty są zatem proporcjonalne do wielkości układu. Jeśli nasze układy są małe to straty też są niskie a im większy układ tym mniejszy uzysk (ang. yield), patrz na rysunek poniżej. Dlatego produkcja 16 bitów DRAMu jest tańsza niż 16 bitów SRAMu. Mniejsze jest lepsze.

![DRAM and SRAM yield](/download/better_yield.jpg)

Zauważmy że zakładając mniej więcej stałą średnicę wafla, ilość układów można skalować również poprzez technologię produkcji np. proces naświetlania. Jeśli układ jest wykonany w technologi 10nm to może pomieścić mniej więcej dwa razy więcej tranzystorów na tej samej powierzchni niż układ wykonany w technologii 22 nm.
Ciekawym przykładem jest firma Intel która tak naprawdę w pierwszej kolejności zajmuje się  produkcją krzemu (procesy, technologia, maszyny) a w drugiej (mówiąc kolokwialnie "na boku") produkcją procesorów (architektura i logika).  To tak jakby huta stali robiła samochody. Strategia Intela do niedawna była prosta -gdy technicznie dogania ją konkurencja (projekt układu) oni wprowadzają nową technologię produkcji krzemu i mogą albo sprzedawać taniej albo proponować bardziej zaawansowane (a często i szybsze) układy. Niestety krzem jako materiał też ma swoje ograniczenia i 10nm nie jest już tak łatwo wprowadzić - [Artykuł o 10nm i Intelu](https://www.tomshardware.com/news/intel-cpu-10nm-earnings-amd,36967.html).

Oczywiście dodatkowo trzeba zapłacić za testy chipów i ich pakowanie. Tutaj koszty są wprost proporcjonalne do ilości układów.

Dla zainteresowanych w tabelkach przykładowe koszty wykonania na podstawie danych firmy Adapteva i uniwersytetu Bar-Ilan z Izraela źródło [Adapteva](http://www.adapteva.com/). Dane z roku 2014. 

Tabela 1: Koszty jednorazowe projektowania układu scalonego.

| Pozycja                           | Koszt         |
| --------------------------------- | ------------- |
| Projektowanie układu              | $300K - $200M |
| Projektowanie sterowników         | $0 - $800M    |
| Licencje za biblioteki IP         | $0 - $10M     |
| Licencje za narzędzia (EDA tools) | $0 - $10M     |
| Projektowanie maski               | $100K - $3M   |
| Projektowanie testów              | $5K - $1M     |
| Suma                              | $1M - $1B     |

Tabela 2: Koszty powracające projektowania układu scalonego.

| Pozycja                             | Koszty       |
| ----------------------------------- | ------------ |
| układ (ang. die)                    | $0.1 - $1000 |
| obudowa (ang. package)              | $0.1 - $30   |
| montaż                              | $0.1 - $50   |
| testowanie                          | $0 - $10     |
| licencje od sztuki (ang. royalties) | $0 - $2      |
| Suma (za sztukę)                    | $0.3 - $1K   |

**Podsumowanie**  

Im większy jest układ scalony tym większe straty w przypadku gdy jest on uszkodzony bądź nie działa poprawnie. Dzięki temu wykonanie DRAMu (ze względu na większą gęstość układów) niesie za sobą niższy koszt ALE NIE CENĘ KOŃCOWĄ układu niż w przypadku SRAMu. Produkcja mniejszego układu scalonego jest proporcjonalnie mniejsza do produkcji dużego układu scalonego - proporcja wynika ze stosunku powierzchni. Dodatkowo im dłużej jest produkowany układ tym więcej usprawnień w cyklu produkcyjnym a więc niższe koszty. Cena powinna zatem spadać wraz z długością cyklu produkcyjnego. Jednak koszty produkcji to nie wszystko. Z punktu widzenia fabryki sprzedaż układu poniżej kosztów to jednoznaczna strata jednak cenę ustala się na podstawie tego co klient jest w stanie zapłacić a nie ile kosztuje produkcja.  Czyli cena DRAMu może być różna w zależności od popytu (ile osób chce go kupić) i podaży (wysokość całej rynkowej produkcji). Tym zajmiemy się w kolejnej części. Zachęcam do komentowania i zadawania pytań! 







