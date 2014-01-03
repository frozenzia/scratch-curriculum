Taso 2

#Kalannälkä

__Johdanto:__
Tehdään Kalannälkä-peli! Ohjaa isoa Nälkäistä Kalaa ja yritä syödä kaikki ympärillä liikkuvaa saalista.

##VAIHE 1: Luo Nälkäinen Kala -hahmo joka seuraa hiiriosoitinta
__Pistetään Nälkäinen Kala uimaan meressä!__

1. Aloita uusi projekti.
2. Valitse esiintymislava, valitse lavan 'Taustat'-välilehti. Tuo kirjastosta Luonto/underwater3 ja poista backdrop1.
3. Muuta Sprite1:n nimi Nälkäiseksi Kalaksi.
4. Tuo Nälkäisen Kalan asuste tiedostosta Resurssit/NälkäinenKala.png ja poista olemassa olevat asusteet costume1 ja costume2. 
5. Varmista, että hahmo suuntaa vain vasemmalle ja oikealle napsauttamalla hahmon tiedoissa: (kuva jossa vasen/oikea-nuolet)
6. Nyt luo skripti jolla Nälkäinen Kala seuraa hiiriosoitinta meressä näin:

```scratch
	kun klikataan LIPPU
	ikuisesti
		osoita kohti hiiriosoitin
		liiku 3 askelta
	(loppu ikuisesti)
```

###Testaa projektisi
__Napsauta vihreätä lippua.__ 
Liikuta hiiriosoitinta ympäri merta. Seuraako kala osoitinta?
Mitä tapahtuu jos et liikuta osoitinta ja kala pääsee siihen kiinni? Miltä se näyttää? Miksi näin tapahtuu?

7. Saat Nälkäisen Kalan hullunkurisen vipattelun loppumaan jos käsket sen liikkumaan vain silloin, kun se on riittävän kaukana hiiriosoittimesta. 
('etäisyys kohteeseen' -lohko on 'Tuntoaisti'-paletissa).


```scratch
	kun klikataan LIPPU
	ikuisesti
		jos etäisyys kohteeseen hiiriosoitin > 10, sitten
			osoita kohti hiiriosoitin
			liiku 3 askelta
		(loppu jos)
	(loppu ikuisesti)
```


###Testaa projektisi

Tallenna projektisi

##Kokeiltavaa

Jos haluat, voit käyttää skriptissä eri numeroita. Miten tämä vaikuttaa Nälkäisen Kalan liikkumiseen? Vaihda etäisyysraja isoksi numeroksi (e.g. 100), tai pieneksi numeroksi (e.g. 1). Vaihda määrä jota kala liikkuu isoksi numeroksi (e.g. 20) tai pieneksi numeroksi (e.g. 1 tai jopa 0).


##VAIHE 2: Lisää saalista

1. Luo uusi hahmo kirjastosta Eläimet/Fish2. 
2. Käytä 'Pienennä' -työkalua (lavan yläpuolella) tehdäksesi hahmosta pienemmän.
3. Luo skripti jolla saalis ui ympäriinsä. Haluamme sen liikkuvan satunnaisesti, joten pistetään se liikkumaan eteenpäin vähän matkaa, kääntymään satunnaisen määrän vasemmalle tai oikealle ja sitten tekemään saman uudelleen.

```scratch
	kun klikataan LIPPU
	ikuisesti
		liiku 2 askelta
		jos 'valitse satunnaisluku väliltä 0 - 1' = 0, sitten
			käänny (vastapäivää) 20 astetta
		muuten
			käänny (myötäpäivää) 20 astetta
		(loppu jos)
		pomppaa reunasta
	(loppu ikuisesti)
```

###Testaa projektisi
__Napsauta vihreätä lippua__ ja katso kun saalis uiskentelee. Uiko se odotetulla tavalla? Uiko se uskottavasti?

