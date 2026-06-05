---
target: papierhandtuecher-hero.html
total_score: 31
p0_count: 1
p1_count: 4
timestamp: 2026-06-05T20-06-24Z
slug: papierhandtuecher-hero-html
---
# Design-Critique — Hero „Papierhandtücher" (Hamburg Papier, Shopware 6 Erlebniswelt)

Register: BRAND (Marketing-Kategorie-Hero). Bewertet gegen die frisch angelegte `PRODUCT.md`
(Doppel-Zielgruppe „Profi-Tiefe + Laien-Brücke", Stimme „nahbar & beratend", Primärziel „ins
Sortiment/Kauf", Anti-Refs: billig / AI-Template / behörden-trocken / verspielt-konsumig).
Quelle vollständig gelesen (HTML+CSS+JS), gestützt auf eine unabhängige 5-Persona-Analyse.

## Design Health Score

| # | Heuristik | Score | Kernproblem |
|---|-----------|-------|-------------|
| 1 | Visibility of System Status | 4 | Hover/Focus, Pfeile disablen an den Enden, `aria-expanded`, Neuer-Tab-Icons. Solide. |
| 2 | Match System / Real World | 2 | Fachsprache (Z-/C-Falz, Interfold, Lagigkeit, TCO/HACCP/ESG) wird vorausgesetzt — sperrt die Laien-Hälfte der definierten Zielgruppe aus. |
| 3 | User Control & Freedom | 4 | Slider beidseitig, Akkordeon auf/zu, neue Tabs gelabelt, `prefers-reduced-motion` sauber. |
| 4 | Consistency & Standards | 3 | Rail-Label-Grammatik bricht („1-lagig · Z-Falz" vs. nacktes „Interfold"); 1 Ziel, 3 Labels; h3/h4 doppelt. |
| 5 | Error Prevention | 3 | Links jetzt echt; aber kein Spender-Fit-Schutz → Laie kann falsche Falz kaufen; Zertifikats-Claims pauschal. |
| 6 | Recognition over Recall | 3 | Echte Fotos + benannte Typen, aber „Z-Falz" verlangt Vorwissen (Recall) vom Neuling. |
| 7 | Flexibility & Efficiency | 3 | Zwei CTAs decken entschlossen/stöbernd ab; FM-Bulk-/Nachbestellpfad fehlt, Preis-Pfad leise. |
| 8 | Aesthetic & Minimalist | 3 | Sehr aufgeräumt, aber Zertifikats-Botschaft 3-fach redundant + dichte Volltexte verwässern. |
| 9 | Error Recovery | 3 | `noscript`-Fallback + `try/catch` garantieren Sichtbarkeit; Bild-Platzhalter vorhanden. Wenig zu „recovern". |
| 10 | Help & Documentation | 3 | „Gut zu wissen" + „Mehr erfahren" + Produktfinder = echte Selbsthilfe, aber auf Profis gepitcht statt auf die, die sie brauchen. |
| **Total** | | **31/40** | **Good** |

Gleiche Kopfzahl wie die Alt-Critique (31), aber **andere Schwäche**: Die alten Reliability-Probleme
(Hero ohne JS unsichtbar, tote Links, leerer Video-Poster) sind behoben. Was den Score jetzt drückt,
ist **Zielgruppen-Fit** — die Match-Real-World-Lücke für die Laien-Hälfte, die `PRODUCT.md` erst
sichtbar macht. Das Thema ist von „funktioniert es?" zu „spricht es alle meine Käufer an?" gewandert.

## Anti-Patterns Verdict

**LLM-Assessment: kein AI-Slop.** Bewusste, markensichere Arbeit. Die frei schwebenden Produktfotos
(`mix-blend-mode:multiply` statt identischem Karten-Grid) sind die Signatur; Bannliste sauber (kein
Gradient-Text, keine Side-Stripe-Borders, kein Hero-Metric-Template, keine Eyebrow-Kicker, keine
Em-Dashes). **Einzige Slop-Drift:** die langen „Gut zu wissen"-Volltexte stapeln Fachbegriffe in
Klammer-Doppelungen (TCO, Cost-in-Use, HACCP, ESG, Green Procurement) so dicht, dass der Ton Richtung
„keyword-gestopft" + „behörden-trocken" kippt — zwei der vier Anti-Referenzen aus `PRODUCT.md`.

**Deterministischer Scan (`detect.mjs --json`): 2 Findings, beide verifiziert FALSE POSITIVE.**
- `em-dash-overuse` „139" → `grep` findet **0** echte Em-Dashes (`—`); gezählt werden die `--hph-*`
  CSS-Custom-Properties und `--` in `calc()`.
- `numbered-section-markers` „01/02/03/04/05/08" → CSS-Dezimalfragmente (`line-height:1.04`,
  `--hph-s:1.05`, `clamp(...)`), keine sichtbaren Sektions-Marker.
