# Tritium-Pion

Independent project workspace for the MARATHON tritium single negative pion production cross-section analysis.

## Quick Start

Start here:

1. Read `docs/STUDENT_HANDOFF.md`.
2. Read `docs/single_pion_physics_goals.md`.
3. Read `docs/single_pion_cross_section_strategy.md`.
4. Inspect `analysis/Yield.C` and the helper headers in `analysis/`.
5. Build a reproducible run database from `run_lists/*.dat`.

## Project Structure

```text
Tritium-Pion/
  README.md
  AGENTS.md
  docs/
    STUDENT_HANDOFF.md
    single_pion_physics_goals.md
    single_pion_cross_section_strategy.md
    figures/
      pion_xs_plot1.png
      pion_xs_plot2.png
    pdf/
      single_pion_physics_motivation_zh.pdf
      single_pion_analysis_plan_zh.pdf
  analysis/
    Yield.C
    TRI_Beam.h
    TRI_Target.h
    TRI_LiveTime.C
    TRI_Tools.h
    TRI_Main.h
    wiser_all_sig.f
    yield_plot.ipynb
  run_lists/
    *.dat
  references/
    qiu_reports/
    papers/
    thesis/
  output/
    single_pion/
```

## Current Physics Goal

Extract inclusive single negative pion production cross sections from MARATHON data:

```text
e + A -> pi- + X,   A = H1, D2, H3, He3
```

The analysis should establish absolute cross sections and target ratios, then compare the data with Wiser-like soft-production baselines, fragmentation-based calculations, joint QCD+QED leading-power calculations, and possible direct or higher-twist pion mechanisms.

## Existing Interpretation

The preliminary cross-section plots show that Wiser/model baselines describe the rough scale but not the detailed `P_T` and `x_bj` dependence. The data appear harder in `P_T` than a simple Wiser baseline and show model failure in the high-`x_bj` region. This motivates treating the result as a JLab fixed-target single-pion production mechanism benchmark, not merely as a byproduct of MARATHON electron DIS.

## First Implementation Milestone

Do not start with a final physics fit. First build the reproducible analysis infrastructure:

- `output/single_pion/run_db.csv`
- `output/single_pion/run_quality.csv`
- `output/single_pion/run_exclusions.csv`
- electron benchmark validation output
- pion PID control plots
- pion trigger/live-time tables
- first H1 pion cross-section table

## Related Feishu Wiki Pages

- MARATHON single-pion production: physics goals and motivation
  https://tmeg-thu.feishu.cn/wiki/VTJ8w96vSi9BXGk9nSdcDzlynvd

- MARATHON inclusive single negative pion cross-section analysis strategy
  https://tmeg-thu.feishu.cn/wiki/If5twuc11i4JdSkvk9LcmN3Anad
