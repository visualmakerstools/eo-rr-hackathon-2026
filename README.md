# Hackathon EO Rhine-Ruhr, 26.11.2026

Vier Stunden, ein Ziel: Du baust aus deinen Dokumenten ein Wiki, das mit jedem Gespräch wächst, und erzeugst daraus Antworten, Entwürfe und LinkedIn-Posts in deiner Sprache.

1. **Klonen und starten.** `git clone <repo-url> mein-os`, `cd mein-os`, `claude`.
2. **Umschauen.** Öffne `wiki/index.md`. Dort steht, was das Wiki schon weiß: drei Kunden aus früheren Gesprächen.
3. **Ingest.** `/ingest` auf die vier Dateien in `inbox/` (ein neues Kundengespräch, ein Folgegespräch, ein Mitarbeitergespräch, eine BWA). Schau zu, wie neue Seiten entstehen oder bestehende ergänzt werden und wie Index und Log wachsen.
4. **Frage ans Wiki.** Zum Beispiel: "Was wissen wir über Kranich Media und was ist offen?" Die Antwort kommt mit Quellpfad.
5. **Lint.** `/lint` prüft das Wiki auf tote Verweise, veraltete Seiten und Widersprüche.
6. **Eigenes Wiki.** `/setup <dein-slug>` stellt das Repo auf deine Firma um (Ordner unter `teilnehmer/`, vom VM-Team vorbereitet) und legt ein leeres Wiki an. Steht dein Ordner nicht da: `/website <url>` und danach `/fake-transkript <slug>`, dann `/setup <slug>`. Danach `/ingest` auf deine eigenen Dokumente und `/post` für Entwürfe.
7. **Learning Loop.** Korrigiere ein Ergebnis und sag: "Schreib das in die Learnings." Der Skill liest die Regel beim nächsten Lauf.

---

# Company-OS Starter

Ein Betriebssystem für dein Unternehmen, das in Dateien lebt statt im Chatfenster.

Du wirfst ein Dokument in einen Ordner: ein Gesprächs-Transkript, ein Mitarbeitergespräch, eine BWA. Claude erkennt, was es ist, sortiert es in ein Wiki ein (neue Seite oder Ergänzung einer bestehenden), zieht die Aufgaben raus und startet je nach Art den nächsten Schritt: einen LinkedIn-Draft, ein Follow-up, einen Angebots-Entwurf. Ohne dass du dabei zusiehst.

Das Repo ist mit fiktiven Demo-Daten gefüllt, damit du in fünf Minuten etwas laufen siehst. Danach ersetzt du sie durch deine eigenen.

## Was du brauchst

Claude Code (oder Cowork) und git. Das hier ist kein Tool zum Anklicken, sondern ein kleines System, das du selbst betreibst und veränderst.

## Loslegen

**1. Klonen und öffnen**

```bash
git clone <repo-url> mein-os
cd mein-os
claude
```

**2. Umschauen**

In `wiki/index.md` steht das Verzeichnis: drei Kunden (Lumeo, FinPeak, Kranich Media), die schon durch die Maschine gelaufen sind. Öffne eine `brief.md` und sieh dir den Aufbau an: Kurzbild, Stand, Verlauf, Zitate, Offene Punkte. In `inbox/` warten vier neue Dokumente. In `asset-foundation.md` steckt, was das System aus den Kundengesprächen über die Kundschaft gelernt hat.

**3. Die Maschine anwerfen**

```
/ingest
```

Schau zu: Der Skill erkennt die Art jedes Dokuments, legt die Wiki-Seite an oder schreibt die bestehende fort (das Folgegespräch mit Kranich Media ergänzt den Brief vom Erstgespräch und markiert, was sich geändert hat), verschiebt das Original nach `raw/`, hängt Aufgaben an und legt bei Kundengesprächen einen Angebots- und einen Mail-Entwurf in `output/` ab. Danach ist `inbox/` leer, und `wiki/index.md` und `wiki/log.md` sind gewachsen.

