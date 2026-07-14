# MARATHON 单 pion 产生截面研究的物理目标与意义

## 摘要

本报告根据 Jian-Wei Qiu 关于 inclusive pion / inclusive hadron production 的两个报告、Jian-Wei Qiu 与 Kazuhiro Watanabe 2026 年关于 single-inclusive hadron and jet production 的联合 QCD+QED 因子化预印本，以及 Andrei Afanasev、Carl Carlson、Christian Wahlquist 等较早关于 hard pion photo/electroproduction 的系列工作，结合 MARATHON 已发表的 A=3 深度非弹电子散射结果和后续的单强子产生、SIDIS 因子化、QED 辐射处理文献，整理从 MARATHON 数据中提取

$$
e + A \rightarrow \pi^- + X,\qquad A = ^1\mathrm{H},\, ^2\mathrm{H},\, ^3\mathrm{H},\, ^3\mathrm{He}
$$

包含式单负 pion 产生截面的物理动机。

核心判断是：这项分析不应只被定位为 MARATHON 电子 DIS 分析的副产品，也不应只被定位为 pion fragmentation function 的校准数据。Qiu-Watanabe 的新工作首次在统一的 QCD+QED collinear factorization 框架下计算了不标记散射电子的高横动量单强子产生，将 lepton-initiated scattering、real-photon-initiated perturbative photoproduction、lepton distribution functions（LDFs）、PDFs 和 FFs 纳入同一 leading-power 描述。MARATHON $\pi^-$ 数据与这一 observable 的实验定义直接对应，但其初步结果覆盖的 $P_T\simeq 0.9$--$1.8\ \mathrm{GeV}$ 处在 leading-power 因子化的边界区。因此，最稳妥的定位是：用绝对截面和靶比值检验联合 QCD+QED leading-power baseline 在 JLab 低能、大 $z$、轻核环境中何时成立，并量化 soft/VMD、vector-meson decay、direct/higher-twist pion、核末态作用和其他 power corrections 造成的偏离。

这里必须区分两种不同含义的 photoproduction：Qiu-Watanabe 文中的 photoproduction 是 real-photon-initiated 的微扰 partonic contribution，属于 leading-power factorization 的一部分；soft/VMD 则是光子向强子态涨落后产生 pion 的非微扰贡献。二者不能合并称为同一种机制。

## 1. 从 Qiu 报告和 Qiu-Watanabe 预印本提炼出的主线

Qiu 两个报告与 Qiu-Watanabe 新预印本共同形成了由物理问题到可计算 baseline 的完整主线：

1. 任何含有指定末态强子的截面都包含非微扰强子化信息，不能只靠微扰 QCD 直接计算。
2. 当前 SIDIS/TMD 解释通常默认观测到的 leading hadron 主要来自 struck parton 的 prompt fragmentation；但在 JLab 固定靶能区，这个前提并非自动成立。
3. 对不测量散射电子的包含式单强子过程

$$
\ell + N/A \rightarrow h + X
$$

观测 hadron 的 $P_T$ 本身提供唯一显式硬尺度。若 $P_T$ 足够大，该过程可以写成 LDF、PDF、FF 与 infrared-safe hard part 的卷积，从而系统包含 lepton-side QED radiation、普通 leptoproduction 和 perturbative photoproduction。

在 leading power 下，其结构可概括为

$$
E_H\frac{d\sigma^{eA\rightarrow H+X}}{d^3P_H}
=
\sum_{i,b,c}
f_{i/e}\otimes f_{b/A}\otimes
\widehat{H}_{ib\rightarrow c+X}\otimes D_{c\rightarrow H}
+\mathcal{O}\!\left(\frac{1}{P_T^n}\right),
$$

其中 $f_{i/e}$ 是电子中的 lepton、photon、quark 或 gluon distribution，$f_{b/A}$ 是靶核 PDF，$D_{c\rightarrow H}$ 是末态强子的 fragmentation function。对 MARATHON 而言，这个公式的价值不在于预先保证 factorization 成立，而在于给出一个可以被数据检验、并能与非 leading-power 机制区分的现代 baseline。

在 Qiu 的表述中，single-inclusive hadron production 是 SIDIS 因子化分析的 prerequisite。新预印本把这一判断推进为可计算的联合 QCD+QED 框架。关键不是先做最复杂的角分布或 spin asymmetry，而是先回答三个基础问题：现有 FFs 与 leading-power hard parts 能否描述截面；collision-induced QED radiation 对谱形的影响有多大；剩余偏差是否需要由低 $P_T$ power corrections、soft/VMD、vector-meson decay、direct pion 或核末态作用解释。

