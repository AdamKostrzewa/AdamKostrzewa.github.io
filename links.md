---
layout: post
title: (HW Sources)
image: /download/z80_circuit.jpg
description: wybrane link do ciekawych prezentacji i wykładów o tematyce hardware hacking i architektura komputerów
permalink: /linki/
---

<!-- Twitter cards -->
<meta name="twitter:site"    content="@{{ site.twitter_username }}">
<meta name="twitter:creator" content="@{{ page.author }}">
<meta name="twitter:title"   content="{{ page.title }}">

{% if page.summary %}
<meta name="twitter:description" content="wybrane link do ciekawych prezentacji i wykładów o tematyce hardware hacking i architektura komputerów">
{% else %}
<meta name="twitter:description" content="wybrane link do ciekawych prezentacji i wykładów o tematyce hardware hacking i architektura komputerów">
{% endif %}

{% if page.image %}
<meta name="twitter:card"  content="summary_large_image">
<meta name="twitter:image" content="https://{{ site.url }}{{ page.image }}">
{% else %}
<meta name="twitter:card"  content="summary">
<meta name="twitter:image" content="https://{{ site.title_image }}">
{% endif %}
<!-- end of Twitter cards -->
    
W tej sekcji przedstawiam wybrane link do ciekawych prezentacji, wykładów i tutoriali o tematyce hardware hacking, elektronika cyfrowa i architektura komputerów. 
Lista powiększy się o low-level programming i OS programming (kernel hacking).

**UWAGA Lista rozwija się!** 

**Twój wkład też się liczy!** - widziałeś coś ciekawego, wrzuć link w komentarzu!

Jeśli jest ciekawy podziel się - *sharing is caring!* :)


**Hardware Hacking**

* Building Trojan Hardware at Home - tytuł mówi chyba wszystko! Dodam że chodzi o modyfikacje
myszek, klawiatur etc.  
prezentacja w pdfie [link do slajdów](https://www.blackhat.com/docs/asia-14/materials/Dunning/Asia-14-Dunning-Building-Trojan-Hardware-At-Home.pdf)  
i wideo z konferencji BlackHat 2014 [link do yt](https://www.youtube.com/watch?v=QJ4KZ8vlo4g)  
* Samy Kamkar's Crash Course in How to Be a Hardware Hacker [link do wideo](https://www.youtube.com/watch?v=tlwXmNnXeSY)
  
temat będzie na blogu ale jeśli jesteście zainteresowani piszcie!

**Klasyka**
* [AT&T Archives: The UNIX Operating System](https://www.youtube.com/watch?v=tc4ROCJYbm0) - z archiwów firmy AT&T, twórcz UNIXa
opowiadają o początkach systemu i jego zasadach działania. Wywiady z głównymi deweloperami  - między innymi Ritchie, Thompson, Brian Kernighan, i wielu innych.
Nikt nie tłumaczy lepiej idei stojących za mechanizmami systemu niż jego twórcy. 


**Trojany Hardwarowe**

* Prof. Christof Paar wyjaśnia podstawy trojanów dopingowych i dlaczego analiza optyczna chipu nie pozwala na jednosznaczne wykrycie:  
wideo z konferencji OpenChaos 2018 [link](https://media.ccc.de/v/c4.openchaos.2018.01.hardware-trojans)  
wideo z konferencji RuhrSec 2017: "How to Build Hardware Trojans" [link](https://www.youtube.com/watch?v=46D_5F3_J4A)  

* Demonstration of Hardware Trojans wideo z konferencji Defcon 16 [link](https://www.youtube.com/watch?v=QGIKhJrb9aA)

* [Podsumowanie Dana Luu na temat CPU backdoors](https://www.youtube.com/watch?v=tc4ROCJYbm0) - zbiór linków (niestety nie aktualizowany) do materiałów o backdoach w CPU.

**Rewers Krzemu**

* Uncaging Microchips - Peter Laackmann, Marcus Janke (niemiecki Infineon) o produkcji krzemu i jego rewersie w warunkach domowych  
wideo z konferencji CCC 2014 [link do yt](https://www.youtube.com/watch?v=pIpxawdUb4I)  
prezentacja w pdfie [link do slajdów](https://events.ccc.de/congress/2014/Fahrplan/system/attachments/2512/original/Uncaging_Microchips-Marcus_Janke_Peter_Laackmann.pdf)  

* Decapping Chips The Strike Easy Hard Way - Adam "Major Malfunction" Laurie & Zac Franken  
rewers krzemu w warunkach domowych z perspektywy USA (dużo o rozpuszczaniu plastiku wentylacji i sprzęcie laboratoryjnym)  
wideo z konferencji Defcon 21 [link do yt](https://www.youtube.com/watch?v=0Z4aF-qiziM)  

**Architektura Komputerów**

klasyka klasyki wykładów o logicznej warstwie architektury komputerów (a także, pamięci, routerów etc.)

* Prof. Onur Multu - dawniej [Carnegie Mellon University](http://users.ece.cmu.edu/~omutlu/) teraz [ETH Zurich](https://people.inf.ethz.ch/omutlu/)  
[Spring 2015 -- Computer Architecture Lectures -- Carnegie Mellon](https://www.youtube.com/watch?v=zLP_X4wyHbY&list=PL5PHm2jkkXmi5CxxI7b3JCL1TWybTDtKq)

* [Christopher J. Terman](http://people.csail.mit.edu/cjt/) i inni 
MIT Computer Science and Artificial Intelligence Laboratory  
[Computer Architecture MIT 6.004 2015](https://www.youtube.com/playlist?list=PLWokBk9W7kzGqZYZz6BiaqtsrHQK_22u7)

* James M. Conrad at the University of North Carolina at Charlotte  
[Embedded Systems Course - Version 3 - 2015](https://www.youtube.com/watch?v=bvEDXDFbM_E&list=PLPIqCiMhcdO5gxLJWt_hY5CPMzqg75IU5)
