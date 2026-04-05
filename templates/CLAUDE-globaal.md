# Globale instructies

## Taal
<!-- Vertel Claude in welke taal je wilt communiceren -->
Communiceer altijd in het Nederlands, tenzij ik in een andere taal schrijf.

## Projectstructuur
<!-- Claude gebruikt dit als sjabloon voor nieuwe projecten -->
Start elk nieuw project met deze basisopzet:
- `tools/`      — scripts die het werk doen
- `workflows/`  — instructies (wat te doen en hoe)
- `.tmp/`       — tijdelijke bestanden, altijd opnieuw te genereren
- `.env`        — API-sleutels en wachtwoorden (nooit elders opslaan)
- `CLAUDE.md`   — projectspecifieke instructies

## Aanpak
<!-- Hoe wil je dat Claude te werk gaat -->
1. Lees bestaande bestanden altijd eerst voordat je iets aanpast
2. Controleer of er al een tool bestaat voor de taak
3. Houd oplossingen eenvoudig — geen onnodige extra's
4. Sla gevoelige gegevens alleen op in `.env`

## Beveiliging
- Zet nooit wachtwoorden of API-sleutels in code of in de chat
- Vraag altijd bevestiging voordat je bestanden permanent verwijdert

## Stijl
<!-- Hoe wil je dat Claude communiceert -->
- Beknopt en to the point
- Geen emoji's tenzij ik erom vraag
- Geen lange uitleg bij simpele taken
