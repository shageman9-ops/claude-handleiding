# Workflow: {{ naam van de workflow }}

## Doel
<!-- Één zin: wat bereik je met deze workflow? -->
{{ Bijv. "Data ophalen uit systeem X en opslaan als CSV." }}

## Benodigde inputs
<!-- Wat heeft Claude nodig om te kunnen starten? -->
- {{ Input 1, bijv. "Een API-sleutel in .env onder de naam API_SLEUTEL" }}
- {{ Input 2, bijv. "De naam van de map waar de bestanden naartoe moeten" }}

## Stappen

### Stap 1 — {{ Naam van stap }}
<!-- Beschrijf wat er moet gebeuren. Voeg een commando toe als dat van toepassing is. -->
{{ Beschrijving }}

```bash
{{ commando als dat nodig is }}
```

Verwacht resultaat: {{ Wat Claude moet zien als de stap geslaagd is }}

### Stap 2 — {{ Naam van stap }}
{{ Beschrijving }}

```bash
{{ commando }}
```

Verwacht resultaat: {{ ... }}

<!-- Voeg meer stappen toe naar behoefte -->

## Verwachte eindoutput
<!-- Wat levert de workflow op als alles goed gaat? -->
{{ Bijv. "Een bestand .tmp/rapport.csv met kolommen X, Y, Z" }}

## Foutafhandeling

- **{{ Fout of situatie 1 }}:** {{ Wat te doen }}
- **{{ Fout of situatie 2 }}:** {{ Wat te doen }}
- **Onbekende fout:** Lees de volledige foutmelding, zoek de oorzaak, los het op, en update deze workflow met wat je geleerd hebt.

## Notities
<!-- Optioneel: beperkingen, kosten, timing of andere bijzonderheden -->
- {{ Bijv. "Dit script maakt API-aanroepen die kosten. Controleer het aantal aanroepen voor je start." }}
- {{ Bijv. "Maximaal 100 verzoeken per minuut — script wacht automatisch." }}
