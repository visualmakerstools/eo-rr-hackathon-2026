# Company-OS Starter

Ein Betriebssystem für dein Unternehmen, das in Dateien lebt statt im Chatfenster.

Du wirfst ein Gesprächs-Transkript in einen Ordner. Claude erkennt, was für ein Gespräch das war, schreibt eine Notiz, zieht die Aufgaben raus und startet je nach Kategorie den nächsten Schritt: einen LinkedIn-Draft, ein Follow-up, einen Angebots-Entwurf. Ohne dass du dabei zusiehst.

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

In `inbox/` liegt ein unverarbeitetes Transkript: das Erstgespräch mit NordSecure. In `meetings/` liegen drei Gespräche, die schon durch die Maschine gelaufen sind. In `asset-foundation.md` steckt, was das System aus diesen drei Gesprächen über die Kundschaft gelernt hat.

**3. Die Maschine anwerfen**

```
/transkript
```

Schau zu: Der Skill erkennt die Kategorie, schreibt die Notiz, hängt Aufgaben an, webt die Kundensprache in die Foundation ein und legt einen Angebots- und einen Mail-Entwurf in `output/` ab. Danach ist `inbox/` leer.

**4. Das Routing umschreiben**

Öffne `CLAUDE.md` und geh zur Tabelle unter "Das Routing". Das ist die Stellschraube des ganzen Systems. Ändere eine Kategorie in etwas, das es bei dir wirklich gibt, und lass `/transkript` nochmal laufen. Die Maschine läuft anders.

**5. Deinen Kontext einsetzen**

In `CLAUDE.md` stehen vier Blöcke: wer ihr seid, was ihr anbietet, wie du klingst, was ein gutes Ergebnis ist. Ersetze sie durch deine eigenen Angaben. Danach arbeiten alle Skills für dich statt für die Demo.

## Wie es aufgebaut ist

```
inbox/              Transkript reinwerfen, der einzige Eingang
meetings/           verarbeitete Notizen, raw/ enthält die Originale
aufgaben.md         alle To-Dos in einer Datei
asset-foundation.md was du über deine Kundschaft weißt, in ihren Worten
output/             posts/, mails/, angebote/
bonus/              Ausbaustufen: Mail-Radar, zeitgesteuerte Läufe
CLAUDE.md           dein Kontext und das Routing
.claude/skills/     transkript (der Router) + foundation, post, mail, angebot
```

Die Skills sind absichtlich kurz. Der ganze Kontext steht in `CLAUDE.md`, damit du an einer Stelle schraubst und nicht an fünf.

## Was hier bewusst fehlt

Kein Dashboard, keine Datenbank, keine Integration. Ein Ordner ist der Status, eine Datei ist ein Vorgang. Das klingt zu einfach und ist genau der Punkt: Du kannst jederzeit reinschauen, es von Hand korrigieren und es versteht auch jemand, der nie in dieses Repo geguckt hat.

## Weiter

**[vom-chat-zum-system.md](vom-chat-zum-system.md)** ist die Anleitung: die fünf Autonomie-Stufen, die drei Voraussetzungen, und in fünf Schritten von einem Prozess in deinem Kopf zu einem, der ohne dich läuft. Lies das, wenn du deinen eigenen Prozess bauen willst statt nur die Demo anzuschauen.

`bonus/routine.md` zeigt, wie der Transkript-Lauf zeitgesteuert startet, ohne dass du einen Chat offen hast.
`bonus/gmail-radar.md` zeigt, wie du deinen Posteingang anschließt.

---

*Alle Firmen, Namen, Zahlen und Zitate in diesem Repo sind erfunden.*
