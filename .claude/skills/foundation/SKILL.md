---
name: foundation
description: Webt Kundensprache aus Gesprächen in die lebende asset-foundation.md ein - Cluster nach Psychografie, 12-Zeilen-Framework pro Cluster. Wird vom transkript-Skill nach Kundengesprächen aufgerufen, kann aber auch direkt gestartet werden, wenn ein neues Gespräch oder eine neue Kundengruppe eingearbeitet werden soll.
---

# Foundation

Destilliert Kundengespräche zu einer strukturierten Foundation, dem Fundament für Posts, Mails und Angebote.

## Immer zuerst lesen

`CLAUDE.md` im Repo-Wurzelverzeichnis. Dort stehen Ton, Angebot und Kriterien für ein gutes Ergebnis.

**Grundprinzip:** Es gibt EINE lebende Foundation unter `asset-foundation.md` im Repo-Root, keine datierten Snapshots. Neue Gespräche werden eingewebt, nicht als neue Datei angelegt.

## Ablauf

### Phase 0: Bestehende Foundation lesen

`asset-foundation.md` lesen: welche Cluster gibt es, welche Zitate, welche offenen Fragen? Dann entscheiden:
- **Weben:** Gespräch passt zu einem bestehenden Cluster → Zitate ergänzen, Zeilen schärfen, offene Fragen updaten.
- **Neues Cluster:** eigene Psychografie, passt in keins der bestehenden → als neue Spalte anhängen.

### Phase 1: Clustering

Cluster nach Psychografie bilden, nicht nach Branche oder Firmengröße: gleiche Schmerzen, gleiche Ängste, gleiche Erfolgsdefinition. Typisch 2-4 Cluster. Kurz erklären, welches Gespräch in welchen Cluster fällt und warum.

### Phase 2: 12-Zeilen-Framework pro Cluster

| # | Dimension | Erklärung |
|---|-----------|-----------|
| 1 | **Position** | Rolle, Unternehmensgröße, Branche, Team, Budget-Hoheit |
| 2 | **Deepest Desires** | Was wollen sie wirklich? In ihren eigenen Worten. |
| 3 | **Up at night** | Was hält sie nachts wach? Existenzielle Angst, nicht Features. |
| 4 | **Frustrated by** | Woran scheitern sie täglich? Direkte Zitate. |
| 5 | **Angry at** | Wer/Was hat ihr Vertrauen gebrochen? Wo wurden sie enttäuscht? |
| 6 | **Tried but failed at** | Welche Lösungen haben sie schon versucht? Tools, Agenturen, Hires - konkret benennen. |
| 7 | **Trends & threats** | Welche Marktveränderungen bedrohen sie, wenn sie nicht handeln? |
| 8 | **Cost of inaction** | Was passiert konkret, wenn sie nichts tun, mit Zeithorizont? |
| 9 | **Solution / Vehicle** | Wie positioniert sich das eigene Angebot als Lösung, für diesen Cluster spezifisch? |
| 10 | **Bodacious Claim** | Eine mutige, messbare Kernaussage. Mappt direkt auf Zeile 2 (Deepest Desire). |
| 11 | **Secondary Benefits** | Quantifizierbare Nebeneffekte (Zeit, Geld, Fehlerrate). |
| 12 | **Auxiliary Benefits** | Emotionale Transformation, wie fühlt sich das Team danach? Identität, nicht Features. |

Nur aus echten Zitaten des Gesprächs füllen, nichts erfinden. Unbekanntes bleibt `[offen: im nächsten Call klären]`.

### Phase 3: Qualitätsprüfung

- Mappt Zeile 10 direkt auf Zeile 2?
- Stehen in Zeile 6 konkrete Tool-/Agenturnamen?
- Ist Zeile 12 Identität ("ich bin endlich..."), nicht Features?
- Klingt es nach Kundensprache oder nach generischem SaaS-Marketing? Wenn Letzteres: zurück zum Gespräch.

### Phase 4: Foundation fortschreiben

Am Ende in `asset-foundation.md`:
- Kopf-Felder "Letzte Aktualisierung" (Datum + was ergänzt wurde) und "Basis" (Liste der zugrunde liegenden Gespräche) fortschreiben.
- 2-3 neue Messaging-Goldstücke ergänzen: Zitate, die direkt als Hook für einen Post oder als Zeile in einem Angebot taugen.

## Input

Wird meist vom `transkript`-Skill mit dem Pfad zu einer frischen Notiz aus `meetings/` aufgerufen. Kann auch direkt vom User mit einem Thema oder mehreren Gesprächen gestartet werden ("web die letzten drei Gespräche in die Foundation ein").

## Grenzen

- Nie erfinden. Was nicht im Gespräch gesagt wurde, bleibt `[offen: im nächsten Call klären]`.
- Keine neue datierte Datei anlegen, immer `asset-foundation.md` im Root aktualisieren.
- Kein Cluster nach Branche oder Firmengröße bilden, nur nach Psychografie.
