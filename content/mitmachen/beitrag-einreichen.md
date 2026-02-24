+++
title = "Beitrag einreichen"
description = "Reiche einen Beitrag für den VOST Hub ein — ohne technische Vorkenntnisse"
date = 2026-02-24
lastmod = 2026-02-24
draft = false
zielgruppe = "alle"
+++

Du möchtest einen Beitrag zum VOST Hub beisteuern? Das geht auch ohne technische Vorkenntnisse. Wähle einfach die passende Option:

## Option 1: Formular ausfüllen

Am einfachsten: Füll das Formular unten aus. Ein Maintainer kümmert sich um den Rest.

{{% details title="Welche Beiträge sind willkommen?" open=true %}}
- **After Action Reviews (AAR)** — Erfahrungsberichte aus Einsätzen (anonymisiert!)
- **Tool-Empfehlungen** — Werkzeuge die sich in der VOST-Arbeit bewährt haben
- **Team-Informationen** — Euer VOST-Team soll auf der Seite erscheinen (nur mit Zustimmung)
- **Korrekturen** — Fehler gefunden? Sag Bescheid
- **Sonstiges** — Ideen, Vorschläge, Feedback
{{% /details %}}

<form action="https://formspree.io/f/DEINE_FORM_ID" method="POST" style="max-width:600px;">
  <div style="margin-bottom:1rem;">
    <label for="name" style="display:block; margin-bottom:0.25rem; font-weight:600;">Name oder Pseudonym</label>
    <input type="text" id="name" name="name" required style="width:100%; padding:0.5rem; border:1px solid #ccc; border-radius:4px;">
  </div>
  <div style="margin-bottom:1rem;">
    <label for="email" style="display:block; margin-bottom:0.25rem; font-weight:600;">E-Mail (optional, für Rückfragen)</label>
    <input type="email" id="email" name="email" style="width:100%; padding:0.5rem; border:1px solid #ccc; border-radius:4px;">
  </div>
  <div style="margin-bottom:1rem;">
    <label for="typ" style="display:block; margin-bottom:0.25rem; font-weight:600;">Art des Beitrags</label>
    <select id="typ" name="typ" required style="width:100%; padding:0.5rem; border:1px solid #ccc; border-radius:4px;">
      <option value="">Bitte wählen...</option>
      <option value="aar">After Action Review</option>
      <option value="tool">Tool-Empfehlung</option>
      <option value="team">Team-Information</option>
      <option value="korrektur">Korrektur / Fehler</option>
      <option value="sonstiges">Sonstiges</option>
    </select>
  </div>
  <div style="margin-bottom:1rem;">
    <label for="inhalt" style="display:block; margin-bottom:0.25rem; font-weight:600;">Dein Beitrag</label>
    <textarea id="inhalt" name="inhalt" rows="10" required style="width:100%; padding:0.5rem; border:1px solid #ccc; border-radius:4px;" placeholder="Schreib deinen Beitrag hier. Einfacher Text reicht — wir kümmern uns um die Formatierung."></textarea>
  </div>
  <div style="margin-bottom:1rem;">
    <label style="display:flex; align-items:flex-start; gap:0.5rem;">
      <input type="checkbox" name="einwilligung" required style="margin-top:0.25rem;">
      <span>Ich bestätige, dass mein Beitrag keine personenbezogenen Daten enthält und zur Veröffentlichung auf vost-hub.de geeignet ist.</span>
    </label>
  </div>
  <button type="submit" style="padding:0.5rem 1.5rem; background:#2563eb; color:white; border:none; border-radius:4px; cursor:pointer; font-weight:600;">Beitrag einreichen</button>
</form>

**Hinweis:** Beiträge werden vor der Veröffentlichung von einem Maintainer geprüft. Personenbezogene Daten und nicht-anonymisierte Einsatzdaten werden nicht veröffentlicht.

## Option 2: Direkt auf GitHub bearbeiten

Wenn du einen GitHub-Account hast, kannst du Seiten direkt im Browser bearbeiten. Jede Seite hat unten einen "Edit this page on GitHub"-Link. Eine ausführliche Anleitung findest du unter [Anleitung: Beiträge über GitHub](/mitmachen/github-anleitung/).
