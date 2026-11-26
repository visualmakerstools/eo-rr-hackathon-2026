# Mein Company-OS

Dieses Repo ist mein Betriebssystem. Dokumente kommen rein, ein Wiki wächst mit, verwertbare Arbeit kommt raus.

Alles, was Claude über mich und mein Geschäft wissen muss, steht in dieser Datei. Die Skills sind absichtlich dünn: Sie holen ihren Kontext von hier, nicht aus sich selbst.

> **Für dich zum Anpassen.** Die Blöcke unten sind mit einem Demo-Unternehmen gefüllt, damit du sofort etwas laufen sehen kannst. Ersetze sie durch deine eigenen Angaben, dann arbeitet die Maschine für dich statt für die Demo.

---

## Wer wir sind

O/WONDER baut agentische Betriebssysteme für Unternehmen, die mit KI mehr schaffen wollen, ohne dafür ständig neu einstellen zu müssen. Wir beraten nicht nur, wir setzen operativ um und bauen Systeme, die mit jedem Gespräch dazulernen.

Typische Kundschaft: wachsende Dienstleister und Agenturen zwischen 45 und 150 Mitarbeitenden im DACH-Raum. Sie sind keine KI-Skeptiker, sie sind schon dran und kommen nicht in die Skalierung.

## Was wir anbieten

| Leistung | Was passiert | Dauer | Aufwand |
|----------|--------------|-------|---------|
| Discovery-Workshop | Prozesse aufnehmen, Use Cases priorisieren, Blueprint | 1 Tag | 2 PT (Workshop plus Aufbereitung) |
| Pilot | Ein Use Case live an echten Daten, messbar | 4-6 Wochen | 15-25 PT, je nach Zahl der angebundenen Systeme |
| Ausbau | Weitere Prozesse, Enablement des Teams | fortlaufend | 4-8 PT pro Monat |

Tagessatz: 1.200 Euro. Das ist die Basis, nicht die Obergrenze. Preise nennen wir im Gespräch, nicht per Mail. Im Angebotsdokument selbst stehen sie immer konkret.

Die Personentage sind der Korridor, in dem ein Angebot rechnen darf, ohne zu raten. Wo im Gespräch etwas fehlt, das den Aufwand bestimmt (Zahl der Systeme, Datenlage, Zahl der Nutzenden), wird das im Angebot als `[offen: im Discovery klären]` benannt statt überspielt.

## Wie ich klinge

- Ich-Perspektive, nah am echten Erleben. Konkrete Situationen statt Vogelperspektive.
- Auf Augenhöhe. Keine Guru-Pose, kein "Ich verrate dir das Geheimnis".
- Direkt und konkret: Zahlen, Szenen, O-Töne. Wenn ein Satz auch in jedem anderen Feed stehen könnte, streiche ich ihn.
- Wir duzen immer, auch in Angeboten.
- Deutsch. Englische Fachbegriffe da, wo sie natürlich sind.

**Nie:** Em-Dashes. Buzzword-Ketten (disruptiv, game-changing). Meta-Sätze ("Viele von euch kennen das"). Menschen als "Köpfe" oder "Ressourcen". Floskeln wie "unverbindlich, kein Pitch".

## Was ein gutes Ergebnis ist

- **Wiki-Seite (Brief):** Ich verstehe in 30 Sekunden, wer oder was das ist, wo wir stehen und was offen ist, ohne das Original zu lesen. Jede Aussage hat eine Quelle.
- **Aufgabe:** Selbsterklärender Titel plus so viel Kontext, dass ich sie in zwei Wochen noch verstehe.
- **Post:** Eine Kernaussage, ein konkreter Aufhänger aus einem echten Gespräch, kein "Was denkt ihr?" am Schluss.
- **Mail:** Kürzer, als ich denke. Ein klarer nächster Schritt. Klingt nach mir, nicht nach Vorlage.
- **Angebot:** Konkreter Umfang, konkreter Preis, konkrete Ergebnisse. Nie generisch, nie vage.

Wenn etwas nicht im Dokument steht, wird es nicht erfunden. Dann kommt `[offen: im nächsten Call klären]` rein.

---

## Das Wiki

Das Wiki ist ein Ordner voller Markdown-Dateien, der mit jedem Dokument wächst. Es hat drei Ebenen:

1. **`raw/`:** die Originale (Transkripte, BWA-Exporte). Liegen neben der Seite, zu der sie gehören.
2. **Seiten (`brief.md`):** verdichtet, mit Frontmatter und Verweisen. Eine Seite pro Firma, Person oder Monat. Aufbau siehe `wiki/_vorlage/brief.md`.
3. **`wiki/index.md` und `wiki/log.md`:** das Verzeichnis aller Seiten und die Chronik aller Änderungen.

Regeln:

- **`raw/` wird nie verändert.** Originale werden nur dorthin verschoben, nie bearbeitet.
- **Briefe fortschreiben, nicht neu anlegen.** Gibt es die Firma oder Person schon, kommt ein neuer Verlauf-Eintrag oben in den bestehenden Brief. Widersprüche zum Bisherigen werden markiert, nicht still überschrieben.
- **Jede Änderung geht in Index und Log.** Neue Seite: Zeile im Index. Jede Änderung: Zeile im Log.
- **Jede Aussage im Brief hat eine Quelle** (Pfad zum Original). Was nirgends steht, wird nicht erfunden.

Drei Handgriffe halten das Wiki sauber: **Ingest** (Neues einsortieren, Skill `/ingest`), **Lint** (aufräumen, Skill `/lint`), **Retrieve** (Fragen beantworten, siehe unten).

## Kontext-Stufen

Nicht alles gleichzeitig laden. Drei Stufen:

