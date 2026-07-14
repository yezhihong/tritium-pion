# MARATHON 包含式单负 pion 产生截面分析策略

## 1. 物理目标

本分析的目标是从 MARATHON 11 GeV 电子束数据中提取包含式单负 pion 产生截面：

$$
e + A \rightarrow \pi^- + X .
$$

当前本地 `run_lists/` 中对应的靶为 `H1`、`D2`、`H3` 和 `He3`。这里明确使用 Helium-3，末态粒子明确限定为 $\pi^-$。

核心思路很直接：MARATHON 已经完成并发表了包含式电子 DIS 截面的分析。我们应最大限度复用其中与末态粒子无关的部分，包括 beam charge、target density、boiling correction、live time、HRS acceptance、run-quality 和 normalization；真正需要替换的是末态粒子选择，即把 electron trigger/PID 改成 $\pi^-$ trigger/PID，并补上 $\pi^-$ 专属的效率和背景修正。

## 2. 已检查的输入

本地文件：

- `papers/MARATHON.pdf`
- `papers/MARATHON——SUPPLEMENTALFILEREVISED.pdf`
- `papers/MARATHON-EMC.pdf`
- `papers/MARATHON-EMC-SupplementalFileFina.pdf`
- `thesis/*.pdf`
- `analysis/Yield.C`
- `analysis/TRI_Beam.h`
- `analysis/TRI_Target.h`
- `analysis/TRI_LiveTime.C`
- `analysis/TRI_Tools.h`
- `analysis/wiser_all_sig.f`
- `run_lists/*.dat`

飞书知识库：

- `Single Pion Production in A=3`
- `MARATHON Inclusive Pion`

飞书文档中已经列出的关键任务包括：检查数据是否全部 replay、确认 replayed ROOT 文件中是否已有 PID/trigger cut、采用两个 PRL 文章中的 target-density normalization、用 GC 和 ECAL 从 S1/S2 trigger 样本中筛选 pion、评估 PID cut efficiency 和 electron contamination、评估 pion tracking 和 pion trigger efficiency、其他与电子分析相同的效率和 acceptance 修正尽量复用，并把 radiative effect 作为低优先级系统误差估计。

## 3. 分析原则

MARATHON 发表的电子 DIS 分析测量的是：

$$
e + A \rightarrow e' + X .
$$

本分析要测量的是：

$$
e + A \rightarrow \pi^- + X .
$$

因此不能把结果称为 electron DIS cross section，也不能直接套用 DIS electron radiative correction 的物理解释。我们要做的是用同一套 MARATHON 实验条件、同一套 HRS 接收度和同一套靶归一化，提取末态 $\pi^-$ 的包含式产生截面。

需要保持不变的部分：

1. beam charge normalization；
2. target areal density 和 boiling correction；
3. run selection 和 data-quality 逻辑；
4. HRS optics、vertex 和 fiducial acceptance；
5. prescale/live-time 计算框架；
6. cross-section normalization 结构。

需要替换或新增的部分：

1. 使用 $\pi^-$ 对应的 trigger bit，而不是 electron trigger；
2. 使用 $\pi^-$ PID，而不是 GC-high、E/p-high electron PID；
3. 评估 $\pi^-$ PID efficiency；
4. 评估 electron leakage into $\pi^-$ sample；
5. 评估 $\pi^-$ trigger efficiency、tracking efficiency 和可能的 hadron survival/absorption；
6. 对 kaon/proton contamination 给出上限或系统误差；
7. 对 radiative/energy-loss effect 做独立估计，不能照搬电子 DIS 修正。

## 4. 截面定义和归一化

每个 target、kinematic setting、HRS arm 上提取：

$$
\frac{d^2\sigma_{\pi^-}}{dp_{\pi} \, d\Omega_{\pi}}
=
\frac{N_{\pi^-}^{\mathrm{corr}}}
{N_e \, N_{\mathrm{tgt}} \, \Delta p \, \Delta \Omega}.
$$

其中 $N_e$ 是入射电子数，$N_{\mathrm{tgt}}$ 是单位面积靶核数，$\Delta p \Delta\Omega$ 是 HRS 在该 bin 或 fiducial 区域内的动量-立体角相空间。

