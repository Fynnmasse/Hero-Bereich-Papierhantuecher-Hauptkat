---
target: papierhandtuecher-hero.html
total_score: 31
p0_count: 1
p1_count: 3
timestamp: 2026-05-29T11-01-05Z
slug: papierhandtuecher-hero-html
---
# Design-Critique — Hero „Papierhandtücher" (Hamburg Papier, Shopware 6 Erlebniswelt)

Register: BRAND (Marketing-Kategorie-Hero). Quelle + gerendert auf Desktop (1440) und Mobil (414).

## Design Health Score

| # | Heuristik | Score | Kernproblem |
|---|-----------|-------|-------------|
| 1 | Visibility of System Status | 3 | Hover/Focus gut; pulsierender „Live"-Punkt am Video suggeriert Livestream, ist aber ein Loop. |
| 2 | Match System / Real World | 4 | „Z-Falzung / Interfold / C-Falz" = exakt die B2B-Einkäufer-Sprache. |
| 3 | User Control & Freedom | 3 | Video-Loop ohne Pause/Stop; reduced-motion respektiert. |
| 4 | Consistency & Standards | 3 | Label-Grammatik gemischt: 4× „X-lagig / Z-Falzung" vs. nackt „Interfold"/„C-Falz". |
| 5 | Error Prevention | 2 | Alle hrefs `#` → bei Live-Gang 6 tote Links + 2 tote CTAs ohne Feedback. |
| 6 | Recognition over Recall | 4 | Echte Produktfotos + benannte Falt-Typen, nichts zu merken. |
| 7 | Flexibility & Efficiency | 3 | Zwei CTAs decken entschlossene + stöbernde Käufer ab. |
| 8 | Aesthetic & Minimalist | 4 | Sehr aufgeräumt, klare Fokus-Spalte, großzügiger Weißraum. |
| 9 | Error Recovery | 2 | `poster=""` leer → wenn .mp4 nicht lädt, leerer Gradient mit schwebender Caption. |
| 10 | Help & Documentation | 3 | „Produktfinder starten" als Self-Service-Hilfe angemessen. |
| **Total** | | **31/40** | **Good** |

## Anti-Patterns Verdict

**Kein AI-Slop.** Das Stück liest sich als bewusste, markenbewusste Arbeit. Die stärkste Anti-Slop-Entscheidung: die frei schwebenden Produktfotos via `mix-blend-mode:multiply` statt identischer Karten-Grid. Bannliste sauber: kein Gradient-Text, keine Side-Stripe-Borders, keine Default-Glassmorphism, kein Hero-Metric-Template, keine Em-Dashes. Einziger Gradient: die Akzentlinie unter der H1.

**Deterministischer Scan:** `detect.mjs --json` → Exit 0, **0 Findings** (echter Bundled-Detector, kein Fallback). Die absichtlichen Inline-`<style>`/`<script>` (nötig für den Erlebniswelt-Paste) wurden korrekt NICHT geflaggt. Keine False Positives.

**Overlay:** kein Live-Overlay (lokale Datei → Fallback auf Screenshot-Evidenz). Render bestätigt: alle 5 Produktfotos + Videoframe laden, keine Broken-Images.

→ LLM-Review und Detektor sind einig, dass es keine maschinellen Anti-Pattern-Tells gibt. Alle echten Schwächen sind semantisch/robustheitsbezogen — genau die Klasse, die ein deterministischer Scanner nicht sieht.

## Overall Impression

Ein wirklich guter, markensicherer Hero, getragen von einer starken Idee (Foto-Rail) und disziplinierter Motion/A11y. Die offene Arbeit ist **Zuverlässigkeit, nicht Geschmack**: ohne JS unsichtbarer Hero, leerer Video-Poster, ungesicherte Platzhalter-Links. Größte Chance: den Hero ohne JS sichtbar machen und die Trust-Signale für B2B (Staffelpreise, Zertifikate, Herkunft) stärken.

## What's Working

1. **Foto-Rail ohne Karten-Chrome** (`mix-blend-mode:multiply`, `object-fit:contain`). Premium, kuratiert, vermeidet den Card-Grid-Trap. Die Signatur des Designs.
2. **Domänengenaue IA & Sprache.** Falt-Typ + Lagigkeit ist exakt das mentale Raster eines Gastro-/Gewerbe-Einkäufers.
3. **Disziplinierte Motion + A11y-Hygiene.** Gestaffelter IntersectionObserver-Reveal, ease-out-Kurve, echte `:focus-visible`-Outlines, gründlicher `prefers-reduced-motion`-Block (pausiert auch das Video).

## Priority Issues

**[P0] Ohne JS ist der gesamte Hero unsichtbar.**
- *Warum:* `.hph-hero__head/.rail/.video` starten mit `opacity:0` und werden NUR durch die per JS gesetzte Klasse `.is-ready` sichtbar. Bei deaktiviertem JS oder einem Script-Fehler irgendwo auf der Seite bleibt der Hero komplett leer. Auf einer kommerziellen Landingpage ist das ein Showstopper.
- *Fix:* Baseline auf `opacity:1` invertieren. Per JS zuerst eine Klasse `hph-hero--js` setzen und nur DANN den Startzustand `opacity:0` anwenden (`.hph-hero--js .hph-hero__head{opacity:0;…}`). Worst Case wird so „keine Animation" statt „kein Hero".
- *Command:* `$impeccable harden`

