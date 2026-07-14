# Physics Goals And Motivation For MARATHON Single-Pion Production

## Abstract

This note summarizes the physics motivation for extracting the inclusive single negative pion production cross section from MARATHON:

$$
e + A \rightarrow \pi^- + X,\qquad
A = ^1\mathrm{H},\, ^2\mathrm{H},\, ^3\mathrm{H},\, ^3\mathrm{He}.
$$

The motivation is based on Jian-Wei Qiu's reports on inclusive pion and inclusive hadron production, the 2026 Qiu-Watanabe preprint on joint QCD+QED factorization for single-inclusive hadron and jet production in lepton-hadron scattering, the earlier work by Andrei Afanasev, Carl Carlson, Christian Wahlquist, and collaborators on hard pion photo/electroproduction, and the published MARATHON A=3 electron DIS results.

The central point is that this analysis should not be framed only as a byproduct of the MARATHON electron DIS program, and it should not be framed only as a pion fragmentation-function calibration. Qiu and Watanabe have provided the first joint QCD+QED collinear-factorization calculation for high-transverse-momentum single-hadron production when the scattered lepton is not tagged. Their framework combines lepton-initiated scattering, real-photon-initiated perturbative photoproduction, lepton distribution functions (LDFs), PDFs, FFs, and infrared-safe hard parts in a single leading-power baseline.

The MARATHON $\pi^-$ data match the experimental definition of this observable, but the preliminary pion kinematics cover roughly $P_T \simeq 0.9$--$1.8\ \mathrm{GeV}$, which is near the lower edge of the region where leading-power factorization is expected to be reliable. The most defensible goal is therefore to use absolute cross sections and target ratios to test where the joint QCD+QED leading-power baseline works in the low-energy, large-$z$, light-nucleus JLab regime, and to quantify residual contributions from soft/VMD production, vector-meson decay, direct or higher-twist pion production, nuclear final-state effects, and other power corrections.

It is essential to distinguish two meanings of photoproduction. In the Qiu-Watanabe paper, photoproduction refers to real-photon-initiated perturbative partonic channels and is part of the leading-power factorized baseline. Soft/VMD production refers to nonperturbative photon-hadron dynamics. These should not be merged into a single mechanism.

## 1. Main Thread From The Qiu Reports And The Qiu-Watanabe Preprint

The Qiu reports and the Qiu-Watanabe preprint establish a consistent chain from the physics question to a calculable baseline:

1. Any cross section with an identified final-state hadron contains nonperturbative hadronization information and cannot be computed from perturbative QCD alone.
2. Many SIDIS/TMD interpretations assume that the observed leading hadron mainly comes from struck-parton fragmentation. At fixed-target JLab kinematics, this assumption is not automatic.
3. For inclusive single-hadron production without a tagged scattered lepton,

$$
\ell + N/A \rightarrow h + X,
$$

the observed hadron transverse momentum $P_T$ provides the explicit hard scale. If $P_T$ is sufficiently large, the cross section can be written as a convolution of LDFs, PDFs, FFs, and infrared-safe hard parts. This organization includes lepton-side QED radiation, ordinary leptoproduction, and perturbative photoproduction in one framework.

At leading power, the structure is schematically:

$$
E_H\frac{d\sigma^{eA\rightarrow H+X}}{d^3P_H}
=
\sum_{i,b,c}
f_{i/e}\otimes f_{b/A}\otimes
\widehat{H}_{ib\rightarrow c+X}\otimes D_{c\rightarrow H}
+\mathcal{O}\!\left(\frac{1}{P_T^n}\right).
$$

Here $f_{i/e}$ is the distribution of a lepton, photon, quark, or gluon inside the electron; $f_{b/A}$ is the target PDF; and $D_{c\rightarrow H}$ is the fragmentation function for producing the observed hadron. For MARATHON, this equation should be treated as a testable modern baseline, not as proof that factorization must already dominate the data.

In Qiu's language, single-inclusive hadron production is a prerequisite for a controlled SIDIS factorization analysis. The Qiu-Watanabe work turns this statement into a calculable joint QCD+QED framework. The first questions are not angular modulations or spin asymmetries, but whether current FFs and leading-power hard parts describe the cross section, how large collision-induced QED radiation effects are, and whether remaining deviations require low-$P_T$ power corrections, soft/VMD production, vector-meson decays, direct pions, or nuclear final-state effects.

