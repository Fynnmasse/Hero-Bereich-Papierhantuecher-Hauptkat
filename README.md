# Hero-Bereich Papierhandtücher (Hauptkategorie)

Neuer, eigenständiger Hero-Bereich für die Shopware-6-Kategorieseite
**Papierhandtücher**. Aufbau von oben nach unten:

1. **Titel** „Papierhandtücher“ + Subline + zwei CTAs („Jetzt kaufen“, „Produktfinder starten“)
2. **Product-Rail** – Apple-artige Reihe verlinkter Unterkategorie-Kacheln
3. **Video** – breites, abgerundetes Banner als stummer Autoplay-Loop

## Datei

- [`papierhandtuecher-hero.html`](papierhandtuecher-hero.html) – fertiger,
  selbst-enthaltener Block (HTML + gescopetes CSS + kleines Vanilla-JS).
  Keine externen Schriftarten oder Libraries; alle Klassen unter dem Präfix `.hph-`.

## Einbindung in Shopware (Erlebniswelt)

1. In der Erlebniswelt ein **HTML-Element** (Custom HTML) hinzufügen.
2. In `papierhandtuecher-hero.html` den Bereich zwischen
   `>>> COPY START >>>` und `<<< COPY END <<<` kopieren
   (das ist `<style>` + `<section>` + `<script>`) und ins HTML-Feld einfügen.
3. Einziger offener `TODO`: die echte **Produktfinder-URL** (zeigt vorerst sicher
   auf die Hauptkategorie). Optional: ein gehostetes **Poster-Bild** fürs Video.

Bereits eingetragen: die 5 Produktfotos, das Produktionsvideo, alle Rail-Links
(`/papierhandtuecher-1-lagig` … `-c-falz`, „Alle ansehen“ → `/papierhandtuecher`)
und beide CTAs.

Die Schrift wird **bewusst nicht** mitgeliefert, sondern vom Shop-Theme geerbt.

### Robustheit

- **Ohne JavaScript** bleibt der Hero vollständig sichtbar (`<noscript>`-Fallback);
  die Einblend-Animation entfällt dann. Das JS ist zusätzlich in `try/catch`
  gekapselt, damit ein Script-Fehler den Inhalt nicht verstecken kann.
- Das Video hat **kein leeres `poster`** mehr; bis ein Standbild ergänzt wird,
  greift der CSS-Gradient als Fallback-Fläche.

### Product-Rail (Apple-Stil)

Die Produktfotos stehen frei auf der Seite (keine Kästen/Rahmen). Damit der weiße
Foto-Hintergrund nahtlos verschmilzt, nutzt `.hph-rail__media img` ein
`mix-blend-mode:multiply` und `object-fit:contain`. Ein eigenes Produktfoto also
einfach mit hellem/weißem Hintergrund als `<img>` einsetzen.

## Anpassen

- **Markenfarben**: oben im `<style>` über die CSS-Variablen
  (`--hph-brand`, `--hph-ink`, …) zentral änderbar.
- **„Neu“-Tag**: optionaler Hinweis unter einer Kachel
  (`<span class="hph-rail__tag">Neu</span>`); Zeile sonst entfernen.
- **Video-Caption**: Text in `.hph-video__caption` anpassen oder das
  `<figcaption>` entfernen.

## Barrierefreiheit & Verhalten

- Sichtbare Fokus-Rahmen (`:focus-visible`), `aria-label` für die Rail,
  `alt`-Slots für Bilder.
- Dezente Einblend-Choreografie beim Scrollen (IntersectionObserver): Titel +
  von links aufziehende Akzentlinie, dann gestaffelt einzeln die Rail-Kacheln,
  zuletzt das Video. Taktiles `:active`-Feedback auf Buttons/Kacheln. Nur
  `transform`/`opacity` (GPU-freundlich); respektiert `prefers-reduced-motion`
  (Animation aus, Video pausiert).
- Rail ist auf schmalen Viewports horizontal scrollbar (Scroll-Snap).

## Lokale Vorschau

`papierhandtuecher-hero.html` direkt im Browser öffnen. Der `<body>`-Wrapper
und ein System-Font dienen nur der Vorschau und werden **nicht** mit
nach Shopware kopiert.