**[P1] Leerer `poster=""` + Autoplay → leeres/janky LCP, kein Fallback.**
- *Warum:* `poster=""` ist schlechter als kein Poster. Lädt die .mp4 langsam/blockiert (Firmennetz, Data-Saver, iOS Low-Power), sieht der Käufer eine leere blaue Fläche mit schwebender Caption. Der Fabrik-Shot ist ein Trust-Asset; leer beim LCP ist das Gegenteil.
- *Fix:* Ein echtes Standbild als `poster` setzen (erster Produktionsframe). Gradient nur als tertiärer Fallback.
- *Command:* `$impeccable harden`

**[P1] Sechs tote `#`-Links + zwei tote CTAs gehen ungesichert live.**
- *Warum:* Bekannte TODOs, aber als Copy-Paste-CMS-Snippet ist „später ausfüllen" genau die Stelle, die vergessen wird. `href="#"` springt zudem nach oben → wirkt kaputt.
- *Fix:* Bis echte URLs da sind, Platzhalter auf die bestehende Kategorie-Listing-Seite zeigen lassen (nichts tot), TODO-Kommentare behalten.
- *Command:* `$impeccable clarify`

**[P1] Inkonsistente Label-Grammatik in der Rail.**
- *Warum:* 4 Labels „{Lagigkeit} / {Falz}", aber „Interfold"/„C-Falz" nackt. Beim Scannen bricht der Rhythmus; wirkt wie unvollständige Daten.
- *Fix:* Auf EIN Muster normalisieren (z. B. „Interfold / 2-lagig", „C-Falz / 1-lagig") oder Lagigkeit aus allen fünf entfernen.
- *Command:* `$impeccable clarify`

**[P2] Pulsierender „Live"-Punkt auf einer Aufzeichnung.**
- *Warum:* Pulspunkt = universelles „LIVE"-Signal; auf einem Loop überverspricht es und ist Motion-Rauschen.
- *Fix:* Durch einen statischen Standort-Pin/Anker ersetzen (Herkunft statt Status) oder entfernen.
- *Command:* `$impeccable polish`

## Persona Red Flags

**Jordan (Erstbesucher/Nicht-Experte):** Falt-Vokabular begeistert Experten, blockiert aber Jordan („Z-Falzung", „C-Falz" setzen Dispenser-Wissen voraus). Rettungsanker „Produktfinder starten" ist als Ghost-Button visuell leiser als die Tiles → Jordan wählt ggf. blind oder springt ab. Die nackten „Interfold"/„C-Falz"-Labels geben noch weniger Anker.

**Riley (Stresstester):** Klickt sofort alle Tiles/CTAs → alle `#` → Seite springt hoch → wirkt kaputt (Top-Finding). Deaktiviert JS → Hero komplett unsichtbar (der P0). Killt das Netz → leerer Poster (der P1). Resize-Band 760–900px: `flex-wrap:wrap` + `space-between` kann eine einzelne Tile mit großen Lücken in Zeile 2 stranden lassen.

**Casey (abgelenkt, mobil):** Auf 414px clippt die Subline am rechten Rand („Für Gastronomie, Gewe…"), bevor sie sauber umbricht. Die Edge-Fade-Maske der Rail versteckt zudem, dass weitere Tiles existieren → ein flüchtiger Daumen-Scroller verpasst evtl. „C-Falz"/„Alle ansehen".

## Minor Observations

- **H1-Unterstrich ist ein Gradient** (`brand → brand-light`) — der einzige Gradient in einem sonst gradient-freien System. Ein solider Balken wäre konsequenter.
- **`--hph-brand-light` (Hue 232)** ist merklich cyaniger als das Brand-Blau (Hue 248). Bewusst? Sonst Richtung Navy ziehen.
- **`.hph-rail__tag`** (oranger „Neu"-Tag) ist im CSS definiert, aber im Markup ungenutzt — toter Stil.
- **Produktfoto-Skalierung uneinheitlich** (das grüne Interfold-Bild rendert deutlich kleiner als die Karton-Shots). `object-fit:contain` ist ehrlich, aber die Quell-Crops variieren stark → Rail wirkt leicht uneben. Quellbilder einheitlicher freistellen.
- **`mix-blend-mode:multiply`** ist hintergrund-fragil (braucht near-white). Hier ok, weil die Rail tief genug unter dem blauen Radial-Glow sitzt.

## Questions to Consider

1. **Verkauft die Rail das Richtige?** Ein Erst-Käufer denkt nicht „ich brauche C-Falz", sondern „Tücher für meinen Spender / mein Budget / in Menge". Sollte die primäre Achse Anwendung/Spender-Fit sein, mit Falz als Sekundärfilter im Produktfinder?
2. **Was kauft das Video, und ist 16:9 unten richtig?** Es ist das größte/schwerste Element und steht UNTER den Produkten. Wenn „Produktion in Hamburg" ein Kern-Trust-Hebel ist, warum nicht in den Kopf weben?
3. **Lohnt eine Reveal-Animation die Fragilität?** „Inhalt standardmäßig sichtbar, Animation als Progressive Enhancement" macht den Worst Case „keine Animation" statt „kein Hero".