## 2. The Afanasev-Carlson Context

Afanasev, Carlson, Wahlquist, and collaborators studied high-transverse-momentum meson photo/electroproduction beginning in the late 1990s. Their starting point is directly relevant here: a final-state pion is not automatically a clean partonic observable. It can be a superposition of several mechanisms, and the dominant mechanism must be identified before the pion data can be used to infer PDFs, FFs, GPDs, or spin/TMD structure.

### 2.1 More Than One Mechanism

The earlier work separates hard pion production into at least three categories:

1. **Leading-twist fragmentation:** a photon or virtual photon scatters from a parton, and the outgoing parton produces the pion through a fragmentation function. This is the default mechanism in modern NLO $\ell N\to hX$ calculations and in many SIDIS interpretations.
2. **Soft/VMD contribution:** the incoming photon fluctuates into vector mesons such as $\rho$, $\omega$, or $\phi$, followed by soft hadronic pion production. Afanasev et al. estimated this component with vector-meson dominance and semi-inclusive hadronic cross-section parameterizations, and found that it may remain sizable near $p_T\sim2\ \mathrm{GeV}$ at fixed-target energies.
3. **Direct or higher-twist isolated pion production:** the pion is produced directly in a short-distance subprocess rather than as a jet-fragmentation product. This contribution is power suppressed asymptotically, but at moderate energies, large $z$, or kinematically isolated pion configurations it can exceed ordinary fragmentation because it is not penalized by the same rapid FF falloff as $z\to1$.

These mechanisms imply different physics. If fragmentation dominates, the data can enter FF/SIDIS global analyses. If soft/VMD dominates, the data mainly benchmark photon-hadron soft dynamics and non-prompt pion sources. If direct higher-twist pion production is important, the data connect to high-$x$ parton distributions, pion distribution amplitudes, semi-exclusive duality, and perturbative kernels related to exclusive/GPD observables.

### 2.2 Why Medium Energies Are Interesting

In *Hard Pion Electroproduction at Medium Energies*, Afanasev and Carlson emphasized that a perturbatively calculable hard-pion region may exist at medium-energy facilities, but it need not be dominated by leading-twist fragmentation. It may instead be dominated by higher-twist direct pion production.

This is important for MARATHON. A simple “prompt fragmentation versus non-prompt pion” dichotomy would miss a calculable contribution that is not a leading-twist FF contribution. MARATHON $\pi^-$ production can therefore test more than FFs; it may probe direct-pion mechanisms, semi-exclusive duality, and high-$x$ partonic dynamics in the JLab energy range.

### 2.3 Virtuality And Soft Suppression

Afanasev-Carlson also noted that soft VMD contributions are suppressed as photon virtuality increases, through factors similar to $m_\rho^2/(m_\rho^2+Q^2)$. Direct and fragmentation contributions also vary with $Q^2$, but not necessarily with the same strong VMD propagator suppression.

For MARATHON, this provides a useful but limited handle. Without a coincidence electron, one cannot reconstruct photon virtuality or missing mass event by event. The first analysis should compare spectra primarily as functions of pion $P_T$, laboratory momentum, angle, and target. The Qiu-Watanabe framework does not require artificially isolating a low-$Q^2$ photoproduction sample; it includes lepton-initiated and real-photon-initiated perturbative channels in the same inclusive cross section. Soft/VMD and direct/higher-twist components should be treated as candidate residuals beyond the leading-power baseline.

### 2.4 The Experimental Gap

The 2003 Afanasev-Carlson work explicitly noted the lack of analyzed data suitable for comparison. Later NLO $\ell N\to hX$ calculations, QCD+QED factorization, and the Qiu reports moved the theory into a modern factorization language, but systematic fixed-target benchmarks for absolute $\pi^-$ production on light nuclei remain limited.

MARATHON can fill part of this gap by using the same high-resolution HRS setup and the same $^1$H/$^2$H/$^3$H/$^3$He target system to provide a fixed-target single-pion benchmark.

## 3. Why The Single-Pion Cross Section Is The Key Observable

### 3.1 Testing The Fragmentation Picture At JLab

The NLO calculations of Hinderer, Schlegel, and Vogelsang show that when the scattered lepton is not measured, the transverse momentum of the observed hadron sets the hard scale. NLO corrections can be large, and quasi-real photon contributions can be important. Qiu-Watanabe reorganize these contributions into a joint QCD+QED leading-power result:

