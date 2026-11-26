---
name: ingest
description: Sortiert neue Dokumente aus inbox/ ins Wiki ein. Erkennt die Art (Kundengespräch, Mitarbeitergespräch, BWA, Sparring), legt die Wiki-Seite an oder schreibt sie fort, verschiebt das Original nach raw/, pflegt wiki/index.md und wiki/log.md, hängt Aufgaben an aufgaben.md und startet die Folgeschritte (foundation, angebot, mail, post). Nutze diesen Skill bei "Transkript", "inbox verarbeiten", "ins Wiki", "BWA", "Mitarbeitergespräch", Meeting-Mitschrift, Gemini-Notizen, wenn etwas in inbox/ liegt oder bei "was muss ich nach dem Call machen".
---

# Ingest

Neues kommt rein, das Wiki wächst. Ein Dokument wird nicht nur abgelegt, sondern in die bestehende Seite eingearbeitet.

## Ablauf

1. **Lesen:** zuerst die eigene `learnings.md` neben dieser Datei, dann `CLAUDE.md` (Routing-Tabelle, Kontext, Wiki-Regeln) und `wiki/index.md`.
2. **Input finden:** Nennt der User eine Datei, nimm die. Sonst alle Dateien in `inbox/`, älteste zuerst (nach dem Datum im Dateinamen; Transkripte als `.md` oder `.txt`, Finanzzahlen als `.csv`). Ist `inbox/` leer, sag das in einem Satz und hör auf. Steht die Datei schon als Quelle in einem Brief (`quellen` im Frontmatter): überspringen und melden.
3. **Art bestimmen:** Lies das Dokument ganz und ordne es der Routing-Tabelle in `CLAUDE.md` zu. Ein Satz Begründung. Passen zwei Arten, gewinnt die spezifischere. Passt keine: frag **einmal** nach.
4. **Entität bestimmen:** Welche Firma, Person oder welcher Monat ist gemeint? Im Index nachsehen.
   - **Slug:** kleingeschrieben, mit Bindestrichen, ohne Rechtsform (z.B. `kranich-media`, `selin-kaya`). Finanzen: Ordner = Berichtsmonat `YYYY-MM`, nicht Dokumentdatum.
   - **Gibt es sie nicht:** Ordner nach Routing-Tabelle anlegen (`wiki/<bereich>/<slug>/`), `brief.md` aus `wiki/_vorlage/brief.md` erzeugen und befüllen.
   - **Gibt es sie:** `brief.md` fortschreiben. Neuer Eintrag oben im Verlauf, Stand und Offene Punkte aktualisieren, `zuletzt_aktualisiert` und `quellen` ergänzen. Ändert sich etwas ggü. früher (Zahl, Termin, Person), **explizit markieren** im Format `Start: 1. September (vorher: August)`, nicht still überschreiben. Geklärte offene Punkte im Verlauf vermerken und oben streichen.
5. **Original verschieben:** von `inbox/` nach `wiki/<bereich>/<slug>/raw/`, Dateiname behalten, Inhalt nie ändern.
6. **Index und Log:** `wiki/index.md` (Zeile neu oder Stand-Datum anpassen) und `wiki/log.md` (neue Zeile oben, Format `- YYYY-MM-DD · Quelle · was angelegt/geändert wurde (Pfade)`, Datum des Dokuments). Geänderte `asset-foundation.md`, `aufgaben.md` und erzeugte `output/`-Entwürfe stehen in derselben Zeile.
7. **Aufgaben:** Zusagen, To-Dos und nächste Schritte an `aufgaben.md` anhängen, im Format der Datei, mit Quelle. Bereits Erledigtes nicht. Bei einem Folgegespräch erledigte Aufgaben abhaken und nach "Erledigt" verschieben. Bei Mitarbeitergesprächen: nur Vereinbarungen, die erledigt werden müssen, mit neutralem Titel plus Verweis auf die Team-Seite, keine vertraulichen Inhalte in `aufgaben.md`. Bei BWA: nur Prüfaufgaben zu auffälligen Abweichungen.
8. **Folgeschritte:** laut Routing-Tabelle (`foundation`, `angebot`, `mail`, `post`). Immer den Pfad zur `brief.md` übergeben, nicht das Original. Jeder Folgeschritt legt seine Datei in `output/` ab.
9. **Bericht**, kompakt:

```
[Dateiname] → Art: [X] → [neu angelegt | ergänzt]
Seite: wiki/...
Aufgaben: 3 neu
Folgeschritte: output/... (Entwurf, wartet auf Freigabe)
```

## Grenzen

- **Nichts erfinden.** Keine Zahlen, Zusagen oder Namen, die nicht im Dokument stehen. Lücken als `[offen: ...]`.
- **Nichts verschicken.** Mails und Angebote bleiben Entwürfe.
- **`raw/` nie ändern.**
- **Nicht doppelt verarbeiten.**
- Vertrauliches (Mitarbeitergespräche) erzeugt keinen Output nach außen und taucht nie in Posts, Mails oder der Foundation auf. In `aufgaben.md` nur neutraler Titel plus Verweis.
