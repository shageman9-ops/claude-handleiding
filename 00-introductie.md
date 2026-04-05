# 00 — Introductie: wat is Claude Code?

## Het verschil met de chatwebsite

Je kent Claude waarschijnlijk van claude.ai — je typt een vraag, Claude antwoordt, klaar. Maar dat gesprek vergeet Claude zodra het venster dicht is. Volgende keer begin je weer van nul.

**Claude Code is anders.** Het is een programma dat je in de terminal draait, en het heeft een geheugen: instructiebestanden die je zelf schrijft. Claude leest die bestanden elke keer opnieuw zodra je een sessie start. Zo weet Claude altijd wie je bent, hoe je werkt, en wat de regels zijn voor jouw project.

---

## Wat kun je ermee?

Voorbeelden van wat je Claude Code kunt laten doen:

- **Data ophalen** — "Haal elke nacht nieuwe gegevens op uit systeem X en sla ze op."
- **Rapporten maken** — "Zet deze CSV om naar een nette Excel met kleuren en filters."
- **Herhaalbare taken** — "Stuur elke vrijdag een samenvatting naar Google Sheets."
- **Scripts schrijven en uitvoeren** — Claude schrijft de code en voert hem ook meteen uit.
- **Bestanden organiseren** — mappen aanmaken, hernoemen, doorzoeken.

Je hoeft niet te kunnen programmeren. Jij beschrijft wat je wilt; Claude schrijft en draait de code.

---

## Het WAT-framework

Simons systeem is gebouwd volgens het **WAT-framework**:

| Laag | Wat het is | Wie doet het |
|---|---|---|
| **W**orkflows | Instructies in markdown-bestanden | Jij schrijft ze |
| **A**gent | De denker die alles coördineert | Claude |
| **T**ools | Python-scripts die het werk uitvoeren | Claude schrijft ze, of je gebruikt bestaande |

Het idee is simpel: **jij schrijft de spelregels, Claude voert ze uit.**

Workflows vertellen Claude *wat* er moet gebeuren. Tools zijn de scripts die het *daadwerkelijk* doen. Claude is de schakel ertussenin.

---

## De drie bestanden die alles bij elkaar houden

| Bestand | Waar | Waarvoor |
|---|---|---|
| `CLAUDE.md` (globaal) | `~/.claude/CLAUDE.md` | Gelden voor *alle* projecten — jouw stijl, taal, basisregels |
| `CLAUDE.md` (project) | In de projectmap | Gelden alleen voor dit project — specifieke instructies |
| `SKILL.md` | In `.claude/skills/naam/` | Snelkoppelingen — typ `/naam` en Claude weet precies wat te doen |

---

## Volgende stap

Ga naar [01-project-opzetten.md](01-project-opzetten.md) om je eerste projectmap te maken.
