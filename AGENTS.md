# AGENTS.md

## Project

This directory is an independent project for the MARATHON tritium single negative pion production cross-section analysis.

Use Chinese for ordinary communication with the user. Use polished academic English only when drafting manuscript text intended for an international publication.

## First Files To Read

Before making analysis or writing changes, read:

1. `docs/STUDENT_HANDOFF.md`
2. `docs/single_pion_physics_goals.md`
3. `docs/single_pion_cross_section_strategy.md`
4. `README.md`

For code work, also inspect:

1. `analysis/Yield.C`
2. `analysis/TRI_Beam.h`
3. `analysis/TRI_Target.h`
4. `analysis/TRI_LiveTime.C`
5. `analysis/TRI_Tools.h`
6. `run_lists/*.dat`

## Scientific Guardrails

- Do not call this an electron DIS cross-section analysis. The observable is inclusive final-state `pi-` production.
- Do not directly reuse electron DIS radiative corrections for pion production without a separate justification.
- Do not claim fragmentation dominance until non-prompt pion, soft/VMD, electron leakage, PID contamination, and model dependence are evaluated.
- Do not interpret `H3/He3` as direct flavor separation before controlling nuclear effects, acceptance, PID, final-state interactions, and charge-exchange/feed-down.
- Distinguish data-supported results, model interpretations, and hypotheses still requiring validation.

## Analysis Priorities

The first milestone is reproducibility, not final physics interpretation.

Build:

- run database from `run_lists/*.dat`
- replay and ROOT file availability checks
- trigger/prescale/scaler branch checks
- electron benchmark reproduction
- pion PID control plots
- pion live-time and trigger-efficiency tables
- first H1 absolute cross-section table

Then extend to D2, H3, and He3 and produce target ratios.

## Output Convention

Write analysis outputs under:

```text
output/single_pion/
```

Recommended files:

```text
output/single_pion/run_db.csv
output/single_pion/run_quality.csv
output/single_pion/run_exclusions.csv
output/single_pion/electron_benchmark.csv
output/single_pion/pion_raw_yields.csv
output/single_pion/pion_corrections.csv
output/single_pion/pion_cross_sections.csv
output/single_pion/pion_systematics.csv
output/single_pion/plots/
```

## Writing Style

For reports:

- Keep claims defensible.
- Separate near-term publishable outputs from high-risk physics interpretations.
- Make formulas readable in Markdown/LaTeX.
- Preserve the distinction between experimental extraction and model interpretation.

For code:

- Preserve the existing MARATHON analysis workflow unless there is a clear reason to refactor.
- Prefer reproducible functions and tables over one-off notebook cells.
- Track data provenance, correction factors, and uncertainty propagation explicitly.