__Tällä hetkellä, Nälkäinen Kala ja saalis eivät vaikuta toisiinsa millään lailla. Tämä korjataan seuraavassa vaiheessa.__

Tallenna projektisi

###Kokeiltavaa

* Kokeile vaihtaa numeroita 'käänny' ja 'liiku'-lohkoissa. Kuinka ne saavat saaliin liikkumaan eri tavalla?
* Mitä 'pomppaa reunasta' -lohko tekee? Poista se ja katso, mitä tapahtuu.

##VAIHE 3: Nälkäinen Kala syö saaliin

__Nyt haluamme Nälkäisen Kalan syövän saaliin!__ Kun Nälkäinen Kala on saanut saaliin suuhunsa, kaksi asiaa pitää tapahtua:
* Nälkäisen Kalan pitäisi sulkea suunsa ja pitää "ahminta" ääntä.
* Saaliin pitää häipyä näkyvistä, sitten ilmestyä uudelleen hetken päästä.

1. Ensin, laitetaan saalis häipymään jos se koskettaa Nälkäistä Kalaa, ja ilmestymään 3 sekuntia myöhemmin. Käytä 'koskettaako'-lohkoa tarkistaaksesi, koskettaako saalis Nälkäistä Kalaa.

```scratch
	kun klikataan LIPPU
	ikuisesti
		liiku 2 askelta
		jos 'valitse satunnaisluku väliltä 0 - 1' = 0, sitten
			käänny (vastapäivää) 20 astetta
		muuten
			käänny (myötäpäivää) 20 astetta
		(loppu jos)
		pomppaa reunasta
		jos 'koskettaako Nälkäinen Kala?', sitten
			piilota
			odota 3 sekuntia
			näytä
		(loppu jos)
	(loppu ikuisesti)
```

###Testaa projektisi
__Kokeile peliäsi uudelleen -- huomaatko ongelmia?__ Huomaa, että saalis häipyy näkyvistä vaikka koskettaa Nälkäistä Kalaa missä tahansa kohtaa. Kala voisi myös vain odottaa 3 sekuntia ja syödä saaliin sillä sekunnilla kun se ilmestyy uudelleen, koska saalis ilmestyy aina samaan paikkaan, mistä on häipynytkin -- eipä ole kovin reilua!

2. Miten voisimme varmistaa, että saalis häipyy vain jos se koskettaa Nälkäisen Kalan suuta? Voisimme käyttää 'koskettaako väriä' -lohkoa ja tarkistaa, koskettaako se kalan sinisiä hampaita. Tee tämä korvaamalla skriptisi 'koskettaako'-lohko 'koskettaako väriä' -lohkolla, napsauta lohkon väri-ruutua ja napsauta vielä kalan hampaita.

3. Seuraavaksi pistetään saalis liikkumaan ruudulla satunnaiseen pisteeseen ennen uudelleenilmestymistä käyttämällä 'mene kohtaan' -lohko, ja antamalla sille satunnaiset arvot x:ksi ja y:ksi.

```scratch
	kun klikataan LIPPU
	ikuisesti
		liiku 2 askelta
		jos 'valitse satunnaisluku väliltä 0 - 1' = 0, sitten
			käänny (vastapäivää) 20 astetta
		muuten
			käänny (myötäpäivää) 20 astetta
		(loppu jos)
		pomppaa reunasta
		jos 'koskettaako väriä []?', sitten
			piilota
			odota 3 sekuntia
			mene kohtaan x:'valitse satunnaisluku väliltä -220 - 220' y:'valitse satunnaisluku väliltä -170 - 170'
			näytä
		(loppu jos)
	(loppu ikuisesti)
```
###Testaa projektisi

Koeaja peli uudelleen -- häipyykö saalis vain kun koskettaa kalan suuta? Ja ilmestyykö uudelleen satunnaisessa pisteessä eikä aina vaan siinä, mistä sitä on syöty?

