# CLAUDE.md — vost-hub

Dieses Dokument ist der primäre Kontext für alle AI-Coding-Assistenten (Claude Code, Copilot) die an diesem Projekt arbeiten. Lies es vollständig bevor du irgendetwas tust.

---

## Was ist dieses Projekt?

**vost-hub.de** ist die zentrale Community-Platform für Virtual Operations Support Teams (VOST) in Deutschland. Es ist die erste einheitliche Anlaufstelle für alle deutschen VOST-Teams — bisher existierte so etwas nicht.

Die Platform bedient drei Zielgruppen gleichzeitig:

1. **Aktive VOST-Mitglieder** — Wissen teilen, Tools finden, vernetzt bleiben
2. **Interessierte / potentielle Mitglieder** — Einstieg finden, Team in der Region kontaktieren
3. **Behörden & Auftraggeber** — Verstehen was VOST ist, Kontakt aufnehmen

---

## Was dieses Projekt NICHT ist

- Kein operatives Tool (das ist `vost-community/vost-desk`)
- Kein internes Kommunikationskanal (kein Ersatz für Signal/Slack der Teams)
- Kein Ausbildungsprogramm (das macht VOSTacademy — wir verlinken, duplizieren nicht)
- Keine dynamische Web-App (rein statisch, kein Backend, kein Login)

---

## Tech Stack

```
Static Site Generator:  Hugo (extended version empfohlen)
Hosting:                GitHub Pages (Branch: gh-pages oder /docs)
Domain:                 vost-hub.de (Custom Domain via CNAME)
Theme:                  [noch zu entscheiden — kein Jekyll, kein Sphinx]
Sprache:                Deutsch (Primär), Englisch (Sekundär für int. Vernetzung)
Versionskontrolle:      GitHub (öffentliches Repo)
CI/CD:                  GitHub Actions → automatischer Build + Deploy bei Push
```

---

## Projektstruktur

```
vost-hub/
├── CLAUDE.md                  ← diese Datei
├── hugo.toml                  ← Hugo-Konfiguration (nicht hugo.yaml)
├── .github/
│   └── workflows/
│       └── deploy.yml         ← GitHub Actions: Build + Deploy zu Pages
├── content/
│   ├── _index.md              ← Startseite
│   ├── mitmachen/
│   │   ├── _index.md          ← Für Nutzergruppe B: Interessierte
│   │   ├── was-ist-vost.md
│   │   └── kontakt.md
│   ├── behoerden/
│   │   ├── _index.md          ← Für Nutzergruppe C: Behörden
│   │   ├── leistungen.md
│   │   └── referenzen.md
│   ├── community/
│   │   ├── _index.md          ← Für Nutzergruppe A: Mitglieder
│   │   ├── teams.md           ← Alle deutschen VOST-Teams
│   │   ├── werkzeuge.md       ← Tool-Empfehlungen
│   │   └── vost-desk.md       ← VOST Desk Beschreibung + Demo-Link
│   ├── wissen/
│   │   ├── _index.md
│   │   └── [after-action-reviews als Einzelseiten]
│   └── ueber-uns.md
├── static/
│   ├── css/
│   ├── img/
│   └── CNAME                  ← vost-hub.de
├── layouts/                   ← Custom Templates (wenn nötig)
├── assets/                    ← SCSS/JS (wenn nötig)
└── themes/
    └── [theme-name]/
```

---

## Content-Richtlinien

### Ton & Sprache
- Professionell aber nicht bürokratisch — wir sind Ehrenamtliche, keine Behörde
- Direkte Ansprache ("Du" intern, "Sie" in Behörden-Sektion)
- Keine Marketing-Sprache — Fakten statt Superlative
- Technische Begriffe erklären (nicht jeder kennt "EOC", "AAR", "BOS")

### Inhalte die wir veröffentlichen
- Erklärungen was VOST ist und macht
- Kontaktdaten und Gebiete der deutschen Teams (nur mit Zustimmung der Teams!)
- After Action Reviews (AAR) — anonymisiert, kein Personenbezug
- Tool-Empfehlungen — mit kurzer Bewertung warum
- Links zu VOSTacademy für Ausbildungsthemen