- lepton-initiated subprocesses such as $e q\rightarrow e q$ and their QCD corrections;
- real-photon-initiated perturbative photoproduction, such as $\gamma q\rightarrow qg$;
- process-independent leading-power QED radiation encoded in LDFs;
- target PDFs and final-state FFs.

The advantage of this framework is that it avoids imposing an extra scattered-electron cut to artificially separate direct and resolved photon contributions. However, it is reliable only when $P_T$ is large enough for power corrections to be controlled.

This is exactly the MARATHON issue. The preliminary pion data cover $P_T\simeq0.9$--$1.8\ \mathrm{GeV}$, close to the lowest scale where QCD factorization can be used. Qiu-Watanabe freeze the evolution scale at $m_c$ when $P_T<m_c$ and write the non-leading-power terms as $\mathcal{O}(1/P_T^n)$. MARATHON is therefore not a clean high-$P_T$ sample in which fragmentation dominance can be assumed. It is a boundary dataset testing the transition of the leading-power description toward low $P_T$.

If the joint QCD+QED NLO baseline fails, possible causes include:

- insufficient constraints on large-$z$ pion FFs;
- $p_T$ or invariant mass too low for leading-power factorization;
- non-prompt pion sources from $\rho$, $\omega$, or other vector-meson decays;
- incomplete treatment of default LDFs or lepton-side QED radiation;
- incorrect balance between perturbative photoproduction and leptoproduction channels;
- nuclear dependence or final-state interactions in light nuclei.

The absolute cross section is therefore a physics result in its own right, not merely a technical calibration for later SIDIS work.

### 3.2 Providing A Controlled Input To SIDIS/TMD Studies

SIDIS usually studies:

$$
e + N \rightarrow e' + h + X
$$

to extract TMDs, FFs, and angular modulations. TMD factorization requires a hard scale $Q$ and a final-state hadron transverse momentum small relative to $Q$. It also typically assumes that the observed hadron is the leading hadron from a fragmenting parton.

Qiu's reports emphasize that this assumption is “unlikely to be satisfied” automatically at JLab kinematics. Inclusive single-pion production provides a simpler prerequisite test:

- Can current pion FFs describe the JLab 12 GeV regime?
- How large is the required non-prompt pion subtraction?
- Do radiative corrections or QED factorization effects alter the cross-section interpretation?
- What theory systematics should be assigned when pion data are used in SIDIS angular-modulation analyses?

### 3.3 Large-$z$ Pion Fragmentation Functions

Qiu-Watanabe show that single-inclusive high-$P_T$ hadron production is especially sensitive to large-$z$ FFs. In the convolution, PDFs usually fall more steeply as $x\to1$ than FFs do with $z$, biasing the result toward lower $x$ and higher $z$. At fixed collision energy, this large-$z$ dominance strengthens as $P_T$ increases. They also show that JAM20 and MAP1.0 pion FF central sets can produce significantly different $P_T$ spectra, with FF-set uncertainty exceeding ordinary factorization/renormalization scale variation in some regions.

Forward high-momentum pions at JLab can therefore provide complementary constraints on large-$z$ pion FFs, especially for $\pi^-$ favored and unfavored fragmentation. However, MARATHON's low-$P_T$ region enhances both large-$z$ sensitivity and power corrections, so these effects must not be interpreted as a pure FF uncertainty.

The first-stage goal should not be a direct FF extraction. A more defensible goal is to publish absolute cross sections and covariance information in a form useful for future FF global analyses.

### 3.4 Leading-Power QED Radiation And LDFs

Qiu-Watanabe separate collision-induced QED effects into: universal leading-power contributions absorbed into LDFs, PDFs, and FFs; process-dependent but perturbatively calculable hard-coefficient contributions; and potentially non-factorizable power-suppressed terms. Their numerical results show that LDF evolution reduces the probability of finding the parent electron near $\xi\to1$ and increases the lower-$\xi$ electron/photon content, reshaping the single-hadron $P_T$ spectrum. Depending on energy and phase space, the effect can reach roughly $50\%$ or more.

