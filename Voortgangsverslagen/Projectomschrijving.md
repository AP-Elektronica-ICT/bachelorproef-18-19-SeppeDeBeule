# Opdrachtomschrijving

Monitoring framework op MECOMS 365

# Bachelor Elektronica-ICT
academiejaar 2018-2019
jaar 3 semester 2

 # Seppe De Beule
 
## Opdrachtomschrijving

### 1	Opdrachtgever

Jurgen Beyens van MECOMS, a Ferranti company

### 2	Samenvatting

MECOMS is een standaard ERP pakket voor nutsbedrijven (elektriciteit, gas, water,..) en is
door Ferranti gebouwd bovenop het standaard ERP pakket Microsoft Dynamics. Naar dat
MECOMS pakket is een monitoring framework gemaakt voor het monitoren van dit business
process.

Het bestaande monitoring framework, gebaseerd op Microsoft SQL en AX2012 moet
geconverteerd worden naar een werkende oplossing in Microsoft Dynamics 365. Het
bestaande framework moet een technologische upgrade ondergaan: het moet gekoppeld
worden met MECOMS 356 en moet in staat zijn om bij onverwachte gebeurtenissen alerts te
maken via SMS, email, telefoon, ..

Bovendien moet het ook in staat zijn om “self-healing” te werken bij gekende issues.
Als er tijd over is kan er naast het framework een app gemaakt worden waarmee je de
actuele status kan monitoren aan de hand van logging en rapportage & waarmee alerts
kunnen worden verstuurd en opgevolgd.

### 3	Situatie As-Is

Het huidige framework is al operationeel en werkt indien fouten/issues optreden. Het heeft
nog wel beperkte UI functionaliteit en is gebaseerd op AX 2012, dat door Microsoft
vervangen gaat worden door een cloud-based oplossing Dynamics 365. Alle servers zijn nu
lokaal, zonder cloud-based oplossing waardoor access rights en connecties tussen de SQL
en MECOMS zelf eenvoudig te regelen zijn, wat niet meer het geval zal zijn de cloud.

### 4	Situatie To-Be
### Projectdefinitie
#### 4.1	Doelstelling

Het framework moet in MECOMS Microsoft Dynamics 365 werken.
Hiervoor zal een oplossing bedacht moeten worden om
geconnecteerd te kunnen zijn met MECOMS die als cloud oplossing
zal draaien. Het moet monitoring acties kunnen uitvoeren en alerts
maken in geval van onverwachte events en bovendien bij gekende
issues moet het self-healing werken.
Voor dit framework moet ook een montoring app gemaakt worden
waarbij de gebruiker de actuele status kan opvolgen aan de hand van
loggin en rapportage. Hierop moet ook een analyse gemaakt kunnen
worden op trends.

#### 4.2	Scope

**Technologie-upgrade van het monitoring framework**  
* Een gedetailleerde analyse van de “As-Is functionaliteit” (functioneel &
technisch)  
* Een gedetailleerde analyse van de “To-Be oplossing” voor de
technologie-upgrade voor de bestaande functionaliteit (functioneel &
technisch)  
* Voorstelling van de oplossing v oor de technologie-upgrade aan het
MECOMS product development team.  
* Implementatie van de “To-Be oplossing” na goedkeuring van de
development, unit- & process testing teams.  
**Eventuele mobiele monitoring app**  
* Een gedetailleerde analyse van de functionaliteit (functioneel &
technisch)  
* Voorstelling van de oplossing aan het MECOMS product development
team  
* Implementatie van de mobiele monitoring app: technisch design,
development, unit & process testing.  

#### 4.3	Niet in Scope

Ferranti kan de implementatie-impact van de technologie-upgrade nog
niet goed inschatten en er zal tijdens het stagetraject nog verder
bepaald worden in welk detail de mobile monitoring app
geïmplementeerd zal worden aan de hand van de beschikbare tijd.

### 5	Planning
#### 5.1	Hoofdlijnen
De volledige development cyclus gaat worden doorlopen: functionele
& technische analyse, development, unit testing & process testing.
#### 5.2	Toelichting fases
* Functionele & technische analyse van “As-Is functionaliteit”  
* Functionele & technische analyse van “To-Be oplossing”  
* Voorstelling van de oplossing voor het MECOMS development team.  
* Agile implementatietraject in sprints van de goedgekeurde oplossing.  

### 6	Functioneel design

* Technologie-conversie van de bestaande functionaliteit  
* De monitoring app is de grootste feature (indien deze ook degelijk gaat gemaakt  
worden) aangezien deze vaak gaat geraadpleegd worden door de gebruiker. Hiermee  
kan je verschillende zaken nakijken:  
  * Het bekijken van de actuele status van het systeem.  
  * Het opvolgen van dringende- en niet dringende alerts.  
  * Bevatten van de logging en rapportage om de performance van het systeem op te volgen.  
  * Een analyse moet kunnen worden gemaakt mbv. Trends.  
  * Versturen en opvolgen van alerts  

### 7	 Technisch design

Het maken van het technische design en niet-functionele eisen maakt ook deel uit van
de stageopdracht.

### 8	Beschrijving van eventuele impact op de huidige infrastructuur

* De opdracht is het beschrijven en implementeren van de impact door een architectuur
en infrastructuur wijziging.  
* Er dient inderdaad Cloud-based storage gebruikt te worden voor de “upgrade” van dit
project.
