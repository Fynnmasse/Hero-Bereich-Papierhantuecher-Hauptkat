# Hero-Bereich Papierhandtücher (Hauptkategorie)

Eigenständiger Hero-Bereich für die Shopware-6-Kategorieseite **Papierhandtücher**
(Erlebniswelt, Element „HTML“). Aufbau von oben nach unten:

1. **Kopf** – H1 „Papierhandtücher“ + Subline (Value Proposition: Falzarten,
   1–3-lagig, Karton/Palette mit Staffelpreis, Siegel) + **Trust-Strip** direkt unter
   der Subline (belegbare B2B-Fakten: Staffelpreise ab Karton, EU Ecolabel & Blauer
   Engel, Lieferzeit) + zwei CTAs: **„Zum ganzen Sortiment“** (primär, gefüllte Pill)
   und **„Hier das richtige Papierhandtuch finden“** (sekundär, tonale Pill, Link zum
   Produktfinder). Rechts ein stummes Loop-Video mit **Pause-Toggle**.
2. **Product-Rail** – 5 verlinkte Unterkategorie-Kacheln (1-/2-/3-lagig Z-Falz,
   Interfold, C-Falz), je mit dem Qualifier
   **„günstigster Preis der Kategorie“** und dem **„ab …€ netto / 1.000 Stück“-Preisanker**
   (der Qualifier stellt klar: der Ab-Preis gilt für die ganze Unterkategorie, nicht für das Foto).
   Dazu eine beschriftete **„Vergleichen“-Checkbox** je Kachel (selbsterklärend,
   kein nacktes Icon); ab der ersten Auswahl erscheint eine schlanke Bar, deren
   **„Vergleichen“** ein **Modal** (natives `<dialog>`) öffnet: gewählte Varianten
   (einzeln entfernbar), Liefermenge (Alle/Karton/Palette) und der Direktlink in den
   vorgefilterten Produktfinder-Vergleich. Fokus-Trap, ESC und Backdrop-Klick inklusive;
   `prefers-reduced-motion` respektiert.
3. **Feature-Karten „Ausgezeichnet nachhaltig“** – EU Ecolabel und Blauer Engel,
   je mit Differenzierungszeile (was das Siegel konkret auszeichnet), „Weitere
   Infos“ (offizielle Siegel-Seite) und „Jetzt kaufen“ (Listing mit Siegel-Filter;
   das Script setzt nach der Navigation eine Filter-Überschrift und scrollt hin).
4. **Falzungs-Schnellvergleich** – scanbare Tabelle (Spendertyp, Entnahme,
   Blattformat, typischer Einsatz × Z-Falz/Interfold/C-Falz), destilliert aus den
   Akkordeon-Texten.
5. **Showcase-Akkordeon „Welche Falzung passt zu Ihrem Spender?“** – drei
   kompakte Erklärtexte mit wechselndem Falz-Schema-Bild, dazu FAQPage-JSON-LD
   (wortgleich mit den sichtbaren Texten; beim Ändern der Panel-Texte mitziehen).

## Datei

- [`papierhandtuecher-hero.html`](papierhandtuecher-hero.html) – fertiger,
  selbst-enthaltener Block (HTML + gescopetes CSS + Vanilla-JS, keine Libraries).
  Alle Klassen unter dem Präfix `.hph-`, kollidiert nicht mit dem Theme.
- [`unterkategorie-abpreis-banner.html`](unterkategorie-abpreis-banner.html) –
  Block **B2**: geteiltes CSS+JS-Snippet, das auf den Unterkategorie-Listing-Seiten
  oberhalb des Produkt-Listings denselben „ab …€“-Bestpreis zeigt wie die Rail
  (gemeinsamer localStorage-Cache + Fetch der ungefilterten Kategorie-URL; Guard,
  fail-open, AJAX-fest). Einbau-Anleitung + Fallback-Wege A/C im Datei-Kopf;
  Einbau via ThemeWare Expert Settings → Others → Individual JS/CSS.
- [`produktfinder-auswahl-bestaetigung.html`](produktfinder-auswahl-bestaetigung.html) –
  CSS+JS-Snippet für die **Produktfinder-Vergleichsseite**: liest die vom Hero-Modal
  übergebenen URL-Parameter (`vglnach`/`vglsets`), übersetzt sie in lesbare Labels und
  zeigt oben eine **„Ihre Auswahl"-Bestätigung** (Varianten + Liefermenge) – damit der
  Kunde sieht, dass die Übergabe funktioniert hat. XSS-sicher, fail-open, Mount via
  `[data-hph-auswahl-mount]`. Einbau-Anleitung im Datei-Kopf (eigenes System →
  Custom-Code-Einbindung nötig).

## Einbindung in Shopware (Erlebniswelt)

1. In der Erlebniswelt ein **HTML-Element** (Custom HTML) hinzufügen.
2. In `papierhandtuecher-hero.html` den Bereich zwischen
   `>>> COPY START >>>` und `<<< COPY END <<<` kopieren
   (`<link>`-Fonts + `<style>` + `<noscript>` + `<section>` + `<script>`)
   und ins HTML-Feld einfügen.
3. Bei Bedarf anpassen: CTA-Ziele im Kopf, Rail-Links/-Bilder, Karten-Inhalte.