修正后的 $\pi^-$ 计数建议写成：

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

更适合代码实现的形式是：

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

本地 `analysis/Yield.C` 已经有一个电子 normalized-yield 原型：

```text
XS = Good_Ele / Ne / Ntg / phase_space * CM2ToNB
```

在 $\pi^-$ 分析中，应改为：

```text
XS_pi_minus = N_pi_minus_corr / Ne / Ntg / phase_space * CM2ToNB
```

相空间可以先用 HRS fiducial cut 的几何近似：

$$
\Delta p \Delta\Omega
\simeq
(p_0 \Delta\delta) \, \Delta\theta \, \Delta\phi .
$$

如果 $\pi^-$ 截面在 HRS acceptance 内变化很快，第一版可以报告 acceptance-averaged cross section；若要和理论曲线逐点比较，则需要进一步做 Monte Carlo acceptance 和 bin-centering correction。

代码注意事项：当前 `Yield.C` 的误差传播中有一项看起来把 `Ne->Sys_Err` 除以了 `Ntg->Value`。这应当检查；物理上该项很可能应除以 `Ne->Value`。

## 5. 分析步骤

### Step 0：建立 run database

先为每个 run 建立可追溯表格：

- run number；
- target：`H1`、`D2`、`H3`、`He3`；
- kinematic setting：`Kin1`、`Kin2`、`Kin3`、`Kin5`、`Kin7`；
- HRS arm；
- central momentum 和 angle；
- magnet polarity；
- beam charge；
- prescale factors；
- electron trigger bit；
- $\pi^-$ trigger bit；
- replay version；
- ROOT file path；
- good/bad run flag；
- exclusion reason。

在没有这个 run database 之前，不应开始正式的物理截面提取。

建议输出：

```text
output/single_pion/tables/run_db.csv
output/single_pion/tables/run_quality.csv
output/single_pion/tables/run_exclusions.csv
```

### Step 1：检查 replay 和 run quality

对 `run_lists/*.dat` 中所有 run 做检查：

1. ROOT 文件是否存在；
2. replayed ROOT 文件是否已经施加过 PID 或 trigger cut；
3. scaler tree 是否完整；
4. $\pi^-$ trigger 对应的 raw scaler branch 是否存在；
5. prescale factors 是否逐 run 正确读取；
6. beam current、BCM calibration 和 charge cut 是否稳定；
7. target 状态、raster、vertex distribution 和 boiling correction 是否正常。

特别要确认 replay 文件中保存的是足够原始的 detector variables。如果 replay 阶段已经只保留 electron sample，那么 $\pi^-$ 分析会有根本偏差。

### Step 2：先复现 electron benchmark

在提取 $\pi^-$ 之前，必须先用当前代码链复现 MARATHON electron normalized yield 或 cross-section 的归一化闭环。目的不是重新发表 electron DIS 结果，而是验证：

- beam charge normalization；
- target areal density；
- boiling correction；
- live time 和 prescale；
- HRS fiducial/acceptance cut；
- run grouping；
- phase-space convention。

本地 `Yield.C` 中的 electron cut 包括：

```text
single track
electron trigger
GC above threshold
ECAL E/p above threshold
vertex cut
tg_th, tg_ph, tg_dp acceptance cuts
```

只有 electron benchmark 闭合后，$\pi^-$ 分析中新增的不确定性才主要来自 PID/trigger/contamination，而不是来自归一化链条本身。

建议输出：

```text
output/single_pion/validation/electron_yield_reproduction.csv
output/single_pion/validation/electron_cross_section_comparison.pdf
```

### Step 3：定义 $\pi^-$ event sample

每个 target 和 kinematic setting 下，$\pi^-$ 候选事件应包含：

- 正确的 S1/S2 hadron 或 pion trigger bit；
- exactly one good HRS track，除非后续明确处理 multi-track；
- 与 electron benchmark 相同的 HRS optics 和 fiducial cut；
- target-cell 内的 vertex cut，并排除 window 区域；
- GC anti-electron cut；
- ECAL 中 MIP-like 或 low-E/p pion band；
- 若 replay 中有 aerogel、TOF 或其他 PID 变量，应纳入控制图和 cut scan。

