Taso 2

#Kilpailu aavikolla

__Johdanto:__
Tämä peli on kahden hengen peli, jossa papukaija ja leijona juoksevat kilpaa aavikossa. Pelaajien pitää painaa jotain näppäintä mahdollisimman nopeasti liikuttaakseen hahmonsa. Ensimmäinen joka pääsee ruudun reunalle on voittaja.


##VAIHE 1: Luo lavasteet ja lisää hahmot

1. Valitse esiintymislava ja lisää kirjastosta Luonto/desert -tausta.
2. Lisää uusi hahmo kirjastosta Eläimet/lion.
3. Lisää toinen hahmo kirjastosta Eläimet/parrot.



##VAIHE 2: Pistä leijona ja papukaija liikkumaan


Haluamme hahmon liikkuvan kun painat jotain näppäintä.

1. Valitse ensin leijonahahmo ja laita se liikkumaan 4 askelta kun painetaan ‘L’ -näppäintä.

```scratch
	kun painetaan l
	liiku 4 askelta
```

2. Valitse seuraavaksi papukaijahahmo ja laita se liikkumaan 4 askelta kun painetaan ‘A’ -näppäintä.

```scratch
	kun painetaan a
	liiku 4 askelta
```

###Testaa projektisi
__Napsauta vihreä lippu__ 
Liikkuvatko papukaija ja leijona ruudun poikki kun painat ‘A’ ja ‘L’ -näppäimet?

Tallenna projektisi


##VAIHE 3: Käynnistä kilpailu

Tarvitaan tapa käynnistää kilpailu ja tapa tietää, kuka sen on voittanut. __Ensin luodaan käynnistysnappi.__

1. Lisää hahmo kirjastosta Asiat/Button1.
2. Muokkaa napin asustetta lisäämällä siihen tekstin 'käynnistä'. Saatat joutua leikkimään fontin kanssa, jotta saat ä-kirjaimet näkymään oikein. Aseta hahmo keskelle esiintymislavaa.
3. Lisää skripti joka näyttää hahmon kun ohjelma ajetaan:

```scratch
	kun klikataan LIPPU
	näytä
```
4. Kun nappia painetaan, haluamme sen lausuvan N... Y... T... NYT! ja sitten menevän piiloon. Lisää toinen skripti näin:

```scratch
	kun tätä hahmoa klikataan
	sano N... 1 sekunnin ajan
	sano Y... 1 sekunnin ajan
	sano T... 1 sekunnin ajan
	sano NYT! 1 sekunnin ajan
	piilota
```
###Testaa projektisi
__Napsauta vihreä lippu.__

Kun painat käynnistysnappia sanooko se "N... Y... T... NYT!" ennen kuin häipyy näkymästä?

Tallenna projektisi

Haluamme kilpailijoiden liikkuvan vasta sen jälkeen kun kilpailu on käynnissä ja haluamme tietää milloin kilpailu on ohi, joten tarvitaan muuttujaa tämän tiedon säilyttämiseen.

5. Tee muuttuja kaikille hahmoille ja anna sille nimi 'kilpaillaan'.  Poista puumerkki sen edestä, jotta sitä ei näytetä esiintymislavalla.
6. Nyt aseta 'kilpaillaan' arvoon 0 kun ohjelma ensin käynnistetään. Muuta aikaisemman `kun klikataan LIPPU` skriptiä näin:

```scratch
	kun klikataan LIPPU
	näytä
	aseta kilpaillaan arvoon 0
```
7. Seuraavaksi aseta kilpaillaan -muuttuja arvoon 1 kun käynnistyslasku on päässyt loppuun.
8. Nyt pitää estää leijonaa ja papukaijaa liikkumasta ellei kilpaillaan -muuttuja ole arvossa 1. Valitse papukaijahahmo. __Lisää ohjauslohko skriptiin__ joka sallii papukaijan liikkua vain jos  __kilpaillaan = 1__.

```scratch
	kun painetaan a
	jos kilpaillaan = 1, sitten
		liiku 4 askelta
	(loppu jos)
```
9. Nyt tee sama leijonahahmolle.

###Testaa projektisi
__Napsauta vihreä lippu.__

Liikkuvatko leijona ja papukaija vasta sen jälkeen kun käynnistyslasku on ohi?

Halutaan vielä tietää kuka voittaa kilpailun ja asettaa sen alulle, jotta voidaan kilpailla uudelleen.

