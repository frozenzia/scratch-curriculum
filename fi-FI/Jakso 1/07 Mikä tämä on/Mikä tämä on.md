Taso 3

#Mikä tämä on

__Johdanto__
Satunnainen esine näytetään vääristyneenä liitutaululla. Pelaajan pitää arvata, mitä se on, valitsemalla oikea kuva alempana. Mitä nopeammin arvaa, sitä enemmän pisteitä saa!

##VAIHE 1: Pistä esineet ilmestymään liitutaululla

Halutaan muutamia kuvia näytettäväksi liitutaululla.

1. Aloita uusi Scratch-projekti ja poista kissahahmo.
2. Napsauta esiintymislavaa ja sitten Taustat-välilehteä. Tuo kirjastosta Sisällä/chalkboard -taustan.
3. Lisää uusi hahmo ja anna sille haluamasi asuste. Voit valita jotain Asiat -kansiosta.
4. Aseta uusi hahmo keskelle liitutaulua. Suurenna tai pienennä se tarvittaessa.
5. Napsauta Asusteet-välilehteä ja tuo neljä lisää asiaa. Voit valita ihan mitä vaan, jippii!
Nyt pistetään satunnainen kuva ilmestymään.
6. Luo tällainen skripti:

```scratch
	kun klikataan LIPPU
	toista valitse satunnaisluku väliltä 1 - 5 kertaa
		seuraava asuste
	(loppu toista)
```

###Testaa projektisi
__Napsauta vihreä lippu.__

Näyttääkö hahmo eri asuste?

__Napsauta sitä muutaman kerran lisää.__
Tuleeko eri asuste joka kerta? Joskus näet saman asusteen pari kertaa peräkkäin, mutta se ei haittaa. Huomaat myös, että hahmo välkkyy hieman kun asuste vaihtuu. Tämä korjataan seuraavassa vaiheessa.

Tallenna projektisi

##VAIHE 2: Make the pictures distorted

__Vääristetään kuva kun sen esiintyy alkuun ja selkeytetään se muutaman sekunnin ajan.__

Käytetään tulos-muuttujaa hallinoimaan, kuinka kovasti kuva on vääristynyt. Jos tulos on korkea, kuva on todella vääristynyt. Sitä mukaan kun tulos laskee, kuva on vähemmän ja vähemmän vääristynyt. Tulos toimii myös ajastimen tavoin, kuten __Timer Scratch-kortissa.__

1. Tieto-paletissa, tee muuttuja nimeltään tulos.

2. Muuta skripti näin:

```scratch
	kun klikataan LIPPU
	piilota
	toista valitse satunnaisluku väliltä 1 - 5 kertaa
		seuraava asuste
	(loppu toista)
	aseta tulos arvoon 110
	toista kunnes tulos = 0
		muuta muuttujan tulos arvoa -10
		aseta tehoste pikselöi kohteeseen tulos
		aseta tehoste väri kohteeseen tulos
		näytä
		odota 1 sekuntia 
	(loppu toista)
```

Sinun pitää lisätä piilota-lohko alkuun ja kaikki muu 'aseta tulos arvoon 110'-lohkosta alaspäin.

###Testaa projektisi
__Napsauta vihreä lippu.__

Esiintyykö satunnainen ja vääristynyt kuva?

Väheneekö vääristys asteittain?

Laskeeko tulos sitä mukaan, kun kuvan vääristys vähenee?

Onko kuva selkeä kun tulos on nolla?

Tuleeko edelleen eri kuva joka kerta kun napsautat vihreätä lippua?

Tallenna projektisi

##Kokeiltavaa

__Kokeile vaihtaa tuloksen alkuarvoa ja kuinka paljon se muuttuu joka kerta kun mennään silmukan läpi.__ Miten tämä vaikuttaa kuvan ulkonäköön? Tekeekö tämä kuvan tunnistamisen vaikeammaksi vai helpommaksi?

__Kokeile eri tehosteita alasvetovalikoista.__ Miten nämä vaikeuttavat tunnistamisen?

##VAIHE 3: Anna pelaajan arvata, mikä kuva on kyseessä