第一步不要直接固定 cut。先做控制图：

```text
GC amplitude vs E/p
GC amplitude vs momentum
E/p vs momentum
beta or TOF proxy vs momentum
vertex distribution by PID region
trigger-bit overlap matrix
```

初始 $\pi^-$ cut 可以写成：

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

GC 和 E/p 阈值必须按 kinematic setting、arm 和 rate 条件做 scan，不应直接照搬 electron cut。

### Step 4：评估 PID efficiency 和 electron contamination

需要建立数据驱动的 PID response matrix：

```text
真实粒子类别 -> 被选择为 pi- 的概率
```

至少要给出：

- $\epsilon_{\mathrm{PID},\pi^-}$；
- electron leakage：$N_{e \rightarrow \pi^-}$；
- kaon/proton contamination 的估计或上限；
- cut variation 带来的系统误差。

可用的控制样本：

- GC-high、E/p-high 的 clean electron region；
- GC-low、MIP-like 的 pion-enriched region；
- electron trigger 和 pion trigger overlap；
- GC/E/p sideband extrapolation；
- H1 上用 Wiser 参数化只做 sanity check，不作为主要修正来源。

建议输出：

```text
output/single_pion/pid/pid_cut_scan_<target>_<kin>.pdf
output/single_pion/pid/pion_pid_efficiency.csv
output/single_pion/pid/electron_contamination.csv
```

### Step 5：计算 $\pi^-$ live time 和 trigger efficiency

如果 $\pi^-$ 使用的 trigger 与 electron trigger 不同，就不能直接复用 electron live time。

需要逐 run 完成：

1. 读取 prescale factors；
2. 确认 $\pi^-$ trigger number；
3. 使用对应的 raw scaler branch，例如 `LeftT_N_` 或 `RightT_N_`；
4. 用 accepted trigger count 和 raw scaler count 计算 DAQ live time；
5. 利用 redundant scintillator trigger 或 trigger overlap 评估 trigger efficiency；
6. 若无法干净测量，给出保守系统误差。

建议输出：

```text
output/single_pion/trigger/pion_trigger_livetime.csv
output/single_pion/trigger/pion_trigger_efficiency.csv
```

### Step 6：tracking、acceptance 和 bin-centering

HRS optics 和 acceptance 结构可沿用 MARATHON electron 分析，但必须对 $\pi^-$ track 检查：

- single-track efficiency；
- tracking efficiency vs rate、target、momentum；
- optics reconstruction quality；
- vertex 和角度 acceptance 稳定性；
- 在 $p_{\pi}$、$\theta_{\pi}$、$\phi_{\pi}$、$\delta$ 中的 bin migration。

第一阶段建议使用保守 fiducial 区域：

```text
|tg_th| < established limit
|tg_ph| < established limit
|tg_dp| < established limit
vertex inside target cell
```

第一版结果可先报告 fiducial acceptance-averaged cross section。等闭环稳定后，再做更细的 bin-centering 或模型依赖修正。

### Step 7：target normalization

靶归一化沿用 MARATHON PRL/supplemental analysis：

$$
N_{\mathrm{tgt}}
=
\frac{\rho L N_A}{A}.
$$

本地 `gGet_TargetInfo()` 当前包含：

```text
H1, D2, H3, He3 target areal densities
```

正式使用前需要和 PRL supplemental material 中的 target density、target length、boiling correction 逐项核对。

### Step 8：背景扣除

需要评估以下背景：

1. electron contamination after $\pi^-$ PID；
2. target-cell wall 或 dummy/empty-target contribution；
3. accidental/noise trigger contribution；
4. kaon/proton contamination；
5. 与 trigger overlap 或 rate 相关的 pile-up effect。

每一项都应明确是：

```text
subtracted
bounded
assigned as systematic
ignored with justification
```

### Step 9：radiative 和 energy-loss effect

$\pi^-$ 是末态强子，不能直接套用 electron DIS radiative correction。不过入射电子的初态辐射仍会改变有效 beam energy 和 pion production spectrum。

建议优先级：

