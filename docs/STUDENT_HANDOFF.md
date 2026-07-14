# Tritium / MARATHON Single Pion Analysis Handoff

Updated: 2026-07-14

This document is the entry point for a student or collaborator taking over the MARATHON tritium single-pion analysis. It does not replace the detailed analysis notes. Its purpose is to collect the current physics motivation, input materials, analysis plan, preliminary interpretation, and near-term tasks in one place.

## 1. Files To Read First

Read the following files in order:

1. `docs/single_pion_physics_goals.md`
   - Physics goals and motivation.
   - Pay special attention to the mechanism separation among the Qiu reports, the Afanasev-Carlson work, soft/VMD sources, fragmentation, and direct or higher-twist pion production.

2. `docs/single_pion_cross_section_strategy.md`
   - Analysis strategy and technical workflow.
   - Focus on which parts of the MARATHON electron DIS normalization chain can be reused and which parts must be rebuilt for pion production.

3. `docs/pdf/single_pion_physics_motivation_zh.pdf`
   - Earlier Chinese PDF version of the physics motivation.

4. `docs/pdf/single_pion_analysis_plan_zh.pdf`
   - Earlier Chinese PDF version of the analysis plan.

5. `docs/figures/pion_xs_plot1.png` and `docs/figures/pion_xs_plot2.png`
   - Early extracted single-pion cross-section plots and Wiser/model comparisons.
   - The final result is not expected to be qualitatively different from these preliminary plots; the main work is to improve reproducibility, systematic uncertainties, and physics interpretation.

6. `analysis/`
   - Existing analysis-code entry points.
   - In particular, inspect `Yield.C`, `TRI_Beam.h`, `TRI_Target.h`, `TRI_LiveTime.C`, `TRI_Tools.h`, `wiser_all_sig.f`, and `yield_plot.ipynb`.

7. `run_lists/`
   - Run lists for H1, D2, H3, and He3 at the available kinematic settings.

8. `references/`
   - Local reports and papers.
   - Qiu reports: `references/qiu_reports/SoLID_ANL_Qiu.pdf`, `references/qiu_reports/SoLID2025July_Qiu.pdf`, and `references/qiu_reports/2607.07664v1.pdf`.
   - Afanasev-Carlson papers: `references/papers/PhysRevD.61.034014.pdf`, `references/papers/1-s2.0-S037594740301176X-main.pdf`, `references/papers/0212376v1.pdf`, and related papers.
   - MARATHON PRL papers and supplemental files.

## 2. Feishu Wiki Pages

Two Markdown notes have also been uploaded as Feishu Wiki pages rather than as ordinary file attachments.

Target knowledge space:

- `Single Pion Production from A=3`

Pages:

- MARATHON single-pion production: physics goals and motivation
  https://tmeg-thu.feishu.cn/wiki/VTJ8w96vSi9BXGk9nSdcDzlynvd

- MARATHON inclusive single negative pion cross-section analysis strategy
  https://tmeg-thu.feishu.cn/wiki/If5twuc11i4JdSkvk9LcmN3Anad

When updating Feishu pages from local Markdown, display equations may need to be converted from `$$...$$` blocks into Feishu-compatible `<latex>...</latex>` blocks before upload. The GitHub Markdown files should keep standard `$$...$$` display math.

## 3. Current Physics Story

This project should not be framed as a byproduct of the MARATHON electron DIS analysis. A more accurate framing is:

The MARATHON inclusive negative pion data provide absolute pion cross sections and target ratios for `H1`, `D2`, `H3`, and `He3` under the same beam, HRS, and cryogenic-target conditions. These data can test final-state pion production mechanisms in the JLab 12 GeV fixed-target regime.

The core questions are:

- Does the observed leading pion mainly come from struck-parton fragmentation?
- Are soft/VMD photoproduction, vector-meson decays, direct or higher-twist isolated pion production, or semi-exclusive dynamics significant?
- Do the `H3/He3` mirror-nucleus ratios show measurable isospin or nuclear dependence?

This is a prerequisite question for SIDIS and TMD pion observables. If the inclusive single-pion cross section cannot be described by a simple fragmentation picture, then pion-based extractions of TMDs, FFs, or spin asymmetries require an explicit mechanism uncertainty.

## 4. Preliminary Plot Interpretation

`docs/figures/pion_xs_plot1.png`:

- The upper panel shows early extracted `D2`, `H3`, and `He3` single-pion cross sections versus `P_T`, compared with a Wiser fit.
- The lower panel shows `sigma_Wiser / sigma_Data`.
- The main feature is that Wiser/Data decreases from roughly `1.5-2.2` at low `P_T` to below 1 at high `P_T`.
- This means the Wiser baseline is high at low momentum and low at high momentum; the measured `P_T` spectrum is harder than Wiser.
- A single normalization factor cannot fix this. The issue is a shape or mechanism-composition problem.

`docs/figures/pion_xs_plot2.png`:

- The upper panel compares the early cross section with a model.
- The lower panel shows `sigma_data / sigma_model` versus `x_bj`.
- The model is close to the data at low to intermediate `x_bj`, but data/model drops significantly at high `x_bj`.
- This may reflect phase-space limitations, radiative smearing, acceptance/bin-centering effects, nuclear attenuation, final-state interactions, or an incomplete mechanism decomposition.

Conservative interpretation:

- Wiser/model baselines describe the rough scale but not the full `P_T` and `x_bj` dependence.
- The data are harder in `P_T` than a simple soft empirical baseline, suggesting possible contributions from prompt fragmentation, direct/higher-twist pions, or semi-exclusive dynamics.
- The A=3 mirror-nucleus comparison can become a new benchmark for pion production in light nuclei, but it should not be described as flavor separation before systematic uncertainties and backgrounds are controlled.

