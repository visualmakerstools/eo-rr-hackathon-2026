---
name: angebot
description: Schreibt einen Angebots-Entwurf nach output/angebote/YYYY-MM-DD_kunde_thema.md, aus einer Notiz aus meetings/ und der Kundensprache aus asset-foundation.md. Wird vom transkript-Skill nach Kundengesprächen aufgerufen, kann aber auch direkt vom User für ein konkretes Gespräch gestartet werden.
---

# Angebot

Schreibt einen Angebots-Entwurf, konkret statt generisch.

## Immer zuerst lesen

`CLAUDE.md` im Repo-Wurzelverzeichnis, besonders die Leistungstabelle und den Tagessatz. Dazu die Notiz aus `meetings/` und `asset-foundation.md` für die Kundensprache.

## Aufbau

1. **Ausgangssituation:** sachlich, in der Sprache des Kunden, mit O-Tönen aus dem Gespräch.
2. **Zielbild:** konkrete Szenarien, wie der Alltag danach aussieht.
3. **Leistungsumfang:** was genau passiert, abgeleitet aus der Leistungstabelle in `CLAUDE.md`.
4. **Ablauf:** Phasen und Zeitraum.
5. **Investition:** konkrete Zahlen auf Basis des Tagessatzes, nie vage.
6. **Nächster Schritt:** genau einer, klar formuliert.

## Regeln

- Konkret statt abstrakt, immer duzen, nie generische Formulierungen.
- Nie konservativ pricen. Der Tagessatz aus `CLAUDE.md` ist die Basis, nicht die Obergrenze.
- Was im Gespräch nicht besprochen wurde, wird als `[offen: im Discovery klären]` markiert statt erfunden.
- Keine Rabatte oder Anrechnungen von sich aus anbieten, das ist ein Verhandlungshebel und bleibt beim User.

## Ablegen

Nach `output/angebote/YYYY-MM-DD_kunde_thema.md`, mit Quelle (Notiz + Foundation-Cluster) im Kopf. Entwurf im Chat zeigen und auf Feedback warten.

## Grenzen

- **Geht nie ohne Freigabe raus.** Immer nur Entwurf.
- Nie erfinden, was nicht im Gespräch stand oder in `CLAUDE.md` steht.
- Keine Rabatte oder Anrechnungen von sich aus anbieten.
