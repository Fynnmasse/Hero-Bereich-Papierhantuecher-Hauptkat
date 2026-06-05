---
target: papierhandtuecher-hero.html (nach Umsetzung)
total_score: 35
p0_count: 0
p1_count: 2
timestamp: 2026-06-05T20-17-56Z
slug: papierhandtuecher-hero-html
---
# Re-Score nach Umsetzung — Hero „Papierhandtücher" (Hamburg Papier)

Code-basierter Audit nach den Schritten onboard → shape → distill → layout → bolder →
clarify → adapt → polish. Bewertet gegen `PRODUCT.md` (Doppel-Zielgruppe, Stimme
„nahbar & beratend"). Browser-Render-Verifikation an einem echten Viewport steht noch aus.

## Design Health Score

| # | Heuristik | vorher | nachher | Änderung |
|---|-----------|:---:|:---:|---|
| 1 | Visibility of System Status | 4 | 4 | – |
| 2 | Match System / Real World | 2 | 3 | Klartext-Hints je Kachel + „Kurz gesagt"-Leads überbrücken die Fachsprache |
| 3 | User Control & Freedom | 4 | 4 | – |
| 4 | Consistency & Standards | 3 | 4 | Rail-Labels jetzt einheitlicher Zweizeiler; Dreifach-Finder-Link aufgelöst |
| 5 | Error Prevention | 3 | 3 | Spender-Leitzeile als weiche Hilfe; Zertifikats-Claims nun im Geltungsbereich klar |
| 6 | Recognition over Recall | 3 | 4 | Klartext-Hints senken die Wissens-Voraussetzung am Entscheidungspunkt |
| 7 | Flexibility & Efficiency | 3 | 3 | – (FM-Bulk-Pfad weiterhin offen) |
| 8 | Aesthetic & Minimalist | 3 | 3 | Tool-Kachel raus (sauberer), aber Zertifikats-Botschaft bleibt 3-fach |
| 9 | Error Recovery | 3 | 3 | – |
| 10 | Help & Documentation | 3 | 4 | Laien-Leads machen die Hilfe für Nicht-Experten nutzbar |
| **Total** | | **31** | **35** | **Good (oberes Drittel)** |

**P0 behoben:** Falz-/Lagen-Jargon hat jetzt eine Laien-Brücke (Hints + Leitzeile + Leads).

## Deterministischer Scan

`detect.mjs --json` → weiterhin 2 Findings, **beide verifizierte False Positives**:
em-dash-overuse zählt `--hph-*`-CSS-Variablen (echte Em-Dashes per `grep`: 0);
numbered-section-markers zählt CSS-Dezimalwerte. Netto 0 echte Tells.

## Offen (braucht Kundendaten / Fachentscheidung)

- EU-Ecolabel-Lizenznummer + Blauer-Engel-RAL-UZ/Gültigkeit (TODO-Marker im Code gesetzt).
- Korrektheit von „3-lagig · Z-Falz" (FM hält das für praxis-fragwürdig).
- Optionaler FM-Bulk-/Angebots-Pfad (nur sinnvoll mit Angebots-Ziel im Shop).
- Offizielle Siegel-Bildmarken statt generischem Icon.
- „Jetzt kaufen" auf Zertifikats-Karten → gefilterte Ansicht (URL nötig).
