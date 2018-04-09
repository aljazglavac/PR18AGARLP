# PR2018AGARLP #

### Avtorji ###

* Aljaž Glavač
* Andraž Raspor
* Luka Perovič

## Vmestno poročilo o pravljenem delu ##
### 13.4.2018 ###

## Predstavitev naše množice podatkov ##

Množica podatkov nad katero bomo opravljali raziskave in ugotavljali kakšne uplive imajo določeni atributi na druge, smo našli na spletni strani www.podatki.gov.si. Na omenjeni spletni strani so različni statistični podatki zbrani iz slovenije, kar je tudi razlog da smo se odločili uporabljati te podatke oz. množico podatkov.

Naša množica sestoji iz podatkov o prvič registriranih vozilih v Sloveniji. Podatki so razdeljeni po mescih in so dostopni za od leta 2012 do 2017. 

Za to množico podatkov smo se odločili saj se nam je zdela zelo zanimiva za ugotvljanje trenodov, kakšne avtomobile slovenci kupujejo, ter druge lastnosti o posameznikovi izbiri avtomobila.

Druga pomembna lastnost podatkov, katera je pomagala da smo se odločili ravno za to množico, je bila da je množica dovolj velika za naše opazovanje. Našli smo veliko drugih podatkov kateri bi bolj ustrezali naši stroki, kot na primer; različna uporaba interneta v slovenskih gospodnistvih, vendar so bile take množice zelo majhne. Pri tako majhni količini podatkov bi bili zagotovo omejeni glede raziskave.

## Manjšanje množice podatkov ##

Ko smo, po skupni odločitvi in izberi podatkov prvič prenesli podatke iz spletne strani smo naleteli na zelo veliko težavo. Kot smo že prej napisali smo izbrali to podatkovno množico, ker je bila tako velika. Vendar se je to sedaj izkazalo da je podatvko preprosto preveč. Preveč jih je bilo za na git ter preveč za naše raziskovanje.

Iz celotne podatkovne množice, smo se nato odločili da vzamemo samo tri leta.
* 2015
* 2016
* 2017

pri vsakem letu smo vzeli vseh 12 mesecev.

## Problem encodinga ##

Ker so podatki iz spletne strani, so seveda vmes med imeni atributov in njihovimi vrednostmi, katere bomo opisali kasneje), najdejo tudi šumniki.

Ko smo prenesli in zreducirali našo množico, samo ugotovili da veliko šumnikov nas jupyter notebook neprepozna, in zato prikaže čudne znake. Zato smo si zadali da to nekako popravimo. To bi nam pomagalo pri izbiranu vrednsoti iz množice (šumnik nebi bilo mogoče izbrati saj "š" znak ni "š" znak ampak neko drugi znak). Pomagali bi nam pa tudi pri reprezentaciji imen atributov na grafih.

Po dolgem raziskovanju kateri encoding uporabiti smo se odločili da ta problem in pomankljivost naše množice zanemarimo. Prej naštet problem izbiranja določenih vrstic, je bil rešen z uporabo idjev katere smo prenesli zravn naših podatkov. Uporabili smo samo encoding 'latin1' kateri prikaže samo določene šumnike.

Kot primer uporabe idjev:

Stoplce "barva vozila" vsebuje vrednost Črna, katera se v našem primeru izpiše pravilno. Zato je bil zraven stoplce "barva vozila" dodan tudi stoplev "id barve vozila". Ta nam omogoča da v excel tabeli najdemo črno barvo in nato preko poizvedne po stoplcu z idji barve izberemo vse tiste vrstice oz. avtomobile katerega barva je črna.

## Branje podatkov ##

Množica podatkov, katero smo prenesli iz spletne strani je bila v obliki csv datotek, kar nam je mogočalo branje le teh z uporabo csv readerja v napih jupyter notebookih. Iz vseh stolpcev smo izbrali samo določene stoplce saj, nas drugi preprosto niso zanimali pri naših raziskavah.

* Datum prve registracije, kjerkoli in nato še samo v SLO
* Status vozila
* Izvajalna enota prve registracije
* Starost uporabnika vozila
* Ali je uporabnik pravna ali fizicna oseba
* Spol uporabnika
* Upravna enota
* Občina
* Starost lastnika vozila
* Znakma, barva, teža vozila
* Vrsta goriva
* Število sedežev
* Dolžina, širina in višina
* Leto izdelave

Primer branje datoteke.
```python
df1501 = pd.read_csv("../data/2015/Podatki_012015.csv", encoding='latin1', sep=';', usecols=stolpci, dtype=tipi)
#                    1.                                 2.                 3.       4.               5.
```
1. pot do datoteke
2. encoding ki delno "razume" šumnike
3. nastavitev razdelilnika na ';'
4. izbira samo določenih stoplev
5. določanje podatkovnega tipa stolpcev

## Opis atrbutov in vrednosti ##

## Grafi ##
