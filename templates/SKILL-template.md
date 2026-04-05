---
name: {{ naam-van-skill }}
# Dit is wat je intypt: /naam-van-skill
# Gebruik alleen kleine letters en koppeltekens, geen spaties

description: {{ Korte beschrijving van wat deze skill doet. Claude ziet dit als jij twijfelt welke skill te gebruiken. }}

allowed-tools: Bash
# Bash = Claude mag terminal-commando's uitvoeren
# Verwijder deze regel als de skill alleen tekst produceert en niets uitvoert
---

<!-- Hieronder schrijf je wat Claude moet doen als je /naam-van-skill typt -->

{{ Beschrijf in gewone taal wat de taak is }}

**Werkmap:** `{{ pad/naar/projectmap }}`

**Commando:**
```bash
{{ het uit te voeren commando }}
```

<!-- Optioneel: stappen als de taak meerdere commando's heeft -->
Dit doet de volgende stappen:
1. {{ Stap 1 beschrijving }}
2. {{ Stap 2 beschrijving }}

**Na voltooiing:**
- {{ Wat Claude moet rapporteren of controleren }}

**Als het mislukt:**
- Controleer `{{ pad/naar/logbestand }}` voor de foutmelding
- {{ Andere herstelstap }}

{{ Sluit af met een instructie aan Claude, bijv. "Voer het commando nu uit en rapporteer de uitkomst." }}
