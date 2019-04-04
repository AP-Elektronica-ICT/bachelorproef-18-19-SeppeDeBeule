# Voortgangsverslag #2
# Monitoring Framework op MECOMS 365
## Promotors

**Stagecoördinator:**  Marc Smets (marc.smets@ap.be)  
**Stagementor:**  Jurgen Beyens (jurgen.beyens@mecoms.com)  
**Stagebegeleider:** Serge Horsmans  (serge.horsmans@ap.be)  
**Opleidingshoofd:**  Yves Masset (yves.masset@ap.be)  

<!--Zet hier alle namen+email van je verschillende promotors (stagebegeleider, stagementor). Zeker in vet zetten indien er veranderingen hebben plaatsgevonden-->

## Abstract
<!--Het abstract is een samenvatting van je totale bachelorproef, inclusief reeds gekende resultaten-->
Het Monitoring Framework op MECOMS 365 is een upgrade van het voormalige systeem op Microsoft AX.
Dit draait op de cloud-gebaseerde Dynamics 365 en werkt bijgevolg met een aparte client, geschreven in het .NET framework.
Deze client kan via het OData protocol een query sturen naar de Dynamics cloud - waarin alle data zich bevindt - om een check uit te voeren.

## Technische omschrijving

<!--Technische omschrijving van de evolutie van het project tijdens de betrokken periode, met aanduiding van de reeds bekomen resultaten en een planning voor de verdere uitwerking, welke problemen zijn ondervonden en hun oplossingen:-->
<!--Minimum 750 woorden-->

### Realisaties 

De eerste twee weken waren vooral toegewijd aan het oriënteren in de voormalige situatie.  
Met *Microsoft SQL Server Management Studio 17* kunnen alle databanken, tabellen en queries worden bekeken en zo is het
mogelijk om vat te krijgen hoe de structuur in elkaar zat.

Na deze verkenning is er een schema gemaakt van hoe de structuur van de upgrade mogelijk in elkaar kon zitten. Deze
was voorgesteld aan Jorgen & Ian (*zie nieuwe contacten onderaan*). Mits wat feedback ben ik verder gegaan op deze oplossing.

Dan kon het opzetten van de nieuwe omgeving van start. Er moest een Virtual Machine opgezet worden voor het runnen van
Dynamics 365. Hiervoor werd Microsoft Azure gebruikt omdat Ferranti hier veel credit ter beschikking heeft door hun samenwerking
met Microsoft.

Bij het developen van de client is er voor het .NET framework gekozen. De reden hierachter is dat er veel packages
beschikbaar zijn voor de communicatie met de Dynamics cloud. Een goed voorbeeld hiervan is OData.

Dit brengt ons bij de volgende keuze die gemaakt moest worden; de manier van communiceren. Al snel bleven er twee
opties over: 
* [BYODB (Bring Your Own Database)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/analytics/export-entities-to-your-own-database)
* [OData](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/data-entities/odata)
 
BYODB houdt in dat er een SQL tabel van de data uit Dynamics tijdelijk wordt ge-exporteerd naar de client om daar 
bijvoorbeeld een check op uit te voeren. Het grote probleem hiermee is dat er in dit project tabellen van miljoenen rijen
voorkomen en dat dit performance-gewijs niet haalbaar is. OData daartegen werkt op de omgekeerde manier. Er kan een opdracht
of query naar de Dynamics cloud worden gestuurd om dan daar iets uit te voeren. Dit is veel efficiënter maar helaas iets
uitdagender in gebruik. De uiteindelijke keuze is dan ook naar OData gegaan.