This elevates radiative effects from a low-priority correction to a core theory issue for MARATHON pion production. Two limitations must be kept explicit: the current paper uses default/model LDFs at $\mu_0=m_c$, not final data-extracted universal LDFs; and published data that have already received traditional radiative corrections cannot be used directly for LDF extraction unless those corrections are removed or consistently accounted for. MARATHON must therefore document whether and how pion data products have received radiative treatment, and compare detector-level, Born-like, and factorized-theory observables only when the definitions match.

## 4. The Unique Value Of MARATHON Data

The published MARATHON electron DIS results demonstrate the experiment's ability to control normalization, cryogenic targets, and HRS analysis for A=3 mirror nuclei. The $F_2^n/F_2^p$ measurement used $^3$H/$^3$He mirror symmetry to reduce theory uncertainties over $0.19<x<0.83$. The A=3 EMC measurement covered $0.20<x<0.83$ and $Q^2=2.7$ to $11.9\ \mathrm{GeV}^2$, providing the first tritium EMC-effect measurement.

For single-pion production, the unique features are:

- simultaneous $^1$H, $^2$H, $^3$H, and $^3$He targets under the same experimental conditions;
- high-resolution HRS momentum and angular measurements suitable for absolute cross sections;
- an existing beam charge, target density, boiling correction, live time, acceptance, and run-quality normalization framework;
- an A=3 mirror-nucleus pair sensitive to the combined effects of isospin, initial-state nuclear modification, and final-state interactions;
- $^1$H and $^2$H baselines for separating nucleon-level mechanisms from A=3 nuclear modifications.

The goal is not a single-target cross-section point, but a coherent A=1,2,3 set of cross sections and ratios.

## 5. Recommended Physics Goals

### Goal 1: Extract Absolute Inclusive $\pi^-$ Cross Sections

The basic result should be:

$$
\frac{d^2\sigma_{\pi^-}}{dp_{\pi}\,d\Omega_{\pi}}
=
\frac{N_{\pi^-}^{\mathrm{corr}}}
{N_e\,N_{\mathrm{tgt}}\,\Delta p\,\Delta\Omega}.
$$

Report this for $^1$H, $^2$H, $^3$H, and $^3$He at the MARATHON kinematic settings. The first stage should report fiducial acceptance-averaged cross sections. Finer binning should wait until Monte Carlo acceptance and bin-centering corrections are stable.

### Goal 2: Build Target Ratios

Key ratios include:

$$
R_{D/H} =
\frac{\sigma_{\pi^-}(^2\mathrm{H})}{\sigma_{\pi^-}(^1\mathrm{H})},
\qquad
R_{t/h} =
\frac{\sigma_{\pi^-}(^3\mathrm{H})}{\sigma_{\pi^-}(^3\mathrm{He})}.
$$

Also useful are:

$$
\frac{\sigma_{\pi^-}(^3\mathrm{H})}{\sigma_{\pi^-}(^2\mathrm{H})},
\qquad
\frac{\sigma_{\pi^-}(^3\mathrm{He})}{\sigma_{\pi^-}(^2\mathrm{H})}.
$$

These ratios cancel common uncertainties in beam charge, parts of acceptance, and detector efficiencies, making them better suited for nuclear/isospin studies. Qiu-Watanabe note that leading-power nuclear effects can be modeled by replacing free-nucleon PDFs with nPDFs when $P_T$ is large enough, but power corrections may be nuclear enhanced and final-state effects may be additional. Their nuclear plots mostly address EIC energies and $^4$He or heavier nuclei, so they are not direct predictions for MARATHON $^3$H/$^3$He. The A=3 ratio should first be treated as a mirror-nucleus pion-production benchmark, not as a direct nPDF or flavor-separation measurement.

### Goal 3: Test The Leading-Power Baseline And Diagnose Residual Mechanisms

For $^1$H and $^2$H, first establish the nucleon-level baseline before attributing discrepancies to nuclear effects. Comparisons should be layered:

- **leading-power baseline:** NLO $\ell N\to hX$ in joint QCD+QED factorization, including lepton-initiated and real-photon-initiated perturbative channels, LDFs, PDFs, and FFs;
- **empirical soft baseline:** Wiser-like parameterizations;
- **nonperturbative photon source:** soft/VMD production and vector-meson decay;
- **power-suppressed candidate:** direct/higher-twist isolated pion production and other low-$P_T$ corrections;
- **nuclear contribution:** nPDF-like initial-state modification, pion absorption, FSI, charge exchange, and feed-down.

