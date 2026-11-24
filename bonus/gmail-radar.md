# Bonus: Gmail-Radar

Nicht Teil des Grundsetups, sondern eine Anleitung zum Nachbauen, wenn das Transkript-Routing läuft und der logische nächste Schritt ansteht: die Inbox selbst.

## Idee

Ein Skill, der die Gmail-Inbox scannt, Threads erkennt die eine Antwort brauchen, und sendefertige Kurz-Entwürfe im eigenen Ton anlegt. Genau wie `mail`, nur dass die Quelle nicht ein Gespräch ist, sondern eine unbeantwortete Mail.

## Was der Connector kann und was nicht

Der Gmail-Connector in Claude Code kann Mails **lesen** und **Drafts anlegen**. Er kann nicht senden. Das ist Absicht, nicht Einschränkung: jede Mail geht erst durch dich, bevor sie raus darf.

## Setup

1. Gmail-Connector in Claude Code verbinden (OAuth-Flow über Google, einmalig). Rechne mit ein paar Minuten für die Berechtigungsfreigabe, Google zeigt eine Liste an Scopes an, die bestätigt werden müssen.
2. Nur Lese- und Draft-Berechtigung freigeben, keine Sende- oder Lösch-Rechte. Wenn der Connector mehr anbietet, das explizit einschränken.
3. Prüfen, ob der Connector in diesem Repo oder projektübergreifend verbunden werden soll. Für ein persönliches Company-OS spricht viel für projektübergreifend.

## Wie der Skill aussehen könnte

Gleicher Aufbau wie die vier Skills hier: dünn, mit Verweis auf `CLAUDE.md` für Ton und Kontext.

- **Input:** Inbox scannen, ungelesene oder unbeantwortete Threads der letzten X Tage.
- **Filter:** welche Threads brauchen wirklich eine Antwort? Newsletter, automatische Benachrichtigungen und bereits beantwortete Threads rausfiltern.
- **Draft anlegen:** pro Thread, der eine Antwort braucht, einen kurzen Entwurf im eigenen Ton (siehe `CLAUDE.md`, Abschnitt "Wie ich klinge") als Gmail-Draft ablegen, nicht als Datei im Repo.
- **Bericht:** im Chat eine Liste der angelegten Drafts mit Betreff und einem Satz Begründung, warum dieser Thread eine Antwort braucht.

## Aufwand ehrlich eingeordnet

Das ist kein Fünf-Minuten-Skill. Der OAuth-Setup ist einmalig, aber die Filterlogik (was braucht wirklich eine Antwort, was ist Rauschen) braucht ein paar Testläufe, bis sie zuverlässig läuft. Rechne mit Nachjustieren, wie beim Transkript-Routing am Anfang auch.

## Warum das der nächste Schritt ist

Das Transkript-Routing verarbeitet, was aus Gesprächen kommt. Die Inbox ist der zweite große Strom an unstrukturiertem Input, der täglich Antworten braucht. Gleiches Prinzip, andere Quelle.
