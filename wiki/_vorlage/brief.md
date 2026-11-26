---
typ: kunde            # kunde | team | finanzen | themen
name: Name der Firma, der Person oder des Monats
status: aktiv         # aktiv | ruhend | abgeschlossen
erstellt: YYYY-MM-DD
zuletzt_aktualisiert: YYYY-MM-DD
quellen:              # Pfade zu den Originalen in raw/, vom Repo-Root aus
  - wiki/<bereich>/<slug>/raw/YYYY-MM-DD_transkript_beschreibung.md
verweise: []          # andere Wiki-Seiten, z.B. wiki/kunden/lumeo/brief.md
---

# Name

<!-- Dies ist die Seitenvorlage. Kopieren, nicht direkt benutzen. Kommentare beim Ausfüllen löschen.
     Jede Aussage hat eine Quelle. Was nicht in den Quellen steht, wird nicht erfunden. -->

## Kurzbild

<!-- 2-3 Sätze: Wer ist das, worum geht es, wo stehen wir. Wer nur diesen Abschnitt liest, soll wissen, womit er es zu tun hat. -->

## Stand

<!-- Der aktuelle Stand in wenigen Zeilen. Wird bei jedem neuen Dokument überarbeitet.
     Zahlen und Fakten mit Quelle. Widersprüche zu früher: markieren, nicht still überschreiben,
     immer im Format `Start: 1. September (vorher: August)`. -->

## Verlauf

<!-- Datierte Einträge, neueste oben. Pro Eintrag: Datum, was war, Quelle als Pfad.
     Format:
     ### YYYY-MM-DD: Anlass
     - Kernpunkt mit Zahl oder O-Ton
     Quelle: wiki/<bereich>/<slug>/raw/<datei> -->

## Zitate

<!-- Nur bei typ kunde (bei den anderen Typen Abschnitt weglassen). Wörtliche Sätze in Anführungszeichen, mit Sprecher und Quelle.
     Daraus bauen Foundation, Posts und Angebote. -->

## Offene Punkte

<!-- Was unklar ist oder zu tun bleibt, jeweils als `[offen: ...]`. Erledigte Punkte nicht löschen,
     sondern im Verlauf als geklärt vermerken und hier streichen. -->

- [offen: ...]
