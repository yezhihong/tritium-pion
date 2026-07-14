# MARATHON Inclusive Single Negative Pion Cross-Section Analysis Strategy

## 1. Physics Goal

The goal of this analysis is to extract inclusive single negative pion production cross sections from the MARATHON 11 GeV electron-beam data:

$$
e + A \rightarrow \pi^- + X .
$$

The targets represented in the local `run_lists/` directory are `H1`, `D2`, `H3`, and `He3`. The helium target is explicitly Helium-3, and the final-state hadron is explicitly restricted to $\pi^-$.

The core idea is straightforward. MARATHON has already completed and published an inclusive electron DIS cross-section analysis. For the pion analysis, we should reuse the parts that do not depend on the final-state particle: beam charge, target density, boiling correction, live time framework, HRS acceptance, run-quality logic, and normalization conventions. The part that must change is the final-state particle selection: electron trigger/PID must be replaced by $\pi^-$ trigger/PID, and pion-specific efficiency and background corrections must be added.

## 2. Inputs Already Checked

Local files:

- `references/papers/MARATHON.pdf`
- `references/papers/MARATHON——SUPPLEMENTALFILEREVISED.pdf`
- `references/papers/MARATHON-EMC.pdf`
- `references/papers/MARATHON-EMC-SupplementalFileFina.pdf`
- `references/thesis/*.pdf`
- `analysis/Yield.C`
- `analysis/TRI_Beam.h`
- `analysis/TRI_Target.h`
- `analysis/TRI_LiveTime.C`
- `analysis/TRI_Tools.h`
- `analysis/wiser_all_sig.f`
- `run_lists/*.dat`

Feishu knowledge-base material:

- `Single Pion Production in A=3`
- `MARATHON Inclusive Pion`

The Feishu notes list the following key tasks: check whether all data have been replayed; verify whether replayed ROOT files already contain PID or trigger cuts; use the target-density normalization from the two MARATHON PRL analyses; select pions from S1/S2-trigger samples using GC and ECAL information; estimate PID-cut efficiency and electron contamination; estimate pion tracking and pion trigger efficiency; reuse electron-analysis efficiency and acceptance corrections only when they are genuinely final-state independent; and treat radiative effects as a separate pion-production systematic rather than as a direct copy of the electron DIS correction.

## 3. Analysis Principles

The published MARATHON electron DIS analysis measured:

$$
e + A \rightarrow e' + X .
$$

This analysis measures:

$$
e + A \rightarrow \pi^- + X .
$$

Therefore, the result must not be called an electron DIS cross section, and the physics interpretation of electron DIS radiative corrections must not be directly transferred to pion production. The goal is to use the same MARATHON beam, HRS, and target-normalization infrastructure to extract an inclusive final-state $\pi^-$ production cross section.

The following components should remain unchanged where possible:

1. beam charge normalization;
2. target areal density and boiling correction;
3. run selection and data-quality logic;
4. HRS optics, vertex, and fiducial acceptance;
5. prescale/live-time calculation framework;
6. cross-section normalization structure.

The following components must be replaced or newly added:

1. use the $\pi^-$ trigger bit rather than the electron trigger;
2. use $\pi^-$ PID rather than GC-high and E/p-high electron PID;
3. estimate $\pi^-$ PID efficiency;
4. estimate electron leakage into the $\pi^-$ sample;
5. estimate $\pi^-$ trigger efficiency, tracking efficiency, and possible hadron survival/absorption effects;
6. bound or correct kaon/proton contamination;
7. estimate radiative and energy-loss effects independently rather than copying the electron DIS correction.

## 4. Cross-Section Definition And Normalization

For each target, kinematic setting, and HRS arm, extract:

$$
\frac{d^2\sigma_{\pi^-}}{dp_{\pi} \, d\Omega_{\pi}}
=
\frac{N_{\pi^-}^{\mathrm{corr}}}
{N_e \, N_{\mathrm{tgt}} \, \Delta p \, \Delta \Omega}.
$$

Here $N_e$ is the number of incident electrons, $N_{\mathrm{tgt}}$ is the target areal density in nuclei per unit area, and $\Delta p \Delta\Omega$ is the momentum-solid-angle phase space covered by the HRS bin or fiducial region.

The corrected $\pi^-$ yield can be written as:

