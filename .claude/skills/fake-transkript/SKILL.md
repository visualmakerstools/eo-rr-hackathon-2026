---
name: fake-transkript
description: Erzeugt ein fiktives, realistisches Übungstranskript für einen Teilnehmer-Ordner (teilnehmer/<slug>/inbox/). Arten: kundengespraech (Default), sparring, team. Nutze diesen Skill bei "/fake-transkript <slug> [art]", wenn Übungsmaterial für den Hackathon fehlt oder noch keine echten Transkripte vorliegen.
---

# Fake-Transkript

Erzeugt ein Gespräch, das so klingt, als hätte es stattgefunden, damit `/ingest` und `/post` etwas zu tun haben.

## Immer zuerst lesen

Die eigene `learnings.md` neben dieser Datei, noch vor allem anderen.

`teilnehmer/<slug>/website.md`, `claude-kontext.md` und `profil.md`. Dazu ein Rohtranskript aus `demo/inbox/` oder `demo/wiki/kunden/*/raw/` als Formatvorbild (liegt dort nichts mehr, steht das Format unten).

## Ablauf

### 1. Art bestimmen

- `kundengespraech`: Erstgespräch mit einer plausiblen Person aus der Zielgruppe der Firma. Default.
- `sparring`: zum Beispiel Podcast-Interview oder Austausch unter Gründern. Liefert Post-Stoff.
- `team`: Mitarbeitergespräch (Halbjahresgespräch o.ä.), vertraulich. Landet beim Ingest in `wiki/team/<person>/`.

Ohne Art-Angabe und wenn in `teilnehmer/<slug>/inbox/` schon Transkripte liegen: die Art wählen, die noch fehlt. Die Art lässt sich am Dateinamen ablesen.

### 2. Gespräch bauen

Ein Transkript pro Aufruf. Format wie die Rohtranskripte des Starters:

```markdown
# Transkript: [Art und Anlass]

> Fiktives Übungstranskript, für den Hackathon generiert. Personen auf Kundenseite und alle Zahlen sind erfunden.

**Datum:** YYYY-MM-DD
**Teilnehmer:** [Name der Teilnehmerin / des Teilnehmers aus profil.md] ([Firma]), [Gegenüber mit Rolle]
**Kontext:** [Eine Zeile: wer ist das Gegenüber, wie kam der Kontakt zustande]

---

**[Name]:** ...

**[Gegenüber]:** ...

---

*Ende Transkript (gekürzt für Demo-Zwecke)*
```

Anforderungen:

- 40 bis 60 Zeilen, Sprecherwechsel als Absätze.
- Gesprochene Sprache: Füllwörter, Abbrüche, Unterbrechungen, kurze Rückfragen.
- Konkrete O-Töne, Schmerzpunkte, plausible Zahlen (Teamgröße, Kosten, Zeitaufwand).
- Das Gegenüber hat echte Einwände (Preis, Zeit, schlechte Erfahrungen, Skepsis), nicht nur Zustimmung.
- Die Teilnehmerin oder der Teilnehmer spricht als sie oder er selbst, mit dem Namen aus `profil.md`. Das Angebot im Gespräch entspricht der Website, nichts Zusätzliches versprechen.
- Gegenüber und deren Firma sind erfunden. Keine echten Kundennamen der Firma verwenden, auch wenn die Website Referenzen nennt.
- Beim Sparring ist das Gegenüber eine erfundene Gastgeberin, ein Founder oder eine Fachkollegin, und es fallen Thesen und Beobachtungen aus dem Alltag der Firma, aus denen sich ein Post bauen lässt.

### 3. Ablegen

Nach `teilnehmer/<slug>/inbox/YYYY-MM-DD_transkript_<art>-<gegenueber>.md`. Das Datum liegt in den letzten vier Wochen vor dem 26.11.2026. `<gegenueber>` ist ein kurzer kebab-case-Name der erfundenen Firma oder des Anlasses. Keine bestehende Datei überschreiben.

### 4. Bericht

Dateipfad, Art, Gegenüber in einer Zeile. Vorschlag: noch eine andere Art erzeugen, oder `/setup <slug>`, falls das noch nicht gelaufen ist. Ist `/setup` schon gelaufen, die Datei zusätzlich nach `inbox/` kopieren.

## Grenzen

- Immer als fiktiv kennzeichnen, die Kopfzeile ist Pflicht.
- Keine echten Personen, keine echten Kundennamen, keine realen Zahlen der Firma.
- Nicht mehr als ein Transkript pro Aufruf.