1. 第一版先完成 detector、trigger、PID、target 和 acceptance 修正；
2. 用 Wiser-like model 或 H1 数据形状估计 incident-energy variation 对 $\pi^-$ cross section 的影响；
3. 暂时作为 systematic uncertainty，而不是完整 radiative correction；
4. 不要把该项表述为 MARATHON DIS radiative correction 的直接复用。

## 6. 最终产物

主结果：

$$
\frac{d^2\sigma_{\pi^-}}{dp_{\pi} d\Omega_{\pi}}
\quad
\text{for}
\quad
H1,\;D2,\;H3,\;He3 .
$$

推荐比值：

```text
D2 / H1
H3 / H1
He3 / H1
H3 / He3
```

后续物理扩展：

- H1 与 Wiser 或其他 inclusive pion production 参数化比较；
- 比较 nuclear dependence；
- 比较 mirror nuclei `H3` 和 `He3`；
- 在 PID、acceptance 和 contamination 控制充分后，再讨论 flavor-sensitive interpretation。

## 7. 代码结构建议

把当前单文件原型拆成清晰模块：

```text
analysis/
  PionYield.C
  TRI_RunDB.h
  TRI_Cuts.h
  TRI_PID.h
  TRI_Corrections.h
  TRI_CrossSection.h
```

推荐输出目录：

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

最终 cross-section table 建议每行包含：

```text
target, kin, arm, run_group,
p0, theta0, p_bin_low, p_bin_high,
N_raw, N_bkg, charge_C, Ne, Ntg,
LT, eps_track, eps_trigger, eps_PID, eps_survival,
phase_space, sigma_nb_per_GeV_sr,
stat_unc, sys_unc, total_unc
```

因为本分析只做 $\pi^-$，表格中不需要 `charge` 作为核心物理自由度；如果保留该列，也应固定为 `pi-`。

## 8. 第一阶段 checklist

第一阶段目标不是立刻出论文图，而是建立可复现闭环：

- [ ] 从所有 `run_lists/*.dat` 生成 `run_db.csv`；
- [ ] 列出所有 ROOT 文件存在/缺失状态；
- [ ] 确认 electron trigger 和 $\pi^-$ trigger bit；
- [ ] 逐 run 读取 prescale factors；
- [ ] 复现 MARATHON electron normalized yield；
- [ ] 画出所有 target/kin 的 $\pi^-$ PID control plots；
- [ ] 用 sideband 方法估计 electron contamination；
- [ ] 计算 $\pi^-$ live time 和 trigger efficiency；
- [ ] 先给出 H1 的第一版 $\pi^-$ cross section；
- [ ] 用 Wiser 只做 sanity check；
- [ ] 将同一 pipeline 推广到 `D2`、`H3`、`He3`。

## 9. 主要风险

1. **trigger ambiguity**：$\pi^-$ trigger number 和 prescale 必须从 run metadata 确认，不能只凭 S1/S2 文字描述假设。
2. **replay-level cuts**：如果 ROOT 文件已经在 replay 阶段筛掉了 hadron/pion event，分析会有结构性偏差。
3. **electron contamination**：GC/ECAL cut 不严或 sideband 不充分时，electron leakage 可能主导系统误差。
4. **kaon/proton contamination**：高动量处需要检查 hadron PID 分离能力。
5. **acceptance/bin-centering**：$\pi^-$ 谱可能在 HRS acceptance 内变化很快，第一版用 acceptance-averaged result 更稳妥。
6. **radiative interpretation**：electron DIS radiative correction 不能直接转移到 $\pi^-$ 产生。
7. **误差传播**：每个 correction 和 uncertainty 都应单独成列，不要隐藏在一个总 scale factor 中。

## 10. 推荐近期工作顺序

1. 建立 run database 和 ROOT 文件检查脚本。
2. 审核 trigger bit、prescale 和 replay cut。
3. 用当前 `Yield.C` 逻辑复现 electron benchmark。
4. 把 electron PID 替换为 $\pi^-$ PID，生成 cut-scan 控制图。
5. 计算 $\pi^-$ live time、trigger efficiency 和 PID efficiency。
6. 先完成 H1 的 $\pi^-$ absolute cross section。
7. 再推广到 D2、H3、He3。
8. 最后做 nuclear ratios 和物理解释。