## 2. Afanasev-Carlson 早期脉络：为什么中等能区的 pion 更有信息量

Afanasev、Carlson、Wahlquist 从 1997 年开始讨论 high transverse momentum meson photoproduction/electroproduction。他们的出发点和 Qiu 报告中的现代问题高度一致：末态 pion 不是一个“自动干净”的 partonic observable，而是多个机制叠加后的产物。只有先定量知道哪个机制占主导，才能把 pion 数据用于 PDF、FF、GPD 或 spin/TMD 物理解释。

### 2.1 三类机制，而不是单一 fragmentation

这些早期工作把 hard pion production 至少分成三类：

1. **leading-twist fragmentation**：光子或虚光子与 parton 硬散射，末态 parton 再通过 fragmentation function 产生 pion。这是现代 $\ell N\to hX$ NLO 计算和许多 SIDIS 解释默认的主机制。
2. **soft / VMD contribution**：入射光子先涨落为 $\rho,\omega,\phi$ 等矢量介子，再通过软强子过程产生 pion。Afanasev et al. 在 Phys. Rev. D 61, 034014 中用 vector meson dominance 和半包含 hadronic cross-section 参数化估计了这部分，并指出在几十 GeV 入射能量、$p_T$ 约 2 GeV 附近，soft contribution 仍可能很大。
3. **direct 或 higher-twist isolated pion production**：pion 在短距离硬过程中直接形成，而不是作为 jet fragmentation 的一部分。这一项在渐近高能下是 higher twist，但在中等能量、较大 $z$ 或 kinematically isolated pion 区域可以超过普通 fragmentation，因为它不受 fragmentation function 在 $z\to 1$ 处快速下降的同样惩罚。

这三类机制对 MARATHON 的意义不同。若数据主要由 fragmentation 描述，它可进入 FF/SIDIS global analysis；若 soft/VMD 占主导，它更多是 photon-hadron soft dynamics 和 non-prompt source 的基准；若 direct higher-twist 占重要比例，它会直接连接高 $x$ parton distributions、pion distribution amplitude、semi-exclusive duality，甚至与 GPD 硬核计算共享相同 perturbative kernel。

### 2.2 中等能量机器的关键反直觉

Afanasev 和 Carlson 在 2003 年的 *Hard Pion Electroproduction at Medium Energies* 中提出一个对 JLab 特别重要的判断：即使在中等能量机器上，也可能存在 perturbatively calculable 的 hard pion 区域，但该区域未必由 leading-twist fragmentation 主导，而可能由 higher-twist direct pion production 主导。

这点对 MARATHON 很关键。若我们只用“prompt fragmentation vs non-prompt pion”二分法，会漏掉一个物理上可计算但不是 leading-twist FF 的贡献。换句话说，MARATHON $\pi^-$ 截面不只是检验 FF 的数据，也可能是在 JLab 能区检验 direct-pion mechanism、semi-exclusive duality 和高 $x$ parton dynamics 的数据。

### 2.3 虚光子条件与 soft suppression

Afanasev-Carlson 还指出，soft VMD 过程会随光子虚度增加而被压低，因为矢量介子 propagator 带来类似 $m_\rho^2/(m_\rho^2+Q^2)$ 的抑制。直接过程和 fragmentation 也会随 $Q^2$ 变化，但通常没有同样强的 VMD propagator suppression。

这给 MARATHON 数据提供了一个清晰但受限的物理切入点：如果没有 coincidence electron，就不能逐事件重建 photon virtuality 或 missing mass；第一版应主要按 pion 的 $P_T$、实验室动量、角度和靶种类比较谱形。Qiu-Watanabe 的联合因子化框架不要求人为切割出一个小 $Q^2$ photoproduction 样本，而是在同一截面中统一包含 lepton-initiated 和 real-photon-initiated partonic channels。soft/VMD 与 direct/higher-twist 成分则应作为 leading-power baseline 之外的候选贡献，通过残差、能量依赖或模型比较约束。

### 2.4 早期文献留下的空白

2003 年 Afanasev-Carlson 文中明确指出，当时缺少可比较的已分析数据。后续 NLO $\ell N\to hX$ 计算、QCD+QED factorization 和 Qiu 的报告把这个问题推进到了现代 factorization 语言，但 JLab 固定靶能区、绝对 $\pi^-$ 截面、轻核靶系统性的实验基准仍不充分。

