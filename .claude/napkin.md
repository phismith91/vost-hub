# Napkin Runbook

## Curation Rules
- Re-prioritize on every read.
- Keep recurring, high-value notes only.
- Max 10 items per category.
- Each item includes date + "Do instead".

## Execution & Validation (Highest Priority)

1. **[2026-02-24] Hextra CSS-Klassen: `hx:` statt `hx-` Prefix!**
   Do instead: Hextra v0.12.0 nutzt `hx:mt-6` (Doppelpunkt), NICHT `hx-mt-6` (Bindestrich). Falsches Prefix = Styles werden ignoriert = Layout zusammengepresst.
2. **[2026-02-24] Hextra-Design NICHT anpassen — Demo-Look beibehalten**
   Do instead: Keine eigenen params.page.width, params.navbar, params.search setzen. Hextra-Defaults nutzen. Homepage muss `layout = "hextra-home"` verwenden.
2. **[2026-02-24] Hextra Homepage: feature-grid statt cards**
   Do instead: `hextra/feature-grid` + `hextra/feature-card` fuer die Startseite verwenden, nicht `cards`. Exakt wie die Hextra-Demo: hero-badge, hero-headline, hero-subtitle, hero-button, dann feature-grid.
3. **[2026-02-24] Hextra erwartet author als Object, nicht String**
   Do instead: `[params.author]` mit `name = "..."` verwenden, nicht `author = "..."`.
4. **[2026-02-24] Raw HTML in Markdown erfordert unsafe=true**
   Do instead: In hugo.toml `[markup.goldmark.renderer] unsafe = true` setzen fuer Hextra Hero-Shortcodes.
5. **[2026-02-23] Hugo Version explizit pinnen**
   Do instead: In GitHub Actions immer `hugo-version: '0.152.2'` pinnen, nie `latest`.

## Shell & Command Reliability

1. **[2026-02-24] Hugo Modules brauchen Go in der Pipeline**
   Do instead: `setup-go@v5` mit `go-version: '1.26'` VOR Hugo Setup in GitHub Actions.
2. **[2026-02-23] Hugo Extended erforderlich**
   Do instead: Immer `extended: true` in GitHub Actions und lokal Hugo Extended verwenden.
3. **[2026-02-23] Bei Hextra: module.imports nutzen, kein theme key**
   Do instead: `[module] [[module.imports]] path = "github.com/imfing/hextra"` in hugo.toml.

## Domain Behavior Guardrails

1. **[2026-02-23] Keine Personendaten ohne Einwilligung**
   Do instead: Team-Kontaktdaten nur mit expliziter Zustimmung veroeffentlichen.
2. **[2026-02-23] VOSTacademy verlinken, nicht duplizieren**
   Do instead: Ausbildungsinhalte immer auf vost-academy.eu verlinken, nie kopieren.
3. **[2026-02-23] Du/Sie-Trennung beachten**
   Do instead: "Du" fuer Mitglieder/Interessierte, "Sie" fuer Behoerden-Sektion.

## User Directives

1. **[2026-02-24] Hextra Demo-Design exakt beibehalten**
   Do instead: KEIN Custom-CSS, KEINE eigenen Layout-Overrides. Design exakt wie https://imfing.github.io/hextra/ belassen. User hat explizit gesagt: "ich will das design exakt so wie in der hextra demo".
2. **[2026-02-24] DevOps: CI mit Tests VOR Deploy**
   Do instead: Separate ci.yml fuer PRs mit Build-Test, kritische Seiten, HTML-Validierung, Linkcheck.
3. **[2026-02-24] hugo.toml minimal halten**
   Do instead: Nur setzen was noetig ist. Hextra-Defaults nicht ueberschreiben. Weniger params = weniger Probleme.