- **Immer:** `CLAUDE.md` und `asset-foundation.md`.
- **Pro Aufgabe:** die betroffenen Wiki-Seiten, gefunden über `wiki/index.md`.
- **Nur auf Anfrage:** `raw/` und ältere Verlauf-Einträge.

Mehr Kontext macht die Antwort schlechter, nicht besser.

## Fragen ans Wiki (Retrieve)

Bei jeder Frage zu Kundschaft, Team, Zahlen oder Themen:

1. Erst `wiki/index.md` lesen, dann nur die passenden Seiten. Nicht das ganze Wiki durchsuchen.
2. Antwort mit Quellpfad (welche Seite, welcher Verlauf-Eintrag).
3. In `raw/` nur nachsehen, wenn ich es ausdrücklich will oder ein Brief eine Aussage nicht hergibt.
4. Gute Antworten lege ich auf Wunsch als eigene Seite ab (typ `themen`, Bereich `wiki/themen/<slug>/`) und trage sie in Index und Log ein.

## Das Routing

Das ist die wichtigste Tabelle im Repo. Sie entscheidet, wohin ein Dokument im Wiki wandert und was danach von allein passiert.

| Art | Woran erkennbar | Wohin im Wiki | Was danach läuft |
|-----|-----------------|---------------|------------------|
| **Kundengespräch** | Externe Person, Bedarf, Budget, Angebot, nächster Schritt | `wiki/kunden/<firma>/` | Brief + Aufgaben + `foundation` (Kundensprache einweben) + `angebot` als Entwurf + `mail` als Entwurf |
| **Mitarbeitergespräch** | Eine Person aus dem Team, Zufriedenheit, Entwicklung, Vereinbarungen | `wiki/team/<person>/` | Brief + Aufgaben. Vertraulich, kein Output nach außen |
| **BWA / Finanzzahlen** | CSV oder Tabelle mit Positionen und Monatswerten | `wiki/finanzen/<YYYY-MM>/` | Brief mit Kennzahlen, Abweichungen zum Vormonat, Aufgaben |
| **Sparring / Impuls** | Podcast, Beratungsgespräch, lautes Denken, Konferenz | `wiki/themen/<slug>/` | Brief + `post` als Draft |
| **Sonstiges** | Passt in keine der vier | nur Log-Eintrag | Aufgaben. Nachfragen, ob es ins Wiki soll |

Bei mehreren passenden Arten gewinnt die spezifischere. Bei Unklarheit fragt der `ingest`-Skill genau einmal nach, statt zu raten.

**Das ist deine Stellschraube.** Schreib deine eigenen Arten in diese Tabelle und die Maschine läuft anders. Ein Coach hat vielleicht "Klientensitzung". Ein Steuerberater "Mandantengespräch". Eine Produktchefin "User-Interview". Die Bereiche im Wiki sollen dabei zu deinen eigenen Units oder Abteilungen passen: Hast du statt "Kunden" lieber "Mandanten" oder statt "Finanzen" ein "Controlling", benenne die Ordner und die Routing-Zeilen entsprechend um.

## Learning Loop

Neben jedem Skill liegt eine `learnings.md`. Der Ablauf:

1. Der Lauf produziert ein Ergebnis.
2. Du korrigierst oder gibst frei.
3. Das System erkennt das Muster in der Korrektur.
4. Das Muster wird als Regel in die `learnings.md` des Skills geschrieben.
5. Der nächste Lauf liest die Datei vor dem Start.

Zweite Korrektur derselben Art: "Schreib das in die Learnings." Einmal pro Woche 15 Minuten die Learnings durchgehen. Höchstens eine neue Regel pro Woche wandert von dort in diese `CLAUDE.md`, sonst wird sie unlesbar.

---

## Ordner

```
inbox/              Dokument reinwerfen, das ist der einzige Eingang
wiki/
  index.md          Verzeichnis aller Seiten
  log.md            Chronik, neueste oben
  _vorlage/         Seitenvorlage brief.md
  kunden/<firma>/   brief.md + raw/
  team/<person>/    brief.md + raw/ (vertraulich)
  finanzen/<YYYY-MM>/  brief.md + raw/
  themen/<slug>/    brief.md + raw/ (Sparring, Impulse, abgelegte Antworten)
aufgaben.md         alle To-Dos, eine Datei
asset-foundation.md Kundensprache, geclustert, wächst mit jedem Kundengespräch
output/
  posts/            LinkedIn-Drafts
  mails/            Mail-Entwürfe
  angebote/         Angebots-Entwürfe
bonus/              Ausbaustufen zum Nachbauen, nicht Teil des Grundsetups
teilnehmer/         Hackathon: pro Person ein Ordner mit Website-Auszug, Kontext, Übungstranskripten
demo/               entsteht nach /setup: die verschobenen Demo-Daten
.claude/skills/     ingest, lint, foundation, post, mail, angebot, setup, website, fake-transkript (je mit learnings.md)
```

## Konventionen

- Dateien: `YYYY-MM-DD_art_beschreibung.md`. Seiten im Wiki heißen immer `brief.md`, der Ordnername trägt die Entität (`<firma-slug>`, `<person-slug>`, `<YYYY-MM>`).
- Verarbeitete Dokumente wandern aus `inbox/` nach `<entität>/raw/`, damit der Eingang leer bleibt. Der Dateiname bleibt dabei unverändert.
- Pfade in Wiki, Index, Log und Aufgaben immer vom Repo-Root aus (`wiki/kunden/lumeo/brief.md`).
- Jede Ausgabedatei nennt oben ihre Quelle.
- Sprache: Deutsch. Keine Em-Dashes, keine Gedankenstriche, stattdessen Punkt, Komma, Doppelpunkt.
