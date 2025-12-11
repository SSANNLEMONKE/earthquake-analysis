#  Data Visualization Project – Earthquake Risk Analysis

Dit project onderzoekt de relatie tussen **aardbevingen**, **tektonische plaatgrenzen** en **bevolkingsrisico**.  
Met behulp van **PySpark** en **Folium** werd een uitgebreide analyse gemaakt van wereldwijde seismische activiteit, waarbij de nadruk ligt op:

- Waar zware aardbevingen het vaakst voorkomen  
- Hoe dicht deze aardbevingen bij tektonische plaatgrenzen liggen  
- Welke landen het grootste risico lopen op menselijke impact op basis van populatie en nabijgelegen seismische activiteit  

---

## **Doel van het project**

Het doel van dit project is na te gaan of:

1. **Zware aardbevingen** (Magnitude ≥ 6.5) voornamelijk voorkomen in de buurt van tektonische plaatgrenzen.  
2. **Dichtbevolkte landen** in deze actieve regio’s daardoor een **hoger risico** lopen op grote menselijke impact.

---

## **Hypothese**

**“Aardbevingen dichter bij de grenzen van tektonische platen hebben gemiddeld een hogere magnitude en komen vaker voor.  
Wanneer deze gebeurtenissen plaatsvinden in dichtbevolkte regio’s, stijgt het risico op menselijke impact aanzienlijk.”**

---

## **Gebruikte technologieën**

- **PySpark** — dataverwerking zonder Pandas  
- **Folium** — interactieve wereldkaarten  
- **Haversine-formule** — berekening van geografische afstand  
- **Spark DataFrames** — filtering, grouping, aggregations  
- **JSON / Python dicts** — opslag van risicoresultaten  

---

## **Datasets**

1. **Aardbevingen**  
   - Bron: ISC-GEM database  
   - Kolommen: Datum, Tijd, Magnitude, Locatie, Diepte, enz.

2. **Tektonische plaatgrenzen**  
   - Coördinaten per plaatsegment (`plate`, `lat`, `lon`)

3. **Bevolkingscijfers per land (2020)**  
   - Kolommen: Land, Populatie, Urban %, Density, enz.

---

## **Visualisaties**

### 1. **Kaart met sterke aardbevingen**
- Rode markers = aardbevingen binnen 100 km van een plaatgrens  
- Blauwe markers = aardbevingen ver van platen  
- Interactieve pop-ups met magnitude en diepte  
- We tonen alleen Magnitude ≥ 6.5  

### 2. **Kaart met tektonische platen + aardbevingen**
- Alle plaatgrenzen geplot met Folium PolyLines  
- Overlap met aardbevingsclusters maakt het patroon duidelijk zichtbaar  


## **Belangrijkste bevindingen**

- Het merendeel van de zware aardbevingen bevindt zich **langs plaatgrenzen**, wat de geologische verwachting bevestigt.  
- Landen als **Japan, Indonesië, Mexico, de Filipijnen en de VS (westkust)** hebben een **hoge risicoscore** doordat zij zowel veel seismische activiteit als een grote bevolking combineren.  
- Grote landen met weinig seismische activiteit (**Duitsland, Nigeria, Frankrijk, Rusland**) scoren laag ondanks een hoge populatie.  
- Bevolking op zichzelf voorspelt géén risico — de combinatie **"plaatactiviteit × bevolkingsdichtheid"** wel.

---

## **Moeilijkheden tijdens het project**

- Veel ontbrekende waarden in de aardbevingsdataset  
- Geen gebruik van Pandas → volledige dataverwerking in Spark  
- Spark ondersteunt geen geospatiale functies → Haversine zelf implementeren  
- Folium werkt niet direct met Spark DataFrames → data moest eerst `collect()` worden  
- Afwegen tussen performance en nauwkeurigheid door sample-gebaseerde benaderingen  
- Geen polygondata beschikbaar → landen benaderd via geografisch middelpunt  
- Visuele balans vinden tussen overlappende lagen en informatieve kaarten  

---

## **Conclusie**

Het project bevestigt de hypothese:  
- **Zware aardbevingen clusteren langs tektonische plaatgrenzen**, niet willekeurig verdeeld.  
- **Dichtbevolkte landen in deze zones hebben een significant hoger risico op menselijke impact.**

De combinatie van geologische data, Spark-verwerking en Folium-visualisatie geeft een duidelijk inzicht in waar op aarde de grootste risicozones liggen.

---

## Auteur

Benjamin Vercauteren  
AP Hogeschool – Data Visualization Project  
2025