MARATHON 的贡献就在这里：它不是重新发现 hard pion production 的想法，而是有机会用同一套高精度 HRS 和 $^1$H/$^2$H/$^3$H/$^3$He 靶，把早期理论中长期缺乏的 fixed-target single-pion benchmark 补上。

## 3. 为什么 single pion cross section 是关键可观测量

### 3.1 检验 JLab 能区的 fragmentation picture

Hinderer、Schlegel、Vogelsang 的 NLO 计算表明，当散射 lepton 不被测量时，单强子产生 $\ell N \to hX$ 的硬尺度主要由观测强子的横动量给出；NLO correction 可能很大，quasi-real photon contribution 也可能重要。Qiu-Watanabe 进一步在 joint QCD+QED factorization 中把这些 contribution 组织为统一的 leading-power 结果：

- lepton-initiated subprocess，例如 $e q\rightarrow e q$ 及其 QCD corrections；
- real-photon-initiated perturbative photoproduction，例如 $\gamma q\rightarrow qg$；
- 由 LDFs 编码的、process-independent 的 leading-power QED radiation；
- 由 PDFs 和 FFs 描述的 initial-state hadron structure 与 final-state fragmentation。

该框架的重要优点是无需用额外的 scattered-electron cut 人为分离所谓 direct/resolved photon contribution。但它只在 $P_T$ 足够大、power corrections 可控时构成可靠的 leading-power baseline。

这正对应 MARATHON 的核心问题：初步 pion 截面覆盖 $P_T\simeq0.9$--$1.8\ \mathrm{GeV}$，接近 QCD factorization 的最低适用尺度。Qiu-Watanabe 的数值计算在 $P_T<m_c$ 时将演化尺度冻结在 $m_c$，并把非 leading-power contribution 写成 $\mathcal{O}(1/P_T^n)$。因此，MARATHON 不是一个可以预设 fragmentation dominance 的干净高 $P_T$ 样本，而是检验 leading-power description 向低 $P_T$ 过渡的边界数据。若 joint QCD+QED NLO baseline 无法描述数据，差异可能来自：

- 大 $z$ pion fragmentation function 约束不足；
- $p_T$ 或 invariant mass 不够大，leading-power approximation 失效；
- $\rho$、$\omega$ 等 vector meson 衰变产生的 non-prompt pion 没有扣除；
- 默认 LDFs 或 lepton-side QED radiation 的处理不充分；
- perturbative photoproduction 与 leptoproduction 的相对贡献估计不准；
- 轻核靶中的 nuclear dependence 或 final-state interaction 改变了 pion 产额。

因此，绝对截面本身就是物理结果，而不是只为后续 SIDIS 分析服务的技术校准。

### 3.2 为 SIDIS/TMD 提供可控前提

SIDIS 的目标通常是利用

$$
e + N \rightarrow e' + h + X
$$

中的二维尺度结构来抽取 TMDs、fragmentation functions 和 angular modulations。TMD factorization 要求硬尺度 $Q$ 足够大，同时末态强子的横动量相对 $Q$ 较小；观测到的 hadron 还应是 fragmenting parton 的 leading hadron。

Qiu 报告强调，在 JLab kinematics 下这一点“unlikely to be satisfied”是需要严肃检查的风险，而不是可以忽略的细节。包含式单 pion 截面可以在不引入 SIDIS 全部角分布复杂性的情况下，先检验：

- 当前 pion FFs 是否能描述 JLab 12 GeV 能区；
- 需要多大的 non-prompt pion subtraction；
- 现有 radiative correction 或 QED factorization 处理是否会改变截面解释；
- 用这些 pion 数据解释 SIDIS angular modulation 时，理论系统误差应如何设定。

### 3.3 约束大 $z$ pion fragmentation functions

Qiu-Watanabe 新预印本定量说明，single-inclusive high-$P_T$ hadron production 对大 $z$ FF 特别敏感：PDF 在 $x\rightarrow1$ 时下降通常比 FF 随 $z$ 的下降更快，使卷积偏向较小 $x$、较大 $z$ 的区域；在固定碰撞能量下，$P_T$ 越高，这种 large-$z$ dominance 越强。论文还显示，JAM20 与 MAP1.0 pion FF central sets 的差异可显著改变预测的 $P_T$ 谱，而且 FF-set uncertainty 可以大于常规 factorization/renormalization scale variation。

JLab 固定靶实验中，高动量 forward pion 因此对大 $z$ FFs、尤其是 $\pi^-$ 相关 favored/unfavored fragmentation 具有潜在约束力。但 MARATHON 的 $P_T$ 较低，large-$z$ sensitivity 与 power corrections 同时增强；不能把二者混为单纯的 FF uncertainty。