The comparison must state clearly that:

- the process is not ordinary inclusive electron DIS;
- if the scattered electron is not part of the event definition, the hard scale cannot simply be described by DIS $Q^2$;
- perturbative photoproduction is not the same as soft/VMD photoproduction;
- QED radiation, FF choice, factorization scale, and $1/P_T^n$ corrections all affect the interpretation;
- data-theory differences are not automatically nuclear effects and must first be checked on hydrogen and deuterium.

### Goal 4: Quantify Non-Prompt Pions And Soft/VMD Backgrounds

Qiu's earlier reports emphasize that JLab kinematics may contain non-prompt pions from vector-meson sources such as $\rho$ decay. The Qiu-Watanabe preprint does not explicitly separate prompt and vector-meson-decay pions, and the inclusive FF-based formula does not by itself provide an experimental prompt/non-prompt decomposition. This component must therefore be constrained using generators, identified vector-meson data, model studies, or data-driven bounds.

Single-pion production should treat non-prompt sources as a physics question, not merely as detector background. A practical decomposition is:

- prompt fragmentation component;
- vector-meson decay component;
- target-window, accidental, and PID contamination;
- nuclear-dependent residual contribution.

### Goal 5: Provide A Test Of QCD+QED Factorization And Radiative Effects

The QCD+QED factorization work of Liu, Melnitchouk, Qiu, and Sato shows that radiation effects complicate simple photon-nucleon frame definitions in SIDIS. Qiu-Watanabe then provide the first joint QCD+QED numerical calculation for single-inclusive high-$P_T$ hadron production and find that LDF-induced leading-power QED radiation can significantly reshape the $P_T$ spectrum.

MARATHON pion production can test:

- whether traditional radiative corrections are adequate when a final-state hadron is required;
- whether default LDFs and future extracted universal LDFs can describe the data consistently;
- whether factorized lepton distribution functions are required;
- how sensitive the cross section is to incident-energy smearing and photon-radiation phase space.

Radiative effects should no longer be treated as a low-priority correction. The first-stage analysis should preserve pion-yield definitions that are not mixed with traditional electron-DIS RC assumptions, record all radiative treatments already applied, and compare no-QED-evolution, default-LDF, and traditional-RC approximations as model systematics. LDF extraction can only be discussed after the experimental observable and theory definition are made consistent.

## 6. Relation To Existing Work

### MARATHON Electron DIS Provides The Normalization Foundation

The MARATHON $F_2^n/F_2^p$ PRL result demonstrates the value of the $^3$H/$^3$He mirror-nucleus method and provides a reliable foundation for cryogenic tritium targets, HRS analysis, beam charge, and target-density normalization. The A=3 EMC PRL further demonstrates the sensitivity of the same dataset to light-nucleus EMC effects.

The pion analysis should reuse final-state-independent normalization elements, but it must rebuild $\pi^-$ trigger, PID, tracking, pion survival, electron leakage, and hadron-contamination corrections. Electron DIS radiative corrections and electron PID cannot be transplanted directly.

### NLO Single-Hadron Production Provides A Comparison Framework

Hinderer, Schlegel, and Vogelsang provide NLO calculations for $\ell N\to hX$ and $\ell N\to \mathrm{jet}X$. They show that when the scattered lepton is unmeasured, the observed hadron or jet transverse momentum is the hard scale, and NLO corrections can be sizable. This framework is the natural starting point for hydrogen and deuterium baseline comparisons.

### Afanasev-Carlson Provides A Mechanism Framework

The 1997-2003 Afanasev-Carlson-Wahlquist work identified several issues central to fixed-target hard pion production: soft contributions can remain significant near $p_T\sim2\ \mathrm{GeV}$; polarization or flavor-sensitive observables can be diluted by soft processes; and at JLab medium energies the calculable region may be dominated by direct/higher-twist isolated pion production rather than leading-twist fragmentation. MARATHON can turn these mechanism estimates into absolute cross-section tests.

### QCD+QED Factorization Provides A Radiative Interpretation

The QCD+QED factorization work of Liu, Melnitchouk, Qiu, and Sato places QED and QCD radiation in a common framework and shows that simple SIDIS photon-nucleon frame definitions become ambiguous when radiation is present. The Qiu-Watanabe 2026 preprint extends this program to single-inclusive hadron and jet production, unifying leptoproduction and perturbative photoproduction and quantifying LDF-induced QED effects, FF-set uncertainties, and leading-power nuclear dependence.