$$
N_{\pi^-}^{\mathrm{corr}}
=
\frac{
N_{\pi^-}^{\mathrm{raw}}
- N_{e \rightarrow \pi^-}
- N_{\mathrm{other\;hadron}}
- N_{\mathrm{target\;window}}
}
{
LT_{\pi^-}
\epsilon_{\mathrm{track}}
\epsilon_{\mathrm{trig},\pi^-}
\epsilon_{\mathrm{PID},\pi^-}
\epsilon_{\mathrm{survival}}
}.
$$

For code implementation, the more compact form is:

$$
N_{\pi^-}^{\mathrm{corr}}
=
\frac{N_{\pi^-}^{\mathrm{raw}} - N_{\mathrm{bkg}}}
{LT_{\pi^-}
\cdot \epsilon_{\mathrm{track}}
\cdot \epsilon_{\mathrm{trig},\pi^-}
\cdot \epsilon_{\mathrm{PID},\pi^-}
\cdot \epsilon_{\mathrm{survival}}}.
$$

The local `analysis/Yield.C` file already contains an electron normalized-yield prototype:

```text
XS = Good_Ele / Ne / Ntg / phase_space * CM2ToNB
```

For the $\pi^-$ analysis, this becomes:

```text
XS_pi_minus = N_pi_minus_corr / Ne / Ntg / phase_space * CM2ToNB
```

The phase space can initially be approximated geometrically from the HRS fiducial cuts:

$$
\Delta p \Delta\Omega
\simeq
(p_0 \Delta\delta) \, \Delta\theta \, \Delta\phi .
$$

If the $\pi^-$ cross section varies rapidly across the HRS acceptance, the first version should report a fiducial acceptance-averaged cross section. Point-by-point comparison with theory requires a Monte Carlo acceptance and bin-centering correction.

Code note: the current `Yield.C` uncertainty propagation appears to divide one `Ne->Sys_Err` term by `Ntg->Value`. This should be checked; physically, that term likely should be divided by `Ne->Value`.

## 5. Analysis Steps

### Step 0: Build The Run Database

For each run, construct a traceable table containing:

- run number;
- target: `H1`, `D2`, `H3`, `He3`;
- kinematic setting: `Kin1`, `Kin2`, `Kin3`, `Kin5`, `Kin7`;
- HRS arm;
- central momentum and angle;
- magnet polarity;
- beam charge;
- prescale factors;
- electron trigger bit;
- $\pi^-$ trigger bit;
- replay version;
- ROOT file path;
- good/bad run flag;
- exclusion reason.

No formal physics cross-section extraction should start before this run database exists.

Recommended outputs:

```text
output/single_pion/tables/run_db.csv
output/single_pion/tables/run_quality.csv
output/single_pion/tables/run_exclusions.csv
```

### Step 1: Check Replay And Run Quality

For every run in `run_lists/*.dat`, check:

1. whether the ROOT file exists;
2. whether the replayed ROOT file already applied PID or trigger cuts;
3. whether the scaler tree is complete;
4. whether the raw scaler branch corresponding to the $\pi^-$ trigger exists;
5. whether prescale factors are read correctly run by run;
6. whether beam current, BCM calibration, and charge cuts are stable;
7. whether target state, raster, vertex distribution, and boiling correction are normal.

It is especially important to verify that the replay files retain sufficiently raw detector variables. If the replay stage kept only an electron sample, the pion analysis would be structurally biased.

### Step 2: Reproduce The Electron Benchmark

Before extracting $\pi^-$ yields, reproduce the MARATHON electron normalized yield or cross-section normalization loop with the current code. The purpose is not to republish electron DIS, but to validate:

- beam charge normalization;
- target areal density;
- boiling correction;
- live time and prescale;
- HRS fiducial/acceptance cuts;
- run grouping;
- phase-space convention.

The electron cuts in local `Yield.C` include:

```text
single track
electron trigger
GC above threshold
ECAL E/p above threshold
vertex cut
tg_th, tg_ph, tg_dp acceptance cuts
```

Only after the electron benchmark closes should the additional pion-analysis uncertainties be attributed mainly to PID, trigger, and contamination rather than to the normalization chain itself.

Recommended outputs:

```text
output/single_pion/validation/electron_yield_reproduction.csv
output/single_pion/validation/electron_cross_section_comparison.pdf
```

### Step 3: Define The $\pi^-$ Event Sample

For each target and kinematic setting, a $\pi^-$ candidate event should contain:

