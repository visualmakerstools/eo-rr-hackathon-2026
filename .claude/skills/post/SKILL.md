---
name: post
description: Schreibt einen LinkedIn-Post-Draft nach output/posts/YYYY-MM-DD_slug.md, aus einem Brief aus wiki/ (z.B. wiki/themen/<slug>/brief.md), einem Messaging-Goldstück aus asset-foundation.md oder einem Thema. Wird vom ingest-Skill nach Sparring-/Impuls-Gesprächen aufgerufen, kann aber auch direkt vom User mit einem Thema gestartet werden.
---

# Post

Schreibt einen einzelnen LinkedIn-Post-Draft im eigenen Stil.

## Immer zuerst lesen

Die eigene `learnings.md` neben dieser Datei, noch vor allem anderen.

`CLAUDE.md` im Repo-Wurzelverzeichnis, besonders die Abschnitte "Wie ich klinge" und "Was ein gutes Ergebnis ist". Dazu `asset-foundation.md` für Kundensprache und Messaging-Goldstücke.

## Ablauf

### 1. Quelle klären

Ein Brief aus `wiki/themen/<slug>/` (typisch Art Sparring/Impuls) oder ein Kundenbrief aus `wiki/kunden/`, ein Messaging-Goldstück aus `asset-foundation.md`, oder ein Thema vom User.

### 2. Cluster-Bezug herstellen

Wenn die Foundation einen passenden Cluster hergibt: für wen ist der Post, welcher Pain wird adressiert? Der Post spricht die Sprache des Clusters, nicht die eigene Fachsprache.

### 3. Draft schreiben

- **Hook in Zeile 1:** konkrete Szene, Kundenzitat oder überraschende Zahl. Nie das Thema ankündigen.
- **Kurze Absätze**, max. 2-3 Zeilen.
- **Eine Kernaussage**, nicht drei.
- **Abschluss:** klarer Takeaway oder eine spezifische Frage, kein "Was denkt ihr?"-Reflex.

Do's: Kundensprache aus der Foundation, konkrete Zahlen statt Rundwerte, eigene Learnings zeigen, Zeilenumbrüche als Rhythmus.

Don'ts: Em-Dashes, Meta-Ebene ("Viele von euch kennen das"), Clickbait ohne Substanz, Buzzword-Ketten (disruptiv, game-changing), Emoji-Aufzählungs-Tapete, Menschen als "Köpfe" oder "Ressourcen".

### 4. Vertraulichkeit

Kundenzitate nur anonymisiert ("ein Vertriebsleiter eines IT-Security-Dienstleisters"), außer der Kunde hat der Nennung zugestimmt.

### 5. Ablegen und zeigen

Nach `output/posts/YYYY-MM-DD_slug.md`:

```markdown
# [Arbeitstitel]

**Status:** Draft v1
**Quelle:** [wiki/... / Foundation-Goldstück / Thema]
**Cluster:** [aus asset-foundation.md, falls zutreffend]

## v1

[Post-Text]
```

Draft im Chat zeigen und auf Feedback warten. Nie selbst als final markieren.

## Grenzen

- Nie erfinden. Zahlen und Zitate kommen aus der Quelle oder der Foundation, sonst bleiben sie weg.
- Nie versenden oder posten, nur der Entwurf.
