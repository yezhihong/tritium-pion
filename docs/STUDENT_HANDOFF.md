# Tritium / MARATHON Single Pion Analysis 学生交接说明

更新日期：2026-07-13

这份文档是给接手学生和他的 Codex 使用的入口文件。目标不是替代正式笔记，而是把当前关于 MARATHON tritium single pion production cross-section 的物理动机、已有材料、分析计划、初步结果解读和下一步工作集中在一个地方，避免重新从零梳理。

## 1. 接手后先读哪些文件

建议按以下顺序阅读：

1. `docs/single_pion_physics_goals.md`
   - 物理目标和意义。
   - 重点理解 Qiu 报告、Afanasev-Carlson 早期工作、soft/VMD、fragmentation、direct/higher-twist pion 的机制分解。

2. `docs/single_pion_cross_section_strategy.md`
   - 分析计划和技术路线。
   - 重点理解哪些 MARATHON electron DIS 链条可以复用，哪些必须为 pion 重新建立。

3. `docs/pdf/single_pion_physics_motivation_zh.pdf`
   - 上述 physics motivation 的中文版 PDF。

4. `docs/pdf/single_pion_analysis_plan_zh.pdf`
   - 上述 analysis plan 的中文版 PDF。

5. `docs/figures/pion_xs_plot1.png` 和 `docs/figures/pion_xs_plot2.png`
   - 早期提取的 single pion cross-section 和 Wiser/model 比较图。
   - 最终结果预计不会与这些初步结果有本质差别，后续分析应围绕系统误差、可复现性和物理解释增强。

6. `analysis/`
   - 已有分析代码入口。
   - 特别关注 `Yield.C`、`TRI_Beam.h`、`TRI_Target.h`、`TRI_LiveTime.C`、`TRI_Tools.h`、`wiser_all_sig.f`、`yield_plot.ipynb`。

7. `run_lists/`
   - H1、D2、H3、He3 各 kinematic setting 的 run list。

8. `references/`
   - 本地参考文献与报告。
   - Qiu 报告：`references/qiu_reports/SoLID_ANL_Qiu.pdf`、`references/qiu_reports/SoLID2025July_Qiu.pdf`。
   - Afanasev-Carlson 早期论文：`references/papers/PhysRevD.61.034014.pdf`、`references/papers/1-s2.0-S037594740301176X-main.pdf`、`references/papers/0212376v1.pdf` 等。
   - MARATHON PRL 和 supplemental files。

## 2. 飞书 Wiki 页面

已把两份 Markdown 上传为真正的飞书 Wiki pages，而不是普通附件。

目标知识空间：

- `Single Pion Production from A=3`

新建页面：

- MARATHON 单 pion 产生截面研究的物理目标与意义  
  https://tmeg-thu.feishu.cn/wiki/VTJ8w96vSi9BXGk9nSdcDzlynvd

- MARATHON 包含式单负 pion 产生截面分析策略  
  https://tmeg-thu.feishu.cn/wiki/If5twuc11i4JdSkvk9LcmN3Anad

上传时已做飞书 Markdown 兼容处理：原始块公式 `$$...$$` 先转换为飞书可识别的 `<latex>...</latex>` 写入，回读验证后公式被飞书恢复为标准公式块。后续若再次用 Codex 更新飞书文档，注意不要直接把复杂 LaTeX 块、尖括号或代码片段未经检查地写入飞书 Markdown。

## 3. 当前物理故事线

这项工作不应被定位为 MARATHON electron DIS 的副产品。更准确的定位是：

MARATHON 的包含式单负 pion 数据提供了同一束流、同一 HRS、同一低温靶系统下 `H1`、`D2`、`H3`、`He3` 的绝对 pion 截面和靶比值，可用于检验 JLab 12 GeV 固定靶能区末态 pion 的产生机制。

核心问题是：

- observed leading pion 到底主要来自 struck parton fragmentation？
- 还是有显著 soft/VMD photoproduction、vector-meson decay、direct/higher-twist isolated pion、semi-exclusive dynamics？
- A=3 mirror nuclei 中的 `H3/He3` 比值是否显示出 isospin/nuclear dependence？

这个问题是 SIDIS/TMD pion observables 的前置约束。如果 single pion 截面本身不能被简单 fragmentation picture 描述，后续用 pion 数据抽取 TMD、FF 或 spin asymmetry 时就必须引入机制系统误差。

## 4. 初步图的物理解读

`docs/figures/pion_xs_plot1.png`：

- 上图是早期提取的 `D2`、`H3`、`He3` single pion cross-section 随 `P_T` 的变化，并与 Wiser fit 比较。
- 下图给出 `sigma_Wiser / sigma_Data`。
- 主要现象：Wiser/Data 从低 `P_T` 的约 `1.5-2.2` 系统下降到高 `P_T` 的小于 1。
- 物理含义：Wiser 在低动量端偏高，在高动量端偏低，真实数据的 `P_T` 谱比 Wiser 更硬。
- 这不是单一 normalization factor 能解决的问题，而是模型形状或机制分解的问题。

`docs/figures/pion_xs_plot2.png`：

- 上图是早期 cross-section 与一个 model 的比较。
- 下图是 `sigma_data / sigma_model` 随 `x_bj` 的变化。
- 主要现象：低到中等 `x_bj` 区域模型接近数据；高 `x_bj` 区域数据/模型显著下降。
- 物理含义：模型在 high-x 或 endpoint 区域失效，可能反映相空间、radiative smearing、acceptance/bin-centering、nuclear attenuation、FSI 或机制分解不足。

稳妥表述：

