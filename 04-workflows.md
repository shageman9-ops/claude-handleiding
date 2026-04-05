# 04 — Workflows: stap-voor-stap instructies

## Wat is een workflow?

Een workflow is een gedetailleerd instructiedocument dat Claude volgt voor een specifieke taak. Zie het als een handleiding die je schrijft voor een nieuwe collega: wat is het doel, wat heb je nodig, welke stappen zijn er, en wat doe je als er iets fout gaat?

**Verschil met een skill:**

| | Skill | Workflow |
|---|---|---|
| **Gebruik** | Typ `/naam` om te starten | Claude leest het op jouw verzoek |
| **Lengte** | Kort — 10 tot 30 regels | Lang — zo gedetailleerd als nodig |
| **Doel** | Snel een bekende taak uitvoeren | Een complexe taak nauwkeurig doorlopen |
| **Locatie** | `.claude/skills/naam/SKILL.md` | `workflows/naam.md` |

Je kunt een workflow en een skill combineren: de skill start de taak, de workflow geeft de gedetailleerde instructies.

---

## Waar staan workflows?

In de map `workflows/` in je project:

```
mijn-project/
└── workflows/
    ├── data-ophalen.md
    ├── rapport-maken.md
    └── runbook.md
```

---

## De opbouw van een workflow

Een goede workflow heeft deze secties:

```markdown
# Naam van de workflow

## Doel
[Één zin: wat bereik je met deze workflow]

## Benodigde inputs
- [Wat heeft Claude nodig om te starten]
- [Bijv. een bestandspad, een datum, een API-sleutel]

## Stappen
1. [Eerste stap]
2. [Tweede stap]
3. ...

## Verwachte output
[Wat levert het op — een bestand, een rapport, een bericht]

## Foutafhandeling
- **Fout X:** [Wat te doen als X fout gaat]
- **Fout Y:** [Wat te doen als Y fout gaat]
```

---

## Echt voorbeeld: een stuk uit Simons runbook

Dit is een deel van `workflows/runbook.md` — wat te doen als het dashboard oude data toont:

```markdown
## Dashboard toont oude data

**Controleer wanneer de laatste synchronisatie was:**
\```bash
cat .tmp/last_sync.json
\```
Verwacht: `synced_at` binnen de afgelopen 25 uur. Als dat niet zo is, zie "Pipeline niet uitgevoerd" hieronder.

**Controleer wat het dashboard daadwerkelijk leest:**
\```bash
wc -l .tmp/lw_normalised_public.csv
\```

**Forceer een nieuwe pipeline-run:**
\```bash
.venv/bin/python3.14 tools/learnworlds_pipeline.py
\```

Na voltooiing: herlaad het dashboard in de browser.
```

Wat maakt dit een goede workflow?
- **Concreet** — exacte commando's, geen vage beschrijvingen
- **Volgorde** — eerst controleren, dan pas actie ondernemen
- **Verwachting erbij** — "Verwacht: ... binnen 25 uur"
- **Verwijzing** — "zie 'Pipeline niet uitgevoerd' hieronder" voor doorkoppeling

---

## Wanneer maak je een workflow?

Maak een workflow als:
- Een taak meer dan 3–4 stappen heeft
- Er dingen fout kunnen gaan en je precies wilt weten wat te doen
- De taak niet elke week hetzelfde is (anders is een skill beter)
- Je wilt dat Claude de logica begrijpt, niet alleen een commando uitvoert

---

## Tips voor goede workflows

**Schrijf commando's letterlijk op.** Claude kan ze dan direct uitvoeren zonder te raden.

**Voeg "verwacht resultaat" toe.** Zodat Claude kan controleren of een stap gelukt is.

**Houd secties kort.** Liever vijf kleine secties dan één lange muur van tekst.

**Update de workflow als je iets nieuws leert.** Als er een betere manier is, of als een grens geraakt wordt (bijv. een API-limiet), schrijf het er meteen bij. Zo verbetert het systeem zichzelf.

---

## Template

Zie [templates/workflow-template.md](templates/workflow-template.md) voor een kant-en-klare template.

---

## Volgende stap

Ga naar [05-eerste-project.md](05-eerste-project.md) om alles samen te brengen in een echt mini-project.