4. Kalan pitää tietää, että se on syönyt jotain, jotta se voi toistaa äänen ja vaihtaa asusteensa. Teemme tämän niin, että saalis lähettää viestin syödyksi tulemisesta ennen kuin häipyy näkyvistä.

```scratch
	kun klikataan LIPPU
	ikuisesti
		liiku 2 askelta
		jos 'valitse satunnaisluku väliltä 0 - 1' = 0, sitten
			käänny (vastapäivää) 20 astetta
		muuten
			käänny (myötäpäivää) 20 astetta
		(loppu jos)
		pomppaa reunasta
		jos 'koskettaako väriä []?', sitten
			lähetä napattu
			piilota
			odota 3 sekuntia
			mene kohtaan x:'valitse satunnaisluku väliltä -220 - 220' y:'valitse satunnaisluku väliltä -170 - 170'
			näytä
		(loppu if)
	(loppu ikuisesti)
```
__Nyt haluamme kalan vastaanottavan tämän viestin ja reagoivan siihen pitämällä "ahminta" ääntä ja napsauttamalla leuat kiinni.__

5. Lisää Nälkäisen Kalan hahmolle tiedostoista Resurssit/SuuKiinni -asuste ja Resurssit/Ahminta -ääni.
6. Sitten, lisää Nälkäiselle Kalalle uusi skripti, joka vastaanottaa saaliin lähettämän viestin. Skriptillä pistetään kala toistamaan 'ahminta'-äänen, vaihtamaan SuuKiinni-asusteeksi, odottamaan hetken ja sitten vaihtamaan alkuperäiseen.

```scratch
	kun vastaanotan napattu
	soita ääni ahminta
	toista 2 kertaa
		vaihda asusteeksi SuuKiinni
		odota 0.5 sekuntia
		vaihda asusteeksi NälkäinenKala
	(loppu toista)
```

__Nyt Nälkäinen Kalamme on valmis syömään, täytetään meri saaliilla. Oikeanapsauta saaliin hahmoa ja valitse 'kopioi' useamman kerran.__

###Testaa projektisi
Napsauta vihreätä lippua.
Syökö Nälkäinen Kala saaliskalat? Syökö se yksittäisiä saaliskaloja?

Tallenna projektisi

###Ajateltavaa
Miksi meidän pitää lisätä 'näytä'-lohko saaliin skriptin alkuun? Ajattele mitä tapahtuisi jos saalis syödään ja peli pysäytetään ennen kuin se taas tulee näkyviin. Mitä tapahtuisi sitten kun peli käynnistettäisiin uudelleen?

__Hienoa, olet tehnyt peruspelin. On kuitenkin vielä muutoksia, mitä voit pelillesi tehdä. Oletko valmis haasteeseen?__


##Haaste 1: Pistä saaliskalat liikkumaan eri tavalla

__Tällä hetkellä kaikki saaliskalat liikkuvat samalla tavalla. Saatko yhden niistä liikkumaan eri tavalla?__
__Vinkki:__ Älä mieti tätä liikaa katsomatta projektin muita tehtäviä.

__Valitse yksi saaliskaloista, jolla kokeilla.__ Jos sillä on sama asuste kuin muilla, tee se eri väriseksi __'aseta tehoste väri kohteeseen' -lohkolla__. Sillä tavalla erotat sen muista saaliista.

Laita tämä saaliskala liikkumaan hitaammin kuin muut. __Vinkki:__ Tarkista 'liiku (2) askelta' -lohkoa.


###Testaa projektisi
Liikkuuko saaliskala hitaammin?  Tekeekö se pelistä paremman?
Jos osasit tämän, __yritä pistää yhden kaloista liikkumaan muita nopeammin.__


Liikkuuko saalis silti järkevällä tavalla?  Tekevätkö nämä muutokset pelistä paremman?
__Vinkki:__ Jos saalisi ui ympyrää, tarkista arvoja 'valitse satunnaisluku'-lohkossa ennen hahmojen 'käänny'-lohkoja.