这类约束与 $e^+e^-$ 数据互补：$e^+e^-$ 对 flavor 组合和大 $z$ 区的约束有限，而 lepton-nucleon 固定靶数据含有 PDF 与 FF 的卷积，对 flavor、target 和 nuclear dependence 更敏感。第一阶段不应过度宣称可直接抽取 FF；更稳妥的目标是给出能被 FF global analysis 使用的绝对截面和协方差。

### 3.4 检验 leading-power QED radiation 与 LDFs

Qiu-Watanabe 将 collision-induced QED contribution 分为三类：由 LDFs、PDFs 和 FFs 吸收的 universal leading-power contribution；进入 hard coefficients 的 process-dependent 但 perturbatively calculable contribution；以及可能不可因子化的 power-suppressed contribution。其数值结果表明，LDF evolution 会降低 parent electron 在 $\xi\rightarrow1$ 区域的概率、增加较低 $\xi$ 的 electron/photon content，从而改变 single-hadron $P_T$ 谱。根据碰撞能量和相空间，这种谱形变化可以达到约 $50\%$ 或更大。

这一结果使 radiative effect 从“低优先级小修正”上升为 MARATHON pion analysis 的核心理论问题。但需要保留两个限制：论文当前使用的是在 $\mu_0=m_c$ 设定的 default/model LDFs，而非由数据提取的最终 universal LDFs；作者还指出，已经施加传统 radiative correction 的 published data 不能在不移除原修正的情况下直接用于 LDF extraction。因此，MARATHON 必须记录 pion 数据产品是否以及如何施加过 radiative treatment，并比较定义一致的 detector-level、Born-like 或 factorized theory observable。

## 4. MARATHON 数据的独特价值

MARATHON 已发表电子 DIS 结果展示了该实验在 A=3 镜像核上的归一化、靶系统和 HRS 分析能力。其 $F_2^n/F_2^p$ 测量利用 $^3$H 与 $^3$He 镜像对称性降低理论不确定性，覆盖 $0.19<x<0.83$；A=3 EMC 结果覆盖 $0.20<x<0.83$、$Q^2=2.7$ 到 $11.9\ \mathrm{GeV}^2$，并给出了首个 tritium EMC effect 测量。

对 single pion production，这套数据的独特性在于：

- 同一实验条件下同时有 $^1$H、$^2$H、$^3$H、$^3$He 靶；
- HRS 提供高分辨率动量和角度测量，适合绝对截面提取；
- MARATHON 电子 DIS 分析已建立 beam charge、target density、boiling correction、live time、acceptance 和 run quality 的归一化框架；
- $^3$H 与 $^3$He 的 mirror nuclei 组合可用于研究轻核中 pion 产生的 isospin、initial-state nuclear modification 与 final-state interaction 的综合效应；
- $^1$H 和 $^2$H 可作为基准，用于先检验 nucleon-level leading-power baseline，再识别 A=3 中额外的 nuclear modifications。

因此，MARATHON pion 分析的目标不只是给出某个靶的单点截面，而是建立一组可比较的 A=1,2,3 截面和比值。

## 5. 推荐物理目标

### 目标 1：提取绝对 $\pi^-$ 包含式截面

基础结果应定义为

$$
\frac{d^2\sigma_{\pi^-}}{dp_{\pi}\,d\Omega_{\pi}}
=
\frac{N_{\pi^-}^{\mathrm{corr}}}
{N_e\,N_{\mathrm{tgt}}\,\Delta p\,\Delta\Omega},
$$

分别给出 $^1$H、$^2$H、$^3$H、$^3$He 在各 MARATHON kinematic setting 下的结果。第一阶段建议报告 fiducial acceptance averaged cross section；只有在 Monte Carlo acceptance 和 bin-centering correction 稳定后，再发布更细 bin 的截面。

### 目标 2：建立 target ratios，降低共同系统误差

建议重点给出：

$$
R_{D/H} = \frac{\sigma_{\pi^-}(^2\mathrm{H})}{\sigma_{\pi^-}(^1\mathrm{H})},
\quad
R_{t/h} = \frac{\sigma_{\pi^-}(^3\mathrm{H})}{\sigma_{\pi^-}(^3\mathrm{He})},
$$

以及

$$
\frac{\sigma_{\pi^-}(^3\mathrm{H})}{\sigma_{\pi^-}(^2\mathrm{H})},
\qquad
\frac{\sigma_{\pi^-}(^3\mathrm{He})}{\sigma_{\pi^-}(^2\mathrm{H})}.
$$