- Ursache: Der Detektor mis-skopt Inline-CSS in einem self-contained Erlebniswelt-Block. **Netto 0
  echte maschinelle Tells** — deckt sich mit dem LLM-Urteil.

**Browser-Overlay:** nicht ausgeführt (self-contained Einzeldatei unter Windows; Live-Server-Injektion
übersprungen, um schwere/fehleranfällige Setup-Schritte zu vermeiden). Fallback-Evidenz: vollständiger
Quell-Read + unabhängige 5-Persona-Analyse.

## Overall Impression

Ein handwerklich überdurchschnittlicher, markensicherer Hero, der für **Profi-Einkäufer schon heute
sehr gut funktioniert** (Falz-IA, Trust-Strip, TCO-Sprache). Die größte Chance liegt exakt dort, wo
`PRODUCT.md` jetzt die zweite Hälfte der Zielgruppe verankert: **die Laien-Brücke**. Wer keinen
Falz-Typ kennt, wird am Entscheidungspunkt allein gelassen. Zweitgrößter Hebel: **Trust belegen statt
behaupten**, damit die ESG-/Vergabe-Persona zitierfähige Nachweise bekommt.

## What's Working

1. **Foto-Rail ohne Karten-Chrome** — premium, kuratiert, vermeidet den Card-Grid-Trap. Die Signatur.
2. **Domänengenaue IA & Trust-Strip** — Falz + Lagigkeit + Staffelpreise/Zertifikate/Lieferzeit ist
   exakt das mentale Raster des Gewerbe-Einkäufers.
3. **Disziplinierte Motion + A11y** — gestaffelter Reveal als Progressive Enhancement, `:focus-visible`,
   gründlicher `prefers-reduced-motion`-Block, Inhalt ohne JS sichtbar.

## Priority Issues

