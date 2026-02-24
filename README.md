# VOST Hub Deutschland

Die zentrale Community-Plattform fuer [Virtual Operations Support Teams](https://vosteurope.org) (VOST) in Deutschland.

**Live:** [vost-hub.de](https://vost-hub.de) (im Aufbau)

## Was ist das?

Der VOST Hub ist die erste einheitliche Anlaufstelle fuer alle deutschen VOST-Teams. Bisher gab es keinen gemeinsamen Ort fuer Wissensaustausch, Vernetzung und Sichtbarkeit — das aendert sich hier.

### Fuer wen?

| Zielgruppe | Was sie hier finden |
| --- | --- |
| **Aktive VOST-Mitglieder** | Teams, Werkzeuge, After Action Reviews |
| **Interessierte** | Was ist VOST, wie mitmachen, Kontakt |
| **Behoerden & Auftraggeber** | Leistungen, Referenzen, Ansprechpartner |

### Was das Projekt NICHT ist

- Kein operatives Tool (das ist [VOST Desk](https://github.com/vost-community/vost-desk))
- Kein Ausbildungsprogramm (das macht [VOSTacademy](https://www.vost-academy.eu))
- Keine dynamische Web-App — rein statisch, kein Backend, kein Login

## Tech Stack

| Komponente | Technologie |
| --- | --- |
| Static Site Generator | [Hugo](https://gohugo.io) (Extended) |
| Theme | [Hextra](https://github.com/imfing/hextra) |
| Hosting | GitHub Pages |
| CI/CD | GitHub Actions |
| Domain | vost-hub.de |

## Schnellstart

### Voraussetzungen

- [Git](https://git-scm.com/)
- [Hugo Extended](https://gohugo.io/installation/) (>= 0.146.0)
- [Go](https://go.dev/dl/) (>= 1.26, fuer Hugo Modules)

### Lokale Entwicklung

```bash
# Repository klonen
git clone https://github.com/phismith91/vost-hub.git
cd vost-hub

# Hugo Module laden
hugo mod tidy

# Dev-Server starten
hugo server
```

Die Seite ist dann unter `http://localhost:1313` erreichbar. Aenderungen werden live aktualisiert.

### Build

```bash
hugo --minify
```

Die fertige Seite liegt dann in `public/`.

## Projektstruktur

```text
vost-hub/
├── content/                 # Alle Inhalte als Markdown
│   ├── _index.md            # Startseite
│   ├── mitmachen/           # Fuer Interessierte
│   ├── community/           # Fuer aktive Mitglieder
│   ├── behoerden/           # Fuer Behoerden (Sie-Form)
│   ├── wissen/              # AARs und Best Practices
│   ├── impressum.md
│   └── datenschutz.md
├── layouts/
│   └── shortcodes/          # team-karte, tool-empfehlung
├── hugo.toml                # Hugo-Konfiguration (alle Hextra-Optionen dokumentiert)
├── .github/workflows/
│   ├── deploy.yml           # Deploy zu GitHub Pages bei Push auf main
│   └── ci.yml               # Build-Test, HTML-Validierung, Linkcheck bei PRs
├── CONTRIBUTING.md           # Anleitung zum Mitmachen
└── CLAUDE.md                 # KI-Assistenten-Kontext
```

## Beitragen

Es gibt zwei Wege, Inhalte beizusteuern — auch ohne technische Vorkenntnisse:

1. **Formular:** Auf [vost-hub.de/mitmachen/beitrag-einreichen/](https://vost-hub.de/mitmachen/beitrag-einreichen/) ein Formular ausfuellen — ein Maintainer kuemmert sich um den Rest
2. **GitHub:** Jede Seite hat einen "Edit this page"-Link, der direkt im Browser-Editor oeffnet

Fuer Details siehe [CONTRIBUTING.md](CONTRIBUTING.md).

### Content-Richtlinien (Kurzfassung)

- Professionell aber nicht buerokratisch
- "Du" fuer Mitglieder/Interessierte, "Sie" im Behoerden-Bereich
- Keine Personendaten ohne Einwilligung
- VOSTacademy verlinken, nicht duplizieren
- Bilder immer mit Alt-Text

## Deployment

Das Deployment laeuft vollautomatisch:

```text
Push auf main → GitHub Actions → Hugo Build → GitHub Pages
```

### Pipelines

| Workflow | Trigger | Aufgabe |
| --- | --- | --- |
| `ci.yml` | Push + PRs | Build-Test, kritische Seiten pruefen, HTML-Validierung, Linkcheck |
| `deploy.yml` | Push auf main | Build + Deploy zu GitHub Pages |

### Manuelles Deployment

```bash
# Build lokal erstellen
hugo --minify

# Oder via GitHub Actions manuell ausloesen:
# Repository → Actions → "Deploy Hugo zu GitHub Pages" → Run workflow
```

## Verwandte Projekte

- [VOST Desk](https://github.com/vost-community/vost-desk) — Operatives Einsatz-Tool
- [VOSTacademy](https://www.vost-academy.eu) — Schulungen und Weiterbildung
- [VOST Europe](https://vosteurope.org) — Europaeisches Netzwerk

## Lizenz

MIT — siehe [LICENSE](LICENSE).
