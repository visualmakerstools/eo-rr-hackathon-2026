---
name: transkript
description: Verarbeitet ein Gesprächs-Transkript aus inbox/. Erkennt die Kategorie, schreibt eine Notiz nach meetings/, hängt Aufgaben an aufgaben.md und startet je nach Kategorie die Folgeskills (foundation, post, mail, angebot). Nutze diesen Skill, wenn ein Transkript, eine Meeting-Mitschrift, Gemini-Notizen oder eine Aufnahme verarbeitet werden sollen, wenn etwas in inbox/ liegt, oder wenn gefragt wird "was muss ich nach dem Call machen".
---

# Transkript

Der Router des Systems. Ein Gespräch kommt rein, und je nachdem, was für ein Gespräch es war, passiert etwas anderes.

## Immer zuerst lesen

`CLAUDE.md` im Repo-Wurzelverzeichnis. Dort stehen die Routing-Tabelle, der Kontext des Unternehmens und die Kriterien für ein gutes Ergebnis. Ohne diese Datei arbeitest du blind.

## Ablauf

### 1. Input finden

Wenn der User eine Datei nennt, nimm die. Sonst alle Dateien in `inbox/` verarbeiten, älteste zuerst. Ist `inbox/` leer, sag das in einem Satz und hör auf.

### 2. Kategorie bestimmen

Lies das Transkript ganz und ordne es der Routing-Tabelle in `CLAUDE.md` zu. Begründe die Zuordnung in einem Satz.

Wenn zwei Kategorien passen, gewinnt die spezifischere. Wenn wirklich keine passt, frag **einmal** nach und rate nicht.

### 3. Notiz schreiben

Nach `meetings/YYYY-MM-DD_kategorie_beschreibung.md`:

```markdown
# [Titel des Gesprächs]

**Datum:** YYYY-MM-DD
**Kategorie:** [aus der Routing-Tabelle]
**Teilnehmende:** [Namen und Rollen]
**Quelle:** meetings/raw/[Dateiname]

## Worum ging es

Zwei bis vier Sätze. Was war der Anlass, was war das Ergebnis.

## Kernpunkte

- Die 3 bis 6 Punkte, die zählen. Konkret, mit Zahlen und O-Tönen aus dem Gespräch.

## Zitate

> Wörtliche Sätze, die etwas auf den Punkt bringen. Nur bei Kundengesprächen und Sparring nötig.

## Offene Punkte

- Was unklar blieb, mit `[offen: im nächsten Call klären]`

## Was jetzt läuft

- [Welche Folgeskills gestartet wurden und was sie erzeugt haben]
```

Nichts erfinden. Was nicht im Transkript steht, steht nicht in der Notiz.

### 4. Aufgaben anhängen

Alle Zusagen, To-Dos und nächsten Schritte an `aufgaben.md` anhängen, im Format der Datei. Jede Aufgabe braucht einen selbsterklärenden Titel und genug Kontext, dass sie in zwei Wochen noch verständlich ist. Die Quelle wird verlinkt.

Aufgaben, die im Gespräch schon erledigt wurden, kommen nicht rein.

### 5. Folgeskills starten

Schau in die Routing-Tabelle, welche Skills für diese Kategorie dran sind, und ruf sie der Reihe nach auf. Übergib dabei immer den Pfad zur frischen Notiz, nicht das Rohtranskript.

Jeder Folgeskill legt seine Datei in `output/` ab und meldet den Pfad zurück.

### 6. Transkript wegräumen

Die Rohdatei von `inbox/` nach `meetings/raw/` verschieben. Der Eingang bleibt leer, damit beim nächsten Lauf klar ist, was neu ist.

### 7. Bericht

Im Chat, kompakt:

```
[Dateiname] → Kategorie: [X]
Notiz: meetings/...
Aufgaben: 3 neu
Erzeugt: output/posts/... (Draft, wartet auf Freigabe)
```

## Grenzen

- **Nichts verschicken.** Mails und Angebote sind Entwürfe, bis der User sie freigibt.
- **Nichts erfinden.** Keine Zahlen, keine Zusagen, keine Namen, die nicht im Transkript stehen.
- **Nicht mehrfach verarbeiten.** Liegt zu einem Transkript schon eine Notiz in `meetings/`, überspringen und das melden.
