# Teilnehmer

Hier liegt pro Person ein Ordner `teilnehmer/<slug>/`. Der Slug ist der Firmenname in kebab-case (zum Beispiel `mueller-steuerberatung`).

Das VM-Team hat die Ordner vorab vorbereitet. Drin liegen:

- `profil.md`: wer du bist, kurz
- `website.md`: Auszug von deiner öffentlichen Website (Angebot, Zielgruppe, wie ihr über euch sprecht)
- `claude-kontext.md`: vorausgefüllter Kontext für die `CLAUDE.md` (die vier Blöcke plus Routing)
- `inbox/`: 2-3 fiktive Transkripte zum Üben

Mit `/setup <dein-slug>` stellst du das Repo auf deine Firma um. Die Demo-Daten wandern dabei nach `demo/`, nichts geht verloren.

## Du stehst nicht auf der Liste?

Dann nutz `/website <url>`. Claude liest deine Website, legt deinen Ordner an und füllt Website-Auszug und Kontext. Danach `/fake-transkript <slug>` für Übungsmaterial und `/setup <slug>`.

## Eigene Transkripte

Echte Gespräche legst du direkt in `inbox/` im Repo-Root. Wenn du Transkripte für deinen Ordner vorbereitest, gilt diese Namenskonvention:

```
YYYY-MM-DD_transkript_<art>-<gegenueber>.md
```

Beispiele: `2026-11-05_transkript_kundengespraech-bauunternehmen-krause.md`, `2026-11-12_transkript_sparring-podcast-mittelstand.md`.

## Vorlage

`_vorlage/` ist das leere Gerüst für neue Ordner. Nicht direkt benutzen, sondern kopieren.

---

*Website-Auszüge stammen von öffentlichen Websites. Transkripte in diesem Ordner sind fiktiv, Personen auf Kundenseite und alle Zahlen sind erfunden.*