### Inhalte die wir NICHT veröffentlichen
- Interne Einsatzdaten oder nicht-anonymisierte Berichte
- Personenbezogene Daten ohne explizite Einwilligung
- Meinungen zu politischen Themen
- Werbung oder gesponserte Inhalte

---

## Coding-Standards

### Hugo-spezifisch
- Konfiguration in `hugo.toml` (nicht YAML, nicht JSON)
- Content als Markdown (`.md`), Frontmatter als TOML
- Shortcodes für wiederkehrende UI-Elemente (z.B. Team-Karte, Tool-Empfehlung)
- Kein inline JavaScript wenn vermeidbar
- Bilder immer mit Alt-Text (Barrierefreiheit)

### GitHub Actions Deploy
```yaml
# Ziel-Workflow: Bei Push auf main → Hugo bauen → zu gh-pages deployen
# Hugo Version: immer explizit pinnen (z.B. hugo-version: '0.140.0')
# Nie: latest verwenden (bricht bei Hugo-Updates)
```

### CSS / Design
- Kein Tailwind, kein Bootstrap (zu viel Overhead für statische Seite)
- Custom CSS so minimal wie möglich
- Mobile-first — viele BOS-Leute lesen auf dem Handy
- Farben: an BOS-Ästhetik anlehnen (dunkel, klar, funktional — kein Pastell)
- Keine Animationen die ablenken

### Barrierefreiheit
- Semantisches HTML (nav, main, article, section)
- Alle Bilder mit Alt-Text
- Ausreichend Kontrast (WCAG AA Minimum)

---

## GitHub Actions Workflow (Vorlage)

```yaml
# .github/workflows/deploy.yml
name: Deploy Hugo zu GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          submodules: recursive

      - name: Hugo Setup
        uses: peaceiris/actions-hugo@v3
        with:
          hugo-version: '0.140.0'
          extended: true

      - name: Build
        run: hugo --minify

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

---

## Content Frontmatter Standard

```toml
+++
title = "Seitentitel"
description = "Kurze Beschreibung für SEO und Social Sharing"
date = 2026-02-22
lastmod = 2026-02-22
draft = false
zielgruppe = "mitglieder"   # mitglieder | interessierte | behoerden | alle
+++
```

---

## Was du NICHT tun sollst

- Kein Backend, keine Datenbank, kein Server-Side-Rendering
- Kein Contact-Form mit eigenem Backend (Netlify Forms oder Formspree als Alternative)
- Kein Google Analytics (Datenschutz) — wenn Tracking nötig: Plausible oder Matomo self-hosted
- Keine Inhalte der VOSTacademy kopieren — verlinken statt duplizieren
- Keine Kontaktdaten von Teams ohne deren explizite Zustimmung veröffentlichen
- Nicht anfangen externe Theme-Bibliotheken einzubauen ohne Rückfrage

---

## Externe Referenzen & Links

- Lean UX Canvas: `docs/lean-ux-canvas.md`
- Backlog: GitHub Projects (vost-community Organisation)
- VOSTacademy: https://www.vost-academy.eu
- THW VOST: https://www.thw.de
- VOST Europe: https://vosteurope.org
- Hugo Docs: https://gohugo.io/documentation/
- GitHub Pages + Hugo Guide: https://gohugo.io/hosting-and-deployment/hosting-on-github/
- vost-desk Tool: https://github.com/vost-community/vost-desk

---

## Domain & DNS

```
Domain:         vost-hub.de
DNS Provider:   [noch registrieren]
GitHub Pages:   Custom Domain in Repo-Settings eintragen
CNAME Datei:    static/CNAME → Inhalt: vost-hub.de
SSL:            automatisch via GitHub Pages (Let's Encrypt)
```

---

*Letzte Aktualisierung: Februar 2026 | Philipp | vost-community/vost-hub*