这些比值在 beam charge、部分 acceptance 和 detector efficiency 上有共同误差抵消，更适合讨论 nuclear/isospin dependence。Qiu-Watanabe 指出，在 $P_T$ 足够大的 leading-power 极限，lepton-nucleus single-hadron production 可以通过以 nPDF 替换 free-nucleon PDF 来描述 initial-state nuclear effects；但 power corrections 可能随核尺寸增强，并且还可能存在额外的 final-state nuclear effects。其数值核结果主要针对 EIC 能量、$^4$He 及更重核，不是对 MARATHON $^3$H/$^3$He 的直接预测。因此，$^3$H/$^3$He 比值应首先作为 A=3 pion-production 镜像核基准，而不是直接解释为 nPDF 或 flavor separation。

### 目标 3：检验 leading-power baseline 并诊断额外机制

对 $^1$H 和 $^2$H，应优先建立 nucleon-level baseline，而不是直接把所有差异解释为 nuclear effect。比较对象应分层组织：

- **leading-power baseline**：joint QCD+QED factorization 下的 NLO $\ell N\to hX$，包括 lepton-initiated 和 real-photon-initiated perturbative channels、LDFs、PDFs 与 FFs；
- **empirical soft baseline**：Wiser-like 参数化；
- **non-perturbative photon source**：soft/VMD 与 vector-meson decay；
- **power-suppressed candidate**：direct/higher-twist isolated pion 与其他低 $P_T$ corrections；
- **nuclear contribution**：nPDF-like initial-state modification、pion absorption、FSI、charge exchange 和 feed-down。

比较时要明确：

- 该过程不是普通 inclusive electron DIS；
- 若散射电子不参与事件定义，硬尺度不能简单用 DIS 的 $Q^2$ 表述；
- perturbative photoproduction 不等同于 soft/VMD photoproduction；
- QED radiation、FF choice、factorization scale 和 $1/P_T^n$ corrections 都可能影响解释；
- 数据与理论差异不能直接等同于 nuclear effect，必须先在 hydrogen/deuterium 上建立机制基准。

### 目标 4：量化 non-prompt pion 与 soft/VMD 背景

Qiu 早期报告强调，JLab 能区可能存在来自 $\rho$ decay 等 vector-meson source 的 non-prompt pions。Qiu-Watanabe 新预印本没有显式分解 prompt 与 vector-meson-decay pion；其 inclusive FF-based formula 本身也不提供实验上可直接分离的 prompt/non-prompt decomposition。因此，这一分量仍需借助 generator、identified vector-meson data、模型或数据驱动约束单独评估。若这些 pion 被当成 clean leading-fragmentation pions，会污染 SIDIS leading-hadron interpretation。

因此，单 pion 截面分析应把 non-prompt source 当作物理问题，而不只是探测器背景。实际分析中可先给出数据驱动上限或模型依赖估计，再逐步发展为：

- prompt fragmentation component；
- vector-meson decay component；
- target window / accidental / PID contamination；
- nuclear-dependent residual contribution。

### 目标 5：为 QCD+QED 因子化和 radiative effects 提供测试场

Liu、Melnitchouk、Qiu、Sato 的 QCD+QED factorization 工作指出，在 SIDIS 中 radiation effects 会破坏简单的 photon-nucleon frame 定义，需要更系统地处理 lepton-side radiation。Qiu-Watanabe 随后首次对 single-inclusive high-$P_T$ hadron production 给出 joint QCD+QED 数值计算，显示 LDF-induced leading-power QED radiation 可以显著重塑 hadron $P_T$ spectrum，在部分运动学下达到约 $50\%$ 或更大。

MARATHON pion 截面可以作为一个实验测试：

- 传统 radiative correction 在含末态强子的过程上是否足够；
- default LDFs 与未来从数据提取的 universal LDFs 是否能一致描述数据；
- lepton distribution functions 的 factorized 处理是否必要；
- 截面对 incident-energy smearing 和 photon radiation phase space 的敏感性有多大。

因此，radiative effect 不应再被放在低优先级。第一阶段应至少保存未被传统 electron-DIS RC 混合处理的 pion yield 定义，记录所有已施加的 radiative treatment，并把“无 QED evolution”“default LDF”“传统 RC 近似”三种理论处理的差异列入模型系统误差。只有在实验 observable 与理论定义一致后，才能进一步讨论 LDF extraction。

## 6. 与已有工作的关系

