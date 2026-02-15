# hypotheses

Versionierte, referenzierbare, **empirisch oder logisch entscheidbare** Hypothesen  
als Brücke zwischen dem epistemischen Kern und der strukturierten Wissensmatrix.

## Zweck dieses Repositories

Dieses Repository enthält **ausschließlich deklarative, testable Hypothesen**, die aus dem epistemischen Kern (`research-program`) abgeleitet oder dort verankert sind.

Es dient als:

- explizite, versionierbare Sammlung von gerichteten Behauptungen
- Referenzpunkt für die Matrix (`matrix`) und die Instanziierungen (`predictions`)
- sichtbarer Ausdruck des Falsifizierbarkeitsprinzips (Popper-konform)

**Wichtig:**  
Hier gibt es **keine** operationalisierten Modelle, keinen Code, keine Prognosen, keine empirischen Daten und keine Fitting-Ergebnisse.  
→ siehe `predictions` für traceable Projektionen und Evaluations

## Architektur-Einbettung (Stand Februar 2026)

Aktuelle Schichten-Reihenfolge:

0. Legacy                ← dismissed / unresolved / pre-formal  
1. research-program      ← epistemischer Kern, harter Kern, Meta-Regeln  
2. **hypotheses**        ← testable, falsifizierbare Claims (dieses Repo)  
3. matrix                ← strukturierte, admissible Wissensrepräsentation  
4. predictions ← traceable Projektionen, Consequence Maps, Evaluations

Fluss: Kernel → Hypothesen → Matrix → Instanziierungen  
Rückkopplung: Spiralmodell mit expliziten Lifecycle- & Admissibility-Regeln

→ Gesamtdokumentation: [ARCHITECTURE.md](../research-program/blob/main/ARCHITECTURE.md) (oder im Profil-README)

## Prinzipien

- Jede Hypothese erhält eine stabile ID: `H001`, `H002`, …  
- Jede Hypothese **muss** explizite Falsifikationsbedingungen enthalten (empirisch oder logisch entscheidbar)  
- **Versionierung**:
  - Major (z. B. H017 → H018): Änderung der logischen Aussage / des semantischen Kerns
  - Minor (z. B. H017-v1 → H017-v2): Ergänzung / Präzisierung der Falsifikationsbedingungen oder Operationalisierung
  - Patch (z. B. H017-v1.0 → H017-v1.1): Sprachliche Klarstellung, Tippfehler, Format-Anpassung
- Falsifizierte Hypothesen werden **nicht gelöscht**, sondern auf Status `falsified` gesetzt  
- Hypothesen dürfen **keine** impliziten ontologischen Annahmen enthalten, die nicht im Kern explizit zugelassen sind  
- Alle Hypothesen müssen **admissible** sein (keine illegitimen Transfers, keine kategorialen Fehler)

→ Detaillierte Lifecycle-Regeln: [HYPOTHESES-LIFECYCLE.md](../research-program/blob/main/HYPOTHESES-LIFECYCLE.md)

## Ordnerstruktur (aktuell)

hypotheses/
├── README.md
├── index.md                  ← zentrale Übersicht / Liste aller Hypothesen
├── H001/
│   ├── statement.md
│   ├── falsification.md
│   ├── evidence-trace.md
│   └── references.yaml
├── H002/
└── schema/                   ← optionales JSON/YAML-Schema für Hypothesen-Format

## Wie man mitarbeitet / prüft

1. Hypothese klonen / referenzieren: `H127`  
2. Falsifikationsbedingung lesen → ist sie prinzipiell entscheidbar?  
3. Gegen Admissibility-Regeln prüfen (MMS)  
4. Bei Unklarheit / Widerspruch: Issue öffnen oder Spiral-Iteration vorschlagen

## Lizenz

CC BY-NC 4.0  
Non-commercial. Kommerzielle Nutzung oder Ableitungen erfordern separate Vereinbarung.

## Verwandte Repositories

- [research-program](https://github.com/finkeissen/research-program) – epistemischer Kern  
- [mms](https://github.com/finkeissen/mms) – normative Prüfmaschine  
- [matrix](https://github.com/finkeissen/matrix) – strukturierte Wissensrepräsentation  
- [predictions](https://github.com/finkeissen/predictions) – traceable Projektionen & Evaluations  
- [legacy](https://github.com/finkeissen/legacy) – dismissed / unresolved Kandidaten

---

Dieses Repository ist **kein Wahrheitsgenerator**, sondern ein **epistemischer Integritätsfilter**.


