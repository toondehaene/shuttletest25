# Shuttle test 2025

## Problemen vorig jaar
De shuttletests van vorig jaar waren een beetje rushed. Het centrale probleem was dat de statistische test enkel significant konden aantonen dat 1 van de 4 categorieen beter was.

**Oorzaken:**
* Te veel type shuttles
* Veel ruis op de data omdat er geen rekening wordt gehouden met in welke staat de laatste shuttle in gebruik was op het einde van de wedstrijd.
* Per match werd de shuttelduurzaamheid berekend als #punten_gespeeld/#shuttles_gebruikt. Dit betekende dat een match waar 3 shuttles worden gebruikt voor 30 punten equivalent was aan een match waar 1 shuttle gebruikt werd voor 10 punten. Echter is de statistische variatie op de 'sample' met 30 punten veel kleiner dan de sample met 10 punten.
* Shuttles censureren was te veel moeite

**Oplossingen**:
* We zouden 3 type shuttles testen
* Half gebruikte shuttles worden meteen in de volgende match gebruikt (dit geeft nog steeds ruis per match maar in de som komt het dan goed)
* Een regressiemodel met gewogen samples wordt gebruikt om meer belang te hechten aan matchen met meer punten/shuttles gespeeld.
* Shuttles worden niet gecensureerd

## Procedure in het kort
//TODO

## Procedure in het lang

### Halfgebruikte shuttles moeten in rotatie blijven:
Praktisch: De shuttle wordt op het veld gelaten. Een shuttle van type A mag niet gebruikt worden in een volgende match waar er ook met type B gespeeld wordt (statistiek kapot dan). Daarom zal op een gegeven veld altijd met dezelfde shuttle gespeeld worden (# velden is deelbaar door 3 gelukkig).

### Spelers vullen data in:
Zoals reeds gezegd moet elke shuttle die op een veld gestart wordt op dat veld blijven tot deze kapot is. Spelers vullen op het einde van elke wedstrijd volgend formulier in:

-------------------
| **FORMULIER** ||
|-----------------|------------|
| Type shuttle: | [ ] A  [x] B  [ ] C |
| Aantal punten gespeeld: Tel zelf op (bv 71) of schrijf de individuele scores op (bv 21 10 21 18) | 13 21 21 23 |
| Aantal shuttles helemaal kapot: | 2 |
-------------------

En steken die papiertje vervolgens in een doos die bij het veld staat.
Om duidelijk te maken dat een shuttle halfgebruikt is en nog in de volgende match gebruikt moet worden, zal er een papier/mandje zijn per veld waar de shutle in geplaatst kan worden.

### Speler bias
Spelers worden aangemoedigd om actief alle types shuttles op te zoeken en niet met 1 soort te spelen.


## Technische implementatie

### Python script uitleg

### Excel en Google Forms integratie