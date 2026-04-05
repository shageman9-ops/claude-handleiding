# 03 — Skills: snelkoppelingen voor Claude

## Wat is een skill?

Een skill is een snelkoppeling die je in Claude Code kunt intypen met een slash: `/naam`.

Stel dat je elke week data wilt ophalen. Zonder skill zou je elke keer aan Claude moeten uitleggen wat er moet gebeuren. Met een skill typ je gewoon `/data-ophalen` — en Claude weet precies wat te doen, inclusief welk script te draaien en wat te doen als het misgaat.

---

## Hoe werkt het technisch?

Een skill is een mapje met één bestand erin: `SKILL.md`.

**Globale skills** (werken in elk project):
```
~/.claude/skills/
└── naam-van-skill/
    └── SKILL.md
```

**Projectskills** (werken alleen in dit project):
```
jouw-project/.claude/skills/
└── naam-van-skill/
    └── SKILL.md
```

---

## De opbouw van een SKILL.md

Een `SKILL.md` heeft twee delen:

### 1. Frontmatter (bovenaan, tussen `---`)
Dit is metadata die Claude Code gebruikt om de skill te herkennen:

```yaml
---
name: naam-van-skill
description: Korte beschrijving van wat deze skill doet.
allowed-tools: Bash
---
```

- `name` — dit is wat je intypt: `/naam-van-skill`
- `description` — Claude ziet dit als je twijfelt welke skill te gebruiken
- `allowed-tools` — welke acties Claude mag uitvoeren (meestal `Bash` voor scripts)

### 2. De instructies (onder de frontmatter)
Hier schrijf je wat Claude moet doen als je de skill aanroept. Gewone tekst, net als een CLAUDE.md.

---

## Echt voorbeeld: `/pipeline-run`

Dit is de skill die Simon gebruikt om handmatig data te synchroniseren:

```markdown
---
name: pipeline-run
description: Voer de datapipeline handmatig uit. Haalt verse data op, normaliseert en synchroniseert naar Google Sheets.
allowed-tools: Bash
---

Voer de pipeline handmatig uit.

**Werkmap:** `projects/learnworlds-dashboard`

**Commando:**
\```bash
cd "projects/learnworlds-dashboard" && .venv/bin/python3.14 tools/learnworlds_pipeline.py
\```

Dit doet drie dingen:
1. `learnworlds_fetch.py` — haalt alle responses op via de API
2. `learnworlds_to_sheets.py` — normaliseert data, schrijft CSVs, synchroniseert Google Sheets
3. Schrijft `last_sync.json` met tijdstip en aantallen

**Als het klaar is:**
- Bekijk `.tmp/last_sync.json` voor het resultaat

**Als het mislukt:**
- Controleer `.tmp/learnworlds_pipeline.log` voor de foutmelding
- Zie `workflows/runbook.md` voor herstelstappen

Voer het commando nu uit en rapporteer de uitkomst.
```

Simon typt `/pipeline-run` → Claude leest dit bestand → voert het commando uit → rapporteert terug.

---

## Echt voorbeeld: `/dashboard-start`

```markdown
---
name: dashboard-start
description: Start het Streamlit-dashboard lokaal.
allowed-tools: Bash
---

Start het dashboard.

**Commando:**
\```bash
cd "projects/learnworlds-dashboard" && .venv/bin/python3.14 -m streamlit run tools/dashboard.py
\```

Dashboard opent op: http://localhost:8501

**Controleer eerst of de databestanden bestaan:**
\```bash
ls projects/learnworlds-dashboard/.tmp/lw_normalised_public.csv
\```
Als het bestand ontbreekt, draai dan eerst `/pipeline-run`.

Voer het startcommando nu uit en bevestig dat het draait.
```

---

## Een skill maken: stap voor stap

**Stap 1 — Maak de map aan:**
```bash
mkdir -p .claude/skills/mijn-skill
```

**Stap 2 — Maak het SKILL.md-bestand aan:**
```bash
touch .claude/skills/mijn-skill/SKILL.md
```

**Stap 3 — Schrijf de inhoud** (gebruik de template in `templates/SKILL-template.md`).

**Stap 4 — Test de skill:**
```bash
claude
```
Typ `/mijn-skill` — Claude leest de skill en voert de instructies uit.

---

## Tips

- **Houd de naam kort en beschrijvend.** `/rapport-maken` is beter dan `/genereer-wekelijks-rapport`.
- **Schrijf de "als het mislukt"-sectie altijd.** Dat bespaart je later veel uitzoekwerk.
- **Eén skill, één doel.** Niet `/doe-alles` maar `/data-ophalen`, `/rapport-maken`, `/versturen`.

---

## Template

Zie [templates/SKILL-template.md](templates/SKILL-template.md) voor een kant-en-klare template.

---

## Volgende stap

Ga naar [04-workflows.md](04-workflows.md) om te leren hoe je gedetailleerde instructies schrijft.