## Schriften & DSGVO

Der Block lädt **Comfortaa** (Überschriften) und **Open Sans** (Text) per
`<link>` von Google Fonts, damit er unabhängig von der Theme-Schrift korrekt
aussieht.

> **DSGVO-Warnung:** Diese Einbindung übermittelt die IP-Adresse der Besucher
> an Google (LG München I, Az. 3 O 17493/20: ohne Einwilligung abmahnfähig).
> Für den Produktivbetrieb die Fonts **selbst hosten** (z. B. per
> google-webfonts-helper ins Theme) und die drei `<link>`-Zeilen ersetzen.
> Bei strenger CSP zusätzlich `fonts.googleapis.com` + `fonts.gstatic.com`
> freigeben bzw. nach dem Self-Hosting entfernen.

## Farb-System

Drei Ebenen, zentral als CSS-Tokens im `.hph-hero`-Block:

- **`--hph-brand`** (Marken-Navy aus dem Theme) – nur Textlinks, Icons,
  Hover-Tints und Fokus-Ringe.
- **`--hph-action`** (sattes Petrol) – ausschließlich gefüllte Conversion-Buttons:
  „Zum Sortiment“, „Jetzt kaufen“, „Vergleichen“ und die angehakte
  „Vergleichen“-Checkbox.
- **`--hph-cert`** (gedecktes Tannengrün) – ausschließlich die Siegel-Chips
  (EU Ecolabel / Blauer Engel). Grün nie an Buttons oder Flächen einsetzen
  (kippt in Öko-Klischee-/Greenwashing-Optik).

## Preisanker: Pflegehinweis

Die „ab …€ netto/Karton“-Preise an den Rail-Kacheln sind **manuell erhoben**
(günstigster Karton-Einzelpreis je Unterkategorie, Stand 11.06.2026:
1-lagig 14,07 € · 2-lagig 17,21 € · 3-lagig 22,08 € · Interfold 17,69 € ·
C-Falz 22,29 €). Sie müssen bei jeder Preisänderung **mitgezogen** werden –
ein veralteter „ab“-Preis ist irreführende Werbung (UWG-Risiko). Empfehlung:
langfristig dynamisch aus Shopware befüllen.

> **Block B2 ist umgesetzt:** Den „ab …€“-Bestpreis zeigt jetzt
> [`unterkategorie-abpreis-banner.html`](unterkategorie-abpreis-banner.html) auf den
> Unterkategorie-Seiten – Quelle/Regex/Label identisch zum Rail-Grundpreis-Sync,
> gespeist aus dem gemeinsamen localStorage-Cache + einem Fetch der **ungefilterten**
> Kategorie-URL (also konsistent zur Rail und unabhängig von Filter/Sortierung/Seite).
> Vor Go-live einmal die Grundpreis-Schreibweise „/ 1000 Stück“ an einer echten
> Unterkategorie verifizieren (Detail im Datei-Kopf).

## Robustheit

- **Ohne JavaScript** bleibt der gesamte Inhalt sichtbar (`<noscript>`-Fallback;
  der verborgene Reveal-Startzustand greift nur unter `.hph-hero--js`). Das JS
  ist in `try/catch` gekapselt; ein Script-Fehler entfernt die Klasse wieder.
  Vergleichs-Toggles, Vergleichs-Bar und Video-Pause-Button erscheinen nur mit JS
  (sonst wären sie inerte Buttons).
- Das Video hat ein Poster; bis es lädt, greift ein CSS-Gradient als Fläche.
- Der Zertifikats-/Listing-Code (Filter-Überschrift, Scroll) hat eigene
  `try/catch`-Blöcke und Fallback-Selektoren – schlägt etwas fehl, bleibt die
  Seite so, wie Shopware sie ausliefert.

## Barrierefreiheit & Verhalten

- Sichtbare `:focus-visible`-Rahmen überall; Rail-Slider, Akkordeon
  (`aria-expanded`/`aria-controls`), Mengen-Auswahl und Vergleichs-Toggles
  (beide `aria-pressed`) sind vollständig tastaturbedienbar.
- **Video-Pause-Button (WCAG 2.2.2):** Toggle unten rechts am Loop-Video mit
  wechselndem `aria-label` („Video pausieren/abspielen“).
- **Schnellvergleichstabelle:** `caption` (Screenreader) + `scope`-Attribute;
  mobil horizontal scrollbar (`role="region"` + `tabindex="0"`).
- `prefers-reduced-motion`: alle Reveals/Transitions aus, Smooth-Scroll → auto,
  Video pausiert und zeigt das Standbild (Pause-Toggle entfällt).
- Scroll-Reveal nur mit `transform`/`opacity` (GPU-freundlich), Szenen per
  IntersectionObserver, Staffelung über `--i`.
- „Zum Sortiment“ und „Alle Papierhandtücher ansehen“ scrollen auf der
  Kategorieseite sanft zum Listing statt neu zu laden; auf anderen Seiten
  navigieren sie normal.

## Lokale Vorschau

`papierhandtuecher-hero.html` direkt im Browser öffnen. Der `<body>`-Wrapper
und sein System-Font dienen nur der Vorschau und werden **nicht** mit nach
Shopware kopiert.
