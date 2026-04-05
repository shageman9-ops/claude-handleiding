# 02 — CLAUDE.md: instructies voor Claude

## Wat is een CLAUDE.md?

Een `CLAUDE.md` is een gewoon tekstbestand in markdown-opmaak. Claude leest het automatisch aan het begin van elke sessie. Het is jouw manier om Claude te vertellen:

- Wie je bent en hoe je werkt
- Wat de regels zijn voor dit project
- Welke aanpak je wilt
- Wat Claude absoluut niet mag doen

Je schrijft het één keer; Claude volgt het altijd.

---

## Twee niveaus: globaal en per project

### Globaal CLAUDE.md
**Locatie:** `~/.claude/CLAUDE.md`

Dit bestand geldt voor **alle projecten**. Schrijf hier je persoonlijke voorkeuren in: welke taal je spreekt, hoe beknopt je antwoorden wilt, basisregels voor beveiliging.

### Project CLAUDE.md
**Locatie:** In de projectmap zelf, naast `tools/` en `workflows/`

Dit bestand geldt **alleen voor dit project**. Schrijf hier projectspecifieke instructies: hoe het systeem werkt, welke scripts er zijn, hoe Claude fouten moet afhandelen.

Beide bestanden worden geladen. Het projectbestand overschrijft niets uit het globale bestand — ze vullen elkaar aan.

---

## Echt voorbeeld: Simons globale CLAUDE.md

```markdown
# Globale instructies

## Taal
Communiceer altijd in het Engels, tenzij ik in een andere taal schrijf.

## Projectstructuur
Start elk nieuw project met deze basisopzet:
- tools/       # Scripts die het werk doen
- workflows/   # Instructies (wat te doen en hoe)
- .tmp/        # Tijdelijke bestanden, altijd opnieuw te genereren
- .env         # API-sleutels (nooit elders opslaan)
- CLAUDE.md    # Projectspecifieke instructies

## Aanpak
1. Lees bestaande code altijd eerst voordat je iets aanpast
2. Controleer of er al een tool bestaat voor de taak
3. Houd oplossingen eenvoudig — geen onnodige abstracties
4. Sla API-sleutels alleen op in .env

## Beveiliging
- Zet nooit geheimen in code, chat of versiebeheer
- Valideer altijd gebruikersinvoer aan de serverkant
- Bij twijfel: vraag eerst

## Stijl
- Communiceer beknopt en to the point
- Geen emoji's tenzij gevraagd
- Geen onnodige uitleg bij simpele taken
```

---

## Echt voorbeeld: het project CLAUDE.md (learnworlds-dashboard)

```markdown
# Agent Instructions

Je werkt in het WAT-framework (Workflows, Agents, Tools).

## Laag 1: Workflows
- Markdown SOP's in `workflows/`
- Elke workflow definieert het doel, inputs, welke tools te gebruiken en hoe met fouten om te gaan

## Laag 2: Agents (jij)
- Lees de relevante workflow, voer tools in de juiste volgorde uit
- Stel vragen als iets onduidelijk is

## Laag 3: Tools
- Python-scripts in `tools/`
- API-aanroepen, datatransformaties, bestandsoperaties
- Inloggegevens staan in .env

## Wat gaat waar
- Resultaten gaan naar cloudservices (Google Sheets)
- .tmp/ is tijdelijk en kan altijd opnieuw gegenereerd worden
```

---

## Hoe schrijf je een goede CLAUDE.md?

**Schrijf in gewone taal.** Claude begrijpt instructies zoals je een collega zou briefen.

**Gebruik kopjes.** Zo kan Claude snel vinden wat relevant is.

**Wees specifiek bij regels.** Niet "wees voorzichtig", maar "vraag altijd bevestiging voordat je bestanden verwijdert".

**Houd het beknopt.** Claude leest dit elk gesprek opnieuw. Tien regels die kloppen werken beter dan vijftig regels vol herhaling.

**Voorbeeldstructuur voor een project CLAUDE.md:**
```markdown
# [Projectnaam] — Instructies

## Doel van dit project
[Één zin: wat doet dit project]

## Hoe het werkt
[Korte beschrijving van de mappenstructuur en de scripts]

## Regels
- [Regel 1]
- [Regel 2]

## Wat Claude nooit mag doen
- Geheimen in code zetten
- Productiedata verwijderen zonder bevestiging
```

---

## Template

Zie [templates/CLAUDE-project.md](templates/CLAUDE-project.md) voor een kant-en-klare template om in te vullen.

---

## Volgende stap

Ga naar [03-skills.md](03-skills.md) om te leren hoe je snelkoppelingen maakt.
