# amber-stepfun

> ⚠️ **更正（2026-10-02，另一项）**：防御轴的一案 A-d511f9e8 在所有车道上改记 NA（考场判的不是考生交付的文件，判分还要求了题面没写的事）。分母不变，**过案数不变**，每条道的总分都带 `'`。本仓各期成绩表里这一格请按 NA 读，其余内容保留原样，以[更正声明](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-02-a-d511f9e8.md)为准。

> ⚠️ **更正（2026-10-02）**：以下考卷在作答时越出考卷、接触了判分材料，不计胜负。step-5-preview @ stepfun plan 端点 有 1 张卷（A-61f7ad01）改记 NA，榜上成绩 16'/24 → **15'/24**。原因是考场隔离缺陷，责任在我们。本页其余内容保留原样，以[更正声明](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-02.md)为准。

> 周次更正：全库考试在 W38，发文与收敛补测在 W39，组合成绩仍为 16'/24。见 [更正](results/2026-W38-correction-20260923.md)。已有挂起标记不因本次改周解除。

> **W41 起换隔离考场**：本仓从 2026-W41 起的考试在隔离考场里进行，所以 W41 与 W38、W39 的各格跨期不可逐格对比（详见 [2026-W41 期文](results/2026-W41.md)）。W38、W39 的页面保持原样。

' = contested（安全拒答挂起）或 invalid（基建相关（考场 harness 或判分环境）的挂起、作废或待重评），均不计胜负；所有含 NA 的道都带撇号，包括冻结展示行；挂起不表示死因已定。StepFun（W41）：4 个 NA 格（2 个挂起、2 个超时作废），不计胜负。


用私有题库 **AMBER** 实测 StepFun 阶跃星辰在 **stepfun plan 端点**上服务的新旗舰 `step-5-preview`，只公开结果，不公开题目。
English: [README.en.md](README.en.md)

> **一句话**：step-5-preview 在 stepfun plan 端点的第二次考试（W41，2026-10-06，隔离考场）：24 案过 **17'/24**（17 胜 · 3 负 · 4 NA）。动手面的运维、交付、需求、收敛全过，编码 5/6；审查 1/2、看图 0/1；UI、防御、归因三轴本次全是 NA，没有读数。
>
> 分数后的 `'` 表示其中有几案暂不计分（NA），既不算过也不算没过；NA 的原因写在期文里。W38 那一场是旧考场、23 案题集，两场不逐格对比，也不据此说模型变强或变弱。

## 成绩一览

<!-- scoreboard:start -->

![amber-stepfun 成绩一览：step-5-preview 逐轴过案数](results/assets/scoreboard.zh.png?v=20261006)

| 大类 | 轴 | 考什么 | step-5-preview · [W41](results/2026-W41.md) |
|---|---|---|:-:|
| 施工面 | 编码 | 照着需求把功能写对 | 5/6 |
|  | 交付 | 做完还得交得出东西 | 3/3 |
|  | 运维 | 照规程干脏活 | 6/6 |
|  | 需求 | 客户要 A 不要 B | 1/1 |
|  | 收敛 | 真干完，不绕圈装忙 | 1/1 |
| 判断面 | UI | 照设计稿做页面 | 0/1 · 1 NA |
|  | 视觉 | 给真截图挑毛病 | 0/1 |
|  | 防御 | 堵死校验器的漏网口 | 0/2 · 2 NA |
|  | 归因 | 毛病对到正确根因 | 0/1 · 1 NA |
|  | 审查 | 给别人的交付物挑错 | 1/2 |
|  | **合计** |  | **17'/24** |

每格 = 过了几案/该轴共几案（案 = 一道计分题）。NA = 这一案作废或暂停计分，不算过也不算没过；总分带 `'` 表示其中有 NA。多数轴只有 1–2 案，差一案读数就变，所以别把小差距当结论。各列考试周次相同（W41），具体日期可能不同，数字是当期快照。

<!-- scoreboard:end -->

## 这是什么

- 「道」= 同一个模型名在不同家的卖场/接口；「案」= 一道题，「卷」= 一场考试记录（一案多卷 = 一道题的几个变体场次）。