- Wiser/model 能抓住量级，但不能完整描述 `P_T` 和 `x_bj` 依赖。
- 数据比简单 soft empirical model 更硬，提示高 `P_T` 区域可能有 prompt fragmentation、direct/higher-twist pion 或 semi-exclusive dynamics 的贡献。
- A=3 mirror-nuclei 比较有潜力成为轻核 pion production 的新基准，但不要在没有系统误差和背景控制前直接宣称 flavor separation。

## 5. 分析目标

第一阶段主结果：

```text
d^2 sigma_pi- / (d p_pi d Omega_pi)
for H1, D2, H3, He3
```

推荐给出的比值：

```text
D2 / H1
H3 / H1
He3 / H1
H3 / He3
H3 / D2
He3 / D2
```

第一阶段应强调：

- 绝对截面；
- target ratios；
- PID、trigger、tracking、acceptance、target normalization 的系统误差；
- electron leakage、kaon/proton contamination、target-window background；
- Wiser/model 只能作为 sanity check 和 soft-source baseline；
- 第一版可报告 fiducial acceptance averaged cross section。

第二阶段再讨论：

- NLO `lN -> hX` / fragmentation comparison；
- VMD/soft、direct/higher-twist mechanism map；
- non-prompt pion 与 vector-meson decay；
- QCD+QED radiative smearing；
- A=3 mirror nuclei 的 nuclear/isospin dependence。

## 6. 分析技术路线

必须先建立 run database：

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

建议输出：

```text
output/single_pion/run_db.csv
output/single_pion/run_quality.csv
output/single_pion/run_exclusions.csv
```

分析步骤：

1. 检查 run lists 和 ROOT/replay 文件是否完整。
2. 确认 replay 是否已经筛掉 hadron/pion events。
3. 确认 pion trigger bit、prescale 和 raw scaler branch。
4. 用当前代码链复现 MARATHON electron normalized yield，验证 normalization chain。
5. 定义 pion event sample：good track、pion trigger、GC anti-electron cut、MIP-like ECAL band、target vertex、HRS fiducial cuts。
6. 用 cut scan 和 sideband 方法估计 PID efficiency 与 electron contamination。
7. 计算 pion live time、trigger efficiency、tracking efficiency。
8. 做 target normalization、dummy/window subtraction、background subtraction。
9. 先给出 H1 absolute cross section，再推广到 D2/H3/He3。
10. 生成 target ratios 和系统误差表。
11. 最后做 Wiser/model comparison 与 physics interpretation。

## 7. 不要踩的坑

- 不要把结果称为 electron DIS cross section；它是末态 `pi-` 的包含式产生截面。
- 不要直接套用 electron DIS radiative correction。
- 不要在没有 non-prompt pion 和 electron leakage 估计前宣称验证了 fragmentation picture。
- 不要只用 leading-twist fragmentation 解释所有高动量 pion。
- 如果没有 coincidence electron，不能逐事件重建 `Q^2`、`x_B` 或 photon virtuality。
- `H3/He3` 差异不能直接解释成 flavor separation；必须先控制 nuclear effect、acceptance、PID、FSI 和 charge-exchange/feed-down。
- 如果 HRS acceptance 内 pion 谱变化快，第一版不要做过细 binning；先报告 acceptance averaged result。

## 8. 给学生使用 Codex 的建议

学生可以在这个 workspace 下启动 Codex，然后先给 Codex 下面这段 prompt：

```text
请先阅读 docs/STUDENT_HANDOFF.md、docs/single_pion_physics_goals.md、
docs/single_pion_cross_section_strategy.md、analysis/Yield.C、
analysis/TRI_Beam.h、analysis/TRI_Target.h、
analysis/TRI_LiveTime.C、run_lists/*.dat。

目标是继续 MARATHON tritium single pi- production cross-section 分析。
请先建立 run database 和 replay/data-quality 检查方案，不要直接改物理结论。
所有结论要区分：已由数据支持、模型解释、待验证假设。
```

如果学生要更新飞书页面，让 Codex 使用 lark-doc/lark-wiki 工作流，并注意飞书 Markdown 对公式的特殊处理：复杂块公式优先写成飞书 `<latex>...</latex>` 或先在本地生成 `.lark.md` 中间文件再上传。

## 9. 建议的近期任务清单

- [ ] 建立 `output/single_pion/run_db.csv`。
- [ ] 检查所有 run list 对应 ROOT 文件和 replay version。
- [ ] 确认每个 run 的 electron trigger 和 pion trigger bit。
- [ ] 确认 prescale factors 和 raw scaler branch。
- [ ] 复现 electron benchmark normalized yield。
- [ ] 画出每个 target/kin 的 GC vs E/p、E/p vs momentum、vertex、trigger overlap 控制图。
- [ ] 定义第一版 pion PID cut。
- [ ] 估计 PID efficiency 和 electron leakage。
- [ ] 计算 pion live time 和 trigger efficiency。
- [ ] 先完成 H1 的第一版 cross section。
- [ ] 推广到 D2、H3、He3。
- [ ] 生成 target ratios 和 Wiser/model comparison plots。
- [ ] 写出系统误差表和最终 physics interpretation。

## 10. 当前应保留的核心结论

当前最有价值的结论不是“Wiser 不对”，而是：

1. Wiser/model 作为经验 soft baseline 能描述大致量级，但不能同时描述 `P_T` 与 `x_bj` 形状。
2. 数据表现出比 Wiser 更硬的 `P_T` spectrum，提示 soft/VMD 之外的机制可能重要。
3. 高 `x_bj` 区域模型明显失效，是最有物理信息、也最需要系统误差控制的区域。
4. A=3 mirror nuclei 提供了少见的 `H3/He3` pion production 基准，应作为 MARATHON 的独特贡献来组织结果。
5. 最终论文或报告应把结果定位为 JLab 固定靶能区 single pion production mechanism benchmark，而不是单纯 FF 校准或 electron DIS 副产品。