### MARATHON 已发表电子 DIS 结果提供归一化基础

MARATHON $F_2^n/F_2^p$ PRL 结果展示了 $^3$H/$^3$He mirror nuclei 方法的价值，也给出了 cryogenic tritium target、HRS、beam charge 和 target-density normalization 的可靠基础。A=3 EMC PRL 进一步展示了同一数据集对轻核 EMC effect 的灵敏度。

single pion 分析应复用这些与末态粒子无关的实验归一化，但必须重新建立 $\pi^-$ trigger、PID、tracking、pion survival、electron leakage 和 hadron contamination 的修正。不能把 electron DIS radiative correction 或 electron PID 直接移植到 pion 截面。

### NLO 单强子产生理论提供比较框架

Hinderer、Schlegel、Vogelsang 已给出 $\ell N\to hX$ 和 $\ell N\to \mathrm{jet}X$ 的 NLO 计算，指出未测散射 lepton 时，观测 hadron/jet 的 transverse momentum 扮演硬尺度角色，且 NLO correction sizable。该框架是 hydrogen/deuterium 基准比较的自然起点。

### Afanasev-Carlson 早期工作提供机制分解框架

Afanasev、Carlson、Wahlquist 的 1997-2003 年系列工作比后来的 NLO $\ell N\to hX$ 计算更早提出了固定靶 hard pion 的几个核心问题：soft contribution 在 $p_T\sim 2\ \mathrm{GeV}$ 仍可能显著；polarization 或 flavor-sensitive observable 会被 soft process 稀释；JLab 中等能量下可计算区域可能不是 leading-twist fragmentation，而是 direct/higher-twist isolated pion production。MARATHON 数据可把这些理论判断从“机制估计”推进到实际的绝对截面检验。

### QCD+QED factorization 提供 radiative interpretation

Liu、Melnitchouk、Qiu、Sato 的工作把 QED 与 QCD radiation 放在同一 factorization 框架中，指出 SIDIS 中简单的 photon-nucleon frame 在 radiation 存在时并非良定义。Qiu-Watanabe 的 2026 年预印本进一步给出 single-inclusive hadron/jet production 的 factorization formula 和首次数值计算，在同一框架内统一描述 leptoproduction 与 perturbative photoproduction，并量化 LDF-induced leading-power QED effect、FF-set uncertainty 和 leading-power nuclear dependence。

该工作为 MARATHON 提供了自然的现代理论 baseline，但不是可以直接套用的成品曲线：论文的 JLab 示例主要是 proton 上的 $\pi^+$、$\sqrt{S}=4.84\ \mathrm{GeV}$、$y=0$；MARATHON 需要针对 $\pi^-$、实际束流能量、HRS 角度和 acceptance、以及 $^1$H/$^2$H/$^3$H/$^3$He 重新计算。论文当前 LDFs 也是 default/model set；作者说明数值代码维护在 private GitHub，可依合理学术请求获取，因此需要与作者合作、申请代码或独立实现后才能做定量比较。

## 7. 研究意义

### 对 hadron structure

这项测量能回答 SIDIS/TMD 分析中一个经常被隐藏的前提：观测到的 pion 是否真能被当作 fragmenting parton 的 leading hadron。若该前提在 JLab kinematics 下失败，许多 SIDIS angular modulation 的解释都需要重新评估其系统误差。若 direct/higher-twist isolated pion 占重要比例，它还会提供一个与 exclusive/GPD 硬核相连的 semi-exclusive 观测量。

### 对 fragmentation functions

高动量 $\pi^-$ 的绝对截面和靶比值可为大 $z$ pion FFs 提供补充约束。尤其是结合 $^1$H、$^2$H、$^3$H、$^3$He 后，可以检验不同 flavor/isospin 与 nuclear scenario；但在 MARATHON 的低 $P_T$ 区域，FF sensitivity 必须与 higher-twist、soft source 和 final-state nuclear effects 同时评估。

### 对 direct pion 与 higher-twist dynamics

如果 MARATHON 的高动量 $\pi^-$ 数据不能由 leading-twist fragmentation 描述，却与 direct pion 或 semi-exclusive 估计更一致，这将把早期 Afanasev-Carlson 的中等能量机制图像转化为可检验的实验结论。这样的结果会对 JLab 能区如何使用 pion observables 提取高 $x$ parton distributions、pion distribution amplitude 或 GPD 相关信息产生直接影响。

### 对轻核 QCD