Tähän asti meillä on satunnainen kuva, joka selkiytyy hiljaa ja tulos, joka pienenee ajan mittaan, mutta miten pelin voi voittaa?  Lisätään ruudun alaosalle hahmoja, joita pelaaja voi napsauttaa. Jos napsauttaa oikeata, voittaa pelin. Jos napsauttaa väärää, hahmo häipyy ja peli jatkuu.

Ensin meidän pitää tietää, mikä on oikea vastaus.

1. Tee muuttuja nimeltään __vastaus__. Varmista, että se on kaikille hahmoille.
2. Muuta skripti niin, että se kirjaa ylös oikean vastauksen. Lisää 'aseta vastaus arvoon asusteen #' -lohko ensimmäisen toista-silmukan jälkeen:

```scratch
	kun klikataan LIPPU
	piilota
	toista valitse satunnaisluku väliltä 1 - 5 kertaa
		seuraava asuste
	(loppu toista)
	aseta vastaus arvoon asusteen #
	aseta tulos arvoon 110
	toista kunnes tulos = 0
		muuta muuttujan tulos arvoa -10
		aseta tehoste pikselöi kohteeseen tulos
		aseta tehoste väri kohteeseen tulos
		näytä
		odota 1 sekuntia 
	(loppu toista)
```
__Nyt pitää lisätä hahmot, joita pelaaja voi napsauttaa.__

3. Kopioi päähahmo ja vedä kopio esiintymislavan vasempaan alakulmaan.
4. Vaihda tämän hahmon nimeksi __vastaus1.__ (Siitä on helpompi puhua.)
5. Poista __vastaus1__:n skripti ja kaikki asusteet paitsi ensimmäinen.
6. Toista 3 viimeistä kohtaa, mutta laita __vastaus2__ hahmo __vastaus1__:n viereen ja poista kaikki sen asusteet paitsi toinen.
7. Tee näin 3 kertaa lisää hahmoille __vastaus3__, __vastaus4__ ja __vastaus5.__
Lopussa pitäisi olla rivi viittä vastaushahmoa esiintymislavan alalaidassa, jokainen näyttäen päähahmon eri asusteita. __Millään vastaushahmolla ei pidä olla skriptiä.__

Nyt halutaa jokainen hahmo reagoimaan napsautuksiin ja tekemään jotain riippuen siitä, onko se oikea vastaus vai ei.

8. Lisää tällainen skripti vastaus1 hahmolle:

```scratch
	kun tätä hahmoa klikataan
	jos vastaus = 1, sitten
		lähetä voitettu
	muuten
		piilota
	(loppu jos)
```

9. Vedä tämä skripti jokaiseen vastaushahmoon. __Jokaisessa hahmossa vaihda ykkönen kakkoseksi, kolmoseksi, jne.__
10. Meidän pitää vielä lisätä jokin, joka reagoi voitettu viestiin.  Lisää tämä skripti päähahmolle:

```scratch
	kun vastaanotan voitettu
	sano yhdistä Onneksi olkoon! Tuloksesi on  ja tulos
```

###Testaa projektisi
__Napsauta vihreä lippu.__

Kun testaat peliä, voit käyttää __vastausvahtia__ esiintymislavalla näyttämään, mikä on oikea vastaus. Se auttaa testaamisessa.

Mitä tapahtuu kun napsautat __oikeata vastausta?__

Mitä tapahtuu kun napsautat __väärää vastausta?__

Mitä tapahtuu väärälle vastaus kun __aloitat uuden pelin?__

Testi paljastaa kaksi ongelmaa. Ensiksi väärät vastaukset eivät enää näyttäydy kun seuraava peli alkaa. Toiseksi, tulos ei pysähdy kun saamme oikean vastauksen.

11. Ensimmäisen ongelman ratkaisemiseksi lisää seuraava skripti kaikille vastaushahmoille:

```scratch
	kun klikataan LIPPU
	näytä
```

Toisen ongelman ratkaisemiseksi meidän pitää pysäyttää __päähahmon__ toista kunnes -silmukkaa kun pelaaja napsauttaa oikeata vastausta. Käytämme tähän uutta muuttujaa. Asetetaan se arvoon __nolla__ kun peli käynnistyy ja arvoon __yksi__ kun peli voitetaan. Pysäytetään toista kunnes -silmukkaa kun joko tulos saavuttaa arvoa __nolla__ TAI __peli voitettu -lippu__ on asetettu arvoon __yksi.__