This work provides a modern theoretical baseline for MARATHON, but not a ready-made curve. Its JLab numerical example is mainly $p(e,\pi^+)X$ at $\sqrt{S}=4.84\ \mathrm{GeV}$ and $y=0$. MARATHON requires calculations for $\pi^-$, the actual beam energy, HRS angle and acceptance, and $^1$H/$^2$H/$^3$H/$^3$He. The current LDFs are default/model sets. The authors state that the numerical code is maintained in a private GitHub repository and may be obtained by reasonable academic request, so quantitative comparison requires either collaboration with the authors or an independent implementation.

## 7. Research Significance

### Hadron Structure

This measurement addresses a hidden assumption in many SIDIS/TMD analyses: whether the observed pion can be treated as the leading hadron from a fragmenting parton. If that assumption fails at JLab kinematics, the interpretation of SIDIS angular modulations needs a revised systematic uncertainty. If direct/higher-twist isolated pion production is important, the observable also connects to semi-exclusive processes and exclusive/GPD hard kernels.

### Fragmentation Functions

Absolute high-momentum $\pi^-$ cross sections and target ratios can provide complementary constraints on large-$z$ pion FFs. With $^1$H, $^2$H, $^3$H, and $^3$He, the data can test flavor/isospin and nuclear scenarios. In the MARATHON low-$P_T$ region, however, FF sensitivity must be evaluated simultaneously with higher-twist effects, soft sources, and final-state nuclear effects.

### Direct Pions And Higher-Twist Dynamics

If the high-momentum $\pi^-$ data are not described by leading-twist fragmentation but are more consistent with direct-pion or semi-exclusive estimates, the result would make the Afanasev-Carlson medium-energy mechanism picture experimentally testable. It would also affect how pion observables are used to extract high-$x$ PDFs, pion distribution amplitudes, or GPD-related information at JLab.

### Light-Nucleus QCD

The A=3 mirror nuclei provide a rare opportunity to compare pion production in $^3$H and $^3$He under the same conditions. A deviation of the $^3$H/$^3$He pion ratio from simple nucleon-counting or isospin expectations may indicate nuclear dependence, final-state interactions, or flavor-dependent fragmentation, but only after the nucleon-level baseline and analysis systematics are controlled.

### Future JLab And EIC Analyses

Qiu-Watanabe find that QED radiation, large-$z$ fragmentation uncertainty, and nuclear dependence can all produce significant shape changes in single-hadron observables at EIC and JLab energies. MARATHON pion cross sections can become a fixed-target benchmark dataset for deciding which theory systematics and power corrections must enter future SIDIS/TMD global analyses.

## 8. Potential MARATHON Contributions

### Contribution 1: Absolute Fixed-Target $\pi^-$ Benchmarks

The earlier Afanasev-Carlson literature and the Qiu reports both point to a lack of systematic single-pion benchmarks in the JLab fixed-target regime. MARATHON can provide absolute $\pi^-$ cross sections for $^1$H, $^2$H, $^3$H, and $^3$He with one spectrometer, one beam, and one target system. This is more valuable than isolated yields because it constrains normalization, mechanism shape, and nuclear dependence at the same time.

### Contribution 2: A Baseline-Residual Mechanism Map

The result should be organized as a baseline-residual map rather than only as a cross-section table. Start from the joint QCD+QED leading-power baseline with FF, scale, and LDF uncertainties; add Wiser-like, soft/VMD, vector-meson decay, and direct/higher-twist sensitivity bands; then show the data residuals relative to each baseline. Labels such as “fragmentation dominated,” “soft dominated,” or “direct-pion candidate” should be used only if one mechanism remains dominant within uncertainties.

### Contribution 3: A=3 Mirror-Nucleus Pion Production

The $^3$H/$^3$He pair is a distinctive MARATHON asset. For $\pi^-$, the ratio contains not only isospin information but also sensitivity to nuclear absorption, final-state interactions, charge-exchange feed-down, and target-remnant fragmentation. Once $^1$H and $^2$H establish the mechanism baseline, the A=3 ratio can become a benchmark for light-nucleus hadronization and nuclear dependence.