A=3 镜像核给出了一个少见机会：在同一实验条件下比较 $^3$H 与 $^3$He 中的 pion production。若 $^3$H/$^3$He pion 比值偏离简单 nucleon counting 或 isospin expectation，可能提示 nuclear dependence、final-state interaction 或 flavor-dependent fragmentation 的效应。

### 对未来 JLab / EIC 分析

Qiu-Watanabe 的数值结果表明，在 EIC 和 JLab 的 single-hadron observable 中，QED radiation、large-$z$ fragmentation uncertainty 和 nuclear dependence 都可能产生显著的谱形变化。MARATHON pion 截面可作为固定靶能区的 benchmark dataset，帮助判断哪些 theoretical systematics 和 power corrections 必须进入未来 SIDIS/TMD global analysis。

## 8. MARATHON tritium single pion 数据的潜在贡献

### 贡献 1：补上固定靶能区的绝对 $\pi^-$ 基准

早期 Afanasev-Carlson 文献和后续 Qiu 报告都指出，JLab 固定靶能区缺少足够系统的 single pion benchmark。MARATHON 可给出同一谱仪、同一束流、同一靶系统下的 $^1$H、$^2$H、$^3$H、$^3$He 绝对 $\pi^-$ 截面。这比单个靶或单个 setting 的产额更有价值，因为它能同时约束 normalization、mechanism shape 和 nuclear dependence。

### 贡献 2：建立 baseline-residual 机制诊断图

建议把结果组织成“baseline-residual map”而不只是截面表：先给出 joint QCD+QED leading-power baseline 及其 FF、scale、LDF uncertainty，再叠加 Wiser-like、soft/VMD、vector-meson decay 和 direct/higher-twist sensitivity bands，最后展示数据相对各 baseline 的残差。只有当一种机制在不确定度范围内稳定占优时，才使用 fragmentation dominated、soft dominated 或 direct-pion candidate 等标签。这样可以直接回答当前因子化框架在 JLab pion 数据上在哪里有效、在哪里需要额外 power corrections。

### 贡献 3：提供 A=3 mirror-nuclei pion production 基准

$^3$H 与 $^3$He 的组合是 MARATHON 的独特资产。对 $\pi^-$ 来说，$^3$H/$^3$He 比值不仅含有 isospin 信息，还可能对 nuclear absorption、final-state interaction、charge-exchange feed-down 和 target remnant fragmentation 敏感。只要先用 $^1$H/$^2$H 建立 mechanism baseline，A=3 比值就能成为轻核中 hadronization/nuclear dependence 的新基准。

### 贡献 4：为未来 SIDIS/TMD 分析提供数据驱动系统误差

如果 single pion 数据显示 non-prompt pion、VMD/soft 或 direct pion 在某些区域不可忽略，那么未来用 JLab SIDIS pion 数据抽取 TMDs、Collins/Sivers asymmetry 或 flavor-separated fragmentation 时，就必须把这些机制作为系统误差或背景项处理。MARATHON 的贡献可以是把这个系统误差从理论猜测变成实验约束。

## 9. 建议的阶段性产物

第一阶段应聚焦可发表的实验结果：

- $^1$H、$^2$H、$^3$H、$^3$He 的 $\pi^-$ absolute cross section；
- target ratios：$D/H$、$^3$H/$^3$He、$^3$H/$D$、$^3$He/$D$；
- 完整的 PID、trigger、tracking、acceptance、target normalization 系统误差表；
- electron contamination 和 non-prompt pion contribution 的数据驱动估计或上限；
- 每个数据产品已经施加的 radiative treatment、energy-loss correction 和 Born-level convention 的完整记录；
- 与 Wiser-like 参数化及 joint QCD+QED NLO baseline 的第一轮比较，后者至少扫描 FF set、scale、default-LDF/no-radiation 两种选择；
- 一张 baseline-residual map，展示数据相对 leading-power、soft empirical 和其他 candidate mechanisms 的残差，而不预先指定 dominance。

第二阶段再做更强物理解释：

- 针对 MARATHON $\pi^-$ 实际束流能量和 HRS acceptance 的 joint QCD+QED calculation；
- 基于 global FF 的理论比较和 large-$z$ FF sensitivity study；
- default LDF、传统 radiative treatment 与未来 extracted LDF 的比较；
- prompt vs non-prompt pion 分量分解；
- direct/higher-twist pion sensitivity study，特别是对 high-$x$ PDFs 和 pion distribution amplitude 的潜在灵敏度；
- A=3 mirror nuclei 的 isospin/nuclear dependence 解释；
- leading-power nuclear PDF baseline、nuclear-enhanced power correction 和 final-state nuclear effect 的分离研究；
- 与 SIDIS/TMD 分析的系统误差传播连接。

