---
name: lint
description: Prüft das Wiki auf Ordnung und Widersprüche und schlägt Korrekturen vor. Findet Seiten ohne Index-Eintrag, Einträge ohne Datei, tote Verweise, unvollständiges Frontmatter, fehlende Originale in raw/, veraltete aktive Briefe und widersprüchliche Angaben zwischen Seiten. Nutze diesen Skill bei "/lint", "Wiki aufräumen", "Wiki prüfen" oder "stimmt das Wiki noch".
---

# Lint

Das Wiki aufräumen. Prüft nur, ändert erst nach Freigabe. Lint ändert keine Wiki-Inhalte, schreibt aber nach dem Lauf genau eine Zeile in `wiki/log.md` (das ist erlaubt).

## Ablauf

1. **Lesen:** zuerst die eigene `learnings.md` neben dieser Datei, dann `wiki/index.md` und `wiki/log.md`.
2. **Prüfen**, über alle `brief.md` unter `wiki/` (`wiki/_vorlage/` ist von allen Prüfungen ausgenommen):
   - Seite ohne Zeile im Index
   - Index-Zeile ohne Datei
   - tote Verweise (`verweise` im Frontmatter oder Pfade im Text)
   - Frontmatter unvollständig (`typ`, `name`, `status`, `erstellt`, `zuletzt_aktualisiert`, `quellen`, `verweise`)
   - `quellen` zeigt auf eine raw-Datei, die es nicht gibt
   - Status `aktiv`, aber `zuletzt_aktualisiert` älter als 90 Tage, gerechnet gegen das heutige Datum
   - Widersprüche zwischen Seiten (z.B. unterschiedliche Zahlen oder Termine zur selben Sache)
3. **Befundliste** ausgeben: pro Befund Seite, was nicht stimmt, Vorschlag zur Korrektur. Keine Befunde: das in einem Satz sagen.
4. **Ändern nur nach Freigabe.** Der User sagt, welche Vorschläge umgesetzt werden. Jede Änderung geht in Index und Log.
5. **Log:** das Ergebnis des Laufs als eine Zeile in `wiki/log.md`, z.B. `- YYYY-MM-DD · lint · 4 Befunde, 2 behoben (Pfade)`.

## Grenzen

- Ohne Freigabe keine Wiki-Inhalte ändern, auch nichts "nur kurz geradeziehen". Einzige Ausnahme: die Log-Zeile des Laufs.
- `raw/` nie ändern.
- Nichts erfinden. Bei Widersprüchen nicht entscheiden, welche Zahl stimmt, sondern beide Quellen nennen und fragen.
