- De graph wordt gepubliceerd in de dataset `rce/Rijksmonumenten-sdo`, zodat deze beschikbaar is voor het termennetwerk.

## Bestanden

| Bestand                        | Omschrijving                                  |
|-------------------------------|-----------------------------------------------|
| `.github/workflows/schemaorg-pipeline.yml` | GitHub Actions workflow                      |
| `pipeline-rm-sdo.json`        | Pipeline-configuratie voor TriplyDB           |

## Secrets

De workflow maakt gebruik van een beveiligd TriplyDB-token via GitHub Secrets.

### Vereist secret:

| Naam             | Omschrijving                     |
|------------------|----------------------------------|
| `TRIPLYDB_TOKEN` | API-token met schrijfrechten op datasets |

Toevoegen via:  
**GitHub repo > Settings > Secrets and variables > Actions > New secret**

## Uitvoeren

- Automatisch: dagelijks om 03:00 's nachts.
- Handmatig: via de **Actions**-tab in GitHub → **Run workflow**

## Voorwaarden

- De construct-query moet beschikbaar zijn als `rce/Rijksmonumenten-sdo-construct` (versie 6) in TriplyDB.
- De graph URI en datasetnamen zijn hardcoded in `pipeline-rm-sdo.json`.

## Onderhoud

- Om queryversies bij te werken: pas `version` aan in `pipeline-rm-sdo.json`.
- Om ander gedrag te automatiseren (bijv. sync van services): breid de workflow uit met een `curl` POST naar de gewenste Triply service endpoint.
