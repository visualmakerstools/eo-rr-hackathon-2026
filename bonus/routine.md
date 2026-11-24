# Bonus: Den Transkript-Skill zeitgesteuert laufen lassen

Der `transkript`-Skill lässt sich jedes Mal im Chat tippen. Der eigentliche Sprung passiert, wenn er von allein läuft, ohne dass dafür ein Chat offen sein muss.

## Weg 1: Routine bzw. Scheduled Task in Claude

Claude Code kennt geplante Läufe (Scheduled Tasks / Routinen). Damit lässt sich hinterlegen: "führe `/transkript` jeden Werktag um 12:00 und 17:00 in diesem Repo aus." Der Lauf passiert im Hintergrund, das Ergebnis liegt danach einfach im Repo.

Vorteil: kein eigener Server nötig, läuft über die gleiche Umgebung wie der Chat.

## Weg 2: Cron-Job

Für alle, die lieber auf der eigenen Maschine automatisieren:

```bash
cd /pfad/zum/repo && claude -p "/transkript"
```

Das als Cron-Eintrag hinterlegen, zum Beispiel zweimal werktags:

```
0 12 * * 1-5 cd /pfad/zum/repo && claude -p "/transkript"
0 17 * * 1-5 cd /pfad/zum/repo && claude -p "/transkript"
```

Vorteil: volle Kontrolle über Zeitpunkt und Umgebung. Nachteil: die Maschine muss zu dem Zeitpunkt laufen und online sein.

## Die Marker-Datei `.last-run`

Nach jedem Lauf schreibt der Skill den Zeitstempel in `.last-run` (Root des Repos, per `.gitignore` ausgeschlossen). Damit ist jederzeit nachvollziehbar, wann zuletzt verarbeitet wurde, auch ohne die Chat-Historie durchzusehen.

## Die eigentliche Statusanzeige ist der leere Ordner

Der `inbox/`-Ordner ist der einzige Eingang. Ist er leer, ist alles verarbeitet. Ist etwas drin, wartet es auf den nächsten Lauf. Kein Dashboard nötig, ein Blick in den Ordner reicht.

## Das ist der Punkt, an dem das System ohne offenen Chat arbeitet

Sobald eine Routine oder ein Cron-Job läuft, kommt die Verarbeitung von allein. Ein Transkript landet in `inbox/`, der nächste geplante Lauf holt es ab, Notiz und Aufgaben entstehen, ohne dass jemand tippen musste. Der Chat wird dann zum Ort, an dem man die Ergebnisse ansieht und Feedback gibt, nicht mehr zum Ort, an dem man sie anstößt.
