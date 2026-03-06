## Was ist HTML?
- HTML = HyperText Markup Language
- Beschreibt die Struktur von Webseiten (Inhalte, Abschnitte, Beziehungen)
- Besteht aus Elementen (Tags) mit optionalen Attributen
- Wird von Browsern interpretiert und gerendert
- Trennung der Schichten: Struktur (HTML), Präsentation (CSS), Verhalten (JavaScript)

---

## Grundgerüst eines HTML-Dokuments
- Pflichtbestandteile: `<!DOCTYPE html>`, `<html>`, `<head>`, `<body>`
- `lang`-Attribut für Sprache setzen
- Metadaten im `head`, Inhalte im `body`
```html
<!DOCTYPE html>
<html lang="de">
  <head>
    <meta charset="utf-8">
    <title>Meine erste Seite</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="Einführung in HTML">
  </head>
  <body>
    <h1>Meine erste Seite</h1>
    <p>Das ist eine HTML-Seite.</p>
  </body>
</html>
```

---

## Elemente, Tags und Attribute
- Öffnender und schließender Tag, z. B. `<p>...</p>`
- Leere Elemente ohne Inhalt, z. B. `<img>`, `<br>`
- Attribute liefern zusätzliche Informationen
- Globale Attribute: `id`, `class`, `title`, `lang`, `dir`
```html
<p id="einleitung" title="Ein kurzer Absatz">Hallo!</p>
<img src="bild.jpg" alt="Beschreibung des Bildes" width="300" height="200">
```

---

## Textstrukturierung
- Überschriften: `<h1>` bis `<h6>` (hierarchisch, nur eine `<h1>` pro Seite empfohlen)
- Absätze: `<p>`
- Betonung: `<em>` (inhaltliche Betonung), `<strong>` (stark betont)
- Inline vs. Block: `<span>` (inline), `<div>` (block)
```html
<h1>Dokumenttitel</h1>
<h2>Unterthema</h2>
<p>Dies ist ein <em>wichtiger</em> Absatz mit <strong>starker Betonung</strong>.</p>
<div><p>Ein Absatz innerhalb eines Blockbereichs</p><p>Ein weiterer Absatz innerhalb desselben Blockbereichs</p></div>
<span>Ein inline-Textstück</span>
```

---

## Links und Navigation
- Hyperlinks mit `<a href="...">`
- Absolute vs. relative URLs
- Barrierefreiheit: Linktexte aussagekräftig formulieren
- Navigation oft in `<nav>`-Bereichen organisiert
```html
<nav>
  <ul>
    <li><a href="/index.html">Startseite</a></li>
    <li><a href="https://example.com">Externe Ressource</a></li>
    <li><a href="#kontakt">Zum Kontaktbereich</a></li>
  </ul>
</nav>
<p id="kontakt">Kontakt: <a href="mailto:info@example.com">E-Mail senden</a></p>
```

---

## Bilder und Medien (ohne CSS)
- Bilder: `<img src alt>` – `alt` ist Pflicht (Beschreibung)
- Figuren mit Beschriftung: `<figure>` und `<figcaption>`
- Einfache Einbettung von Video/Audio
```html
<figure>
  <img src="landschaft.jpg" alt="Berglandschaft im Sonnenuntergang">
  <figcaption>Berglandschaft</figcaption>
</figure>

<video controls width="480">
  <source src="clip.mp4" type="video/mp4">
  Ihr Browser unterstützt das Video-Tag nicht.
</video>

<audio controls>
  <source src="musik.ogg" type="audio/ogg">
  Ihr Browser unterstützt das Audio-Tag nicht.
</audio>
```

---

## Listen und Tabellen
- Ungeordnete Listen: `<ul>`, geordnete Listen: `<ol>`, Einträge: `<li>`
- Beschreibungslisten: `<dl>`, `<dt>`, `<dd>`
- Tabellen: `<table>`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, `<td>`
```html
<ul>
  <li>Apfel</li>
  <li>Banane</li>
</ul>

<dl>
  <dt>HTML</dt>
  <dd>Auszeichnungssprache für Webinhalte</dd>
</dl>

<table>
  <thead>
    <tr><th>Produkt</th><th>Preis</th></tr>
  </thead>
  <tbody>
    <tr><td>Buch</td><td>12,99 €</td></tr>
    <tr><td>Stift</td><td>1,50 €</td></tr>
  </tbody>
</table>
```

---

## Semantische HTML5-Elemente
- Strukturieren Inhalte in bedeutungsvolle Bereiche:
  - `<header>` Kopfbereich
  - `<nav>` Navigation
  - `<main>` Hauptinhalt (einmal pro Seite)
  - `<article>` in sich geschlossener Beitrag
  - `<section>` thematischer Abschnitt
  - `<aside>` ergänzende Inhalte
  - `<footer>` Fußbereich
```html
<header>
  <h1>Mein Blog</h1>
</header>
<main>
  <article>
    <h2>Erster Beitrag</h2>
    <p>Inhalt...</p>
  </article>
  <aside>Newsletter-Anmeldung</aside>
</main>
<footer>&copy; 2026</footer>
```
---

## Gute Praxis, Validierung und Ressourcen
- Saubere Struktur, semantische Tags, sinnvolle `alt`-Texte
- Einhaltung der Barrierefreiheit (z. B. sinnvolle Überschriftenhierarchie, Labels)
- Validierung: https://validator.w3.org/
- Performance: sinnvolle Mediengrößen, `meta viewport` für Mobilgeräte
- Ressourcen:
  - MDN Web Docs (developer.mozilla.org)
  - HTML Living Standard (whatwg.org)
  - WebAIM (webaim.org) für Accessibility