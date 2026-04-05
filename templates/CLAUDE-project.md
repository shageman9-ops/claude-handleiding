# {{ Projectnaam }} — Instructies

## Doel van dit project
<!-- Één zin: wat doet dit project? -->
{{ Beschrijf hier het doel, bijv. "Haalt dagelijks verkoopdata op en zet het om naar een Excel-rapport." }}

## Hoe het werkt
<!-- Kort overzicht van de mappenstructuur en scripts -->
- `tools/{{ script-naam }}.py` — {{ wat dit script doet }}
- `workflows/{{ workflow-naam }}.md` — {{ wat deze workflow beschrijft }}
- `.tmp/` — tijdelijke bestanden (kunnen altijd opnieuw gegenereerd worden)
- `.env` — bevat: `{{ NAAM_VAN_API_SLEUTEL }}`

## Regels
<!-- Specifieke afspraken voor dit project -->
- {{ Regel 1, bijv. "Vraag altijd bevestiging voordat je productiedata overschrijft" }}
- {{ Regel 2 }}
- Sla gevoelige gegevens uitsluitend op in `.env`

## Wat Claude nooit mag doen
- Geheimen in code of in de chat zetten
- {{ Projectspecifieke verboden, bijv. "De productiedatabase aanraken zonder expliciete toestemming" }}

## Hoe met fouten omgaan
<!-- Optioneel maar nuttig voor complexere projecten -->
1. Lees de volledige foutmelding
2. Los het script op en test opnieuw
3. {{ Andere stappen die specifiek zijn voor dit project }}
