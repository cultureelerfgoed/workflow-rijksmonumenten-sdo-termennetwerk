# Rijksmonumenten in schema.org voor het Termennetwerk

Deze workflow zet rijksmonumentendata uit de Linked Data Voorziening
van de Rijksdienst voor het Cultureel Erfgoed (RCE) om naar schema.org.
De uitvoer komt in een afzonderlijke TriplyDB-dataset voor het Termennetwerk.

Na de pipeline vraagt de workflow synchronisatie aan van de
Elasticsearch- en Jena-services van de doeldataset.

## Gegevensverwerking

| Onderdeel | Waarde |
|---|---|
| Brondata | `rce/cho` |
| Opgeslagen query | `rce/Rijksmonumenten-sdo-construct` |
| Queryversie | `7` |
| Doeldataset | `rce/Rijksmonumenten-sdo` |
| Doelgraaf | `https://linkeddata.cultureelerfgoed.nl/graph/rijksmonumenten-sdo` |
| Elasticsearch-service | `Rijksmonumenten-sdo-elas` |
| Jena-service | `Rijksmonumenten-sdo-jena` |

De workflow gebruikt het platform:
https://api.linkeddata.cultureelerfgoed.nl

## Uitvoeren

### Automatisch

De workflow staat dagelijks gepland om 03:00 UTC.
Dat is 04:00 uur in de Nederlandse wintertijd en 05:00 uur in de zomertijd.

### Handmatig

1. Open de tab **Actions**.
2. Kies **Draai schema.org pipeline**.
3. Klik op **Run workflow**.

## Configuratie

Stel het repositorysecret `TRIPLYDB_TOKEN` in met het API-token
van Triply-gebruiker `RCEBot`.

Je vindt dit onder:
**Settings > Secrets and variables > Actions > New repository secret**.

Het token moet toegang hebben tot de benodigde datasets en query,
en de publicatieservices kunnen laten synchroniseren.

De services `Rijksmonumenten-sdo-elas` en `Rijksmonumenten-sdo-jena`
moeten in de doeldataset bestaan.

## Bestanden

| Bestand | Functie |
|---|---|
| `.github/workflows/schemaorg-pipeline.yml` | Planning, uitvoering en synchronisatieverzoeken |
| `pipeline-rm-sdo.json` | Bron, doel, doelgraaf en queryversie |
| `LICENSE` | Licentietekst van deze repository |

De workflow draait op een Windows-runner en downloadt bij iedere
uitvoering de TriplyDB CLI als `triplydb.exe`.

## Controle na uitvoering

Bekijk de uitvoer van de workflow in **Actions**.
Controleer bij problemen welke stap faalt: het downloaden van de CLI,
de pipeline of het aanvragen van de servicesynchronisatie.

De workflow verstuurt synchronisatieverzoeken, maar bevat geen
vervolgcontrole die wacht totdat beide services klaar zijn.

## Beheer

Pas de queryversie en datasetinstellingen aan in `pipeline-rm-sdo.json`.
Werk deze README bij wanneer die instellingen veranderen.

## Licentie

Deze repository bevat een CC0-1.0-licentie. Raadpleeg `LICENSE`.
Controleer de gebruiksvoorwaarden van de brondata afzonderlijk.