### Contribution 4: Data-Driven Systematics For Future SIDIS/TMD Work

If non-prompt pion sources, VMD/soft production, or direct pion mechanisms are non-negligible in some regions, future JLab SIDIS pion analyses must treat them as systematic uncertainties or background components. MARATHON can turn this systematic from a theory guess into an experimental constraint.

## 9. Recommended Stage Products

The first stage should focus on publishable experimental results:

- $\pi^-$ absolute cross sections for $^1$H, $^2$H, $^3$H, and $^3$He;
- target ratios: $D/H$, $^3$H/$^3$He, $^3$H/$D$, and $^3$He/$D$;
- complete PID, trigger, tracking, acceptance, and target-normalization systematic tables;
- data-driven estimates or upper bounds for electron contamination and non-prompt pion sources;
- a complete record of radiative treatment, energy-loss correction, and Born-level convention for every data product;
- first comparisons with Wiser-like parameterizations and the joint QCD+QED NLO baseline, scanning FF set, scale, default LDF, and no-radiation choices;
- a baseline-residual map showing residuals relative to leading-power, soft empirical, and other candidate mechanisms without assuming dominance in advance.

The second stage can pursue stronger physics interpretation:

- a joint QCD+QED calculation for the actual MARATHON $\pi^-$ beam energy and HRS acceptance;
- global-FF comparisons and large-$z$ FF sensitivity studies;
- comparison of default LDFs, traditional radiative treatment, and future extracted LDFs;
- prompt versus non-prompt pion decomposition;
- direct/higher-twist pion sensitivity, especially to high-$x$ PDFs and pion distribution amplitudes;
- A=3 mirror-nucleus isospin/nuclear interpretation;
- separation of leading-power nPDF baselines, nuclear-enhanced power corrections, and final-state nuclear effects;
- propagation of these uncertainties into SIDIS/TMD analyses.

## 10. Key Risks And Wording Boundaries

- Do not call this an electron DIS cross section. It is an inclusive final-state $\pi^-$ production cross section.
- Do not directly use MARATHON electron DIS radiative corrections to interpret pion production.
- Do not conflate Qiu-Watanabe perturbative photoproduction with soft/VMD photoproduction. The former is part of the leading-power partonic baseline; the latter is a nonperturbative candidate contribution.
- Do not claim that all MARATHON settings are safely in the leading-power region simply because a joint QCD+QED factorization formula exists. At $P_T\simeq0.9$--$1.8\ \mathrm{GeV}$, $1/P_T^n$ corrections may be large.
- Do not use the Qiu-Watanabe $p(e,\pi^+)X$, $y=0$ example curve directly for MARATHON $\pi^-$. The calculation must be redone for the actual energy, angle, acceptance, and targets.
- Do not treat default/model LDFs as data-determined universal LDFs, and do not use traditionally radiatively corrected data directly for LDF extraction.
- Do not claim that the data validate the fragmentation picture before estimating non-prompt pion sources.
- Do not explain all high-momentum pions with leading-twist fragmentation alone. Direct/higher-twist isolated pion production and soft/VMD contributions may compete at JLab energies.
- Without a coincidence electron, event-by-event $Q^2$, $x_B$, or photon virtuality cannot be reconstructed. Any direct/VMD/fragmentation decomposition must state its model inputs and systematic uncertainty.
- Do not treat Qiu-Watanabe EIC-energy predictions for $^4$He and heavier nuclei as direct A=3 predictions.
- Do not interpret $^3$H/$^3$He differences as direct flavor separation before controlling initial-state nuclear effects, acceptance, PID, pion absorption, FSI, and charge-exchange/feed-down.
- If the pion spectrum varies rapidly within the HRS acceptance, the first version should report an acceptance-averaged cross section and state the model dependence of bin-centering corrections.

## 11. References

Local reports and papers:

