---
name: website
description: Liest die öffentliche Website einer Firma und legt daraus einen Teilnehmer-Ordner an (website.md und claude-kontext.md in teilnehmer/<slug>/). Nutze diesen Skill bei "/website <url>", wenn jemand nicht auf der Teilnehmerliste steht, oder wenn aus einer Website ein Firmenkontext gebaut werden soll.
---

# Website

Baut aus einer öffentlichen Website den Startkontext für eine Firma.

## Immer zuerst lesen

`CLAUDE.md` (die vier Blöcke und das Routing als Muster) und `teilnehmer/_vorlage/`. Ohne die Vorlage weißt du nicht, welche Struktur gefragt ist.

## Ablauf

### 1. Seiten lesen

Per WebFetch die Startseite und bis zu fünf relevante Unterseiten: Leistungen oder Angebot, Über uns, Referenzen oder Cases, Team, ein Blog-Artikel. Mehr nicht. Kein Login, keine Formulare, robots.txt und Paywalls respektieren. Ist eine Seite nicht erreichbar, überspringen und in den Lücken vermerken.

### 2. Ordner anlegen

Slug aus dem Firmennamen in kebab-case (Umlaute ausgeschrieben: `mueller-steuerberatung`). Ordner `teilnehmer/<slug>/` aus `teilnehmer/_vorlage/` anlegen, falls er nicht existiert. Existiert er schon, nachfragen, bevor etwas überschrieben wird.

### 3. website.md befüllen

Nach der Struktur der Vorlage. Nur, was auf der Website steht. Wörtliche Claims als Zitat mit Quell-URL, 3 bis 6 Stück. Alles andere, vor allem Preise, Dauer, Teamgröße, bleibt `[offen: ergänzen]` und kommt in den Abschnitt Lücken. Quellen mit Abrufdatum auflisten.

### 4. claude-kontext.md befüllen

Die vier Blöcke und das Routing, aus `website.md` abgeleitet. Das Routing an das Geschäft anpassen: ein Steuerberater bekommt "Mandantengespräch", ein Coach "Klientensitzung", eine Agentur "Kundengespräch". Wie die Firma klingt, aus der Tonalität der Website ableiten (Du oder Sie, Stil). Duzen ist im Hackathon der Standard, weicht die Website ab, steht das als Hinweis dabei.

### 5. profil.md

Name der Person, falls auf der Website zu finden (Team- oder Impressumsseite), sonst `[offen: ergänzen]`. Firma, Website, Branche eintragen.

### 6. Bericht und nächster Schritt

Kurz melden: Slug, gelesene Seiten, wie viele Felder offen sind. Dann vorschlagen: `/fake-transkript <slug>` für Übungsmaterial, danach `/setup <slug>`.

## Grenzen

- Nur öffentliche Seiten, kein Login, keine Formulare.
- Nichts erfinden. Was nicht auf der Website steht, bleibt `[offen: ergänzen]`.
- Keine Kundennamen aus Referenzen als erfundene Gesprächspartner weiterverwenden, sie dienen nur als Beleg im Website-Auszug.
- Bestehende Ordner nicht ohne Rückfrage überschreiben.
