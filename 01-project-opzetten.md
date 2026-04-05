# 01 — Een project opzetten

## De standaard mappenstructuur

Elk project volgt dezelfde opzet. Maak deze mappen aan in de map waar jij werkt:

```
mijn-project/
├── tools/          # Scripts die het echte werk doen
├── workflows/      # Instructies: wat moet er gebeuren en hoe
├── .tmp/           # Tijdelijke bestanden (mogen altijd opnieuw gemaakt worden)
├── .env            # API-sleutels en wachtwoorden — NOOIT ergens anders
└── CLAUDE.md       # Instructies voor Claude, specifiek voor dit project
```

---

## Wat gaat waar?

### `tools/`
Python-scripts die Claude schrijft en uitvoert. Denk aan:
- `haal_data_op.py` — roept een API aan
- `maak_rapport.py` — zet data om naar Excel
- `verstuur_email.py` — stuurt een bericht

Jij hoeft deze scripts niet te schrijven. Jij beschrijft wat je nodig hebt; Claude maakt ze.

### `workflows/`
Markdown-bestanden (.md) met instructies. Claude leest deze als je zegt: "Volg de workflow in `workflows/data-ophalen.md`."

Zie [04-workflows.md](04-workflows.md) voor hoe je ze schrijft.

### `.tmp/`
Tijdelijke bestanden: ruwe data, tussenliggende exports, logbestanden. Alles hier kan opnieuw gegenereerd worden. Sla hier nooit iets op wat je niet kwijt wilt raken.

### `.env`
Een tekstbestand met gevoelige informatie:
```
API_SLEUTEL=jouw-sleutel-hier
WACHTWOORD=geheim
```
Claude leest dit bestand maar zet de inhoud nooit in code of in de chat. Nooit dit bestand delen of uploaden naar GitHub.

### `CLAUDE.md`
Instructies die Claude elke sessie leest. Zie [02-claude-md.md](02-claude-md.md).

---

## Een project aanmaken: stap voor stap

**Stap 1 — Open de terminal en ga naar de plek waar je wilt werken:**
```bash
cd ~/Documents
```

**Stap 2 — Maak de mappen aan:**
```bash
mkdir mijn-project
cd mijn-project
mkdir tools workflows .tmp
```

**Stap 3 — Maak een leeg `.env`-bestand:**
```bash
touch .env
```

**Stap 4 — Maak een `CLAUDE.md` aan** (zie het volgende hoofdstuk voor de inhoud).

**Stap 5 — Open Claude Code in deze map:**
```bash
claude
```

Claude leest nu automatisch jouw `CLAUDE.md` en weet hoe het project in elkaar zit.

---

## Echt voorbeeld: het learnworlds-dashboard project

Zo ziet Simons project eruit:

```
learnworlds-dashboard/
├── tools/
│   ├── dashboard.py              # De Streamlit webapplicatie
│   ├── learnworlds_fetch.py      # Haalt data op via de API
│   ├── learnworlds_to_sheets.py  # Verwerkt data en schrijft naar Google Sheets
│   └── learnworlds_pipeline.py   # Voert beide bovenstaande scripts na elkaar uit
├── workflows/
│   ├── runbook.md                # Wat te doen als er iets fout gaat
│   └── dashboard.md              # Uitleg van het hele systeem
├── .tmp/                         # Tijdelijke databestanden
├── .env                          # API-sleutels
└── CLAUDE.md                     # WAT-framework instructies
```

---

## Volgende stap

Ga naar [02-claude-md.md](02-claude-md.md) om te leren hoe je de instructies voor Claude schrijft.