- the correct S1/S2 hadron or pion trigger bit;
- exactly one good HRS track, unless multi-track events are explicitly handled later;
- the same HRS optics and fiducial cuts as the electron benchmark;
- a target-cell vertex cut excluding window regions;
- a GC anti-electron cut;
- a MIP-like or low-E/p pion band in ECAL;
- aerogel, TOF, or other PID variables in control plots and cut scans if available in the replay.

Do not fix the cut immediately. First make control plots:

```text
GC amplitude vs E/p
GC amplitude vs momentum
E/p vs momentum
beta or TOF proxy vs momentum
vertex distribution by PID region
trigger-bit overlap matrix
```

An initial $\pi^-$ cut can be written as:

```text
pi_minus_candidate =
    good_track
 && pi_minus_trigger
 && GC below electron threshold
 && E/p in MIP-like hadron band
 && electron PID sideband veto
 && target vertex cut
 && HRS fiducial cuts
```

GC and E/p thresholds must be scanned by kinematic setting, arm, and rate condition. They should not be copied directly from the electron cuts.

### Step 4: Estimate PID Efficiency And Electron Contamination

Build a data-driven PID response matrix:

```text
true particle species -> probability of being selected as pi-
```

At minimum, provide:

- $\epsilon_{\mathrm{PID},\pi^-}$;
- electron leakage: $N_{e \rightarrow \pi^-}$;
- kaon/proton contamination estimates or upper bounds;
- systematic uncertainties from cut variation.

Useful control samples include:

- GC-high and E/p-high clean electron regions;
- GC-low and MIP-like pion-enriched regions;
- electron-trigger and pion-trigger overlap samples;
- GC/E/p sideband extrapolations;
- H1 Wiser-parameterization checks as sanity tests only, not as the main correction source.

Recommended outputs:

```text
output/single_pion/pid/pid_cut_scan_<target>_<kin>.pdf
output/single_pion/pid/pion_pid_efficiency.csv
output/single_pion/pid/electron_contamination.csv
```

### Step 5: Compute $\pi^-$ Live Time And Trigger Efficiency

If $\pi^-$ uses a trigger different from the electron trigger, electron live time cannot be reused directly.

For each run:

1. read prescale factors;
2. identify the $\pi^-$ trigger number;
3. use the corresponding raw scaler branch, such as `LeftT_N_` or `RightT_N_`;
4. compute DAQ live time from accepted trigger counts and raw scaler counts;
5. estimate trigger efficiency using redundant scintillator triggers or trigger-overlap samples;
6. assign a conservative systematic uncertainty if the efficiency cannot be measured cleanly.

Recommended outputs:

```text
output/single_pion/trigger/pion_trigger_livetime.csv
output/single_pion/trigger/pion_trigger_efficiency.csv
```

### Step 6: Tracking, Acceptance, And Bin-Centering

The HRS optics and acceptance framework can follow the MARATHON electron analysis, but $\pi^-$ tracks require separate checks:

- single-track efficiency;
- tracking efficiency versus rate, target, and momentum;
- optics reconstruction quality;
- vertex and angular acceptance stability;
- bin migration in $p_{\pi}$, $\theta_{\pi}$, $\phi_{\pi}$, and $\delta$.

Use a conservative fiducial region in the first stage:

```text
|tg_th| < established limit
|tg_ph| < established limit
|tg_dp| < established limit
vertex inside target cell
```

The first result can report a fiducial acceptance-averaged cross section. More differential bin-centering or model-dependent corrections should wait until the normalization and PID closure tests are stable.

### Step 7: Target Normalization

The target normalization follows the MARATHON PRL and supplemental analyses:

$$
N_{\mathrm{tgt}}
=
\frac{\rho L N_A}{A}.
$$

The local `gGet_TargetInfo()` currently includes:

```text
H1, D2, H3, He3 target areal densities
```

Before final use, these values must be checked against the target densities, target lengths, and boiling corrections in the PRL supplemental material.

### Step 8: Background Subtraction

Estimate the following backgrounds:

1. electron contamination after $\pi^-$ PID;
2. target-cell wall or dummy/empty-target contributions;
3. accidental or noise-trigger contributions;
4. kaon/proton contamination;
5. pile-up or rate-dependent effects associated with trigger overlap.

For every item, state explicitly whether it is:

```text
subtracted
bounded
assigned as systematic
ignored with justification
```

### Step 9: Radiative And Energy-Loss Effects