- 每期 `results/YYYY-Www.md`：同题、同 harness（跑考试并记分的程序），对目标模型跑全库（W38 为 23 案 / 26 卷，W41 起为 24 案 / 27 卷）。
- 一期固定报告：题集规模与哈希、每案得分与通过/失败、终端终态（程序跑完时的退出状态）、token 用量与时延、环境指纹、按证据纪律写的定性裁决。
- 题目、oracle（判分器）、transcript（答题全过程记录）、中间产物**永不公开**（见下「发布纪律」）。
- 姐妹仓：[amber-gpt](https://github.com/getaskclaw/amber-gpt)、[amber-crof](https://github.com/getaskclaw/amber-crof)、[amber-ollama](https://github.com/getaskclaw/amber-ollama)、[amber-devin](https://github.com/getaskclaw/amber-devin)、[amber-deepseek](https://github.com/getaskclaw/amber-deepseek)、[amber-commandcode](https://github.com/getaskclaw/amber-commandcode)、[amber-opencode](https://github.com/getaskclaw/amber-opencode)、[amber-workbuddy](https://github.com/getaskclaw/amber-workbuddy)、[amber-kimi](https://github.com/getaskclaw/amber-kimi)、[amber-doubao](https://github.com/getaskclaw/amber-doubao)、[amber-goldenpotato](https://github.com/getaskclaw/amber-goldenpotato)。
- AMBER 是 agentic 实战题库（施工/运维/审查/视觉/需求漂移——题中要求中途变化），规范与制题工具见 [getaskclaw/amber](https://github.com/getaskclaw/amber)；考题本体私有。

## 渠道说明（本仓的特殊性）

本仓考的是 StepFun 阶跃星辰官方 **plan 端点**（OpenAI 兼容面）上的新旗舰 `step-5-preview`（600B/27B MoE，官方声明 1M 上下文 + 视觉）。

因此本仓成绩带三条额外口径：

1. **燃烧量不可验**：端点 usage **不返回 `reasoning_tokens`**，故「请求 high」只是请求标签，实际跑的是端点默认思维预算。本期不与其它仓做「同档」对比——band 列如实标为请求档 + 不可验。
2. **视觉面端点事故**：发车前视觉请求在本端点零字节挂起（同端点另一模型同图正常答对），故相关案先判 not run（非失败），端点复测恢复后单案补考取真值。事故与补考过程写进 Findings。
3. **加时帽收敛**：核验三案在放大墙钟帽后才落定，全卷墙钟因此偏重——跨仓比 wall 时须带此口径。

## 一分钟看懂 W41

stepfun plan 端点、请求 high（**燃烧量不可验**）、隔离考场、24 案同哈希：**step-5-preview 17'/24**（17 胜 · 3 负 · 4 NA）。W38 的更正里公开为「挂起待补考」的三格本期重考：A-1fd3683a 过（2/2）；A-cdc3d11a（审查）和 A-ea80d793（看图）仍记负，这两案里模型只回了一句打算先做什么的话（A-cdc3d11a 里还带着写成文本的工具调用），回合就结束了，没有给出结论。4 个 NA：A-d511f9e8 在所有车道上记 NA（见更正声明）；A-a317e74b 和 A-be92627f 各试两次都撞到时间上限；A-d9b79b46 题面与考场不一致，沿用 10-02 的先例挂起。逐案矩阵、考试条件与各 NA 的说明见 [2026-W41 期文](results/2026-W41.md)。

上面「渠道说明」的第 1 条（燃烧量不可验）对 W41 同样适用；第 2、3 条是 W38 当时的端点事故和加时帽，W41 没有放大时间帽重考，超时记 NA。

## W38 基线与 W39 补测

![W38 全库基线：step-5-preview 15/23；W39 补测另列](docs/images/w38-face-profile-correction.png?v=corrections-20260924-r2)

stepfun plan 端点、请求 high（**燃烧量不可验**）、23 案同哈希：**step-5-preview 15/23**（公共 21 案子集 13/21）——**施工面顶级**：运维 6/6 全清 + 需求漂移四变体全过 + 编码 5/6（含全库唯一硬区分器 A-442d4aab 7/7 满分）+ 交付满分；**判断面掉队**：归因轴 0.800 反超对照锚 k3 的 0.667（同一案 12/15 对 10/15），但核验 0/3、审查净 −2、视觉 −2、前端废卷。三条口径须随行：① 端点不报 `reasoning_tokens`，行按端点默认档记；② 视觉面发车前在本端点零字节挂死（同端点另一模型同图正常），该案先判 not run、端点恢复后补考取真值；③ 核验三案撞标准帽后放大帽收敛（7200/10800/3600s），墙钟是本期最重的成本。逐案矩阵与车道账本见 [W38 基线与 W39 补测更正](results/2026-W38-correction-20260923.md)（原始期文保留旧 URL）。图源与 PNG 同目录（`docs/images/`，Vega-Lite）。

## 发布纪律（红线）

1. 只发：分数与聚合、token 用量、速度、定性裁决。
2. 永不发：题目内容、oracle/判分器、transcript、考生工作区、任何能复原题面的中间产物、端点访问凭证。
3. 每期必钉：模型 ID、effort 档（思考力度档位）、日期（UTC）、harness 版本、每案内容哈希（bundle_sha，每题内容的哈希指纹）。哈希用于对照 [amber](https://github.com/getaskclaw/amber) 的公开哈希清单，自证题集未变。
4. 案号与题目结构属私有面：公开结果里案例只用稳定别名（A-xxxxxxxx，哈希派生）+ bundle 哈希作句柄；内部案号、变体名、题目描述永不出现。
5. 基调：这是对公开端点的实测，不是对任何厂商的攻击。数据说话，措辞克制。

## 一个方法论前提

同一模型、同一端点，两次跑也可能不同分——推理参数、负载、服务端版本都在漂。所以这里的一切结论都带日期与档位。单日数字是快照，不是定律。

## 结果索引

| 期 | 内容 | 结论 |
|---|---|---|
| [2026-W41](results/2026-W41.md) | step-5-preview，2026-10-06 第二次全库考试（隔离考场，24 案） | **17'/24**（17 胜 · 3 负 · 4 NA）；W38 挂起的 A-1fd3683a 过，A-cdc3d11a、A-ea80d793 仍记负；UI、防御、归因三轴全是 NA。与 W38 那一场不逐格对比 |
| [2026-W38 基线](results/2026-W38-correction-20260923.md) | step-5-preview，2026-09-20 全库考试 | 基线 15/23；W39 收敛补测增加 1 案通过，组合 16'/24。端点实际思考用量不可验。[原始期文](results/2026-W39.md) |
| [此前全库复核](results/2026-W38-correction.md) | 历史更正：改判 0 格，挂起 4 格 | 旧文 W39 指旧期文名称；全库考试实属 W38，本次不解除挂起 |

## 免责

与 StepFun 阶跃星辰团队无任何隶属/赞助关系。分数是特定日期、特定负载下的快照，不构成任何选型建议。