12. Tee uusi muuttuja nimeltään voitettu?
13. Muuta skripti näin:

```scratch
	kun klikataan LIPPU
	piilota
	toista valitse satunnaisluku väliltä 1 - 5 kertaa
		seuraava asuste
	(loppu toista)
	aseta vastaus arvoon asusteen #
	aseta tulos arvoon 110
	toista kunnes tulos = 0 tai voitettu? = 1
		muuta muuttujan tulos arvoa -10
		aseta tehoste pikselöi kohteeseen tulos
		aseta tehoste väri kohteeseen tulos
		näytä
		odota 1 sekuntia 
	(loppu toista)

	kun vastaanotan voitettu
	aseta voitettu? arvoon 1
	poista graafiset tehosteet
	sano yhdistä Onneksi olkoon! Tuloksesi on  ja tulos
```

Tallenna projektisi

__Hienoa! Olet tehnyt peruspelin loppuun!__

Mutta vielä on muutoksia, mitä voit tehdä. Kokeile näitä haasteita!


##Haaste 1: Make the game harder or easier

Change how difficult the game is.

* Try changing how fast the picture is revealed and how fast the score goes down.
* Try changing the distortions on the picture.
* Try changing the pictures being guessed, to make them either more similar or more different. If you do this, don’t forget to change the vastaus sprite’s costume.

Tallenna projektisi

##Haaste 2: Distort the picture differently in each game

At the moment, each play of the game uses the same distortion. In Step 2, you might have tried some different distortions that work at least as well as the colour + pixelation we used.

Find some different distortions that work well. 

Change the game so that each game uses a different distortion in the repeat until loop.

__Vinkki:__ Try creating a new variable, called distortion to use. Set it to a random value at the start of the game. Use if blocks in the body of the repeat until loop to apply the correct distortion for this game.

Tallenna projektisi

##Haaste 3: Make a game have a few rounds

At the moment, each game is independent. Change it so that the game proceeds in several rounds. For instance, have one game take three rounds, so the player has to guess three pictures and can score up to 300 points.

__Vinkki:__ You’ll need an extra variable to store the grand total across all the rounds. You’ll also need a loop to go through the different rounds.

__Vinkki:__ You’ll also have to make the wrong guesses reappear at the start of each round. Perhaps you could use a broadcast message to do that?

Tallenna projektisi

##Haaste 4: Make later rounds more difficult

As you go through different rounds, make the game harder each time.

Does each round need to score the same? Should you get more points for guessing quickly in the later, more difficult rounds?

__Vinkki:__ How will you know which round you’re in? How can you use that to change the difficulty and the score?

Tallenna projektisi

##Haaste 5: Keep playing until the player gets it wrong

Instead of using a fixed number of rounds, keep playing the game until the player doesn’t get a picture right. This probably only works if the game gets harder in later rounds.

Tallenna projektisi

##Haaste 6: Make the game harder or easier depending on how well the player does

Rather than always making the game harder, make the game adjust the difficulty depending on the skill of the player. If they get the right picture quickly, make the next game a bit harder. If they don’t get the right picture, or only get it late, make the next game a bit easier.

This idea only really works if you don’t add up someone’s score over several rounds.

Tallenna projektisi

##Haaste 7: Keep track of the highest score

Keep track of the highest score. If someone manages to beat it, ask for their name and update the highest score. Make sure the highest score, and the name of the person who scored it, are displayed.

Tallenna projektisi


##Haaste 8: Make wrong guesses expensive

At the moment, there’s no penalty to just clicking on all the vastaus sprites as quickly as you can. Change the game so that the score goes down a bit every time you make an incorrect guess.

Does this make the game better?

Tallenna projektisi


__Hienoa, olet tehnyt harjoituksen, nyt voit nauttia pelistä!__
Muista, että voit jakaa pelisi kavereitesi ja perheesi kanssa valitsemalla  __Jaa__ valikkopalkista!
