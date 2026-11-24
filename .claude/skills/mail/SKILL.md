---
name: mail
description: Schreibt einen Mail-Entwurf nach output/mails/YYYY-MM-DD_empfaenger_thema.md, typisch als Follow-up nach einem Kundengespräch. Wird vom transkript-Skill nach Kundengesprächen aufgerufen, funktioniert aber für jede Mail mit einem Thema vom User.
---

# Mail

Schreibt einen Mail-Entwurf, nie eine fertig versendete Mail.

## Immer zuerst lesen

`CLAUDE.md` im Repo-Wurzelverzeichnis, besonders Ton und die Kriterien für ein gutes Ergebnis. Dazu die zugehörige Notiz aus `meetings/`, wenn vorhanden.

## Ablauf

1. **Bezug finden:** was aus dem Gespräch oder Thema greift die Mail konkret auf? Kein generischer Dank, sondern ein echter Anknüpfungspunkt (ein Zitat, ein Punkt aus dem Gespräch, eine offene Frage).
2. **Nächsten Schritt festlegen:** genau einen, klar formuliert. Keine zwei parallelen Optionen anbieten.
3. **Schreiben:** kürzer, als man denkt. Duzen. Keine Preise nennen, Pricing gehört ins Gespräch oder ins Angebotsdokument.
4. **Ablegen** nach `output/mails/YYYY-MM-DD_empfaenger_thema.md`:

```markdown
**Betreff:** [Betreff]
**Empfänger:** [Name, Rolle]

[Mailtext]

---

## Woraus das kommt

- [referenzierte Stelle aus dem Gespräch, mit Zitat oder Fundstelle]
```

5. Entwurf im Chat zeigen und auf Feedback warten.

## Grenzen

- **Nie versenden.** Immer nur Entwurf, unabhängig davon wie eindeutig der nächste Schritt ist.
- Nie erfinden. Was nicht im Gespräch stand, wird nicht als Zusage formuliert.
- Keine Preise oder Rabatte in der Mail.