Because $\pi^-$ is a final-state hadron, the electron DIS radiative correction cannot be applied directly. However, incident-electron radiation can still change the effective beam energy and the pion production spectrum.

Recommended priority:

1. first complete detector, trigger, PID, target, and acceptance corrections;
2. use a Wiser-like model or the H1 data shape to estimate sensitivity to incident-energy variation;
3. treat this as a systematic uncertainty in the first version rather than as a full radiative correction;
4. do not describe it as a direct reuse of the MARATHON DIS radiative correction.

## 6. Final Products

Main result:

$$
\frac{d^2\sigma_{\pi^-}}{dp_{\pi} d\Omega_{\pi}}
\quad
\text{for}
\quad
H1,\;D2,\;H3,\;He3 .
$$

Recommended ratios:

```text
D2 / H1
H3 / H1
He3 / H1
H3 / He3
```

Physics extensions:

- compare H1 with Wiser or other inclusive pion production parameterizations;
- compare nuclear dependence;
- compare mirror nuclei `H3` and `He3`;
- discuss flavor-sensitive interpretation only after PID, acceptance, and contamination are controlled.

## 7. Code-Structure Recommendation

Split the current single-file prototype into clear modules:

```text
analysis/
  PionYield.C
  TRI_RunDB.h
  TRI_Cuts.h
  TRI_PID.h
  TRI_Corrections.h
  TRI_CrossSection.h
```

Recommended output directory:

```text
output/single_pion/
  run_db.csv
  run_quality.csv
  electron_benchmark.csv
  pion_raw_yields.csv
  pion_corrections.csv
  pion_cross_sections.csv
  pion_systematics.csv
  plots/
```

The final cross-section table should include:

```text
target, kin, arm, run_group,
p0, theta0, p_bin_low, p_bin_high,
N_raw, N_bkg, charge_C, Ne, Ntg,
LT, eps_track, eps_trigger, eps_PID, eps_survival,
phase_space, sigma_nb_per_GeV_sr,
stat_unc, sys_unc, total_unc
```

Because this analysis only treats $\pi^-$, the table does not need `charge` as a core physics degree of freedom. If such a column is retained, it should be fixed to `pi-`.

## 8. First-Stage Checklist

The first-stage goal is not a final publication plot, but a reproducible closed analysis loop:

- [ ] Generate `run_db.csv` from all `run_lists/*.dat`.
- [ ] List ROOT-file availability and missing-file status.
- [ ] Identify the electron trigger and $\pi^-$ trigger bit.
- [ ] Read prescale factors for each run.
- [ ] Reproduce the MARATHON electron normalized yield.
- [ ] Produce $\pi^-$ PID control plots for all targets and kinematic settings.
- [ ] Estimate electron contamination with sideband methods.
- [ ] Compute $\pi^-$ live time and trigger efficiency.
- [ ] Produce the first H1 $\pi^-$ cross section.
- [ ] Use Wiser only as a sanity check.
- [ ] Extend the same pipeline to `D2`, `H3`, and `He3`.

## 9. Main Risks

1. **Trigger ambiguity:** the $\pi^-$ trigger number and prescale must be confirmed from run metadata, not inferred only from S1/S2 labels.
2. **Replay-level cuts:** if ROOT files already removed hadron/pion events during replay, the analysis will be structurally biased.
3. **Electron contamination:** weak GC/ECAL cuts or insufficient sideband constraints can make electron leakage a leading systematic.
4. **Kaon/proton contamination:** high-momentum settings require checks of hadron PID separation.
5. **Acceptance/bin-centering:** the $\pi^-$ spectrum may vary rapidly across the HRS acceptance; acceptance-averaged results are safer for the first version.
6. **Radiative interpretation:** electron DIS radiative corrections cannot be transferred directly to $\pi^-$ production.
7. **Uncertainty propagation:** every correction and uncertainty should appear in a separate column rather than being hidden in one total scale factor.

## 10. Recommended Near-Term Work Order

1. Build the run database and ROOT-file checking script.
2. Audit trigger bits, prescales, and replay cuts.
3. Reproduce the electron benchmark with the current `Yield.C` logic.
4. Replace electron PID with $\pi^-$ PID and generate cut-scan control plots.
5. Compute $\pi^-$ live time, trigger efficiency, and PID efficiency.
6. Complete the H1 $\pi^-$ absolute cross section.
7. Extend the pipeline to D2, H3, and He3.
8. Produce nuclear ratios and then physics interpretation.