Mitä jos laittaisit jokaisen saaliskalan käyttäytymään eri tavalla, käyttäen eri kombinaatioita näistä muutoksista?

Tekevätkö mikään näistä muutoksista pelistä paremman? Tekevätkö ne pelistä mielenkiintoisemman, hauskemman, vaikeamman tai helpomman? Ovatko mitkään näistä "parempia"?

Tallenna projektisi

##Haaste 2: Pistä saalis väistämään Nälkäistä Kalaa

Pelin saaliskalat ovat todella tyhmiä! Ne vaan uiskentelee satunnaisesti ympäri kunnes ne syödään. Oikeat kalat uivat pakoon saalistajia. __Laitetaan yhden saaliskaloista uivan pakoon Nälkäistä Kalaa.__

Scratchissä ei ole lohkoa, jolla tutkia missä suunnassa toinen hahmo on. Mutta voi käskeä hahmon osoittamaan toisen hahmon suuntaan ja kääntää sen sitten vastakkaiseen suuntaan. Tarvitsemasi lohkot löytyvät __Liike__ paletista.

Käyttäen tätä ideaa, __tee niin, että yksi saaliskaloista on aina selin Nälkäiseen Kalaan.__ Voit kenties haluta laittaa se wigglaamaan kun se ui pois.

###Testaa projektisi
Onko kala nyt vaikeammin kiinniotettavissa?  Onko peli nyt parempi?

Tallenna projektisi

##Haaste 3: Lisää pisteytys
Ei riitä, että syödään kalat. Mistä voi tietää, että on parempi pelissä kuin kavereita? __Tarvitaan tapa pitää kirjaa pisteistä, eli lisätään pistetaulu.__ Katso __"Keep Score" Scratch-kortista__ miten tämän voisi tehdä. 

Mihin kohtaan pitäisi pelitilannetta muuttava lohko sijoittaa?

Varmista, että tilanne nollaantuu pelin alussa.  Mihin tämä lohko kuuluu?

###Testaa projektisi
Nollaantuuko tilanne pelin alussa? Kasvaako se joka kerta saaliin syödessä?

Tallenna projektisi

##Haaste 4: Lisää ajastin

__Anna itsellesi aikarajoituksen pelissä.__ Kuinka monta kalaa pystyt ahmimaan 30 sekunnissa?

Katso __"Timer" Scratch-kortista__ miten peliin voi lisätä ajastimen. Aloita siitä, että peli kestää kolmekymmentä sekuntia.

###Testaa projektisi
Alkaako ajastin 30:sta?

Laskeeko se oikealla nopeudella?

Pystyykö saamaan saaliin kiinni ajastimen käydessä?

Loppuuko peli kun ajastin pääsee nollaan?

Tallenna projektisi

##Haaste 5: Lisää bonuspisteytys
Palkitse isolla bonuspistemäärällä jos pystyy syömään kolme saaliskalaa samanaikaisesti. Mistä voi tietää, kuinka monta kalaa on syönyt?
__Vinkki:__ Eräs tapa on tehdä näin __käytä muuttujaa laskeaksesi kuinka monta saaliskaa uiskentelee vedessä.__

Tallenna projektisi

##Haaste 6: Muuta peli: pidä saaliskalat hengissä! Joskus voi saada loistavia, uusia ideoita ottamalla olemassa olevan idean ja kääntämällä sen päälaelleen.

__Muuta peli niin, että saalistajakalan sijaan ohjaatkin saaliskalan.  Saaliskala uiskentelee meressä, joka on täynnä Nälkäisiä Kaloja.__ Miten pitkään kestät tulematta syödyksi?

Tallenna projektisi

__Hienoa, olet tehnyt harjoituksen, nyt voit nauttia pelistä!__
Muista, että voit jakaa pelisi kavereitesi ja perheesi kanssa valitsemalla  __Jaa__ valikkopalkista!