Allereerst kwam ik op [deze GitHub repo](https://github.com/Microsoft/Dynamics-AX-Integration/tree/master/ServiceSamples/ODataConsoleApplication).
Deze had enkele voorbeelden van een toepassing met OData. Deze voorbeelden maakten gebruik van een ODataClient add-on die al snel
niet geschikt bleek te zijn voor onze toepassing. Er wordt namelijk een ODataClient.tt bestand lokaal aangemaakt. Dat bestand dient
als "register" voor alle packages in Dynamics 365, maar dat zijn er in onze situatie zodanig veel dat de client niet meer wilde runnen.

Vervolgens zijn we op [Simple.OData.Client](https://github.com/simple-odata-client/Simple.OData.Client) uitgekomen. Deze was
meer geschikt en bovendien gemakkelijker in gebruik.

Samen met OData wordt er gebruik gemaakt van AAD authenticatie. Deze connectie is reeds succesvol tussen de client en de 
Dynamics cloud.

![Screenshot_15](images/Screenshot_15.png "Screenshot_15")

<!--Kort oplijsting gedane werk zowel onderzoek, analyse als realisaties.-->

### Huidige werkpunten

Op maandag 18 maart was er een feedbackmoment met de stagebegeleider & stagementor via Skype. Hierbij zijn er 
enkele werkpunten aan het licht gekomen waar vanaf die dag aan is gewerkt.  
Het grootste werkpunt dat aan bod kwam was het feit dat er meer proactief werk werd verwacht. Hiermee wordt bedoeld
dat er sneller om hulp moet worden gevraagd als er een probleem is. Initieel werd er soms een dag verspeeld als iets
niet wil werken. Nu wordt er sneller iemand geraadpleegd.

Bovendien was dit feedbackmoment nog iets te vroeg in de gehele stageperiode aangezien de stage zo'n twee weken later is begonnen
vergeleken met de normale startdatum. Voeg hier bovenop de gigantische oriëntatie en setup van dit project bij en tijdens
dat feedbackmoment was er nog niet veel gerealiseerd om op te reflecteren.

Een positief punt aan de feedback was het feit dat er veel werd gedocumenteerd. Er zijn vele screenshots genomen,
niet alleen voor het troubleshooten maar ook voor het verslaggeven.
<!--Beschrijven wat de huide focus punten zijn zodat er progressie is in de BAP/Stage-->

### Toekomst

Op het moment van dit voortgangsverslag moeten de essentiële checks en functies worden "vertaald" naar de Dynamics
oplossing. Dit zal hopelijk klaar zijn tegen het einde van de eerste twee sprints op vrijdag 12 april. 

Tijdens het feedbackmoment is er ook aangeraden geweest om de sprint planning anders in te delen. De initiële zes
sprints waren te ambitieus. Momenteel zijn de eerste twee sprints bij elkaar gevoegd en de laatste twee (die als bonus werden
beschouwd) voorlopig uit de planning gehaald. Ondanks dat ze er uit zijn gehaald zou het zeer interessant zijn moest er minstens
een user interface, of toch een basisversie er van al gemaakt zijn tegen het einde van de stageperiode eind mei.

Dit is de huidige sprint planning:

![Screenshot_16](images/Screenshot_16.png "Screenshot_16")

**Sprint 1 & 2 (18/03/2019 - 12/04/2019)**
Het bestaande framework omzetten naar de Dynamics oplossing, zorgen dat er checks kunnen uitgevoerd worden op deze nieuwe manier.  
Zorgen dat het framework op version-control kan checken. Eerst zien of een nieuwe versie in een test-environment werk voordat die in productie gaat.

**Sprint 3 (15/04/2019 - 03/05/2019)**
Een configureerbare planning voor de checks (instellen van hun frequentie, etc.)

**Sprint 4 (06/05/2019 - 27/05/2019)**
Het framework moet self-healing werken. Het kan gekende issues na een check automatisch oplossen.

<!--Mogelijk richting naar waar de BAP/Stage kan evolueren in de toekomst-->

## Extra informatie

### Bijscholingen
<!--Bijgewoonde seminaries, presentaties, workshops, bedrijfsbezoeken etc in deze periode (onderwerp, datum, korte samenvatting en beoordeling)-->

### Nieuwe contacten
Naast mijn stagementor zijn er ook drie personen die me altijd bijstaan en die geraadpleegd kunnen worden.  
* Jorgen Bosman (Jorgen.Bosman@mecoms.com) +32 3 540 49 93 | Solution Architect bij MECOMS
* Ian Bruyninckx (Ian.Bruyninckx@mecoms.com) +32 3 545 78 05 | Product Architect bij MECOMS
* Thomas De Witte (Thomas.DW@mecoms.com) +32 3 543 67 53 | Training Consultant bij MECOMS
<!--Nieuwe contacten gemaakt in deze periode (naam, voornaam, e-mail, telefoonnummer, bedrijf, functie, relevantie voor het werk)-->

### Literatuur
<!--Nieuwe contacten gemaakt in deze periode (naam, voornaam, e-mail, telefoonnummer, bedrijf, functie, relevantie voor het onderzoek)-->
