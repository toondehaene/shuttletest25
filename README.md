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
* Shuttle

## Procedure 

### Halfgebruikte shuttles moeten in rotatie blijven:
Praktisch: De shuttle wordt op het veld gelaten. Een shuttle van type A mag niet gebruikt worden in een volgende match waar er ook met type B gespeeld wordt (statistiek kapot dan). Daarom zal op een gegeven veld altijd met dezelfde shuttle gespeeld worden (# velden is deelbaar door 3 gelukkig).

### Spelers vullen data in:
Zoals reeds gezegd moet elke shuttle die op een veld gestart wordt op dat veld blijven tot deze kapot is. Spelers vullen op het einde van elke wedstrijd volgend formulier in:

-------------------
| **FORMULIER** | **ANTWOORDEN**|
|-----------------|------------|
| Type shuttle: | [ ] A  [x] B  [ ] C |
| Aantal punten gespeeld: Tel zelf op (bv 76) of schrijf de individuele scores op (bv 21 10 21 18) | 13 21 21 23 |
| Aantal shuttles helemaal kapot: | 2 |
-------------------

En steken die papiertje vervolgens in een doos die bij het veld staat.
Om duidelijk te maken dat een shuttle halfgebruikt is en nog in de volgende match gebruikt moet worden, zal er een papier/mandje zijn per veld waar de shutle in geplaatst kan worden.

### Speler bias
Spelers worden aangemoedigd om actief alle types shuttles op te zoeken en niet met 1 soort te spelen.

## Voorstel shuttles
[RSL Classic Tourney](https://www.badmintonplanet.be/rsl-classic-tourney-speed-78): heb ik mee in Denemarken gespeeld. Staat in Nederland in de hoogste categorie van goedgekeurde shuttles (zou dus gemakkelijk in Belgie er ook op komen, maar is dus momenteel niet).

[Stein P Grade 1](https://www.allrackets.com/en/webshop/winkel/stein-p-grade-1/): 
Stein P Grade 1: Wordt momenteel gebruikt door de Nero's. Staat nog lang op de lijst met goedgekeurde shuttles. Hun marketing is "*The Danish answer to the ever increasing shuttle prices.*"

[Forza VIP](): als ijking/ basis om mee te vergelijken


## <span style="color:red;">Open vragen:</span>


- Heeft de club momenteel enkel Forza VIP speed **78**? Zo ja dus ook speed 78 bestellen voor te testen shuttles. Zo niet overwegen om speed 77 (zomer snelheid) te kopen voor in mei op het clubtoernooi

## Technische implementatie

### Python script uitleg

In het script `script.ipynb` wordt een statistische analyse uitgevoerd om de duurzaamheid van shuttlecocks te vergelijken.

#### Wat het script doet:

1. **Gegevens maken**: 
   - Er worden testgegevens aangemaakt voor drie soorten shuttlecocks (A, B en C)
   - Voor elke shuttlecock wordt bijgehouden hoeveel punten ermee gespeeld zijn en hoeveel shuttles gebruikt zijn
   - De duurzaamheid wordt berekend als: gespeelde punten gedeeld door aantal gebruikte shuttles

2. **Realistische ruis toevoegen**:
   - Er wordt wat willekeurige variatie toegevoegd aan de metingen
   - Sommige wedstrijden gebruiken 1, 2 of 3 shuttles
   - Dit maakt de gegevens realistischer, zoals bij echte tests

3. **Statistische analyse**:
   - Een speciaal type regressiemodel (gewogen kleinste kwadraten) wordt gebruikt
   - Dit model houdt rekening met het feit dat metingen met meer gebruikte shuttles betrouwbaarder zijn
   - Het berekent de gemiddelde duurzaamheid voor elke categorie shuttlecock

4. **Resultaten bekijken**:
   - De duurzaamheid van elke shuttlecock wordt geprint
   - In de code is ingebouwd dat shuttle C het langst meegaat, gevolgd door B, en dan A
   - De resultaten worden geprint zodat we kunnen zien of de analyse dit patroon herkent

Dit script is de basis voor een hypothesetest die we later uitvoeren om te bepalen of de verschillen tussen shuttlecocks statistisch significant zijn, en of bijvoorbeeld shuttlecock C echt minstens 2 punten langer meegaat dan shuttlecock B.

### Excel en Google Forms integratie
Eventueel kan er een google form gemaakt worden zodat een groepje mensen acteraf gemakkelijk samen de resultaten van de papiertjes gezamelijk digitaal kan invullen.

