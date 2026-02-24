+++
title = "Anleitung: Beiträge über GitHub"
description = "Schritt-für-Schritt-Anleitung zum Bearbeiten von Seiten über den GitHub Web-Editor"
date = 2026-02-24
lastmod = 2026-02-24
draft = false
zielgruppe = "alle"
+++

Du brauchst **kein** Git, keine Kommandozeile und kein Programmierwissen. Alles passiert im Browser.

## Voraussetzung

Ein kostenloser GitHub-Account. [Hier registrieren](https://github.com/signup) (dauert 2 Minuten).

## Bestehende Seite bearbeiten

### Schritt 1: "Edit this page" klicken

Jede Seite auf dem VOST Hub hat unten einen Link **"Edit this page on GitHub"**. Klick darauf.

### Schritt 2: Anmelden

Wenn du nicht eingeloggt bist, fragt GitHub nach deinem Login. Danach landest du direkt im Editor.

### Schritt 3: Aenderungen vornehmen

Du siehst den Text der Seite im Markdown-Format. Markdown ist einfach:

| Was du willst | Was du schreibst |
|---|---|
| **Fett** | `**Fett**` |
| *Kursiv* | `*Kursiv*` |
| Überschrift | `## Überschrift` |
| Link | `[Linktext](https://url.de)` |
| Aufzählung | `- Punkt 1` |

Ändere den Text direkt im Editor. Du kannst zwischen "Edit" und "Preview" wechseln um deine Änderungen zu prüfen.

### Schritt 4: Änderung vorschlagen

1. Scrolle nach unten zu **"Commit changes"**
2. Schreib eine kurze Beschreibung was du geändert hast (z.B. "Tippfehler korrigiert" oder "Tool-Empfehlung ergänzt")
3. Wähle **"Create a new branch for this commit and start a pull request"**
4. Klick auf **"Propose changes"**

### Schritt 5: Pull Request erstellen

GitHub zeigt dir eine Zusammenfassung. Klick auf **"Create pull request"**. Fertig — ein Maintainer prüft deine Änderung und schaltet sie frei.

## Neue Seite erstellen

1. Gehe zum [Content-Ordner auf GitHub](https://github.com/phismith91/vost-hub/tree/main/content)
2. Navigiere in den passenden Unterordner (z.B. `wissen/` für einen AAR)
3. Klick auf **"Add file" → "Create new file"**
4. Gib einen Dateinamen ein (z.B. `mein-beitrag.md`)
5. Füge oben den Kopfbereich ein:

```
+++
title = "Dein Seitentitel"
description = "Kurze Beschreibung"
date = 2026-02-24
draft = false
+++

Dein Text hier.
```

6. Folge Schritt 4 und 5 von oben

## Hilfe

Falls du nicht weiterkommst:
- Erstell ein [Issue auf GitHub](https://github.com/phismith91/vost-hub/issues/new) — beschreibe was du beitragen möchtest
- Oder nutze das [Einreichungsformular](/mitmachen/beitrag-einreichen/) — ganz ohne GitHub