## 5. Analysis Goals

The first-stage result is:

```text
d^2 sigma_pi- / (d p_pi d Omega_pi)
for H1, D2, H3, He3
```

Recommended ratios:

```text
D2 / H1
H3 / H1
He3 / H1
H3 / He3
H3 / D2
He3 / D2
```

The first stage should emphasize:

- absolute cross sections;
- target ratios;
- PID, trigger, tracking, acceptance, and target-normalization systematics;
- electron leakage, kaon/proton contamination, and target-window background;
- Wiser/model comparisons only as sanity checks or soft-source baselines;
- fiducial acceptance-averaged cross sections as the first robust result.

The second stage can address:

- NLO `lN -> hX` and fragmentation comparisons;
- VMD/soft and direct/higher-twist mechanism maps;
- non-prompt pion sources and vector-meson decays;
- QCD+QED radiative smearing;
- nuclear and isospin dependence in A=3 mirror nuclei.

## 6. Technical Analysis Route

The first required product is a run database:

```text
run number
target: H1, D2, H3, He3
kinematic setting: Kin1, Kin2, Kin3, Kin5, Kin7
HRS arm
central momentum and angle
magnet polarity
beam charge
prescale factors
electron trigger bit
pi- trigger bit
replay version
ROOT file path
good/bad flag
exclusion reason
```

Recommended output files:

```text
output/single_pion/run_db.csv
output/single_pion/run_quality.csv
output/single_pion/run_exclusions.csv
```

Analysis sequence:

1. Check whether every run-list entry has a corresponding ROOT/replay file.
2. Check whether the replay has already removed hadron or pion events.
3. Identify the pion trigger bit, prescale, and raw scaler branch.
4. Reproduce the MARATHON electron normalized yield with the current code to validate the normalization chain.
5. Define the pion event sample: good track, pion trigger, GC anti-electron cut, MIP-like ECAL band, target vertex, and HRS fiducial cuts.
6. Estimate PID efficiency and electron contamination using cut scans and sidebands.
7. Compute pion live time, trigger efficiency, and tracking efficiency.
8. Apply target normalization, dummy/window subtraction, and background subtraction.
9. Produce the first H1 absolute cross section, then extend the same pipeline to D2, H3, and He3.
10. Generate target ratios and systematic-uncertainty tables.
11. Only then perform Wiser/model comparisons and physics interpretation.

## 7. Main Pitfalls

- Do not call the result an electron DIS cross section. The observable is inclusive final-state `pi-` production.
- Do not directly apply electron DIS radiative corrections.
- Do not claim that the data validate a fragmentation picture before estimating non-prompt pion sources and electron leakage.
- Do not explain all high-momentum pions with leading-twist fragmentation alone.
- Without a coincidence electron, event-by-event `Q^2`, `x_B`, or photon virtuality cannot be reconstructed.
- `H3/He3` differences cannot be interpreted directly as flavor separation before nuclear effects, acceptance, PID, FSI, and charge-exchange/feed-down are controlled.
- If the pion spectrum varies rapidly across the HRS acceptance, avoid overly fine binning in the first version and report an acceptance-averaged result.

## 8. Suggested Starting Prompt For A New Codex Session

```text
Please first read docs/STUDENT_HANDOFF.md,
docs/single_pion_physics_goals.md,
docs/single_pion_cross_section_strategy.md,
analysis/Yield.C, analysis/TRI_Beam.h,
analysis/TRI_Target.h, analysis/TRI_LiveTime.C,
and run_lists/*.dat.

The goal is to continue the MARATHON tritium single pi- production
cross-section analysis. First build the run database and replay/data-quality
check plan. Do not modify the physics interpretation before the analysis chain
is reproducible. Separate data-supported results, model interpretations, and
hypotheses that still require validation.
```

If a Feishu page must be updated, use the `lark-doc` or `lark-wiki` workflow and remember that Feishu Markdown handles display equations differently from GitHub Markdown. Complex display equations may need Feishu `<latex>...</latex>` blocks in an upload intermediate file.

## 9. Near-Term Task List

- [ ] Build `output/single_pion/run_db.csv`.
- [ ] Check ROOT-file availability and replay versions for all run-list entries.
- [ ] Identify the electron trigger and pion trigger bit for each run.
- [ ] Read prescale factors and raw scaler branches.
- [ ] Reproduce the electron benchmark normalized yield.
- [ ] Produce GC vs E/p, E/p vs momentum, vertex, and trigger-overlap control plots for every target/kinematic setting.
- [ ] Define the first pion PID cut.
- [ ] Estimate PID efficiency and electron leakage.
- [ ] Compute pion live time and trigger efficiency.
- [ ] Complete the first H1 cross section.
- [ ] Extend the same pipeline to D2, H3, and He3.
- [ ] Generate target ratios and Wiser/model comparison plots.
- [ ] Write the systematic-uncertainty table and final physics-interpretation note.

## 10. Core Conclusions To Preserve

The most valuable conclusion is not simply that “Wiser is wrong.” The useful statements are:

1. Wiser/model baselines describe the approximate scale but not both the `P_T` and `x_bj` shapes.
2. The data show a harder `P_T` spectrum than Wiser, suggesting mechanisms beyond a simple soft/VMD baseline.
3. The high-`x_bj` model failure is the region with the most physics content and the greatest need for systematic control.
4. A=3 mirror nuclei provide a rare `H3/He3` pion-production benchmark and should be organized as a distinctive MARATHON contribution.
5. The final paper or report should frame the result as a JLab fixed-target single-pion production mechanism benchmark, not as a simple FF calibration or electron DIS byproduct.
