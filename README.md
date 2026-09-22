# amber-stepfun

用私有题库 **AMBER** 实测 StepFun 阶跃星辰在 **stepfun plan 端点**上服务的新旗舰 `step-5-preview`，只公开结果，不公开题目。
English: [README.en.md](README.en.md)

## 这是什么

- 「道」= 同一个模型名在不同家的卖场/接口；「案」= 一道题，「卷」= 一场考试记录（一案多卷 = 一道题的几个变体场次）。

- 每期 `results/YYYY-Www.md`：同题、同 harness（跑考试并记分的程序），对目标模型跑全库（23 案 / 26 卷）。
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

## 一分钟看懂 W39

![W39 首考画像：step-5-preview 15/23，施工满格、判断面掉队](docs/images/w39-face-profile.png?v=20260921)

stepfun plan 端点、请求 high（**燃烧量不可验**）、23 案同哈希：**step-5-preview 15/23**（公共 21 案子集 13/21）——**施工面顶级**：运维 6/6 全清 + 需求漂移四变体全过 + 编码 5/6（含全库唯一硬区分器 A-442d4aab 7/7 满分）+ 交付满分；**判断面掉队**：归因轴 0.800 反超对照锚 k3 的 0.667（同一案 12/15 对 10/15），但核验 0/3、审查净 −2、视觉 −2、前端废卷。三条口径须随行：① 端点不报 `reasoning_tokens`，行按端点默认档记；② 视觉面发车前在本端点零字节挂死（同端点另一模型同图正常），该案先判 not run、端点恢复后补考取真值；③ 核验三案撞标准帽后放大帽收敛（7200/10800/3600s），墙钟是本期最重的成本。逐案矩阵与车道账本见 [2026-W39 期文](results/2026-W39.md)。图源与 PNG 同目录（`docs/images/`，Vega-Lite）。

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
| [2026-W39](results/2026-W39.md) | step-5-preview @ stepfun plan 端点 全库首考 | 案级 15/23；运维 6/6、需求四变体、编码 5/6（含硬区分器满分）、交付满分；归因轴胜对照锚；审查半、核验 0/3、视觉 −2、前端废卷；端点不报 reasoning burn |
| [2026-W38 更正特刊](results/2026-W38-correction.md) | W38 全库复核:本仓改判 0 格 · 挂起 4 格 | W39 首考矩阵 4 格挂起;若平反 15/23 可能上移 |

## 免责

与 StepFun 阶跃星辰团队无任何隶属/赞助关系。分数是特定日期、特定负载下的快照，不构成任何选型建议。
