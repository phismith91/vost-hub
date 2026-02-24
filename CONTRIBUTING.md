# Contributing Guide — VOST Hub

Danke, dass du zum VOST Hub beitragen moechtest! Dieses Dokument erklaert, wie du mitmachen kannst.

## Voraussetzungen

- [Git](https://git-scm.com/)
- [Hugo Extended](https://gohugo.io/installation/) (v0.152.2 oder neuer)
- [Go](https://go.dev/dl/) (fuer Hugo Modules)

## Lokale Entwicklung

### 1. Repository klonen

```bash
git clone https://github.com/phismith91/vost-hub.git
cd vost-hub
```

### 2. Hugo Module laden

```bash
hugo mod tidy
```

### 3. Lokalen Server starten

```bash
hugo server
```

Die Seite ist dann unter `http://localhost:1313` erreichbar. Aenderungen werden live aktualisiert.

## Inhalte bearbeiten

### Neue Seite erstellen

```bash
hugo new content/bereich/seitenname.md
```

### Frontmatter

Jede Seite braucht TOML-Frontmatter:

```toml
+++
title = "Seitentitel"
description = "Kurze Beschreibung fuer SEO"
date = 2026-02-23
lastmod = 2026-02-23
draft = false
zielgruppe = "mitglieder"   # mitglieder | interessierte | behoerden | alle
+++
```

### Hextra Shortcodes

Fuer Karten auf Uebersichtsseiten:

```markdown
{{</* cards */>}}
  {{</* card link="seite" title="Titel" subtitle="Beschreibung" icon="icon-name" */>}}
{{</* /cards */>}}
```

Fuer ausklappbare Details:

```markdown
{{%/* details title="Titel" */%}}
Inhalt hier
{{%/* /details */%}}
```

## Pull Requests

1. Erstelle einen Feature-Branch: `git checkout -b feature/mein-feature`
2. Nimm deine Aenderungen vor
3. Pruefe lokal mit `hugo server`
4. Committe mit einer aussagekraeftigen Nachricht
5. Pushe und erstelle einen Pull Request

### CI/CD Pipeline

Bei jedem Pull Request laeuft automatisch:
- Hugo Build-Test (prueft ob die Seite fehlerfrei baut)
- HTML-Validierung

Bei Merge auf `main`:
- Automatisches Deployment auf GitHub Pages

## Content-Richtlinien

- **Ton:** Professionell aber nicht buerokratisch
- **Sprache:** "Du" fuer Mitglieder/Interessierte, "Sie" fuer Behoerden-Sektion
- **Bilder:** Immer mit Alt-Text
- **Links:** VOSTacademy verlinken, nicht duplizieren
- **Datenschutz:** Keine Personendaten ohne Einwilligung, keine Team-Kontaktdaten ohne Zustimmung

## Fragen?

Erstelle ein [Issue auf GitHub](https://github.com/phismith91/vost-hub/issues) oder kontaktiere uns ueber die Community-Kanaele.