**4. Das Wiki befragen**

Stell eine Frage, zum Beispiel "Was wissen wir über Kranich Media und was ist offen?". Claude liest erst den Index, dann nur die passenden Seiten, und nennt den Quellpfad.

**5. Aufräumen**

```
/lint
```

Der Skill prüft das Wiki und gibt eine Befundliste mit Vorschlägen aus. Geändert wird erst nach deiner Freigabe.

**6. Das Routing umschreiben**

Öffne `CLAUDE.md` und geh zur Tabelle unter "Das Routing". Das ist die Stellschraube des ganzen Systems. Ändere eine Art in etwas, das es bei dir wirklich gibt, passe die Wiki-Bereiche an deine Units oder Abteilungen an und lass `/ingest` nochmal laufen. Die Maschine läuft anders.

**7. Deinen Kontext einsetzen**

In `CLAUDE.md` stehen vier Blöcke: wer ihr seid, was ihr anbietet, wie du klingst, was ein gutes Ergebnis ist. Ersetze sie durch deine eigenen Angaben, am schnellsten mit `/setup <slug>`. Danach arbeiten alle Skills für dich statt für die Demo.

**8. Lernen lassen**

Korrigiere ein Ergebnis, und wenn du dasselbe ein zweites Mal korrigierst: "Schreib das in die Learnings." Jeder Skill hat eine `learnings.md`, die er vor jedem Lauf liest.

## Wie es aufgebaut ist

```
inbox/              Dokument reinwerfen, der einzige Eingang
wiki/
  index.md          Verzeichnis aller Seiten
  log.md            Chronik, neueste oben
  _vorlage/         Seitenvorlage brief.md
  kunden/<firma>/   brief.md + raw/ (Originale)
  team/<person>/    brief.md + raw/ (vertraulich)
  finanzen/<YYYY-MM>/  brief.md + raw/
  themen/<slug>/    brief.md + raw/ (Sparring, Impulse, abgelegte Antworten)
aufgaben.md         alle To-Dos in einer Datei
asset-foundation.md was du über deine Kundschaft weißt, in ihren Worten
output/             posts/, mails/, angebote/
bonus/              Ausbaustufen: Mail-Radar, zeitgesteuerte Läufe
CLAUDE.md           dein Kontext, das Wiki-Regelwerk und das Routing
.claude/skills/     ingest und lint (Wiki) + foundation, post, mail, angebot, je mit learnings.md
```

Die Skills sind absichtlich kurz. Der ganze Kontext steht in `CLAUDE.md`, damit du an einer Stelle schraubst und nicht an fünf.

## Was hier bewusst fehlt

Kein Dashboard, keine Datenbank, keine Integration. Ein Ordner ist der Status, eine Datei ist eine Seite. Das klingt zu einfach und ist genau der Punkt: Du kannst jederzeit reinschauen, es von Hand korrigieren und es versteht auch jemand, der nie in dieses Repo geguckt hat.

## Weiter

**[vom-chat-zum-system.md](vom-chat-zum-system.md)** ist die Anleitung: die fünf Autonomie-Stufen, die drei Voraussetzungen, die Stufen eines Wikis und in fünf Schritten von einem Prozess in deinem Kopf zu einem, der ohne dich läuft. Lies das, wenn du deinen eigenen Prozess bauen willst statt nur die Demo anzuschauen.

`bonus/routine.md` zeigt, wie der Ingest-Lauf zeitgesteuert startet, ohne dass du einen Chat offen hast.
`bonus/gmail-radar.md` zeigt, wie du deinen Posteingang anschließt.

---

*Alle Firmen, Namen, Zahlen und Zitate in der Demo sind erfunden, auch das Mitarbeitergespräch und die BWA in `inbox/` (die CSV trägt keinen Hinweis im Kopf, damit sie sauber lesbar bleibt). Die Website-Auszüge unter `teilnehmer/` stammen von öffentlichen Websites, die Transkripte dort sind fiktiv.*
