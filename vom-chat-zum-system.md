# Vom Chat zum System

Wie du einen eigenen Prozess baust, der ohne dich weiterläuft.

Fast alle nutzen KI heute im Chat. Man fragt, bekommt etwas, kopiert es raus. Das Ergebnis ist oft gut, aber die Arbeit bleibt trotzdem bei dir: Du bist der Kontext, du bist der Auslöser, du bist die Ablage. Der Sprung, um den es hier geht, ist der von "ich frage etwas" zu "es passiert etwas".

## Fünf Stufen

| Level | Name | Was das heißt |
|-------|------|---------------|
| 01 | Toolbox | Du machst alles. AI hilft nur. |
| 02 | Memory | Du machst die Arbeit, aber mit einem System, das sich erinnert. |
| 03 | Micromanager | Human in the loop. AI arbeitet Schritt für Schritt, du gibst jeden Schritt frei. |
| 04 | Macromanager | Human on the loop. AI arbeitet end-to-end, du gibst nur das Ergebnis frei. |
| 05 | Outcome | Nicht mehr Output, sondern Ziel. Das System misst selbst, ob es funktioniert hat. |

Die meisten sitzen auf 01 und glauben, das nächste Tool bringt sie auf 04. Tut es nicht. Der Unterschied zwischen 01 und 03 ist keine Tool-Frage, sondern eine Frage der Vorbereitung.

Dieses Repo liegt auf **Level 03 bis 04**: Der Ingest-Lauf arbeitet end-to-end durch, aber Mails und Angebote bleiben Entwürfe, bis du sie freigibst.

## Drei Voraussetzungen

Bevor irgendein Prozess autonom laufen kann, brauchst du diese drei. Keine davon ist eine Tool-Frage, deshalb kommt man mit einem neuen Tool auch nicht weiter.

**Kontext.** Die AI muss wissen, wer ihr seid, was ihr verkauft und wie ihr klingt. Und sie muss zum richtigen Zeitpunkt auf das richtige Stück Hintergrundwissen zugreifen. Alles auf einmal ist so unbrauchbar wie nichts.

**Zugriff.** Sie muss in die Systeme rein, in denen die Arbeit wirklich passiert. Ein Agent, der nur im Chatfenster lebt, kann nichts abnehmen.

**Sicherheit.** Sie muss wissen, was sie darf, was sie nicht darf und was nie ohne dich passiert. Datenschutz gehört hierher, nicht zu Zugriff: Die Frage ist nicht, ob die AI an Daten darf, sondern welche und mit welcher Regel.

In diesem Repo: Kontext steht in `CLAUDE.md`. Zugriff ist erstmal nur das Dateisystem, mehr braucht der erste Prozess nicht. Sicherheit steht als "Grenzen" am Ende jedes Skills.

## Die fünf Schritte

In dieser Reihenfolge, nicht in einer anderen. Wer bei Schritt 4 anfängt, baut Skills ohne Kontext und wundert sich, dass die Ergebnisse beliebig sind.

### 1. Kontext, Zugriff und Guardrails festlegen

Entscheide, worauf das System zugreifen darf und was nie ohne dich passiert. Fang eng an: nur dieses Repo, nichts wird verschickt. Erweitern kannst du immer noch.

### 2. Unternehmenswissen explizit machen

Das, was in Gesprächen, Decks und Slack steckt, muss an einen Ort, den eine Maschine lesen kann. Vier Fragen reichen für den Anfang:

- Warum existiert das Unternehmen, und wo soll es in drei Jahren stehen?
- Was verkauft ihr genau, zu welchen Konditionen?
- Wer kauft das, und mit welchen Worten beschreibt diese Person ihr Problem?
- Wie klingt ihr, und was sagt ihr nie?

Das ist genau der Inhalt von `CLAUDE.md` und `asset-foundation.md` in diesem Repo. Dazu kommt das Wiki unter `wiki/`: Es hält fest, was ihr über einzelne Kunden, Menschen und Monate wisst, und wächst mit jedem Dokument. Die Foundation ist der Sonderfall: Sie schreibt sich nach dem ersten Mal selbst fort, weil jedes Kundengespräch neue Kundensprache liefert.

Diesen Schritt überspringt fast jeder, und danach klingen alle Ergebnisse nach niemandem.

### 3. Den ersten Prozess explizit machen

Such dir einen Prozess, den du oft machst und der dich nervt. Dann schreib auf, wie er wirklich läuft, nicht wie er laufen sollte:

- Was ist der Auslöser? (Bei uns: eine Datei landet in `inbox/`.)
- Welche Schritte gehst du, in welcher Reihenfolge?
- Woher kommt an jedem Schritt die Information?
- Woran erkennst du, dass das Ergebnis gut ist?
- Was darf auf keinen Fall automatisch passieren?