- Jian-Wei Qiu, `SoLID_ANL_Qiu.pdf`, *Inclusive Hadron Production and Relation to TMDs*, June 17-20, 2024.
- Jian-Wei Qiu, `SoLID2025July_Qiu.pdf`, *Inclusive Pion Production in Lepton-Hadron Collision*, SoLID Collaboration Meeting, JLab, July 7-8, 2025.
- J.-W. Qiu and K. Watanabe, `2607.07664v1.pdf`, *Single inclusive hadron and jet production in lepton-hadron scattering*, arXiv:2607.07664v1 [hep-ph], July 8, 2026. This is the v1 preprint. The PTEP year, volume, page, and DOI on the title page are placeholders and should not be cited as final publication metadata.
- A. Afanasev, C. E. Carlson, C. Wahlquist, `PhysRevD.61.034014.pdf`, *Soft Contributions to Hard Pion Photoproduction*, Phys. Rev. D 61, 034014 (2000).
- A. Afanasev, C. E. Carlson, `1-s2.0-S037594740301176X-main.pdf`, *Hard Pion Electroproduction at Medium Energies*, Nucl. Phys. A 721, 763c-768c (2003).

Published or public papers:

- A. Afanasev, C. E. Carlson, C. Wahlquist, *Probing Polarized Parton Distributions with Meson Photoproduction*, Phys. Lett. B 398, 393-399 (1997). Online: https://arxiv.org/abs/hep-ph/9701215
- A. Afanasev, C. E. Carlson, C. Wahlquist, *Measuring Polarized Gluon and Quark Distributions with Meson Photoproduction*, Phys. Rev. D 58, 054007 (1998). Online: https://arxiv.org/abs/hep-ph/9706522
- A. Afanasev, C. E. Carlson, C. Wahlquist, *Soft Contributions to Hard Pion Photoproduction*, Phys. Rev. D 61, 034014 (2000). Online: https://arxiv.org/abs/hep-ph/9903493
- A. Afanasev, C. E. Carlson, *Interplay of Hard and Soft Processes at JLab Energies*, arXiv:hep-ph/0212376. Online: https://arxiv.org/abs/hep-ph/0212376
- S. J. Brodsky, M. Diehl, P. Hoyer, S. Peigne, *Semi-Exclusive Processes: New Probes of Hadron Structure*, Phys. Lett. B 449, 306-312 (1999). Online: https://arxiv.org/abs/hep-ph/9812277
- P. Eden, P. Hoyer, A. Khodjamirian, *Duality in Semi-Exclusive Processes*, JHEP 0110, 040 (2001). Online: https://arxiv.org/abs/hep-ph/0110297
- A. Szczurek, V. Uleshchenko, J. Speth, *$\bar d-\bar u$ asymmetry and semi-inclusive production of pions in DIS*, Phys. Rev. D 63, 114005 (2001). Online: https://arxiv.org/abs/hep-ph/0009318
- Z.-B. Kang, A. Metz, J.-W. Qiu, J. Zhou, *Exploring the structure of the proton through polarization observables in $l p\to \mathrm{jet}\,X$*, Phys. Rev. D 84, 034046 (2011). Online: https://arxiv.org/abs/1106.3514
- MARATHON Collaboration, *Measurement of the Nucleon $F_2^n/F_2^p$ Structure Function Ratio by the Jefferson Lab MARATHON Tritium/Helium-3 Deep Inelastic Scattering Experiment*, Phys. Rev. Lett. 128, 132003 (2022). Online: https://arxiv.org/abs/2104.05850
- MARATHON Collaboration, *EMC Effect of Tritium and Helium-3 from the JLab MARATHON Experiment*, Phys. Rev. Lett. 135, 062502 (2025). Online: https://arxiv.org/abs/2410.12099
- P. Hinderer, M. Schlegel, W. Vogelsang, *Single-Inclusive Production of Hadrons and Jets in Lepton-Nucleon Scattering at NLO*, Phys. Rev. D 92, 014001 (2015). Online: https://arxiv.org/abs/1505.06415
- T. Liu, W. Melnitchouk, J.-W. Qiu, N. Sato, *A new approach to semi-inclusive deep-inelastic scattering with QED and QCD factorization*, JHEP 11, 157 (2021). Online: https://arxiv.org/abs/2108.13371
- J. Cammarota, J.-W. Qiu, K. Watanabe, J. Y. Zhang, *Radiative corrections in lepton-hadron scattering from QED factorization*, arXiv:2408.08377 and arXiv:2505.23487. These are useful for theory context but should be treated as preprint inputs unless a journal version is confirmed.
- J.-W. Qiu and K. Watanabe, *Single inclusive hadron and jet production in lepton-hadron scattering*, arXiv:2607.07664v1 [hep-ph] (2026). Online: https://arxiv.org/abs/2607.07664