##VAIHE 4: Kilpailun loppu

1. Lisää papukaijan skriptiin lohko, joka asettaa kilpaillaan -muuttuja arvoon 0 kun hahmo koskettaa ruudun reunaa.

```scratch
	kun painetaan a
	jos kilpaillaan = 1, sitten
		liiku 4 askelta
		jos koskettaako reuna?, sitten
			aseta kilpaillaan arvoon 0
		(loppu jos)
	(loppu jos)
```
2. Nyt halutaan papukaijan ilmoittavan meille jos se voittaa kilpailun. Äänitä papukaijahahmolle uusi ääni, jota toistetaan kun papukaija voittaa. Napsauta __Äänet__ ja äännitä sitten ääni, jonka papukaija päästää voittaessaan kilpailun!
3. Lisää nyt lohkot, joilla toistat äänen ja pistät papukaijan kertovan voittaneensa:

```scratch
	kun painetaan a
	jos kilpaillaan = 1, sitten
		liiku 4 askelta
		jos koskettaako reuna?, sitten
			aseta kilpaillaan arvoon 0
			soita ääni whistle2
			sano Papukaija voittaa! 3 sekunnin ajan
		(loppu jos)
	(loppu jos)
```
4. Toista leijonalle.

###Testaa projektisi
__Napsauta vihreä lippu.__

Saatko painettua käynnistysnappia ja liikkuuko hahmot kun painetaan ‘A’ and ‘L’ -näppäimet?
Toistaako hahmot voittoäänensä ja sano voittaneensa kun pääsevät maalille?

Tallenna projektisi

##VAIHE 5: Pelin resetointi
Kun kilpailu on ohi, meidän pitää ilmoittaa asiasta muille hahmoille ja resetoida pelin, jotta voimme pelata uudestaan.

__Tarvitaan, että voittava hahmo viestittää voittonsa.__

1. Napsauta papukaijahahmoa.
Lisää lohko joka lähettää viestin "voitin" sen jälkeen kun hahmo sanoo voittaneensa.

```scratch
	kun painetaan a
	jos kilpaillaan = 1, sitten
		liiku 4 askelta
		jos koskettaako reuna?, sitten
			aseta kilpaillaan arvoon 0
			soita ääni whistle2
			sano Papukaija voittaa! 3 sekunnin ajan
			lähetä voitin
		(loppu jos)
	(loppu jos)
```
2. Nyt pitää lisätä uusi skripti joka odottaa voitin -viestiä ja siirtää papukaijan takaisin alkuun. Mitä tapahtuu jos muutat x:n arvoa?

```scratch
	kun vastaanotan voitin
	aseta x:lle arvo -175
```
3. Lisää nyt saman skriptin leijonalle. Kokeile eri x-arvoja ja varmista näin, että leijona ja papukaija ovat samalla viivalla alussa.
4. Halutaan leijonan ja papukaijan myös lähtevän samasta paikasta kun ohjelma ajetaan, eli lisää skripti, jolla ne asetetaan lähtöviivalle kun klikataan lippu.

```scratch
	kun klikataan LIPPU
	aseta x:lle arvo -175
```
5. Napsauta nyt nappihahmoa ja lisää skripti, jolla se tulee jälleen näkyviin kun se vastaanottaa voitin -viestin.
###Testaa projektisi
__Napsauta vihreä lippu.__


Pystytkö kilpailemaan ystävän kanssa niin, että toinen teistä liikuttaa papukaijaa painamalla ‘A’-näppäintä ja toinen liikuttaa leijonaa painamalla ‘L’-näppäintä?

Tallenna projektisi

##Haaste: Lisää boosteri

* __Yritä lisätä boosteri__ jota voi käyttää kerran kilpailussa, joka liikuttaa papukaijan tai leijonan __30 askelta kerrallaan.__
* __Lisää uusi asuste__ jossa tuli suihkuaa hahmon takaa ja laita se näkyviin kun boosteri painetaan.
* __Luo vielä yhden äänen__ jota hahmo pitää kun boosteri painetaan.

###Testaa projektisi

Tallenna projektisi

__Hienoa, olet tehnyt harjoituksen, nyt voit nauttia pelistä!__
Muista, että voit jakaa pelisi kavereitesi ja perheesi kanssa valitsemalla  __Jaa__ valikkopalkista!