**[P0] Falz-/Lagen-Begriffe unerklärt am Entscheidungspunkt.**
- *Warum:* Rail-Labels („1-lagig · Z-Falz", „Interfold", „C-Falz") setzen Spender-/Falz-Wissen voraus.
  Für die in `PRODUCT.md` gleichrangig definierte Laien-Hälfte (Gastro, Erstbesucher) ist das ein
  Abbruchpunkt — verstößt direkt gegen Design Principle 1 „Erst führen, dann Fachtiefe".
- *Fix:* Klartext-Mikrocopy je Kachel („ergiebig & günstig" / „weicher fürs Gäste-WC" / „passt in
  Standard-Zickzack-Spender") + ein Intro-Satz „Die Falzung muss zu Ihrem Spender passen — so finden
  Sie sie". Progressive Disclosure: Klartext oben, Fachbegriff dahinter.
- *Command:* `$impeccable onboard`

**[P1] Kein „Welches passt zu mir?" / Spender-Einstieg.**
- *Warum:* Die Subline verspricht „die passende Falzung für jeden Spender", liefert dann aber keinen
  Pfad dahin. Es fehlt ein niedrigschwelliger Einstieg (Betriebsart/Spendertyp → Empfehlung).
- *Fix:* Dritter, ruhiger Einstieg „Unsicher? Passende Falzung finden" oder ein „So erkennen Sie Ihren
  Spender"-Visual. Keine neue Tab-Flucht für Laien.
- *Command:* `$impeccable shape`

**[P1] Zertifikats-Claims pauschal/unbelegt — UWG-/Greenwashing-Risiko.**
- *Warum:* Trust-Strip behauptet „EU Ecolabel & Blauer Engel" für die Kategorie, die Belege decken aber
  je nur EIN Einzelprodukt. Lizenznummer/Gültigkeit fehlen; der 2-lagig-Text bietet „Recycling ODER
  Frischzellstoff", ohne zu sagen welche Variante welches Siegel trägt. Verstößt gegen Principle 2.
- *Fix:* Lizenznr. (EU-Ecolabel DE/004/…), RAL-UZ-Vergabegrundlage + Gültigkeit ergänzen; Produkt-zu-
  Siegel-Zuordnung klarstellen; unbelegte „messbar/erheblich" belegen oder streichen. **Braucht echte
  Daten von Hamburg Papier.**
- *Command:* `$impeccable clarify`

**[P1] Ein Ziel, drei Wege — Produktfinder-Link 3×, Preis-Pfad zu leise.**
- *Warum:* „Staffelpreise vergleichen" (Ghost), Rail-Kachel „Preise vergleichen", Karten-Head „Zum
  Produktfinder" zeigen alle auf dieselbe URL mit drei Labels → verwässerte CTA-Hierarchie. Der für FM
  kaufentscheidende Preis-Pfad ist zugleich der leiseste Touchpoint. Verstößt gegen Principle 3.
- *Fix:* Auf einen benannten Primär-Pfad bündeln, Labels vereinheitlichen, visuelles Gewicht erhöhen.
- *Command:* `$impeccable distill`

**[P1] „Gut zu wissen"-Volltexte zu dicht — kippen in zwei Anti-Referenzen.**
- *Warum:* Jargon-Wände (TCO/HACCP/Cost-in-Use/ESG) bedienen nur FM/ESG; Gastro/Erstbesucher schalten
  ab. Ton driftet Richtung „behörden-trocken" + „AI-buzzword" — beides explizit unerwünscht.
- *Fix:* Pro Karte ein alltagsnaher Lead + Faustregel zuerst („Für kleine Betriebe heißt das: …"),
  dann die Profi-Tiefe; Begriffsdichte etwa halbieren, Stimme „nahbar & beratend" treffen.
- *Command:* `$impeccable distill`

## Persona Red Flags

**Jordan (Erstbesucher/Nicht-Experte):** Falz-Vokabular ohne eine einzige Inline-Definition; „Mehr
erfahren" verspricht Hilfe, liefert aber Einkäufer-Argumentation. Klickt „Zum Sortiment" blind oder
springt ab.

**Casey (abgelenkt, mobil):** H1 „Papierhandtücher" kann bei kleinster `clamp`-Stufe via `hyphens:auto`
mitten im Wort getrennt werden („Papierhand-tücher"); die Rail-Edge-Fade-Maske + Chevrons verstecken,
dass weitere Kacheln existieren → C-Falz/„Preise vergleichen" werden übersehen.

**Mehmet (Gastro-Inhaber, projektspezifisch):** Will in 30 Sek. „das Richtige für mein Café" + fairen
Preis. Bekommt fünf kryptische Falz-Kacheln, keinen sichtbaren „ab"-Preis und ESG-lastige Erklär-Karten
(2 von 4 sind Siegel). Findet keinen Einstieg, der ihn meint.

**Dr. Berg (ESG-Beschaffung, projektspezifisch):** Belege liegen unabhängig & verlinkt vor (stark!),
aber ohne Lizenznummer/Gültigkeit nicht vergabeakten-tauglich; „messbar/erheblich" ohne Bezugsgröße ist
nicht zitierfähig; offizielle Bildmarken (Ecolabel-Blume, Blauer-Engel-Zeichen) fehlen.

## Minor Observations

- **h3/h4-Dublette:** Der Detail-Titel wiederholt wortgleich den Karten-Titel nach dem Aufklappen.
- **Tool-Kachel bricht das Foto-System:** Rail-Kachel 6 ist ein Utility-Objekt im Foto-Look und braucht
  eine auffällige Sonderskalierung (`--hph-s:1.14; --hph-y:20px`) — gehört optisch nicht ins Raster.
- **„Jetzt kaufen" auf Zertifikats-Karten** führt auf die ungefilterte Gesamtliste statt auf
  zertifizierte Produkte — Erwartungsbruch für die ESG-Persona.
- **3-lagig** ist in der Rail wählbar, hat aber keine Erklär-Karte; FM hält „3-lagig · Z-Falz" zudem für
  praxis-fragwürdig (Beleg oder Korrektur).
- **Lieferzeit „ca. 4 Werktage"** ohne Karton-/Palettenbezug ist für FM-Disposition nicht belastbar.
- **Generisches Siegel-Icon** statt offizieller Bildmarke schwächt einen sonst belegbaren Claim.

## Questions to Consider

1. Sollte die **primäre Achse** der Rail „Anwendung/Spender-Fit" sein, mit Falz als Sekundärfilter —
   statt umgekehrt? Das würde Profi und Laie gleichzeitig bedienen.
2. Was wäre der **eine** sichtbare „ab"-Preis, der Mehmet zum Klick bewegt, ohne die Premium-Ruhe zu
   brechen?
3. Verträgt die Zertifikats-Sektion eine **Eskalation** (kurzer Trust-Hinweis → bei Interesse Tiefe)
   statt der aktuellen 3-fachen Flach-Wiederholung?
