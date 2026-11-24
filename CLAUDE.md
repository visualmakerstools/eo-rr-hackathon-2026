# Mein Company-OS

Dieses Repo ist mein Betriebssystem. Gespräche kommen rein, verwertbare Arbeit kommt raus.

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

- **Notiz:** Ich verstehe in 30 Sekunden, was besprochen wurde und was jetzt ansteht, ohne das Transkript zu lesen.
- **Aufgabe:** Selbsterklärender Titel plus so viel Kontext, dass ich sie in zwei Wochen noch verstehe.
- **Post:** Eine Kernaussage, ein konkreter Aufhänger aus einem echten Gespräch, kein "Was denkt ihr?" am Schluss.
- **Mail:** Kürzer, als ich denke. Ein klarer nächster Schritt. Klingt nach mir, nicht nach Vorlage.
- **Angebot:** Konkreter Umfang, konkreter Preis, konkrete Ergebnisse. Nie generisch, nie vage.

Wenn etwas nicht im Transkript steht, wird es nicht erfunden. Dann kommt `[offen: im nächsten Call klären]` rein.

---

## Das Routing

Das ist die wichtigste Tabelle im Repo. Sie entscheidet, was nach einem Gespräch von allein passiert.

| Kategorie | Woran erkennbar | Was danach automatisch läuft |
|-----------|-----------------|------------------------------|
| **Kundengespräch** | Externe Person, Bedarf, Budget, Angebot, nächster Schritt | Notiz + Aufgaben + `foundation` (Kundensprache einweben) + `angebot` als Entwurf + `mail` als Follow-up |
| **Team-Meeting** | Interne Runde, Abstimmung, Status, Entscheidungen | Notiz + Aufgaben mit Zuständigkeit |
| **Sparring / Impuls** | Podcast, Beratungsgespräch, lautes Denken, Konferenz | Notiz + `post` als Draft |
| **Sonstiges** | Passt in keine der drei | nur Notiz + Aufgaben |

Bei mehreren passenden Kategorien gewinnt die spezifischere. Bei Unklarheit fragt der `transkript`-Skill genau einmal nach, statt zu raten.

**Das ist deine Stellschraube.** Schreib deine eigenen Kategorien in diese Tabelle und die Maschine läuft anders. Ein Coach hat vielleicht "Klientensitzung". Ein Steuerberater "Mandantengespräch". Eine Produktchefin "User-Interview".

---

## Ordner

```
inbox/              Transkript reinwerfen, das ist der einzige Eingang
meetings/           verarbeitete Notizen, eine Datei pro Gespräch
aufgaben.md         alle To-Dos, eine Datei
asset-foundation.md Kundensprache, geclustert, wächst mit jedem Gespräch
output/
  posts/            LinkedIn-Drafts
  mails/            Mail-Entwürfe
  angebote/         Angebots-Entwürfe
bonus/              Ausbaustufen zum Nachbauen, nicht Teil des Grundsetups
teilnehmer/         Hackathon: pro Person ein Ordner mit Website-Auszug, Kontext, Übungstranskripten
demo/               entsteht nach /setup: die verschobenen Demo-Daten
```

## Konventionen

- Dateien: `YYYY-MM-DD_kategorie_beschreibung.md`
- Verarbeitete Transkripte wandern aus `inbox/` nach `meetings/raw/`, damit der Eingang leer bleibt
- Jede Ausgabedatei nennt oben ihre Quelle
- Sprache: Deutsch. Keine Em-Dashes, kurze Bindestriche.
