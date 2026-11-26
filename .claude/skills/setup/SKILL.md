---
name: setup
description: Stellt das Repo von der Demo auf die eigene Firma um. Räumt die Demo-Daten (inklusive Demo-Wiki) nach demo/, übernimmt Kontext und Routing aus teilnehmer/<slug>/ in CLAUDE.md, legt ein leeres Wiki-Gerüst und eine leere asset-foundation.md an und kopiert die vorbereiteten Transkripte in inbox/. Nutze diesen Skill bei "/setup", "/setup <slug>", "mein Ordner", "auf meine Firma umstellen" oder "Demo wegräumen".
---

# Setup

Macht aus dem Demo-Repo dein eigenes. Die Demo bleibt erhalten, sie zieht nur um.

## Immer zuerst lesen

Die eigene `learnings.md` neben dieser Datei, noch vor allem anderen.

Dann `teilnehmer/README.md` und `teilnehmer/<slug>/claude-kontext.md`, `website.md`, `profil.md`. Dazu die aktuelle `CLAUDE.md`, `asset-foundation.md` und `wiki/index.md`, damit die Struktur beim Umbau erhalten bleibt.

## Ablauf

### 1. Slug klären

Ohne Slug oder mit unbekanntem Slug: alle Ordner unter `teilnehmer/` auflisten (ohne `_vorlage`) und **einmal** nachfragen. Steht die Firma nicht auf der Liste, auf `/website <url>` verweisen und aufhören.

### 2. Prüfen, ob schon umgestellt wurde

Existiert `demo/` schon, ist `/setup` bereits gelaufen. Das melden und fragen, was gewollt ist. Nicht ein zweites Mal verschieben.

### 3. Demo wegräumen

Nach `demo/` verschieben, Struktur erhalten:

- `inbox/*` nach `demo/inbox/`
- `wiki/index.md`, `wiki/log.md` und alle Bereiche mit Inhalt (`wiki/kunden/*`, `wiki/team/*`, `wiki/finanzen/*`, `wiki/themen/*`, jeweils inklusive `raw/`) nach `demo/wiki/` mit gleicher Struktur
- `output/posts/*`, `output/mails/*`, `output/angebote/*` nach `demo/output/posts/` und so weiter
- `asset-foundation.md` nach `demo/asset-foundation.md`
- `aufgaben.md` nach `demo/aufgaben.md`

`wiki/_vorlage/` bleibt an Ort und Stelle. Nur verschieben, nichts löschen. `.gitkeep`-Dateien bleiben an Ort und Stelle.

### 4. CLAUDE.md umstellen

In `CLAUDE.md` die vier Blöcke (**Wer wir sind**, **Was wir anbieten**, **Wie ich klinge**, **Was ein gutes Ergebnis ist**) durch den Inhalt aus `teilnehmer/<slug>/claude-kontext.md` ersetzen. Ersetzt wird alles von `## Wer wir sind` bis zum `---` vor `## Das Wiki`. Dazu den Abschnitt **Das Routing** (bis zum nächsten `##`) durch die Routing-Tabelle aus dem Kontext-File ersetzen. Hat die Tabelle dort nur drei Spalten, ergänze die Spalte "Wohin im Wiki" (Standard: `wiki/kunden/<firma>/` für externe Gespräche, `wiki/team/<person>/`, `wiki/finanzen/<YYYY-MM>/`, `wiki/themen/<slug>/`) und lass im Zweifel `[offen: ergänzen]` stehen.

Unverändert bleiben: Titel, Einleitung, **Das Wiki**, **Kontext-Stufen**, **Fragen ans Wiki (Retrieve)**, **Learning Loop**, **Ordner** und **Konventionen**. Hinweise in eckigen Klammern aus dem Kontext-File, die noch drinstehen, nicht mit übernehmen, sondern als `[offen: ergänzen]` stehen lassen.

Heißen die Bereiche der Firma anders (z.B. "Mandanten" statt "Kunden"), nachfragen, ob die Ordner unter `wiki/` und die Routing-Zeilen entsprechend umbenannt werden sollen.

### 5. Wiki-Gerüst, Foundation und Aufgaben neu anlegen

**Wiki:** leeres Gerüst unter `wiki/`:

- Ordner `wiki/kunden/`, `wiki/team/`, `wiki/finanzen/`, `wiki/themen/`, jeweils mit `.gitkeep`
- `wiki/index.md` mit Kopf (Titel, ein Absatz Erklärung wie in `demo/wiki/index.md`) und je Bereich eine leere Tabelle (Pfad | Einzeiler | Stand)
- `wiki/log.md` mit Kopf (Titel, Formatzeile `- YYYY-MM-DD · Quelle · was angelegt oder geändert wurde (Pfade)`), noch ohne Einträge
- `wiki/_vorlage/brief.md` bleibt unverändert

**Foundation:** `asset-foundation.md` als leeres Gerüst, gleiche Kopfstruktur wie in `demo/asset-foundation.md`:

- Titel und Hinweis, dass es DIE eine lebende Foundation ist
- Kopf-Felder: **Erstellt** (heute), **Letzte Aktualisierung** (`noch keine Gespräche`), **Basis** (`noch keine Gespräche`), **Methode**, **Zweck**
- Abschnitt Clustering-Erklärung (leer, mit einem Satz, dass Cluster nach dem ersten Gespräch entstehen)
- Tabelle mit den 12 Zeilen (Position bis Auxiliary Benefits), eine leere Spalte
- Abschnitt **Messaging-Goldstücke** (leer)
- Abschnitt **Offene Fragen** (leer)

Zusätzlich ein Abschnitt **Selbstbild laut Website** mit den Claims aus `website.md`. Klar kennzeichnen: Das ist eine Hypothese darüber, wie die Firma über sich spricht, nicht die Sprache der Kundschaft. Kundensprache kommt erst aus echten oder Übungs-Transkripten.

**Aufgaben:** `aufgaben.md` leer im Starter-Format (Kopf, Formatvorlage, Abschnitte "Offen" und "Erledigt").

### 6. Transkripte bereitstellen

Alle Dateien aus `teilnehmer/<slug>/inbox/` nach `inbox/` **kopieren**, nicht verschieben. `.gitkeep` nicht mitkopieren.

### 7. Zielordner erhalten

Leere Ordner (`inbox/`, `output/posts/`, `output/mails/`, `output/angebote/`) mit `.gitkeep` versehen.

### 8. Bericht

Kompakt im Chat:

```
Umgestellt auf: [Firma] ([slug])
Demo liegt in: demo/ (inklusive Demo-Wiki)
CLAUDE.md: 4 Blöcke + Routing ersetzt ([n] Arten)
Wiki: leeres Gerüst (kunden, team, finanzen, themen), Index und Log mit Kopf
Foundation: leeres Gerüst + Selbstbild laut Website
Transkripte in inbox/: [n]
Offen in CLAUDE.md: [Anzahl der [offen: ...]-Stellen]
Nächster Schritt: /ingest, danach /post
```

Dazu ein Hinweis: Die Beispiel-Learnings in `.claude/skills/ingest/learnings.md` stammen aus der Demo und können bleiben oder gelöscht werden.

## Grenzen

- Nichts löschen, nur verschieben oder kopieren.
- Nichts erfinden. Was in `claude-kontext.md` fehlt, bleibt `[offen: ergänzen]`.
- Nicht doppelt umstellen: existiert `demo/`, melden und nachfragen.
- Dateien unter `teilnehmer/` nicht verändern.
