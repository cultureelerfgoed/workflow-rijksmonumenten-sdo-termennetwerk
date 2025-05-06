
- De data komt terecht in de dataset `rce/Rijksmonumenten-sdo`.
- Na afloop worden automatisch de publicatieservices gesynchroniseerd:
- Virtuoso: `Rijksmonumenten-sdo`
- Jena: `Rijksmonumenten-sdo-jena`

## Bestandsoverzicht

| Bestand                                | Functie                                                   |
|----------------------------------------|------------------------------------------------------------|
| `.github/workflows/schemaorg-pipeline.yml` | GitHub Actions workflowbestand                          |
| `pipeline-rm-sdo.json`                 | Configuratiebestand voor de TriplyDB pipeline             |
| `triplydb.exe`                         | Wordt automatisch gedownload tijdens de workflow          |

## Secrets

| Secret             | Omschrijving                                  |
|--------------------|-----------------------------------------------|
| `TRIPLYDB_TOKEN`   | API-token van Triply-gebruiker `RCEBot`       |

Instellen via:  
**Settings > Secrets and variables > Actions > New repository secret**

## Uitvoeren

### Automatisch

- Draait elke nacht om 03:00 UTC via cron.

### Handmatig

1. Ga naar de **Actions-tab** in deze repository.
2. Kies de workflow "Draai schema.org pipeline".
3. Klik op **Run workflow**.

## Opmerkingen

- De CLI gebruikt geen `--account`, het juiste contextaccount wordt automatisch bepaald via de token.
- Platform:  
[https://api.linkeddata.cultureelerfgoed.nl](https://api.linkeddata.cultureelerfgoed.nl)

## Beheer

- De query wordt uitgevoerd: `rce/Rijksmonumenten-sdo-construct`, versie 6.
- De brondata staat in `rce/cho`
- De services `Rijksmonumenten-sdo` (Virtuoso) en `Rijksmonumenten-sdo-jena` (Jena) moeten bestaan en bereikbaar zijn.

