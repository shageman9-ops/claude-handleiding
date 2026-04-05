# 05 — Je eerste project: een boodschappenlijst-assistent

In dit hoofdstuk bouwen we samen een mini-project van begin tot eind. Na afloop heb je een werkende projectmap met een CLAUDE.md, een skill en een workflow.

**Wat gaan we bouwen?**
Een eenvoudige assistent die boodschappenlijstjes beheert. Je kunt items toevoegen, de lijst bekijken, en de lijst leegmaken. Claude doet het echte werk; jij geeft instructies.

---

## Stap 1 — Projectmap aanmaken

Open de terminal en maak de map aan:

```bash
mkdir ~/Documents/boodschappen-assistent
cd ~/Documents/boodschappen-assistent
mkdir tools workflows .tmp
touch .env
```

Je mappenstructuur ziet er nu zo uit:
```
boodschappen-assistent/
├── tools/
├── workflows/
├── .tmp/
└── .env
```

---

## Stap 2 — CLAUDE.md schrijven

Maak een nieuw bestand `CLAUDE.md` in de projectmap en plak deze inhoud erin:

```markdown
# Boodschappen-assistent — Instructies

## Doel van dit project
Beheer een boodschappenlijst via tekstbestanden.

## Hoe het werkt
- De lijst staat in `.tmp/boodschappen.txt`, één item per regel
- Scripts staan in `tools/`
- Workflows staan in `workflows/`

## Regels
- Verwijder nooit de lijst zonder te vragen
- Maak scripts zo eenvoudig mogelijk
- Bevestig altijd wat er gedaan is na een actie

## Wat Claude nooit mag doen
- Bestanden buiten deze projectmap aanraken
- Geheimen in code zetten
```

---

## Stap 3 — Een workflow schrijven

Maak `workflows/lijst-beheren.md` en schrijf:

```markdown
# Workflow: boodschappenlijst beheren

## Doel
Items toevoegen aan, bekijken van, of verwijderen uit de boodschappenlijst.

## Benodigde inputs
- De gewenste actie: toevoegen / bekijken / leegmaken
- Bij toevoegen: het item of de items

## Stappen

### Bekijken
\```bash
cat .tmp/boodschappen.txt
\```
Als het bestand niet bestaat: de lijst is leeg.

### Toevoegen
\```bash
echo "ITEM" >> .tmp/boodschappen.txt
\```
Vervang ITEM door het toe te voegen product.

### Leegmaken
Vraag altijd bevestiging voordat je de lijst leegmaakt.
\```bash
> .tmp/boodschappen.txt
\```

## Verwachte output
- Bij bekijken: de inhoud van de lijst (of "lijst is leeg")
- Bij toevoegen: bevestiging van het toegevoegde item
- Bij leegmaken: bevestiging dat de lijst leeg is

## Foutafhandeling
- Bestand bestaat niet → behandel als lege lijst, maak het aan bij de eerste toevoeging
```

---

## Stap 4 — Een skill aanmaken

Maak de skill-map aan:
```bash
mkdir -p .claude/skills/boodschappen
```

Maak `.claude/skills/boodschappen/SKILL.md` en schrijf:

```markdown
---
name: boodschappen
description: Beheer de boodschappenlijst — toevoegen, bekijken of leegmaken.
allowed-tools: Bash
---

Beheer de boodschappenlijst via `workflows/lijst-beheren.md`.

Vraag de gebruiker wat ze willen doen:
- Lijst bekijken
- Item toevoegen (vraag welk item)
- Lijst leegmaken (vraag altijd om bevestiging)

Voer daarna de bijbehorende stap uit de workflow uit en bevestig het resultaat.
```

---

## Stap 5 — Testen

Open Claude Code in de projectmap:
```bash
claude
```

Probeer het volgende:

1. **Typ `/boodschappen`** — Claude vraagt wat je wilt doen.
2. **Zeg "toevoegen" en noem een paar items** — Claude voegt ze toe.
3. **Typ `/boodschappen` opnieuw en kies "bekijken"** — je ziet de lijst.
4. **Kies "leegmaken"** — Claude vraagt bevestiging, dan wordt de lijst leeggemaakt.

---

## Wat je geleerd hebt

Je hebt nu:

| Wat | Bestand | Wat het doet |
|---|---|---|
| Projectstructuur | Mappen + `.env` | Alles op de juiste plek |
| Instructies | `CLAUDE.md` | Claude weet hoe dit project werkt |
| Gedetailleerde stappen | `workflows/lijst-beheren.md` | Claude volgt dit bij complexere acties |
| Snelkoppeling | `.claude/skills/boodschappen/SKILL.md` | Eén commando om alles te starten |

Dit patroon werkt voor elk project, hoe groot of klein ook. Vervang de boodschappenlijst door een API, een spreadsheet, of een rapport — de structuur blijft hetzelfde.

---

## Wat kun je nu zelf proberen?

- Voeg een nieuwe actie toe aan de workflow: bijv. een item van de lijst verwijderen
- Maak een tweede skill `/boodschappen-leeg` die altijd eerst de lijst toont en dan vraagt of je wilt leegmaken
- Schrijf een globale `CLAUDE.md` in `~/.claude/CLAUDE.md` met jouw persoonlijke stijlvoorkeuren

---

Ga naar de [templates](templates/) map voor kant-en-klare bestanden om te kopiëren.
