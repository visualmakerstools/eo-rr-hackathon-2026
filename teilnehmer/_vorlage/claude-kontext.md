# Kontext für CLAUDE.md

> Diese vier Blöcke plus das Routing ersetzen beim `/setup` die gleichnamigen Abschnitte in `CLAUDE.md`. Die Hinweise in eckigen Klammern beim Ausfüllen löschen.

## Wer wir sind

[2-3 Sätze: Was macht die Firma, für wen, womit unterscheidet sie sich. Dann ein Satz zur typischen Kundschaft: Branche, Größe, Region.]

## Was wir anbieten

| Leistung | Was passiert | Dauer | Aufwand |
|----------|--------------|-------|---------|
| [offen: ergänzen] | [Was der Kunde konkret bekommt] | [offen: ergänzen] | [offen: ergänzen] |

[Satz zu Preisen: Wie wird abgerechnet, was nennt ihr im Gespräch, was steht im Angebot. Unbekannte Preise als `[offen: ergänzen]`.]

## Wie ich klinge

[4-6 Stichpunkte zum Stil: Perspektive, Ton, Du/Sie, Sprache. Dann eine Zeile "Nie:" mit dem, was in keinem Text vorkommen soll.]

## Was ein gutes Ergebnis ist

- **Wiki-Seite (Brief):** [Woran erkennst du, dass eine Wiki-Seite taugt?]
- **Aufgabe:** [...]
- **Post:** [...]
- **Mail:** [...]
- **Angebot:** [...]

Wenn etwas nicht im Dokument steht, wird es nicht erfunden. Dann kommt `[offen: im nächsten Call klären]` rein.

## Das Routing

Arten an das Geschäft anpassen: Ein Steuerberater hat "Mandantengespräch", ein Coach "Klientensitzung", eine Produktchefin "User-Interview". Die fünf Standardrollen (externes Gespräch mit Angebot, Mitarbeitergespräch, Finanzzahlen, Sparring/Impuls, Sonstiges) bleiben, nur die Namen, Erkennungsmerkmale und Wiki-Bereiche ändern sich. Die Bereiche sollen zu deinen eigenen Units oder Abteilungen passen.

| Art | Woran erkennbar | Wohin im Wiki | Was danach läuft |
|-----|-----------------|---------------|------------------|
| **[Art für Gespräche mit Interessenten oder Kundschaft]** | [Externe Person, Bedarf, Budget, nächster Schritt] | `wiki/kunden/<firma>/` | Brief + Aufgaben + `foundation` + `angebot` als Entwurf + `mail` als Entwurf |
| **[Mitarbeitergespräch]** | [Eine Person aus dem Team, Zufriedenheit, Entwicklung, Vereinbarungen] | `wiki/team/<person>/` | Brief + Aufgaben. Vertraulich, kein Output |
| **[Finanzzahlen]** | [BWA oder Tabelle mit Monatswerten] | `wiki/finanzen/<YYYY-MM>/` | Brief mit Kennzahlen, Abweichungen zum Vormonat, Aufgaben |
| **[Sparring / Impuls]** | [Podcast, Austausch unter Gründern, lautes Denken] | `wiki/themen/<slug>/` | Brief + `post` als Draft |
| **Sonstiges** | Passt in keine der vier | nur Log-Eintrag | Aufgaben, nachfragen ob ins Wiki |

Bei mehreren passenden Arten gewinnt die spezifischere. Bei Unklarheit fragt der `ingest`-Skill genau einmal nach, statt zu raten.
