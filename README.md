
- De output komt in de dataset `rce/Rijksmonumenten-sdo`.
- De Triply-services `virtuoso` en `jena` worden automatisch gesynchroniseerd zodat het termennetwerk bijgewerkt is.

## Bestandsoverzicht

| Bestand                                | Functie                                                   |
|----------------------------------------|------------------------------------------------------------|
| `.github/workflows/schemaorg-pipeline.yml` | GitHub Actions workflow die alles uitvoert                |
| `pipeline-rm-sdo.json`                 | Configuratiebestand voor de TriplyDB pipeline             |
| `triplydb.exe`                         | Wordt automatisch gedownload tijdens de workflow          |

## Secrets

De workflow gebruikt een TriplyDB-token die als GitHub Secret is opgeslagen.

| Secret             | Omschrijving                                  |
|--------------------|-----------------------------------------------|
| `TRIPLYDB_TOKEN`   | Persoonlijke Triply API-token met toegang tot `rce` datasets |

Toevoegen via:  
**Settings > Secrets and variables > Actions > New repository secret**

## Hoe voert u dit uit?

### Automatisch

- De workflow draait elke dag automatisch om **03:00 UTC** via een cronjob.

### Handmatig

1. Ga naar de **Actions-tab** in deze repository.
2. Klik op **"Draai schema.org pipeline"**.
3. Klik op **"Run workflow"** om de actie handmatig te starten.

## Geen Python of dependencies vereist

- Er is **geen `requirements.txt`** of `pip install` nodig.
- De Triply CLI (`triplydb.exe`) wordt automatisch gedownload tijdens de workflow.
- Alles draait zelfstandig op de GitHub Windows-runner.

## Onderhoud

- Om een nieuwe versie van de construct-query te gebruiken, wijzig het versienummer in `pipeline-rm-sdo.json`.
- U kunt extra services toevoegen aan de sync-stap door het workflowbestand uit te breiden.