## 10. 关键风险与表述边界

- 不应把该结果称为 electron DIS cross section；它是末态 $\pi^-$ 的包含式产生截面。
- 不应直接用 MARATHON 电子 DIS radiative correction 解释 pion 截面。
- 不应把 Qiu-Watanabe 的 perturbative photoproduction 与 soft/VMD photoproduction 混为一谈；前者属于 leading-power partonic baseline，后者是非微扰候选贡献。
- 不应因为存在 joint QCD+QED factorization formula 就宣称 MARATHON 全部 setting 已处于可靠的 leading-power 区域；$P_T\simeq0.9$--$1.8\ \mathrm{GeV}$ 下的 $1/P_T^n$ corrections 可能很大。
- 不应把 Qiu-Watanabe 的 $\pi^+$ proton、$y=0$ 示例曲线直接用于 MARATHON $\pi^-$；必须按实际能量、角度、acceptance 和靶重新计算。
- 不应把 default/model LDF 当成已经由数据确定的 universal LDF，也不能把施加过传统 RC 的数据直接用于 LDF extraction。
- 不应在没有 non-prompt pion 估计前宣称数据已经验证 fragmentation picture。
- 不应只用 leading-twist fragmentation 解释所有高动量 pion；JLab 能区可能存在 direct/higher-twist isolated pion 和 soft/VMD contribution 的竞争。
- 若单 pion 样本没有 coincidence electron，就不能逐事件重建 $Q^2$、$x_B$ 或 photon virtuality；direct/VMD/fragmentation 分解必须明确模型输入和由此产生的系统误差。
- 不应把 Qiu-Watanabe 在 EIC 能量对 $^4$He 及更重核的 nPDF prediction 当成 A=3 直接预测。
- 不应把 $^3$H/$^3$He 差异直接解释为 flavor separation；必须先控制 initial-state nuclear effect、acceptance、PID、pion absorption、FSI 和 charge-exchange/feed-down。
- 若 HRS acceptance 内 pion 谱变化很快，第一版应报告 acceptance-averaged cross section，并明确模型依赖的 bin-centering correction。

## 11. 参考资料

本地报告：

- Jian-Wei Qiu, `SoLID_ANL_Qiu.pdf`, *Inclusive Hadron Production and Relation to TMDs*, June 17-20, 2024.
- Jian-Wei Qiu, `SoLID2025July_Qiu.pdf`, *Inclusive Pion Production in Lepton-Hadron Collision*, SoLID Collaboration Meeting, JLab, July 7-8, 2025.
- J.-W. Qiu and K. Watanabe, `2607.07664v1.pdf`, *Single inclusive hadron and jet production in lepton-hadron scattering*, arXiv:2607.07664v1 [hep-ph], July 8, 2026. 当前为 v1 预印本；PDF 首页的 PTEP 年份、卷页和 DOI 是占位信息，不应作为正式出版信息引用。
- A. Afanasev, C. E. Carlson, C. Wahlquist, `PhysRevD.61.034014.pdf`, *Soft Contributions to Hard Pion Photoproduction*, Phys. Rev. D 61, 034014 (2000).
- A. Afanasev, C. E. Carlson, `1-s2.0-S037594740301176X-main.pdf`, *Hard Pion Electroproduction at Medium Energies*, Nucl. Phys. A 721, 763c-768c (2003).

已发表或公开论文：

- A. Afanasev, C. E. Carlson, C. Wahlquist, *Probing Polarized Parton Distributions with Meson Photoproduction*, Phys. Lett. B 398, 393-399 (1997). Online: https://arxiv.org/abs/hep-ph/9701215
- A. Afanasev, C. E. Carlson, C. Wahlquist, *Measuring Polarized Gluon and Quark Distributions with Meson Photoproduction*, Phys. Rev. D 58, 054007 (1998). Online: https://arxiv.org/abs/hep-ph/9706522
- A. Afanasev, C. E. Carlson, C. Wahlquist, *Soft Contributions to Hard Pion Photoproduction*, Phys. Rev. D 61, 034014 (2000). Online: https://arxiv.org/abs/hep-ph/9903493
- A. Afanasev, C. E. Carlson, *Interplay of Hard and Soft Processes at JLab Energies*, arXiv:hep-ph/0212376; conference version related to *Hard Pion Electroproduction at Medium Energies*. Online: https://arxiv.org/abs/hep-ph/0212376
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