Die letzte Frage ist die wichtigste. Sie bestimmt, ob du auf Level 03 oder 04 landest.

### 4. Skills dafür bauen

Ein Skill ist eine Markdown-Datei mit einer Anleitung. Mehr nicht. Er wohnt in `.claude/skills/<name>/SKILL.md`, hat oben zwei Zeilen Metadaten und darunter den Ablauf in Prosa.

Zwei Regeln, die den Unterschied machen:

**Der Skill bleibt dünn.** Der ganze Kontext steht in `CLAUDE.md`, nicht im Skill. Sonst pflegst du dieselbe Information an fünf Stellen und irgendwann widersprechen sie sich.

**Ein Skill, ein Job.** Der `ingest`-Skill hier sortiert ein und routet. Er schreibt keine Posts, dafür ruft er `post` auf. Das klingt umständlich und ist der Grund, warum du einzelne Teile austauschen kannst, ohne alles anzufassen.

Am schnellsten baust du einen Skill, indem du Claude im Chat den Prozess einmal machen lässt, ihn korrigierst bis er stimmt, und dann sagst: "Schreib daraus einen Skill."

### 5. Den Prozess agentisieren

Jetzt kommt der Sprung. Bisher tippst du `/ingest`. Ab jetzt läuft es von allein.

Drei Dinge machen aus einem Skill einen Prozess:

**Ein Auslöser, der nicht du bist.** Ein Zeitplan, ein Ordner, der beobachtet wird, ein eingehendes Ereignis. In `bonus/routine.md` steht, wie das hier geht.

**Ein Router statt eines Kommandos.** Nicht du entscheidest, was passieren soll, sondern eine Regel. Genau dafür ist die Routing-Tabelle in `CLAUDE.md` da: Kategorie rein, Folgeprozess raus. Sie ist die eine Stelle, an der du das Verhalten des ganzen Systems änderst.

**Eine Übergabestelle zwischen Skills.** Der `ingest`-Skill legt eine Wiki-Seite ab und gibt den Pfad an `post` weiter. Zwei Skills, die sich unterhalten, ohne dass du dazwischen sitzt. Das ist der eigentliche Moment, in dem Agents aus dem Chat aussteigen.

## Die Stufen eines Wikis

Ein Wiki aus Markdown-Dateien wächst in fünf Stufen. Du musst nicht alle auf einmal bauen.

1. **Ablage:** Originale landen sortiert in `raw/` und werden nie verändert.
2. **Verzeichnis:** `wiki/index.md` listet jede Seite mit einem Einzeiler, damit Claude (und du) nicht suchen müssen.
3. **Ingest:** Neue Dokumente werden nicht nur abgelegt, sondern in die bestehende Seite eingearbeitet, mit Verlauf und Quelle.
4. **Pflege:** `/lint` findet tote Verweise, veraltete Seiten und Widersprüche, bevor sie jemand im Gespräch bemerkt.
5. **Lernen:** Korrekturen werden zu Regeln in der `learnings.md` neben dem Skill, und der nächste Lauf liest sie.

## Der Learning Loop

Ein automatisierter Prozess ist ab Tag eins veraltet. Was ihn lebendig hält, ist deine Korrektur.

```
01  Der Lauf produziert ein Ergebnis
02  Du korrigierst, oder gibst frei
03  Das System untersucht die Korrektur: wo, warum, welches Muster
04  Das Muster wird als Regel gespeichert
05  Der nächste Lauf testet dagegen
```

Der Trick steckt in Schritt 03. "Der Text war nicht gut" ist keine Information. "Das war zu lang, wieder mal, und zwar immer an derselben Stelle" ist eine Regel.

Praktisch: Neben jedem Skill liegt eine `learnings.md` (`.claude/skills/<skill>/learnings.md`), und der Skill liest sie als ersten Schritt vor jedem Lauf. Wenn du etwas zum zweiten Mal korrigierst, sag: "Schreib das in die Learnings." Dann kommt eine Zeile mit Datum, Anlass und Regel dazu. Einmal pro Woche 15 Minuten durchgehen, und höchstens eine Regel pro Woche in die `CLAUDE.md` hochziehen, sonst wird sie unlesbar. Nach zwei Wochen sind die Learnings die wertvollsten Dateien im Repo, weil dort dein Bauchgefühl steht, explizit gemacht.

## Wo du anfängst

Nimm den Prozess, den du diese Woche mindestens dreimal machst. Nicht den wichtigsten, nicht den größten. Den, der oft genug passiert, dass du die Korrekturschleife noch vor dem Wochenende zweimal durchläufst.

Level 03 an einem echten Prozess ist mehr wert als Level 05 auf dem Papier.
