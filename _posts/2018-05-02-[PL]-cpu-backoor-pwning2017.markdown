---
layout: post
title:  "[PL] CPU Backdoor PWNING2017"
date:   2018-05-28 14:38:12 +0200
categories: jekyll update
---
Artykuł ktróry został opublikowany jako materiał towarzyszący konferencji PWNING 2017 w Warszawie.
Całość w PDF: [Pobierz plik](/download/Segregator1.pdf) 

Streszczenie:
Backdoor to metoda ominięcia mechanizmów bezpieczeństwa wykorzystująca podatność w systemie lub sprzęcie.
Od dawna dyskutuje się na temat możliwości celowej implementacji podatności sprzętowych w produktach komercyjnych, 
np. komputerach typu mainframe, routerach czy procesorach desktopowych [3] pozwalających na łatwą implementację backdoora. 
Jak dotąd, większość tych spekulacji nie 
znajduje potwierdzenia, jednak pytanie, czy można budować 
bezpieczeństwo, w szczególności infrastruktury krytycznej,
np. banki, szpitale, instytucje rządowe, wojsko, w oparciu 
o komercyjne produkty, wciąż pozostaje otwarte. Mimo że znaleziono już backdoory sprzętowe w układach FPGA
[1], jak i sprzęcie sieciowym, np. Linksysy WAG200G [2], to procesory pozostają przez wielu uznawane za bezpieczne.
Celem artykułu jest przypomnienie, że bezpieczeństwo systemów komputerowych opiera się na swoistej „symbiozie”
pomiędzy mechanizmami sprzętowymi i oprogramowaniem,
które wymaga zaufania do obydwu komponentów. Konsekwentnie chcemy zapoznać czytelnika z teorią działania luk
w procesorach, a także pokazać, że ich zaimplementowanie jest relatywnie proste i mieści się w kilku liniach kodu VHDL.
Dodatkowo jest tanie, a także bardzo trudne do wykrycia.
Dyskusję zaczniemy od przedstawienia mechanizmów bezpieczeństwa wbudowanych w procesor. Kolejno pokażemy,
jak zaprojektować podatność, a następnie, jak ją wykorzystać, i przy użyciu prostego exploita, napisanego dla systemu Linux, uzyskać backdoor. 
Ostatecznie przenalizujemy możliwe warianty implementacji pod kątem łatwości wykrycia, potrzebnych zasobów, a także wydajności.

[1] Sergiei Skorbogatov: „Hardware Assurance and its importance to National Security”. 
Dostępna pod adresem http://www.cl.cam.ac.uk/~sps32/sec_news.html#Assurance [Online 06.08.2017],
[2] Eloi Vanderbeken: „Some codes and notes about the backdoor listening on
TCP–32764 in linksys WAG200G”. Dostępna pod adresem https://github.com/elvanderb/TCP–32764 [Online.06.08.2017],
[3] Dan Luu: „CPU Backdoors” 2015. Dostępna pod adresem https://danluu.com/cpu–backdoors/ [Online 06.02.2017]

