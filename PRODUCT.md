# Product

## Register

brand

## Users

B2B-Beschaffung über den Shopware-6-Shop von Hamburg Papier (Herm. Kemme GmbH).
Einstieg ist die Kategorieseite „Papierhandtücher". Fünf reale Nutzergruppen mit
sehr unterschiedlichem Vorwissen:

- **Facility Management / Gebäudereiniger-Dienstleister** — kaufen Karton-/Palettenware
  für viele Objekte. Denken in Spender-Kompatibilität, Staffelpreisen, TCO,
  Nachfüllintervallen und Logistik. Wiederkehrende Großbestellungen, rationaler Einkauf.
- **Gastronomie & Gewerbe (klein)** — zeitknapp, *kein* Papier-Experte. Wollen in
  30 Sekunden „das Richtige für meinen Betrieb" plus einen fairen Preis.
- **Büro / Verwaltung** — moderater Bedarf, pragmatische Auswahl.
- **ESG-/Nachhaltigkeits-Beschaffung & öffentliche Auftraggeber** — brauchen belegbare
  Zertifikate (EU Ecolabel, Blauer Engel, FSC) für Ausschreibungen und Green Procurement.
  Prüfen Claims kritisch.
- **Erstbesucher / Nicht-Experten** — kennen weder Falz-Typen (Z-Falz, C-Falz, Interfold)
  noch ihren eigenen Spendertyp.

**Job to be done:** das passende Papierhandtuch finden (nach Spender-Fit, Lagigkeit,
Zertifikat, Menge/Preis) und in den Shop bzw. die richtige Unterkategorie gelangen —
Profis schnell und ohne Reibung, Laien geführt und ohne Fachwissen.

## Product Purpose

Eigenständiger, in die Shopware-6-Erlebniswelt eingebetteter Kategorie-Hero (selbst-
enthaltenes HTML + gescopetes `.hph-`-CSS + Vanilla-JS, kein Framework, Schrift vom
Theme geerbt). Er führt Besucher von der Kategorie in die passende Unterkategorie bzw.
zum Kauf, baut B2B-Vertrauen auf (Staffelpreise ab Karton, Umweltzertifikate, Lieferzeit)
und überbrückt die Wissenslücke zwischen Profi-Einkäufern und Nicht-Experten.

**Primäres Conversion-Ziel:** direkt ins Sortiment / zum Kauf (gefüllter „Zum Sortiment"-
CTA). Sekundär: Produktfinder / Staffelpreis-Vergleich. Erfolg = Klick in eine
Unterkategorie oder ins Sortiment; sekundär Produktfinder-Nutzung.

## Brand Personality

**Nahbar & beratend, aber fachlich fundiert.** Drei Wörter: *hilfsbereit, kompetent,
vertrauenswürdig.*

Die Stimme nimmt an die Hand und erklärt, ohne herablassend zu sein — Fakten statt
Floskeln, warm statt distanziert, seriös statt behördlich. Sie darf einen Laien beruhigen
(„unsicher? so finden Sie die passende Falzung") und einem Profi gleichzeitig die harten
Eckdaten liefern. Emotionales Ziel beim Besucher: *„Die verstehen mein Geschäft und machen
mir die richtige Wahl leicht."*

## Anti-references

Der Hero soll ausdrücklich **nichts** davon sein:

- **Billig-/Discounter-Look** — Rabatt-Geschrei, grelle Banner, Reizüberflutung,
  „Knaller-Preis"-Optik.
- **Generischer AI-/Template-Baukasten** — austauschbare Stock-Optik und Slop-Tells
  (Eyebrow-Kicker über jeder Sektion, Gradient-Text, identische Icon-Karten-Grids,
  Buzzword-Stacking). *Aktuelle Schwachstelle:* die langen „Gut zu wissen"-Volltexte
  driften durch dichtes Fachwort-Stapeln (TCO, HACCP, Cost-in-Use, ESG, Green Procurement)
  genau in diese Falle.
- **Behörden-/Datenblatt-trocken** — Textwüste, kalt, Jargon-Wand ohne Einstiegshilfe.
- **Verspielt-konsumig / B2C-Lifestyle** — Emojis, Lifestyle-Stockfotos, Toy-/Spiel-Optik.

## Design Principles

1. **Erst führen, dann Fachtiefe.** Jede Auswahlstelle muss auch ohne Vorwissen
   funktionieren. Fachsprache (Falz, Lagigkeit, Spendertyp) wird angeboten, nie
   vorausgesetzt — Klartext und Faustregel oben, Profi-Detail per Progressive Disclosure
   dahinter.
2. **Belegen statt behaupten.** Trust-Claims (Zertifikate, Staffelpreise, Lieferzeit) nur
   mit nachprüfbarem Beleg und korrekter Produkt-zu-Siegel-Zuordnung. Lieber konkret und
   belegt als pauschal — schützt vor Greenwashing-/UWG-Risiko und stärkt gerade die
   ESG-Persona.
3. **Ein klarer Weg in den Shop.** Eine Primär-Aktion (ins Sortiment/Kauf); sekundäre
   Pfade ordnen sich sichtbar unter. Keine drei konkurrierenden Vergleichs-Links mit
   demselben Ziel.
4. **Warm und sachlich zugleich.** Beratend im Ton, ruhig im Bild. Vertrauen entsteht
   durch Klarheit und Aufgeräumtheit, nicht durch Lautstärke, Rabatt-Druck oder
   Verspieltheit.
5. **Scanbar für Einkäufer.** Harte Eckdaten (Blatt/Karton, Spender-Fit, Maß, „ab"-Preis)
   gehören dorthin, wo gescannt wird — an Kachel und Karte, nicht nur tief im Fließtext.

## Accessibility & Inclusion

Ziel-Niveau **WCAG 2.1 AA** (im aktuellen Stand bereits weitgehend erfüllt und zu halten):

- Sichtbare `:focus-visible`-Outlines, vollständige Tastatur-Bedienbarkeit von Rail-
  Slider und „Mehr erfahren"-Akkordeon, `aria-label`/`aria-expanded`/`aria-controls`.
- `prefers-reduced-motion`: alle Reveals/Transitions aus, Smooth-Scroll → auto.
- Inhalt ohne JavaScript vollständig sichtbar (`<noscript>`-Fallback + `try/catch`);
  Animation ist reines Progressive Enhancement, nie Voraussetzung für Sichtbarkeit.
- Kontrast ≥ AA für Fließtext (≥ 4.5:1) und große Schrift (≥ 3:1), auch auf den
  getönten Flächen (grauer Info-Karten-Bereich).
- Sprache: Deutsch (B2B). Klartext-Prinzip (s. Design Principle 1) ist zugleich eine
  Inklusionsmaßnahme für fachfremde Nutzer.
