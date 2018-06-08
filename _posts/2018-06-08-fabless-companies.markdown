% !TeX spellcheck = pl_PL
---
layout: post
title:  "[PL] Modele Ataku Trojanów Sprzętowych"
date:   2018-06-08 08:38:12 +0200
categories: jekyll update
---

Do napisania tego tekstu skłoniły mnie komentarze i dyskusje odbyte na Confidence 2018.

Większość z nich dotyczyła dwóch tematów / problemów:

1. jak wyglądałby atak przeprowadzony profesjonalnie?
2. jak bardzo realistyczny jest atak poprzez ingerencje w układ scalony?

Pytania przedyskutuje w tej właśnie kolejności. Modele ataku związane z trojanami w układach scalonych są ściśle związane z łańcuchem dostawców i wykonawców w procesie produkcji krzemu. Obecnie w mikroelektronice stosuje się tzw. foundry model (ang. model odlewni) polegający na oddzieleniu produkcji chipów (krzemu) od projektowania układów scalonych. Prace te wykonywane są przez osobne firmy bądź jednostki biznesowe wewnątrz tej samej organizacji. Model ten bierze nazwę od analogicznego procesu w przemyśle samochodowym (i ciężkim) gdzie projektowanie pojazdu (maszyny) jest wykonywane przez inne firmy i instytucje niż huty stali i odlewnie. Czasami jednak bardzo duży koncern samochodowy może pozwolić sobie na zakup huty. Analogią w świecie elektroniki będzie np. Intel, który zarówno projektuje jak i produkuje układy scalone.

Firmy bez produkcji krzemu (fabless),  dane na rok 2017 na podstawie raport IC Insights, źródło https://www.design-reuse.com/news/43336/2017-top-10-fabless-system-ic-companies.html.

| Miejsce | Firma         | Kraj     |
| ------- | ------------- | -------- |
| 1       | Qualcomm      | USA      |
| 2       | Broadcom Ltd. | Singapur |
| 3       | Nvidia        | USA      |
| 4       | MediaTek      | Tajwan   |
| 5       | Apple         | USA      |
| 6       | AMD           | USA      |
| 7       | HiSilicon     | Chiny    |
| 8       | Xilinx        | USA      |
| 9       | Marvell       | USA      |
| 10      | Unigroup      | Chiny    |

Firmy produkujące krzem (foundries), dane z https://www.electronicsweekly.com/news/business/top-ten-foundries-2017-2017-12/



| Miejsce | Firma           | Kraj             | Udział w rynku |
| ------- | --------------- | ---------------- | -------------- |
| 1       | TSMC            | Tajwan           | 55,9 %         |
| 2       | Globalfoundires | USA              | 9,4 %          |
| 3       | UMC             | Tajwan           | 8,5 %          |
| 4       | Samsung         | Chiny            | 7,7 %          |
| 5       | SMIC            | Tajwan           | 5,4 %          |
| 6       | TowerJazz       | Izrael           | 2,4 %          |
| 7       | Powerchip       | Tajwan           | 1,8 %          |
| 8       | VIS             | Tajwan           | 1,4 %          |
| 9       | Hua Hong Semi   | Chiny            | 1,4 %          |
| 10      | Dongbu Hitek    | Korea Południowa | 1,2 %          |



Model odlewni prowadzi do podziału firm produkujących elektronikę na takie, które mają możliwości produkcji krzemu i takie, które wykonanie krzemu muszą zlecać podwykonawcom. W tabelkach zestawienie największych firm z obu kategorii. O ile te firmy, które nie produkują krzemu są w większości dobrze rozpoznawalne to te które produkują są w wiekszości nieznane. Jest to analogiczne do sytuacji na rynku smochodów gdzie rozpoznajemy marki pojazdów ale nie huty stali badź odlewnie gdzie części zostały fizycznie wykonane.

W mikroelektronice prowadzi to do wyszczególnienia następujących podmiotów w procesie produkcyjnym:

1. dostawca IP (ang. 3PIP 3rd party IP provider) - firma produkująca konkretne elementy układu np. sterowniki pamięci, szyny danych, sieci na chipe, interfejsy etc. Analogią softwarową jest dostawca bibliotek np. silnika graficznego, API, bądź kompresji. 
2. deweloper systemu (ang. SoC designer) - firma integrująca elementy w jeden system, często posiada również własną produkcję komponentów IP. 
3. silicon foundry (ang. odlewnia krzemu) - firma odpowiedzialna za proces produkucji krzemu

Na tej bazie można wyszczególnić siedem modeli ataku przyjmując jako kryterium zaufanie do poszczególnych podmiotów biorących udział w produkcji , patrz Tabela:

| Model | Opis                                                | dostawca IP   | deweloper systemu | foundry       |
| ----- | --------------------------------------------------- | ------------- | ----------------- | ------------- |
| 1     | niezaufany dostawca                                 | brak kontroli |                   |               |
| 2     | niezaufany integrator                               |               | brak kontroli     |               |
| 3     | niezaufane foundry                                  |               |                   | brak kontroli |
| 4     | produkt dostępny komercyjnie                        | brak kontroli | brak kontroli     | brak kontroli |
| 5     | niezaufane biuro projektowe                         | brak kontroli | brak kontroli     |               |
| 6     | biuro projektowe bez produkcji krzemu               | brak kontroli |                   | brak kontroli |
| 7     | niezaufany dostawca używający zaufanych komponentów |               | brak kontroli     | brak kontroli |

Opis poszczególnych modeli ataku:

1. niezaufany dostawca  - w większości systemów komponenty pochodzą od różnych dostawców np. interfejsy USB, interfejsy sieciowe  bądź pamięci i procesory. Jeśli nie mamy kontroli nad ich procesem projektowania to dostajemy produkt którego zasad działania nie znamy (typu closed source). W konsekwencji wiemy co robi ale nie jak
2. niezaufany integrator - wprowadzenie trojana na poziomie syntezy układów scalonych i / bądź poprzez integracje i łaczenie elementów
3. niezaufane foundry — większość firm produkujących elektronikę nie ma technologi wykonania krzemu tyn. zleca to innym firmom. Prowadzi to do utraty kontroli nad końcowym etapem produkcji czyli trawieniem wafli krzemowych (zmiana masek, nieprawidłowo działające tranzystory), więcej [Trojany Dopingowe](https://www.emsec.rub.de/media/crypto/veroeffentlichungen/2015/03/19/beckerStealthyExtended.pdf)
4. produkt dostępny komercyjnie  - tutaj jako klient mamy dostęp tylko dostęp do gotowego prouktu. Wprowadzenie trojana może nastąpić na każdym etapie produkcji a jego wykrycie jest kosztowne i trudne, więcej [Prezentacja Confidence 2018 ](https://adamkostrzewa.github.io/jekyll/update/2018/06/06/prezentacja-confidence-2018.html)
5. niezaufane biuro projektowe - firma posiada kontrolę nad procesem produkcji krzemu jednak modyfikacja może nastąpić w procesie projektowania komponentów bądź integracji systemu 
6. biuro projektowe bez produkcji krzemu - integrator nie ma kontroli nad częścią komponentów projektowanego systemu, jak i procesem produkcji krzemu, ta sytuacja dotyczy większości firm działających na rynku
7. niezaufany dostawca używający zaufanych komponentów - dostawca komponentów (np. bibliotek HDL) może stracić kontrole nad własnym produktem na etapie integracji bądź produkcji krzemu. Sytuacja trudna, bo by udowodnić swoją niewinność musi ujawnić źródła produktu / komponentu.



**Przykładowy atak**

całość w [tekście](https://adamkostrzewa.github.io/jekyll/update/2018/05/16/PL-trojany-sprzetowe-confidence.html)

Opiszmy zatem zagrożenie na teoretycznym przykładzie ataku inspirowanego ostatnimi doniesieniami prasowymi, np. lukami w CClenearze czy płytami głównymi DELLa. Po pierwsze, ze względu na specyfikę musimy uwzględnić wysoki stopień wyrafinowania atakującego rozumiany jako doświadczenie techniczne i posiadane zasoby. Załóżmy zatem że plan operacji jest przygotowany przy współudziale/współpracy producenta podzespołów elektronicznych z dalekiego wschodu. Atakujący ma profesjonalny zespół inżynierów i zasoby finansowe pozwalające na rozłożenie całego przedsięwzięcia w czasie - nawet na kilka lat. Pierwszym krokiem będzie wprowadzenie zainfekowanego sprzętu na rynek. Duże firmy, np. HUAWEI, mogą od razu wbudować go w swój produkt - pierwszy etap. To jednak wiąże się z dużym ryzykiem utraty zaufania klientów w przypadku wykrycia. Dodatkowo raz zmodyfikowanych  produktów nie sposób wycofać z rynku. Dlatego atakujący decyduje się na alternatywne rozwiązanie: wprowadzenie trojana w module dostarczonym przez podwykonawcę. Może się to odbyć przy jego współpracy na pierwszym bądź drugim etapie produkcji, bądź też bez jego wiedzy lub zgody na drugim i trzecim etapie. Przykładem takiego ataku jest historia związana z [oświadczeniem firmy DELL](http://www.theregister.co.uk/2010/07/21/dell_server_warning/) która ostrzegała użytkowników że w niektórych produktach (płytach głównych) występuje trojan sprzętowy najprawdopodobniej wprowadzony przez podwykonawcę. By dodatkowo zabezpieczyć się na wypadek wykrycia, atakujący projektuje funkcjonalność tak aby można ją było uznać za błąd projektowy. Słynnym przykładem są [dynamicznie zmienialny mikrokod AMD](https://www.realworldtech.com/forum/?threadid=35566&curpostid=35566) które według producenta miały służyć łataniu (pathowaniu) działającego procesora. Okazało się jednak że umożliwiają atakującemu wprowadzenie tylnej furtki (backdoora) w procesie aktualizacji i ominięcie systemu ochrony sprzętowej rodząc wiele spekulacji i kontrowersji. Oczywiście AMD uznało sprawę za błąd projektowy. 

 Następnie gotowy produkt jest rozprowadzany na rynku. Atakujący na tym etapie nie aktywuje trojana tylko czeka i pozwala użytkownikom cieszyć się podstawową funkcjonalnością układu. Po pewnym, czasie np. od pół/roku do dwóch lat następuje nasycenie rynku. Produkt pojawia się w naturalny sposób (w wyniku zakupu, napraw gwarancyjnych, podmiany czy czasowej wymiany sprzętu) w  wybranych obiektach np. bankach, fabrykach, instytucjach rządowych. 

Wtedy można przystąpić do właściwego ataku.  Istnieje  wiele  sposobów aktywacji i komunikacji z trojanami: przez tylne furtki w protokole, przez manipulacje protokołem, atak bocznym kanałem czy w końcu przez wprowadzenie błędu. Tylne furtki w protokole to jedna z popularniejszych metod która polega na wbudowaniu sterowania trojanem w już istniejącą komunikację używając znaków wodnych bądź technik stegano tzn. wybrane i znane tylko atakującym fragmenty transmisji służą do wydawania poleceń złośliwemu układowi bądź odbioru danych. 

Nasz atakujący wybiera zatem pierwszy sposób. Aktywacja i wyprowadzanie danych może nastąpić jako element procesu instalacji / aktualizacji sterowników. Połączenie z serwerami producenta odbywa się wtedy za wiedzą i zgodą użytkownika. Warto wziąć pod uwagę i bardziej wysublimowane formy ataku. Możliwe jest zakupienie praw do produktu firmy trzeciej niepowiązanej bezpośrednio z atakującym. Świetnym przykładem jest niedawny skandal z aplikacją [CCleaner](http://www.cyberdefence24.pl/665382,napastnicy-stojacy-za-infekcje-ccleanera-prawdopodobnie-osiagneli-swoj-cel-komentarz-exatela). Znany i lubiany program CCleaner przez prawie miesiąc ( od 15 sierpnia, do 12 września kiedy kolejny update usunął podatność) infekował miliony komputerów swoich użytkowników. [Badacze z firmy Talos](https://zaufanatrzeciastrona.pl/post/wiadomo-juz-kto-byl-celem-ataku-na-uzytkownikow-ccleanera/), którzy jako pierwsi publicznie opisali atak, opublikowali raport na temat celów ataku wymieniając [fabrykę sprzętu AGD Samsunga](https://zaufanatrzeciastrona.pl/post/na-liscie-celow-tajemnicznych-chinskich-wlamywaczy-znalazla-sie-polska-fabryka-agd/) w Polsce. 

Wykrycie ataku będącego kombinacją sprzętowo softwarową byłoby jeszcze trudniejsze niż w przypadku CCleanera. Po pierwsze, jak opisaliśmy wcześniej, całość funkcjonalności służącej ominięciu zabezpieczeń systemu jest wykonana w sprzęcie. Jak pokazują [wyniki](https://danluu.com/cpu-backdoors/) uzyskane przez badaczy zabezpieczeń sprzętowych, np. backdoorow w procesorach, warstwa oprogramowania jest praktycznie bezbronna. Większość mechanizmów zabezpieczających [od lat 70tych ](http://www.multicians.org/protection.html)opiera się na założeniu, że sprzęt na którym pracują zachowuje się według zasad ściśle określonych w specyfikacji np. pierścienie ochrony pracy procesora.

W rezultacie, atakujący musi jedynie zamaskować komunikację z trojanem dokonywaną w celu infiltracji albo eksfiltracji. Techniki kryptograficzne np. stegano czy znaki wodne, dowodzą że można wykonać to nie wzbudzając podejrzeń - nie znając protokołu komunikacyjnego jest niezwykle trudno wykryć przebieg i cel połączenia. W konsekwencji atakujący może odczytać i interesujące go wartości i prowadzić sterowanie np. za pomocą danych diagnostycznych wysłanych za wiedzą i zgodą użytkownika. 



**Prawdziwe historie**

Dobrym przykładem są chińskie firmy Huawei i ZTE które po fali krytki oskarżającej o stoswanie trojanów sprzętowych i softwarowych w produktach telekomunikacyjcnych [4], [5], [6] znalazla sie na celowniku kogresu USA. W 2012 kongres zarządał wykluczenia firmy z przetargów publicznych na terenie kraju [7],[8]. Wymowne nagłówki amerykanskiej prasy NYT „[Panel kongresu US uznaje Huawei i ZTE za zagrożenie dla bezpieczeństwa narodowego](http://www.nytimes.com/2012/10/09/us/us-panel-calls-huawei-and-zte-national-security-threat.html)” czy niemieckiej telewizji publicznej Arte „[Huawei szpieg z Chin](http://info.arte.tv/de/huawei-der-spion-aus-china)” najlepiej oddają sytuację. 

    [4] http://www.nytimes.com/2012/10/09/us/us-panel-calls-huawei-and-zte-national-security-threat.html
    [5] https://www.theguardian.com/technology/2012/oct/08/china-huawei-zte-security-threat
    [6] https://www.forbes.com/forbes/welcome/?toURL=https://www.forbes.com/sites/simonmontlake/2012/10/08/u-s-congress-flags-chinas-huawei-zte-as-security-threats
    [7] http://www.spiegel.de/netzwelt/netzpolitik/us-kongress-will-chinas-telekom-firmen-huawei-und-zte-aussperren-a-860014.html
    [8] http://info.arte.tv/de/huawei-der-spion-aus-china
