## 4.1 Gezichtsherkenningssoftware en Demografische Ongelijkheden

### Casestudy: Falen bij het Herkennen van Niet-Witte Gezichten

- Gezichtsherkenningssystemen (bijv. Microsoft, IBM, Amazon) tonen aanzienlijke foutmarges bij mensen met een donkere huid, vooral vrouwen.
- Voorbeeld: Onderzoeker Joy Buolamwini’s gezicht werd alleen herkend toen ze een wit masker droeg.
- Hooggeplaatste misidentificaties: Michelle Obama werd als man aangeduid, burgerrechtenactiviste Ida B. Wells werd verkeerd gegenderd.

### Oorzaken van Ongelijkheden in Herkenningsnauwkeurigheid

- **Vooroordelen in trainingsdata**: Databases bevatten overwegend witte mannelijke gezichten vanwege oververtegenwoordiging in media en technologie.
- **Gebrek aan diversiteit in ontwikkelingsteams**: Homogene teams kunnen randgevallen die minderheidsgroepen treffen over het hoofd zien.

### Gevolgen in de Praktijk

- Gebruik door de politie in de VS en Europa (bijv. Londen, Brussel) leidt tot onterechte arrestaties van mensen met een donkere huid.
- Beveiligingssystemen op luchthavens en tools voor telefoonontgrendeling werken onbetrouwbaar voor niet-witte gebruikers.

## 4.2 Algoritmische Discriminatie Buiten Gezichtsherkenning

### Proxyvariabelen bij Kredietscores

- De Apple-kredietkaart uit 2019 kende lagere limieten toe aan vrouwen, ondanks genderneutrale algoritmen.
- **Proxydiscriminatie**: Winkelgewoonten (bijv. aankoop van make-up) werden indirect gebruikt om geslacht te bepalen.
- Postcode- of buurtgegevens kunnen als proxy voor ras fungeren, wat indirecte vooroordelen mogelijk maakt.

### Taalmodellen en Sociale Vooroordelen

- Microsoft’s Twitter-bot “Tay” nam racistische taal over na interacties met gebruikers.
- Google-zoekvoorstellen in 2016 koppelden “Jood” aan gierigheid en “Islam” aan terrorisme, wat maatschappelijke vooroordelen weerspiegelde.

### Tools voor Werkselectie

- AI-tools voor werving, getraind op historische gegevens, bevoordelen mannelijke kandidaten als eerdere aanwervingen voornamelijk mannelijk waren.
- Voorbeeld: Amazon’s geschrapte aanwervingsalgoritme benadeelde cv’s waarin het woord “vrouwen” voorkwam.

## 4.3 Ethische en Juridische Uitdagingen in AI-ontwikkeling

### Het “Black Box”-Probleem

- Deep learning-systemen missen transparantie, waardoor het moeilijk is discriminerende beslissingen te traceren.
- Ontwikkelaars coderen vooroordelen mogelijk niet opzettelijk, maar niet-representatieve data versterken ongelijkheden.

### Juridische Kaders en Verantwoordelijkheid

- Antidiscriminatiewetten (bijv. EU-regelgeving) verbieden expliciet gebruik van ras/geslacht in besluitvorming.
- **Handhavingsproblemen**: Proxy’s en ondoorzichtige algoritmen bemoeilijken juridische aansprakelijkheid.

## 4.4 Het Verminderen van Vooroordelen in AI-systemen

### Technische Oplossingen

- **Diverse trainingsdata**: Neem ondervertegenwoordigde groepen op (bijv. mensen met een donkere huid, vrouwen).
- **Tests voor implementatie**: Evalueer prestaties over demografische categorieën (ras, geslacht, leeftijd).
- **Verklaarbare AI (XAI)**: Ontwikkel tools om besluitvormingsprocessen te interpreteren.

### Organisatorische en Regulerende Maatregelen

- **Diverse ontwikkelingsteams**: Betrek stemmen van gemarginaliseerde gemeenschappen in de ontwerpfase.
- **EU-ethische richtlijnen**: Bevorder transparantie, verantwoording en menselijke supervisie.
- **Verplichte effectbeoordelingen**: Vereis audits voor vooroordelen in toepassingen met grote impact (bijv. politie, werving).

## 4.5 Maatschappelijke Verantwoordelijkheid en Toekomstige Richtingen

### AI Afstemmen op Ethische Normen

- AI moet aspiraties van de maatschappij weerspiegelen, niet bestaande vooroordelen repliceren.
- Voorbeeld: Een “perfect” wervingsalgoritme kan discriminatie op de werkvloer na aanwerving niet oplossen.

### Beleidsaanbevelingen

- **Transparantiemandaten**: Maak gegevensbronnen, doelstellingen en testprotocollen openbaar.
- **Mens-in-de-lus-systemen**: Zorg ervoor dat eindbeslissingen (bijv. arrestaties, leningen) door mensen worden beoordeeld.

# 4 Key Points to Remember

- **Vooroordelen in gezichtsherkenning**: Foutmarges zijn het hoogst voor vrouwen met een donkere huid door niet-representatieve trainingsdata.
- **Proxydiscriminatie**: Algoritmen gebruiken correlaties (bijv. winkelgedrag, postcodes) om indirect beschermde groepen te targeten.
- **Beperkingen van de black box**: Deep learning-systemen missen transparantie, wat detectie van vooroordelen bemoeilijkt.
- **Strategieën voor vermindering**: Diverse datasets, demografische tests en regulerende supervisie zijn cruciaal.
- **Juridische aansprakelijkheid**: Bestaande antidiscriminatiewetten moeten worden aangepast aan algoritmische vooroordelen.
- **Maatschappelijke impact**: AI weerspiegelt en versterkt menselijke vooroordelen; ethisch ontwerp vereist bewuste inclusiviteit.
