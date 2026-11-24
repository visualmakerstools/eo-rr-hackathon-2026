---
name: setup
description: Stellt das Repo von der Demo auf die eigene Firma um. Räumt die Demo-Daten nach demo/, übernimmt Kontext und Routing aus teilnehmer/<slug>/ in CLAUDE.md, legt eine leere asset-foundation.md an und kopiert die vorbereiteten Transkripte in inbox/. Nutze diesen Skill bei "/setup", "/setup <slug>", "mein Ordner", "auf meine Firma umstellen" oder "Demo wegräumen".
---

# Setup

Macht aus dem Demo-Repo dein eigenes. Die Demo bleibt erhalten, sie zieht nur um.

## Immer zuerst lesen

`teilnehmer/README.md` und `teilnehmer/<slug>/claude-kontext.md`, `website.md`, `profil.md`. Dazu die aktuelle `CLAUDE.md` und `asset-foundation.md`, damit die Struktur beim Umbau erhalten bleibt.

## Ablauf

### 1. Slug klären

Ohne Slug oder mit unbekanntem Slug: alle Ordner unter `teilnehmer/` auflisten (ohne `_vorlage`) und **einmal** nachfragen. Steht die Firma nicht auf der Liste, auf `/website <url>` verweisen und aufhören.

### 2. Prüfen, ob schon umgestellt wurde

Existiert `demo/` schon, ist `/setup` bereits gelaufen. Das melden und fragen, was gewollt ist. Nicht ein zweites Mal verschieben.

### 3. Demo wegräumen

Nach `demo/` verschieben, Struktur erhalten:

- `inbox/*` nach `demo/inbox/`
- `meetings/*` (inklusive `raw/`) nach `demo/meetings/`
- `output/posts/*`, `output/mails/*`, `output/angebote/*` nach `demo/output/posts/` und so weiter
- `asset-foundation.md` nach `demo/asset-foundation.md`
- `aufgaben.md` nach `demo/aufgaben.md`

Nur verschieben, nichts löschen. `.gitkeep`-Dateien bleiben an Ort und Stelle.

### 4. CLAUDE.md umstellen

In `CLAUDE.md` die vier Blöcke (**Wer wir sind**, **Was wir anbieten**, **Wie ich klinge**, **Was ein gutes Ergebnis ist**) und **Das Routing** durch den Inhalt aus `teilnehmer/<slug>/claude-kontext.md` ersetzen. Ersetzt wird alles von `## Wer wir sind` bis zum `---` vor `## Ordner`. Der Titel, die Einleitung, der Abschnitt **Ordner** und der Abschnitt **Konventionen** bleiben unverändert. Hinweise in eckigen Klammern aus dem Kontext-File, die noch drinstehen, nicht mit übernehmen, sondern als `[offen: ergänzen]` stehen lassen.

### 5. Foundation und Aufgaben neu anlegen

`asset-foundation.md` als leeres Gerüst, gleiche Kopfstruktur wie in `demo/asset-foundation.md`:

- Titel und Hinweis, dass es DIE eine lebende Foundation ist
- Kopf-Felder: **Erstellt** (heute), **Letzte Aktualisierung** (`noch keine Gespräche`), **Basis** (`noch keine Gespräche`), **Methode**, **Zweck**
- Abschnitt Clustering-Erklärung (leer, mit einem Satz, dass Cluster nach dem ersten Gespräch entstehen)
- Tabelle mit den 12 Zeilen (Position bis Auxiliary Benefits), eine leere Spalte
- Abschnitt **Messaging-Goldstücke** (leer)
- Abschnitt **Offene Fragen** (leer)

Zusätzlich ein Abschnitt **Selbstbild laut Website** mit den Claims aus `website.md`. Klar kennzeichnen: Das ist eine Hypothese darüber, wie die Firma über sich spricht, nicht die Sprache der Kundschaft. Kundensprache kommt erst aus echten oder Übungs-Transkripten.

`aufgaben.md` leer im Starter-Format (Kopf, Formatvorlage, Abschnitte "Offen" und "Erledigt").

### 6. Transkripte bereitstellen

Alle Dateien aus `teilnehmer/<slug>/inbox/` nach `inbox/` **kopieren**, nicht verschieben. `.gitkeep` nicht mitkopieren.

### 7. Zielordner erhalten

Leere Ordner (`inbox/`, `meetings/raw/`, `output/posts/`, `output/mails/`, `output/angebote/`) mit `.gitkeep` versehen.

### 8. Bericht

Kompakt im Chat:

```
Umgestellt auf: [Firma] ([slug])
Demo liegt in: demo/
CLAUDE.md: 4 Blöcke + Routing ersetzt ([n] Kategorien)
Foundation: leeres Gerüst + Selbstbild laut Website
Transkripte in inbox/: [n]
Offen in CLAUDE.md: [Anzahl der [offen: ...]-Stellen]
Nächster Schritt: /transkript, danach /post
```

## Grenzen

- Nichts löschen, nur verschieben oder kopieren.
- Nichts erfinden. Was in `claude-kontext.md` fehlt, bleibt `[offen: ergänzen]`.
- Nicht doppelt umstellen: existiert `demo/`, melden und nachfragen.
- Dateien unter `teilnehmer/` nicht verändern.
