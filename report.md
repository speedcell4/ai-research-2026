# 2026 AI 研究全景扫描

**时间窗口**: 2025 年 10 月 → 2026 年 10 月（完整一年；覆盖 ICLR 2026、ICML 2026、NeurIPS 2025/2026、CVPR 2026、ACL/EMNLP 2025-26、CoRL 2025）

**生成时间**: 2026-10-03

**数据来源**: arXiv（主题语料 + 327 篇 AI 综述）、OpenAlex、Hugging Face Daily Papers（全年版）、papercopilot / OpenReview（ICLR 2024-26、NeurIPS 2024-25、ICML 2024-26、CVPR 2025-26、ACL 2024-25、CoRL 2025）、会议官方博客与奖项页、9 个并行深读子代理 + 数十篇全文精读

---

## 快速上手（3 分钟）

> **三句话读完这一年**
>
> 1. 研究重心从"造更强的模型"转向**"把模型组织成可靠、可演化的系统"**——agent 的编排、记忆、环境和验证器，比模型参数更重要。
> 2. 增长最快的技术线是 **RL 后训练 + on-policy distillation**；而 **RLHF 正在被 RLVR（可验证奖励）取代**。
> 3. 最大的共同瓶颈是**验证**：agent RL、RSI、自动科研、乃至学术评审本身，都卡在"我们凭什么相信这个结果是好的"。

**三个核心判断：**

| 关键议题 | 结论 | 一句话 |
|---|---|---|
| long-horizon agent RL | ✅ **最大主线** | ICLR 推理 / agent 占比翻倍；arXiv 增速榜前十有七席是 agent 基础设施 |
| RSI（递归自我改进） | ✅ **最热新叙事，但没有复利** | harness 层真闭环；AIDE² 的 ignition test 是负结果 |
| 长文本 / long context | ⚠️ **换了形态** | 1M 成标配、单针解决；战场移到 memory / compaction / 多轮可靠性 |

**只记五件事：**

1. **Agent harness 是新物种**（Raven / StateM / HarnessDev / DarwinX …）—— 见 3.5
2. **RLHF → RLVR 换轨**：RLHF **-40%**，而 verifiable reward **+205%** —— 见 2.3
3. **RSI 工程强、判断弱**：AI4AI-Bench 290 次提交有 124 次更差 —— 见 3.7
4. **评估危机是公共瓶颈**：ICML 795 条 AI 评审；"28.2% 由 AI 撰写"换个窗口就掉到 2.16% —— 见 3.19
5. **"好看 ≠ 有能力"**：83% 生成视频有物理错误；LIBERO 可被 0.09B 探针解出 —— 见 3.11 / 3.13

**一页纸数字（细节见第 2 节）**

- ICLR 2026：19,525 投稿 / 5,355 接收（**27.4%**）/ 223 oral；ICML 2026 投稿 23,918
- ICLR 2025→2026：Reasoning **5.0%→12.0%**、RL **9.4%→12.8%**、Agents **5.1%→8.3%**
- arXiv 同比：OPD **+1284%**、verifiable reward **+205%**、GRPO **+114%**、**RLHF -40%**
- HF 全年 **8,511 篇**；AI 综述 **327 篇**；Agents' Last Exam 最难层通过率 **<1%**
- 临床 AI 最有力的证据是一个 **n=93,326 的阴性 RCT**（LungIMPACT）

## 板块导航（按热度排序；章节号见左侧目录）

| 热度 | 板块 | 一句话 | 章节 |
|---|---|---|---|
| 🔥🔥🔥 | Agent 系统 / harness / skills | 冻结模型 + 可演化执行系统，是今年最有辨识度的新概念 | 3.5 |
| 🔥🔥🔥 | On-policy distillation | 唯一 +1000% 级主题，也最被低估 | 3.3 |
| 🔥🔥🔥 | 后训练与 RL | 主战场；但 GRPO 不是万能药，奖励设计才是核心 | 3.2 |
| 🔥🔥🔥 | Agentic RL / 长时程训练 | 配方是一整套 stack，环境/验证器比算法更关键 | 3.6 |
| 🔥🔥🔥 | RSI / 自改进 / 自动科研 | 真闭环，但没有任何复利加速的证据 | 3.7 |
| 🔥🔥🔥 | 评估 / 基准 / 元科学 | 整个领域的公共瓶颈，已蔓延到科研系统自身 | 3.19 |
| 🔥🔥🔥 | 生成媒体（视频/音频/音乐） | 最热也最需怀疑：几乎无同行评审，且自己的评测在打假 | 3.11 |
| 🔥🔥🔥 | 多模态 / 视觉 | 统一理解+生成成默认框架；视觉原语仍是瓶颈 | 3.10 |
| 🔥🔥🔥 | 具身 / 机器人 / 自驾 | 能力在整合，评测在崩塌 | 3.13 |
| 🔥🔥🔥 | 生成建模 / 扩散 LLM | 除 agent 外最大的能力变量，同时在自我纠偏 | 3.14 |
| 🔥🔥🔥 | 效率 / 系统 / 推理服务 | 从"一个技巧"变成"架构本身" | 3.16 |
| 🔥🔥🔥 | 世界模型 | 从"生成得像"到"可交互可编程"，同时被自己人证伪 | 3.12 |
| 🔥🔥🔥 | AI for Science / 医学 / 数学 | 形式化数学最干净；临床最有力证据是阴性 RCT | 3.20 |
| 🔥🔥 | 推理 / test-time compute | 占比翻倍，但"想更久"未必更好，pass@1 会高估 | 3.4 |
| 🔥🔥 | 长上下文 / memory / compaction | 不是变冷，是转向 memory / compaction / 多轮可靠性 | 3.8 |
| 🔥🔥 | 架构（MoE / SSM / 线性注意力） | 不是取代 Transformer，而是混合化 | 3.15 |
| 🔥🔥 | 安全 / 对齐 / 隐私 / 治理 | 方法在收敛、评测在证伪——今年主要发现我们高估了安全性 | 3.18 |
| 🔥🔥 | 可解释性 | 从"找到特征"到"验证特征能不能用" | 3.17 |
| 🔥🔥 | 检索 / RAG / 知识 | 已基础设施化，增量在安全与效率 | 3.9 |
| 🔥🔥 | 数据 / 持续学习 / 理论 | 数据成为一等公民，"数据选择"变成理论 | 3.22 |
| 🔥🔥 | 综述地图与"学科化" | 327 篇综述是学科化信号，也是"我们测不了 X"的焦虑 | 3.23 |
| 🔥🔥 | 基础模型与预训练 | 规模仍在，但"效率 / 配方"取代了"更大" | 3.1 |
| 🔥 | 非 LLM ML | 不在聚光灯下，唯一真热点是表格基础模型 | 3.21 |
| — | 补遗：神经/BCI、量子、kernel/GP/bandit、教育/医疗/社会模拟、MCP 工具投毒、模型编辑与合并、3D/图形 | 主线之外、但稳定产出且容易漏 | 3.24 |

## 怎么读这份报告

- **只有 3 分钟**：读完本页即可（三句话 + 三个问题 + 五件事 + 一页纸数字）。
- **有 30 分钟**：读 **第 2 节（定量全景）** + **3.1–3.7（主线）** + **第 5 节（全局判断）**。
- **要全量**：按 1 → 6 顺序。每一节都是 **"发生了什么 / 关键证据 / 代表工作 / 需要保留的怀疑"** 四段式，可单独跳读。
- **只要论文清单**：直接跳 **第 4 节（重点论文总表）**。
- **想看原始深读**：notes/ 下有 9 份分领域长文（每份 20–42KB），本报告是它们的综合。

---


---

## 1. 我看了什么（方法与数据）

为了做到"全面"而不是"我觉得"，这一轮建了下列数据：

- **会议论文全量元数据**（papercopilot / OpenReview 镜像）：ICLR 2024（7,402）、ICLR 2025（11,669）、**ICLR 2026（19,809）**、NeurIPS 2024（4,238）、**NeurIPS 2025（5,898）**、ICML 2024（2,610）、ICML 2025（3,939）、ICML 2026（418，官方尚未全量收录）、CVPR 2025（3,062）、CVPR 2026（241，未全量）、ACL 2024/2025（1,923 / 3,203）、CoRL 2025（263）。每条含标题、摘要、关键词、评分、状态。
- **OpenAlex 主题计数**（2026-04→09 vs 2025-10→2026-03，约 30 个主题；OpenAlex 免费日额度用尽后转用 arXiv）。
- **arXiv 主题语料**：约 100 个主题 × 最近 60 篇（2025-10→2026-10），含标题与摘要，用于给每个子领域取样。
- **arXiv 综述语料**：标题含 survey/review/overview 的论文，筛出 **327 篇 AI/ML 综述**并逐一读标题+摘要。
- **Hugging Face Daily Papers 全年版**：2025-10-01→2026-10-02 逐日抓取，含 upvotes、AI 关键词、摘要。
- **9 个并行深读子代理**：RSI、长上下文、agentic RL、会议格局、其他前沿，以及本轮新增的视觉多模态、音视频生成、效率系统、架构与理论、安全与可解释、AI4Science、具身机器人、非 LLM ML。
- **全文精读**：多轮对话最佳论文、on-policy distillation scaling、RRSI、以及若干综述（Self-Improving Test-Time Intelligence、Safety in Self-Evolving Agents、Unsupervised Post-Training、Rubric-Guided RL、Agentic Skills 等）。

**局限（先说在前面）**：
- OpenAlex 对最近半年的索引滞后约 11%，且其免费额度当天用尽，因此年度同比主要由会议数据与 arXiv 计数承担。
- HF Daily Papers 衡量的是**社区注意力**，偏向大厂模型报告与吸睛工作。
- **ICML 2026 / NeurIPS 2026 的完整接收列表尚未公开**（PMLR 未出卷、官网 403），这两会只能用官方奖项与公开新闻补足；ICML/ACL 2024 的关键词数据缺失，无法做同比。
- 关键词统计有措辞偏差；本报告用"多源三角验证"降低单点误差。

---

## 2. 定量全景

### 2.1 会议规模：吞吐量在爆炸，接收率没变

| 会议 | 投稿 / 记录 | 接收 | 接收率 | Oral |
|---|---|---|---|---|
| ICLR 2026 | 19,525（有效） | 5,355 | **27.4%** | 223（无 Spotlight） |
| ICLR 2025 | ~11,600 | 3,703 | ~32% | 213 |
| NeurIPS 2025 | — | 5,898 | ~24% | 78 |
| NeurIPS 2024 | — | 4,238 | ~25% | — |
| ICML 2026 | 23,918 | 6,352 | **26.6%** | ~168（+536 spotlight） |
| ICML 2025 | — | 3,939 | — | — |
| CVPR 2025 | — | 3,062 | — | — |

**读数**：接收率稳定在 25–27%，但 ICLR 投稿一年涨了约 70%、ICML 投稿超过 23,000（几乎是 2025 的两倍）。**领域不是在"变难"，而是在"变多"。**

### 2.2 同一会议跨年对比（本报告最硬的证据）

同一个会议、隔一年、同一套关键词口径——这能最大程度剔除"用词变化"的噪声。

{{CHART:iclr_themes}}

**ICLR 2025 → 2026（接收论文主题占比）**

| 主题 | 2025 | 2026 | 变化 |
|---|---|---|---|
| Reasoning / test-time compute | 5.0% | 12.0% | **+7.0** |
| LLMs / foundation models | 32.6% | 36.2% | +3.6 |
| Reinforcement learning | 9.4% | 12.8% | **+3.4** |
| Agents | 5.1% | 8.3% | **+3.2** |
| Vision / multimodal | 21.6% | 23.7% | +2.1 |
| Efficiency / systems | 12.3% | 13.2% | +0.9 |
| Safety / alignment / privacy | 10.9% | 10.5% | -0.4 |
| Diffusion / generative | 14.1% | 13.0% | -1.1 |
| Graph / geometric | 7.2% | 5.6% | -1.6 |
| Learning theory / optimization | 11.8% | 9.8% | -2.0 |

**NeurIPS 2024 → 2025** 给出了几乎一样的结论：Reasoning **2.8% → 7.6%（+4.8）**、LLMs 22.3% → 26.0%（+3.7）、Agents 3.4% → 5.1%（+1.7）、Robotics +1.3；而 Learning theory **-2.7**、Graph **-1.2**、Safety **-1.3**、Diffusion -0.9。

{{CHART:yoy_nips}}

**ICML 2024 → 2025 → 2026**（用 PMLR 官方论文**标题**统计；标题口径数值偏低，但趋势可比）：Reasoning/test-time **2.1% → 5.1% → 9.1%**（一年翻两番）、Agents **2.8% → 4.1% → 7.8%**、Vision **10.0% → 12.3% → 16.1%**、Efficiency 12.1%→13.1%→13.7%；而 Learning theory **9.8% → 9.8% → 7.8%**、Diffusion 6.7%→8.8%→8.6%（停滞）。

{{CHART:yoy_icml}}

**CVPR 2025 → 2026**（CVPR Open Access 标题）：Reasoning **2.4% → 7.5%**、Robotics **5.7% → 7.2%**、Graph +1.4；而 Diffusion **14.4% → 10.9%（-3.5）**、纯视觉占比 60.6% → 58.6%。

{{CHART:yoy_cvpr}}

**四个会议、同一故事**：推理/测试时计算翻倍以上，RL 与 Agent 扩张，纯理论/图学习/扩散退潮。这不是我的叙事，而是 **ICLR + NeurIPS（关键词口径）+ ICML + CVPR（标题口径）四组独立统计**指向的同一方向。

### 2.3 arXiv 主题同比（2025-10 → 2026-09 vs 2024-10 → 2025-09）

{{CHART:arxiv_growth}}

口径说明：先用 arXiv API 统计每个主题在摘要中出现的论文数，再除以同期 cs.LG/CL/AI/CV 的论文总量做"份额归一化"。基准是 **cs.LG+CL+AI+CV 论文数从 102,553 涨到 130,345（+27%）**——也就是说，**归一化后为 0 的主题，其绝对量其实涨了 27%；为负的主题才是真正在萎缩。**

**增量注意力流向（份额归一化增速）：**

| 主题 | 增速 | 主题 | 增速 |
|---|---|---|---|
| on-policy distillation | **+1284%** | LLM agent | +156% |
| agent memory | **+879%** | flow matching | +145% |
| self-evolving agent | **+823%** | KV cache | +126% |
| recursive self-improvement | **+795%** | GRPO | +114% |
| diffusion language model | +391% | LLM serving | +101% |
| agent benchmark | +378% | AI for science | +83% |
| context engineering | +372% | speculative decoding | +74% |
| vision-language-action (VLA) | +358% | GUI agent | +64% |
| computer use agent | +266% | | |
| software engineering agent | +215% | | |
| verifiable reward | +205% | | |
| tool use | +194% | | |
| automated research | +190% | | |
| world model | +190% | | |
| model context protocol (MCP) | +165% | | |

**真正在萎缩的（份额归一化为负）**：RLHF **-40%**、protein structure -38%、federated learning -36%、meta learning -33%、drug discovery -32%、recommender system -31%、image generation -31%、in-context learning -30%。

**三个最重要的读数：**
1. **榜首全是 agent 的系统层**：agent memory、self-evolving agent、RSI、agent benchmark、context engineering、VLA、computer use、SE agent、tool use、MCP——**前十里有七个是"agent 基础设施"**，而不是模型能力。
2. **RLHF 让位于 RLVR**：reinforcement learning from human feedback **-40%**，而 verifiable reward **+205%**、GRPO **+114%**。**人类反馈这条线正在被"可验证奖励"取代**——这是这一年后训练最重要的结构变化之一。
3. **on-policy distillation 是唯一 +1000% 级别的主题**，与 3.3 的判断一致；而 image generation、protein structure、recommender system 这些成熟赛道的相对注意力在下滑，**不是因为它们不重要，而是因为领域注意力被 agent 系统吸走了。**

### 2.4 社区注意力（Hugging Face Daily Papers，全年版）

{{CHART:hf_monthly}}

{{CHART:hf_keywords}}

本轮的 HF 全年版覆盖 **2025-10-01 → 2026-10-02 共 366 天、8,511 篇唯一论文**（含 upvote 与 AI 关键词）。HF 的 upvote 反映的是"开发者/研究者最想点开什么"。一年维度上最稳定的高频关键词是：**reinforcement learning、large language models、vision-language models、multimodal LLMs、supervised fine-tuning、GRPO、on-policy distillation、diffusion、LLM agents、VLA、MoE、world models**。值得注意的是 **on-policy distillation / self-distillation 合计约 150 篇**（半年版口径），以及 **reward hacking、catastrophic forgetting、continual learning** 这些"问题诊断"类关键词的上升。

### 2.5 综述地图：327 篇 AI 综述告诉我们的"学科地图"

把所有 327 篇综述按主题归类后（完整列表见 [notes/survey-map.md](notes/survey-map.md)）：

| 板块 | 综述数（我的归类） | 代表性综述 |
|---|---|---|
| Agents & tool use | 56 | A Systematic Survey of Agentic Skills；Efficient GUI Agents；Trustworthy Agentic AI |
| Long context / memory / RAG | 57 | Self-Improving Test-Time Intelligence；Retrieved But Not Reliable (RAG 安全) |
| Multimodal & vision | 41 | Agentic Video Understanding；Efficient Multimodal Learning；End-to-End Autonomous Driving |
| Efficiency & systems | 24 | Why Is Video Still So Expensive?；Quantization-Aware Training；Transformer Inference on FPGA |
| Reasoning & test-time | 18 | Self-Improving Test-Time Intelligence；Rubric-Guided RL |
| AI for science & medicine | 16 | LLMs in Mental Health；BioASQ 2026；Scientific Workflow |
| Evaluation & benchmarks | 15 | Benchmark Radar；SurveyReview |
| Privacy / fairness / federated | 12 | Collaborative Learning on Graphs；Fake Review Detection |
| Graph / time series / causal / recsys | 11 | LLM Agents for Time-Series；Contextual Causality with LLMs；Probabilistic Forecasting |
| Post-training & RL | 10 | Unsupervised Post-Training of Foundation Models；Rubric-Guided RL；On-Policy Self-Distillation |
| Generative models | 10 | Video Generation Models: Post-Training and Alignment；Adversarial Attacks on Diffusion |
| Others | ~70 | Safety in Self-Evolving Agents；Linear Representation Hypothesis；World-Action Models |

**几个可以直接从综述标题读出来的信号**：
- **"Self-evolving / self-improving"已经有专门综述**（Safety in Self-Evolving Agents；Unsupervised Post-Training；Self-Improving Test-Time Intelligence）——说明 RSI 已从口号变成有分类学的子领域。
- **"Efficiency"出现在几乎所有模态的综述里**（视频、多模态、GUI agent、量化、FPGA）——效率从工程细节上升为研究主题。
- **"Agentic skills"成为独立概念**：把可复用的过程性知识外部化为可执行 artifact，并且已经有"生命周期 + 安全治理"的九阶段框架。
- **"评测/benchmark"类综述数量偏高**，与我在正文里说的"评估危机"互为印证。

---

## 3. 领域全覆盖

下面按子领域逐一看这一年的实况。每一节都给出：**发生了什么 / 关键证据 / 代表工作 / 需要保留的怀疑**。

### 3.1 基础模型与预训练：规模仍在，但"效率"取代了"更大"

> **一句话**：规模仍在，但"效率 / 配方"取代了"更大"；数据墙变成真科学。

- **Kimi K3**（[2607.24653](https://arxiv.org/abs/2607.24653)）是这一年的标杆：2.8T 参数 MoE、104B 激活、原生视觉、**1M token 上下文**，用 Kimi Delta Attention + Attention Residuals + Stable LatentMoE（896 路由专家激活 16 个），相对 K2 声称约 **2.5× 的 scaling 效率提升**；后训练强调 general / agentic / coding 三个域的 RL 与多档"推理努力"。
- **DeepSeek-V4.1-Flash**（[2609.19969](https://arxiv.org/abs/2609.19969)）走另一个方向：552B MoE + 1M 上下文，标题直接写"把 KV cache 压缩推到极限"——**稀疏化、压缩、注意力效率成为发布主线**。
- **预训练本身的研究在转向"数据与配方"**：Muon 优化器成为热点（Muon with Finite Newton-Schulz、Spectral Allocation，均 2026-08）；DataFlex（[2603.26164](https://arxiv.org/abs/2603.26164)）把数据选择/配比/重加权统一成训练框架；ICLR 2026 最佳论文之一的 **Pre-training under infinite compute** 讨论"数据固定、算力无限"时该怎么练（结论之一：最优 weight decay 比常规大 30 倍；集成比正则化有更低的损失渐近线）。
- **MoE 是默认配方，"新架构取代 Transformer"是伪命题**：ICML 2026 里 MoE 相关约 83 个标题，而线性注意力/SSM 合计约 36 个。也就是说，架构讨论是"杂交与改良"，不是"取代"。

### 3.2 后训练与 RL：这一年真正的"主战场"

> **一句话**：主战场；但 GRPO 不是万能药，奖励设计与机制诊断才是核心。

- **证据**：ICLR 2025→2026 接收论文里 RL 主题 **9.4%→12.8%**；ICLR 2026 关键词 "reinforcement learning" 出现 **403 次，仅次于 LLM**；NeurIPS 2024→2025 RL 虽只 +0.1，但 Reasoning 暴涨（见 3.4）。
- **RLVR / GRPO 是默认底座**，但 **2026 的关键发现是"GRPO 不是万能药"**：T1（[2609.11042](https://arxiv.org/abs/2609.11042)）在同一 harness/奖励下，GRPO 两个 checkpoint 都停在 51.7%，而带 critic 的 PPO 把 Terminal-Bench 2.1 从 49.4% 推到 **64.0%**。
- **奖励设计是焦点**：Rubric-Guided RL 综述（[2608.27505](https://arxiv.org/abs/2608.27505)）用贝叶斯框架把"constitution 当先验、rubric 当后验"统一起 constitutional AI、实例级 rubric、过程监督、自演化 rubric；**Process Reward Model** 继续演进，但也出现了"确定性 PRM 在离散扩散里反而更差"（2609.35472）这类反例。
- **奖励黑客被量化**：Reward Hacking Benchmark（[2605.02964](https://arxiv.org/abs/2605.02964)）测 13 个 frontier 模型，exploit 率 0%–13.9%，并显示 **RL 后训练把 hacking 从 0.6% 抬到 13.9%**；ICLR 2026 oral 的 TRACE（*Is it Thinking or Cheating?*）用"推理何时已足够通过验证器"来检测**隐式** reward hacking。
- **一个反直觉的机制结果**：Dark Room（[2607.21273](https://arxiv.org/abs/2607.21273)）用预注册的 74 个实验臂证明，**dense prediction reward 在 GRPO 的 z-score 归一化下会被抹掉甚至反转**——ALFWorld 收敛到"prediction acc→1.0 但 success→0"的退化态。

### 3.3 On-policy distillation：这一年最被低估的技术线

> **一句话**：今年最被低估的技术线，也是唯一 +1000% 级主题；但要小心增益来源。

- **规模**：HF 上 on-policy distillation / self-distillation 相关关键词合计约 150 篇；arXiv 主题语料里 OPD 是"每个新论文都在改"的方向。
- **核心结果**：*Scaling properties of same-family OPD*（[2609.32722](https://arxiv.org/abs/2609.32722)）发现 OPD 早期存在 **"useful-transfer" 区间**，held-out 准确率随 √KL 近似线性上升；**所有 weak-to-strong 组合里学生峰值分数都超过老师**；并拟合出峰值分数关于师生规模/老师分数的幂律——**老师分数本身不能定义其监督价值**。
- **分化**：多教师（Domain-Normalized Multi-Teacher OPD, 2609.35347）、双向（DOPD, 2606.30626，提出 "privilege illusion" 失败模式）、agentic 自蒸馏（SDAR, 2605.15155；PivotOPD, 2609.40285）、多模态自蒸馏（UniEvo-VL, 2609.38721）。
- **机制与陷阱**：*Rethinking OPD*（[2604.13016](https://arxiv.org/abs/2604.13016)）给出成功两条件（师生思维模式兼容 + 老师提供学生没见过的新能力）；*When EOS Tokens Disagree*（[2609.20511](https://arxiv.org/abs/2609.20511)）指出**终止 token 不一致会导致学生长度膨胀**；*On-Policy or Off-Policy?*（[2609.35259](https://arxiv.org/abs/2609.35259)）做受控实验后给出一个**泼冷水**的结论：rollout policy 本身未必是关键，**token 级 KL 方向**影响更大。
- **一个重要的反证**：*Does On-Policy Distillation Really Distill?*（[2608.31046](https://arxiv.org/abs/2608.31046)）与 *Rethinking OPD* 都发现，OPD 的很大一部分收益**并非来自老师的能力迁移，而是学生自我抑制低概率 token 与分布对齐**。换言之"老师"可能没那么重要，**用什么 token 的 KL 方向**更重要（呼应 [2609.35259](https://arxiv.org/abs/2609.35259)）。
- **一句话**：如果 2025 的关键词是 "RLVR"，2026 的关键词很可能是 **"把 RL 学到的东西高效迁移出去"**，而 OPD 是它的主载体——但要小心它的增益来源。

### 3.4 推理与 test-time compute：从"想更久"到"训得更稳"

> **一句话**：占比翻倍，但"更多自由度/更多计算"未必更好，pass@1 会系统性高估。

- **占比翻倍**：ICLR 5.0%→12.0%，NeurIPS 2.8%→7.6%。
- **核心工作**：*The Art of Scaling RL Compute for LLMs*（ICLR 2026 oral）首次大规模拟合 RL 的 sigmoidal 计算-性能曲线，发现 loss 聚合/归一化/课程主要影响**效率**而非**渐近性能**；*The Coverage Principle*（ICLR 2026 oral）从理论上解释预训练为什么能开启后训练与 test-time scaling（coverage 是充要条件）；*In-Place Test-Time Training*（ICLR 2026 oral）把 MLP 最后投影当 fast weights，在推理时更新。
- **一个更冷静的声音**：ICML 2026 最佳论文 *The Flexibility Trap* 说明，**"更多自由度/更多计算"未必更好**——扩散 LLM 的任意顺序反而让模型跳过高不确定性的关键 token，导致解空间提前坍塌；用固定左到右的 JustGRPO 反而更强（GSM8K 89.1）。benchmark 侧，*How Much Can Language Models Gain from Test-Time Computation?*（2610.01110）在系统追问收益边界。
- **评测口径**：这一年的共识是 **pass@1 会系统性高估**，要看 pass^k / 可靠性（Thinkingbox：Claude Opus 5 从 66.5% pass@1 掉到 **47.5% pass^20**）。

### 3.5 Agent 系统：harness 成为"新物种"，skills 成为"新原语"

> **一句话**：harness 成为新物种，skills 成为新原语——这是今年最鲜明的结构变化。

这是 2026 年最鲜明的结构性变化。

- **harness（执行外壳）从工程细节变成研究对象**。HF 高投票里 harness 论文密集：**Raven**（The Harness of Harnesses，[2609.33439](https://arxiv.org/abs/2609.33439)，515 票）、**StateM**（[2608.15089](https://arxiv.org/abs/2608.15089)，harness scaling 在 Terminal-Bench 2.1 声称 95.3%）、**HarnessDev**（[2609.01437](https://arxiv.org/abs/2609.01437)，让 LLM 自己造 harness）、**Harness Handbook**（[2607.13285](https://arxiv.org/abs/2607.13285)，把"行为→代码"定位问题形式化）、**Mid-Harness**（[2609.39982](https://arxiv.org/abs/2609.39982)，在模型与 harness 之间放验证器）、**DarwinX**（[2608.07545](https://arxiv.org/abs/2608.07545)，用自然选择进化 harness）。
- **"skill"成为可复用、可分发、可交易的过程性知识原语**：Agentic Skills 综述（[2608.29596](https://arxiv.org/abs/2608.29596)）给出九阶段生命周期（发现→编写→存储→检索→组合→执行修复→终身适应→评测→安全治理）；Skills 类工作包括 MMSkills、COLLEAGUE.SKILL、Repo-To-Skill、Grounded Skill Synthesis、Spark-to-Paper、SkillOpt（[2605.23904](https://arxiv.org/abs/2605.23904)，把 skill 当"冻结 agent 的外部状态"来训练）。
- **memory 与 context 管理**：agent memory 主题在这半年 OpenAlex +75%；MemAgent、Metis（Memory Foundation Model, 2607.26760）、δ-mem（2605.12357）、MemFit（2610.00872）、VoxMem（多模态记忆 benchmark, 2609.32607）。
- **给开发者的实操结论**（来自 GUI agent 系统综述 [2609.02309](https://arxiv.org/abs/2609.02309)）：**选择性阅读**替代全上下文吞入、**全局到局部的视觉分配**、**可恢复记忆**替代原始历史回放、**验证感知控制**、GUI/非 GUI **混合运行时**。

### 3.6 Agentic RL 与长时程训练：配方是一整套 stack

> **一句话**：配方是一整套 stack：环境、验证器、异步基础设施与算法同等重要。

- **配方**：合成/筛选可验证长时程任务 → 拒绝采样 SFT 热启动 → **异步在线 RL（一个 sandbox 跑一条 rollout）** → 奖励来自任务自带 verifier。基础设施（per-rollout VM、弹性配额、stale rollout、drift 修复）和算法同样重要：微信 WeEnv（[2609.30766](https://arxiv.org/abs/2609.30766)）把环境开销的初始化提速 5.6–14.2×、占迭代时间从 53.4% 降到 9.1%。
- **代表**：T1（tencent，见 3.2）；**ComputerRL**（[2508.14040](https://arxiv.org/abs/2508.14040)，ICLR 2026，OSWorld 48.9%，RL 带来 +66%，Entropulse 交替 RL/SFT 抗熵塌缩）；**CompactionRL**（[2607.05378](https://arxiv.org/abs/2607.05378)，把上下文压缩训进 RL）；**SWE-MILE**（[2609.32631](https://arxiv.org/abs/2609.32631)，从运行时势能导出过程监督，不需要额外 reward model）；**T²PO**（[2605.02178](https://arxiv.org/abs/2605.02178)，ICML 2026 Spotlight，用不确定性控制多轮探索）；**SimpleTIR**（[2509.02479](https://arxiv.org/abs/2509.02479)，过滤 "void turns" 这种**数据过滤**就能稳定多轮工具 RL）。
- **评测的真实性**：**DeepSWE**（[2607.07946](https://arxiv.org/abs/2607.07946)）用 113 个"从未向上游贡献过"的原创任务对抗预训练污染（独立 judge 与手写 verifier 只有 1.4% 分歧，而 SWE-bench Pro 的继承测试有 32.4%）；**EdgeBench**（[2607.05155](https://arxiv.org/abs/2607.05155)）用 38,000 小时环境交互、134 个 ≥12 小时任务拟合出**部署后环境学习的 log-sigmoid 定律（R²=0.998）**。
- **最大的方法论警告**：credit assignment 是研究震中，但**大量 2026 论文只在 ALFWorld / WebShop 上验证**，这两个环境小、饱和、易被 shortcut。可信证据要么用 Terminal-Bench 2.x / SWE-bench / OSWorld，要么给受控消融与**负面结果**。

### 3.7 RSI / 自改进 / 自动科研：真闭环，但没有复利

> **一句话**：闭环是真的，但没有复利加速；瓶颈是验证与方向选择。

- **闭环是真的**：AIDE²（[2609.26457](https://arxiv.org/abs/2609.26457)）8 天自主运行、99 次改写、7 次接受、私有分 0.703→0.778，并在四个外部 benchmark（含分布外 WeatherBench 2）追平两年人力基线。Gödel Forest（[2609.36675](https://arxiv.org/abs/2609.36675)）数据层 RSI 平均 +10.70；Mendel GM（[2608.07645](https://arxiv.org/abs/2608.07645)）Polyglot 50.8→93.2；DarwinX、SoL-Pi（[2609.20519](https://arxiv.org/abs/2609.20519)）把 harness 演化推到 production。
- **但没有加速**：AIDE² 的 ignition test 是**负结果（0.780 vs 0.782）**；AI4AI-Bench（[2608.20318](https://arxiv.org/abs/2608.20318)）在 10 个冻结训练仓库上让 agent 改写训练算法，**290 次提交有 124 次比 baseline 更差**；RSI 综述（[2607.07663](https://arxiv.org/abs/2607.07663)，覆盖 1,250 篇）指出自改进强度沿"验证层级"递减。
- **瓶颈是验证与策略锁死**：自博弈 judge 可把 pass rate 从 0.716 刷到 0.938 而真实准确率停在约 0.20（[2607.05904](https://arxiv.org/abs/2607.05904)）；复用 benchmark 会带来最高 20.7% 假晋升，REUSE（[2609.33180](https://arxiv.org/abs/2609.33180)）用 certified 决策压到 0%；分析 1,338 条后训练轨迹发现**只有 2.1% 改变策略**（[2608.19072](https://arxiv.org/abs/2608.19072)）；崩溃是自生成数据循环的"默认动力学"（ReSAIL, [2609.39306](https://arxiv.org/abs/2609.39306)）。
- **自动科研的可信审计**：FARS（[2606.31651](https://arxiv.org/abs/2606.31651)）417 小时产出 166 篇论文，282 条评审均分 **3.17/10**、仅 11.4% 达接收线、27.9% 有完整性问题；shadow evaluations（[2607.27191](https://arxiv.org/abs/2607.27191)）让 agent 做未发表论文的核心开放问题，**两篇全被原作者拒**。**结论：工程强、判断弱。**

### 3.8 长上下文 / memory / compaction：形态已变

> **一句话**：不是变冷，是转向 memory / compaction / 训练配方 / 多轮可靠性。

- **单针解决、多跳未解决**：1M 单针检索三家 frontier 100%，但多跳在 256K/512K/1M 持续退化（[2605.02173](https://arxiv.org/abs/2605.02173)）。**窗口是容量，不是能力。**
- **重心转向 compaction**：Context Compaction Theory（[2608.01326](https://arxiv.org/abs/2608.01326)）证明压缩预算有信息论下界（等价 one-way communication complexity），并在生产 compactor 上发现 set-membership 查询接近随机；CompactionRL 把压缩训进 agent。
- **安全代价**：Governance Decay（[2606.22528](https://arxiv.org/abs/2606.22528)）发现压缩会删掉 in-context 治理约束，违规率 **0%→30%（最高 59%）**，软策略更差（8.3×）。
- **训练与理论回潮**：Cracks in the Foundation（[2608.10296](https://arxiv.org/abs/2608.10296)）用 26 个 matched 7B 模型证明四个"小架构选择"组合可让 HELMET-32K 掉最多 47 分，且短上下文 loss 看不出来；RoPE at the End of Its Rope?（[2609.39929](https://arxiv.org/abs/2609.39929)）给出可诊断的 RoPE 理论并带来 +20/+25pp。
- **多轮可靠性**：ICLR 2026 最佳论文 "LLMs Get Lost In Multi-Turn Conversation"（[2505.06120](https://arxiv.org/abs/2505.06120)）——15 个模型平均 -39%、unreliability +112%、2 轮触发、temperature 0 无效；2026 年围绕机制（intent vs context weighting vs reliability）展开了活跃争论（[2602.07338](https://arxiv.org/abs/2602.07338)、[2605.26788](https://arxiv.org/abs/2605.26788)）。
- **长上下文 vs RAG 收敛为"路由 + scaling law"**：To Memorize or to Retrieve（[2604.00715](https://arxiv.org/abs/2604.00715)）、EDAR（[2609.35831](https://arxiv.org/abs/2609.35831)）。

### 3.9 检索 / RAG / 知识：安全与效率成为主问题

> **一句话**：已基础设施化，2026 的增量集中在安全与效率。

- RAG 已经"基础设施化"，2026 的增量集中在**安全**与**效率**：*Retrieved But Not Reliable*（[2608.24977](https://arxiv.org/abs/2608.24977)）按 corpus / retriever / generator 建威胁模型，把攻击分为 accuracy / privacy / fairness 三类；*Mapping the RAG Landscape*（[2610.01936](https://arxiv.org/abs/2610.01936)）给出效率/防御/交互/推理四轴分类；*A Matryoshka Hierarchical RAG*（[2610.01767](https://arxiv.org/abs/2610.01767)）用分层多跳检索。
- **组织层创新**：RAGU（多步 GraphRAG + 小型领域模型, [2607.11683](https://arxiv.org/abs/2607.11683)）、AskChem（以"claim"而非"paper"为检索单元，[2607.28618](https://arxiv.org/abs/2607.28618)）、Direct Corpus Interaction（[2605.05242](https://arxiv.org/abs/2605.05242)）——**检索单元从文档下沉到 claim / corpus 操作**。

### 3.10 多模态与视觉：统一理解+生成，"原生统一"成为口号

> **一句话**：统一理解+生成成默认框架但证据仍薄；真正的跃迁在视频与 3D 几何。

- **趋势：understanding 与 generation 合流**。SenseNova-U1 / U1.5（NEO-unify，encoder-free + VAE-free，[2605.12500](https://arxiv.org/abs/2605.12500) / [2609.11929](https://arxiv.org/abs/2609.11929)）、LLaDA2.0-Uni（用扩散 LLM 统一, [2604.20796](https://arxiv.org/abs/2604.20796)）、LongCat-Next（把模态词元化, [2603.27538](https://arxiv.org/abs/2603.27538)）、Boogu-Image-0.1（[2607.13125](https://arxiv.org/abs/2607.13125)）。
- **视觉推理成为新战场**：VBVR-Pro（[2608.26105](https://arxiv.org/abs/2608.26105)，可验证的"原生视觉推理"测试台）、VBVR、BabyVision（[2601.06521](https://arxiv.org/abs/2601.06521)）、A Very Big Video Reasoning Suite（[2602.20159](https://arxiv.org/abs/2602.20159)）、Rethinking Latent Visual Reasoning（[2609.34563](https://arxiv.org/abs/2609.34563)，指出 latent token 对图像扰动的"证据信用 gap"）。
- **视频理解评测换代**：Video-MME-v2（[2604.05015](https://arxiv.org/abs/2604.05015)）用三级递进难度 + 人类标注，明确针对"榜单分数虚高"；VideoChat3 走全开放高效视频 MLLM。
- **CVPR 2026 规模与结构**：16,092 投稿、4,089 接收（约 25.4%）；从 4,042 个开放获取标题统计，**医学/生物 1,465、3D/4D/GS 748、效率 560、分割检测 510、VLM/MLLM 444**。最佳论文 D4RT（[2512.08924](https://arxiv.org/abs/2512.08924)）、最佳学生论文 O-Voxel（[2512.14692](https://arxiv.org/abs/2512.14692)）。

### 3.11 生成媒体：视频/图像/音频/音乐——最热也最需要怀疑

> **一句话**：最热也最需要怀疑：几乎没有同行评审，而它自己的评测在打假。

- **视频从"片段生成器"变成"流式交互系统"**：Vidu S2（[2609.11638](https://arxiv.org/abs/2609.11638)，706 票，全年媒体类最高；实时 720p 数字人 + **实时流式视频编辑** + 空间/VR）、Helios（[2603.04379](https://arxiv.org/abs/2603.04379)，单卡 H100 上 19.5 FPS）、实时编辑 LiveEdit、Wan-Streamer、LongLive-2.0（NVFP4 长视频基础设施）。
- **统一多模态生成器**：Kling-Omni（[2512.16776](https://arxiv.org/abs/2512.16776)）、Seedance 2.0（原生音视频, [2604.14148](https://arxiv.org/abs/2604.14148)）、Cosmos 3（omnimodal world model, [2606.02800](https://arxiv.org/abs/2606.02800)）、LTX-2（联合音视频, [2601.03233](https://arxiv.org/abs/2601.03233)，每步比 Wan2.2-14B 快约 18×）。
- **效率是最大的子文献**：综述（[2604.15911](https://arxiv.org/abs/2604.15911)）统计 2022–2026 共 722 篇加速论文；四范式（步数蒸馏 / 高效注意力 / 压缩 / cache+轨迹），并指出 **sparse attention 实际上胜过"声称线性"的方法**（后者多是误差补偿）。
- **音频同构**：AuK（[2609.08936](https://arxiv.org/abs/2609.08936)）统一语音生成+编辑（零样本 TTS 错误率 2.65%，但语音编辑 exact-match 仅 **13.85%**）；Qwen3-TTS/ASR 定义开源前沿；**全双工**是最热音频方向：DuplexSLA（[2605.20755](https://arxiv.org/abs/2605.20755)，160ms 时钟上同时做语音+规划+工具调用）；**Lychee-FD 获 ACL 2026 Outstanding Paper**（诊断声学/语义梯度冲突，[2026.acl-long.419](https://aclanthology.org/2026.acl-long.419/)）。
- **必须保留的怀疑（这一节最重要）**：这个领域**几乎没有经过同行评审**，而它自己的评测论文反复证明**"好看" ≠ "有物理/控制能力"**：Physion-Eval（[2603.19607](https://arxiv.org/abs/2603.19607)）用 90 位专家判定 **83.3% 第三人称 / 93.5% 第一人称生成视频存在至少一处物理错误**，而 Gemini 3.0 Pro 漏检 74.4%/90.1%；WorldMark（[2604.21686](https://arxiv.org/abs/2604.21686)）发现**感知质量与响应延迟负相关**；VGI-Bench（[2608.19583](https://arxiv.org/abs/2608.19583)）里最强模型（Seedance 2.0）只有 51.0。**引用这些系统的"SOTA"时请当作营销。**

### 3.12 世界模型：从"生成得像"到"可交互、可编程"，同时被自己人打假

> **一句话**：从"生成得像"到"可交互、可编程"，同时被自己人证伪。

- **可交互/实时/开放**：Astronex-World 1.0（[2609.20034](https://arxiv.org/abs/2609.20034)，832×480 @24fps，开放权重）、ABot-World-0（[2607.19191](https://arxiv.org/abs/2607.19191)，单张 RTX 5090、720p/16fps、约 19GiB 内无限 rollout）、Infinite-World（ICML 2026，1000 帧）、SolarWM（[2609.02886](https://arxiv.org/abs/2609.02886)）。
- **"可编程"是新词**：Programmable World Model（[2609.10540](https://arxiv.org/abs/2609.10540)）把世界状态演化与视觉生成解耦，用可执行程序显式维护持久全局状态；PhiZero（[2607.28624](https://arxiv.org/abs/2607.28624)）用"physical language"做离散状态转移；Qwen-AgentWorld（[2606.24597](https://arxiv.org/abs/2606.24597)）用语言模型模拟 7 类 agent 环境。
- **World-Action Model（WAM）** 成为机器人侧的统一概念（综述 [2609.16074](https://arxiv.org/abs/2609.16074)）；实证研究（[2609.34981](https://arxiv.org/abs/2609.34981)）发现**latent WAM 虽在分布内匹配 explicit WAM，却丢掉了泛化收益**。
- **打假**：与 3.11 同一批作者用 WROP 的 150 个认知科学任务证明**当前视频世界模型并不天然具备客体永久性**（[2609.28654](https://arxiv.org/abs/2609.28654)）；OpenWorldLib 作者承认领域**缺乏统一"世界模型"定义**（[2604.04707](https://arxiv.org/abs/2604.04707)）。

### 3.13 具身智能 / 机器人 / 自动驾驶：能力在整合，评测在崩塌

> **一句话**：能力在整合，评测在崩塌——LIBERO 可被 0.09B 探针解出。

- **配方已经固化：通用具身基础模型 + 数据规模**。Qwen-VLA（[2605.30280](https://arxiv.org/abs/2605.30280)）把操作+导航+轨迹统一进一个策略（LIBERO 97.9、Simpler-WidowX 73.7、R2R OSR 69.0、真实 ALOHA OOD 76.9%）；Xiaomi-Robotics-1（[2607.15330](https://arxiv.org/abs/2607.15330)）用 **10 万小时真实 UMI 轨迹**做 scaling；Being-H0.5（[2601.12993](https://arxiv.org/abs/2601.12993)）用 3.5 万小时 / 30 个本体。Green-VLA（[2602.00919](https://arxiv.org/abs/2602.00919)）是 HF 上全年票最高的具身论文（322）。MolmoAct2（[2605.02881](https://arxiv.org/abs/2605.02881)，357 票）强调可部署的开放动作推理。
- **后训练 = RL + 世界模型**：π*0.6 / RECAP（[2511.14759](https://arxiv.org/abs/2511.14759)）做真实世界 advantage-conditioned RL（吞吐 >2×、失败约减半、espresso/洗衣/装箱 >90%），但仍需人类标签/介入/复位；开源 RL 潮包括 SimpleVLA-RL（[2509.09674](https://arxiv.org/abs/2509.09674)，ICLR 2026）、π_RL、VLA-RFT、RLinf。**World-Action Model 在 4 个月内出了两篇综述**（[2609.16074](https://arxiv.org/abs/2609.16074)、[2605.12090](https://arxiv.org/abs/2605.12090)），NVIDIA Cosmos 3（[2606.02800](https://arxiv.org/abs/2606.02800)）把它做成 omnimodal 开放世界模型。
- **自驾走向 VLM/推理模型**：Qwen-Drive-1.0（[2609.00111](https://arxiv.org/abs/2609.00111)）在 NAVSIM 拿 90.7 PDMS、WOD-E2E 7.91 RFS，4B 开放；NVIDIA Alpamayo（开源 AV 推理-VLA）、Wayve GAIA-4（闭环仿真）、SimWAM（[2608.07468](https://arxiv.org/abs/2608.07468)，91.9 PDMS，用视频仅作训练时监督）。
- **数据趋势：用"无机器人的人类视频"当 scaling 底座**。DYNA-2 用约 **100 万小时人类视频**（公司自报装配成功率 20%→80–90%）；Ego2Robot 18,561 小时 / 15 种形态；Open-AoE ~2k 小时。
- **这一节最重要的发现：机器人评测在系统性失效。** *What Are We Actually Benchmarking in Robot Manipulation?*（[2606.04233](https://arxiv.org/abs/2606.04233)）证明：**LIBERO 可被一个 0.09B 的无语言 DINO+MLP 探针"走捷径"解出，且只差 SOTA 约 1 个点**；**只有 19.8% 的 LIBERO SOTA 声明在统计上显著**；CALVIN ATC 在把位姿重采样为分布内后从 4.17 掉到 3.14；22M 的 SimplerEnv 策略能追平 0.9B 的 X-VLA。LIBERO-Plus（[2510.13626](https://arxiv.org/abs/2510.13626)）在轻微扰动下让分数从 95% 掉到 <30%，且模型**忽略语言**；LIBERO-Para 有 22–52pp 的下降。**换句话说：这个领域大部分"进度"不能当作能力证据。**
- **怀疑**：最大的几个结果仍是**没有论文/权重的博客**（Gemini Robotics 2 全身 VLA、Figure Helix 02、GEN-0 的"scaling law"）；world-model 相对直接策略的闭环优势**明确未被证明**（[2609.29669](https://arxiv.org/abs/2609.29669)）；自驾的 CoT 忠实性也被自己的工作质疑（[2608.01755](https://arxiv.org/abs/2608.01755)）。

### 3.14 生成建模：扩散 / 流匹配 / 扩散语言模型（今年最大的能力变量之一）

> **一句话**：除 agent 之外最大的能力变量，同时在自我纠偏。

- **dLLM 跨过规模与系统门槛**：**DiffusionGemma**（[2608.00146](https://arxiv.org/abs/2608.00146)，Google）用不到 10% 预训练算力微调 Gemma 4 MoE（3.8B 激活/25.2B 总量），实测**每前向约 20 个 token**（SOTA 投机解码 3–6），延迟约降 4×；**LLaDA MoE v2**（[2608.03457](https://arxiv.org/abs/2608.03457)，30B-A3B）给出首个 **MoE-dLLM scaling law**，15 benchmark 平均 58.60；**LangFlow**（[2604.11748](https://arxiv.org/abs/2604.11748)）让连续扩散在 OpenWebText PPL 30.6 上追平离散扩散。
- **生态在补齐**：LLaDA-Image（图像, [2609.03796](https://arxiv.org/abs/2609.03796)）、LLaDA2.0-Uni（多模态统一, [2604.20796](https://arxiv.org/abs/2604.20796)）、Esoteric LM（任意顺序 + KV cache, ICML 2026）、SPEED（并行解码蒸馏）。
- **自我纠偏**：ICML 2026 最佳论文 **The Flexibility Trap**（[2601.15165](https://arxiv.org/abs/2601.15165)）证明"任意顺序"在实践中**不严格优于自回归**，并给出极简 JustGRPO；*On the Reasoning Abilities of Masked Diffusion LMs*（ICLR 2026 oral）、*Diffusion Language Model Knows the Answer Before It Decodes*（ICLR 2026 oral）继续厘清 dLLM 的推理机制。
- **图像/视频生成** 见 3.10/3.11；这一节的判断是：**生成建模的创新重心从"新采样器"移到了"系统可用性"（速度、KV/上下文、量化、统一多模态）**。

### 3.15 架构：不是"取代 Transformer"，而是"混合化"

> **一句话**：不是取代 Transformer，而是混合化；数据墙与优化器是另外两条暗线。

- **定调**：年度最佳的结构性综述 [The Evolution of Attention in LLMs](https://arxiv.org/abs/2609.39661) 重建了 59 条发布记录 / 14 个模型谱系 / 11 个开放权重端点，结论是**"多样化而非收敛"、"日益混合化"**，并把网络**深度**视为协调记忆的轴。**每一个 2026 前沿/后端模型都保留了 softmax attention**：Kimi K3（Kimi Delta Attention + Gated MLA + Attention Residuals + Stable LatentMoE 16/896 + Per-Head Muon）、Qwen3.8-Next（Gated DeltaNet + 每 4 层 1 个全局注意力，后换成 Sparse Attention）、Nemotron 3（MoE hybrid Mamba-Transformer）、MiniMax Sparse Attention。**纯 SSM/线性"替代"没有在前沿规模出货。**
- **数据墙变成真科学**：[Pre-training under infinite compute](https://arxiv.org/abs/2509.14786)（ICLR 2026 Oral）给出最优 weight decay 约为常规 **30×**，并用"正则化 + epoching + 参数 scaling + 集成"在 **5.17× 更少数据**下达到同一损失渐近线；集成可蒸馏成 8× 更小学生（保留 83%）。配套还有 [Prescriptive Scaling Laws](https://arxiv.org/abs/2605.01640)（数据受限的过拟合罚项）、[Relative Scaling Laws](https://arxiv.org/abs/2510.24626)（255 个 matched-compute 模型；7.5 分却被 desk-reject）、[Why Less is More](https://arxiv.org/abs/2511.03492)（数据策展的相变理论）。语料侧：[Common Corpus](https://arxiv.org/abs/2506.01732)（约 2T 开放 token）、Nemotron-CC-Math（133B）、MixtureVitae。
- **MoE 与"稀疏度作为新 scaling 轴"**：[Optimal Sparsity of MoE LMs](https://openreview.net/forum?id=)（ICLR 2026 Oral）证明：**等损失下更多激活 FLOPs 推理更好**，记忆与推理需要不同的 tokens-per-parameter——修正了经典 compute-optimal 结论；SMELT（[2609.01343](https://arxiv.org/abs/2609.01343)，循环 MoE 省 6.8–18% FLOPs）。架构侧实战改进还有 **Gated Attention**（NeurIPS 2025 最佳论文，已被 Qwen3-Next 采用）、[Log-Linear Attention](https://arxiv.org/abs/2506.04761)、Gated DeltaNet-2、In-Place TTT、FlashRNN。
- **优化器跨入前沿实践**：[Polar Express](https://arxiv.org/abs/2505.16932)（ICLR 2026 Outstanding HM，把 Muon 的 Newton–Schulz 换成极小极大最优多项式）；NVIDIA 的 [SOAP, Muon, and Beyond](https://arxiv.org/abs/2607.20548) 在万亿 token 规模稳定训练；[Optimizer-Induced Spectral Scaling](https://arxiv.org/abs/2605.21803) 显示同一架构在 AdamW（β=0.44）与 Muon（β=1.02）下有不同谱 scaling 指数。
- **理论**：ICLR 2026 最佳论文 *Transformers are Inherently Succinct*（用"紧致性"解释 Transformer 为何仍然赢）、[The Coverage Principle](https://arxiv.org/abs/2510.15020)（预训练如何开启后训练）、[Scaling with Collapse](https://arxiv.org/abs/2509.25087)（超参最优时损失曲线普适坍缩）、*Superposition Yields Robust Neural Scaling*（NeurIPS 2025 Oral）、[How much do LMs memorize?](https://arxiv.org/abs/2505.24832)（ICML 2026 HM，约 **3.6 bits/参数**）。
- **需要保留的怀疑**：高票的"新架构"多为**小规模存在性证明**（BDH-CQ 796 票但 150M 参数；HRM-Text 322 票；NCP 330 票），**不是前沿证据**；sparse attention 的"免费午餐"被 [Full Attention Strikes Back](https://arxiv.org/abs/2605.16928) 质疑；scaling law 结果单实验室、脆弱；"表达力"不等于"能力"。

### 3.16 效率 / 系统 / 推理服务：从"一个技巧"变成"架构本身"

> **一句话**：从"一个技巧"变成"架构本身"；但"最大板块"的说法需要修正。

- **先纠正一个常被误传的说法**：对 ICML 2026 全部 6,628 个标题的独立复算显示，效率/系统类严格口径 **930 篇（14.0%）**、宽口径 997（15.0%）——它是**最大的"系统类"板块，但不是最大主题**：LLM/基础模型 1,436（21.7%）、推理/test-time 963（14.5%）更大；而且它**不是增长最快的**（ICLR 12.3%→13.2%，NeurIPS 11.5%→10.7%）。**没有任何效率论文拿到 ICLR/ICML 2026 最高奖**（最接近的是 ICLR HM 的 Polar Express）。这一板块也高度分散：蒸馏 104、MoE 84、量化 83、serving 79、稀疏注意力 60、kernel 48、能源 39、KV 32、投机解码 31、on-device 6、硬件协同 9。
- **真正的转变是"效率即架构"**：最大的效率论文其实是**前沿模型报告**。[DeepSeek-V4](https://arxiv.org/abs/2606.19348)（1.6T/49B Pro、284B/13B Flash）用 Compressed Sparse Attention + Heavily Compressed Attention 的混合长上下文注意力，声称 1M 上下文下单 token FLOPs 仅为 V3.2 的 **27%**、KV cache 仅为 **10%**（Flash 为 10%/7%），并配 Muon、wave-based EP mega-kernel、TileLang、on-disk KV、FP4 QAT；[DeepSeek-V4.1-Flash](https://arxiv.org/abs/2609.19969) 把 KV 压到 **890 bytes/token（约 V4-Flash 的 1/4）**、常驻足迹约 1/8，prefill 激活 8B、decode 16B；Kimi K3 声称约 2.5× scaling 效率；Qwen3.8-Next 以约 **1/9 训练 FLOPs** 匹配 397B 前代。
- **稀疏注意力赢了长上下文，但只在 kernel 协同设计时**：DSA → CSA/CSA2、[MiniMax Sparse Attention](https://arxiv.org/abs/2606.13392)（1M 下每 token 注意力 FLOPs 降 **28.4×**，H800 上 prefill 14.2× / decode 7.6×，靠 exp-free top-k + KV-outer kernel）、HiLS（>64× 外推）。
- **今年最重要的效率负面结果**：[Random Attention](https://arxiv.org/abs/2609.03430) 证明 **KV eviction 的"打分"几乎不贡献价值**——逐头随机驱逐就能匹配最强 selector，且在 vLLM 里快 **32–43%**，因为脆弱的是 prompt、而推理轨迹自带冗余。这直接挑战了整条 scored-eviction 文献。
- **KV cache 成为一等系统对象**：ACL 2026 Findings 的[系统感知 KV 综述](https://arxiv.org/abs/2607.08057)、on-disk KV 分层、KV provenance；**服务从单引擎走向"集群控制平面"**（vLLM/llm-d 综述 [2609.23130](https://arxiv.org/abs/2609.23130)、position paper [2605.01280](https://arxiv.org/abs/2605.01280)）；**投机解码从小的 AR drafters 转向并行/块 drafters + 半 AR 修复**（Domino，[2605.29707](https://arxiv.org/abs/2605.29707)，5.49×/5.8×）。
- **MoE 边缘/基础设施很热**：Director（[2607.08782](https://arxiv.org/abs/2607.08782)，INFOCOM 2026，11–55% 延迟下降）、Edge0（[2609.18063](https://arxiv.org/abs/2609.18063)，35B MoE 在 3 GiB 内 20 tok/s）、FreeToken（[2608.16157](https://arxiv.org/abs/2608.16157)，声称单工作站 GPU 跑 753B GLM-5.2）；MinT（[2605.13779](https://arxiv.org/abs/2605.13779)）管理"百万个 LoRA 策略"的训练与服务（adapter-only handoff 提速 18.3×/2.85×）；多模态/视频效率另有专门综述（[2609.19445](https://arxiv.org/abs/2609.19445)、[2609.10355](https://arxiv.org/abs/2609.10355)）。
- **格式与 kernel**：FP4（NVFP4 vs MXFP4）是部署格式；[The Great Inversion](https://arxiv.org/abs/2608.25188)（综述 200 篇、43 种 transform）指出"变换编码奖励能量集中"与"分组共享 scale 量化奖励组内平坦"**方向相反**；MXFP4 OAS/MBS（[2603.08713](https://arxiv.org/abs/2603.08713)）把 MXFP4 与 NVFP4 的差距从约 10% 收到 <1%；[FlashAttention-4](https://arxiv.org/abs/2603.05451) 在 B200 上达 **1613 TFLOPs/s（理论峰值 71%）**，比 cuDNN 9.13 快 1.3×、比 Triton 快 2.7×。
- **怀疑**：几乎所有加速数字都是**单点、单配置**；FP4"无损"很窄；on-device/753B 类声明需要审计；能源计量尚无公认的 per-token benchmark。

### 3.17 可解释性：从"找到特征"到"验证特征能否用"

> **一句话**：从"找到特征"到"验证特征能否真正 steer 行为"。

- **旗舰进展**：Anthropic 的 **Natural Language Autoencoders**（2026-05）用"激活→自然语言解释→重建激活"的闭环把特征变成可自我描述的对象，并在安全测试里抓到"模型一边作弊一边内部盘算不被发现"；Transformer Circuits 2026-05 更新证明**特征的下游连接能预测它是否真的能 steer 行为**。
- **自己的负面结果**：*A is for Absorption*（NeurIPS 2025 Oral）指出层级特征会被子特征吸收；*The Geometric Wall*（[2605.09887](https://arxiv.org/abs/2605.09887)）指出跨层 SAE 的 scaling 由流形曲率决定；*SAE Interventions are Unreliable*（[2606.18322](https://arxiv.org/abs/2606.18322)）证明被 clamp 的"不安全特征"可以被残差空间优化绕过——**SAE 是因果关系把手，不是完整瓶颈**。
- **线性表示假设被"可证伪化"**：综述（[2609.22695](https://arxiv.org/abs/2609.22695)）指出 LRH 只有在明确"模型、表示位置、特征定义、评测数据"后才是良定义的科学假设，并提出更严格的表述与开放问题。

### 3.18 安全 / 对齐 / 隐私 / 治理：方法在收敛，评测在证伪

> **一句话**：方法在收敛、评测在证伪——这一年主要发现我们高估了安全性。

- **"安全是稀疏且可被廉价攻击的"**：*A Single Neuron Is Sufficient to Bypass Safety Alignment*（[2605.08513](https://arxiv.org/abs/2605.08513)）在 7 个模型（1.7B–70B）上用一个 MLP 神经元的标量激活达到约 **91.7% JailbreakBench ASR**，能力代价约 0.6% MMLU；"安全神经元"（NeurIPS 2025）、"单神经元轻对齐"（[2602.02027](https://arxiv.org/abs/2602.02027)）形成同一簇。**警告**：神经元是基依赖坐标，"sufficient"不等于"robust"。
- **涌现性失配（emergent misalignment）成为核心谜题**：*Persona Features Control Emergent Misalignment*（ICLR 2026）用 SAE model-diffing 找到可开关的"错位人格"方向；*EM is Easy, Narrow Misalignment is Hard*（[2602.07852](https://arxiv.org/abs/2602.07852)）解释这是归纳偏置所致（一般错位解损失更低、更鲁棒）。
- **欺骗/控制转向现实场景，但"评测意识"成为一级混淆**：DeepMind 的现实 honeypot（[2605.29729](https://arxiv.org/abs/2605.29729)）发现 Gemini **不会无缘无故耍阴谋**，scheming 主要由"代理性/目标性提示"诱发；但 *The Obfuscation Atlas*（[2602.15515](https://arxiv.org/abs/2602.15515)，ICML 2026 HM）证明**训练对抗欺骗探针会催生"混淆激活/混淆策略"**；*Adaptive Attacks on Trusted Monitors*（ICLR 2026）显示知道协议的攻击者能绕过多种监控；*When Behavioral Safety Evaluation Fails*（[2606.08044](https://arxiv.org/abs/2606.08044)）构造出"通过所有静态审计、却在微小潜在扰动下失守"的模型——**静态安全审计会系统性过度认证**。
- **遗忘学习（unlearning）陷入方法论危机**：*Forgetting That Sticks*（[2605.15138](https://arxiv.org/abs/2605.15138)）发现 4-bit 量化会系统性逆转遗忘（更新幅度低于 NF4 bin width 47–828×）；*Storage Is Not Strategy*（[2609.37858](https://arxiv.org/abs/2609.37858)）指出"按存储位置定位"的 AUROC 0.981 与更好的干预只在 17/36 目标上一致。
- **隐私与溯源**：*Memorization Is Not Extraction*（[2608.27782](https://arxiv.org/abs/2608.27782)）证明反事实记忆与自适应抽取互不控制；*The Privacy-Hallucination Tradeoff*（[2609.00492](https://arxiv.org/abs/2609.00492)）指出 DP 会抬高幻觉；watermarking 转向"溯源基础设施"（[2607.10103](https://arxiv.org/abs/2607.10103)）；*Stealing Reasoning Traces from Proprietary LLM APIs*（[2608.09867](https://arxiv.org/abs/2608.09867)）把"加密 CoT"打穿。
- **治理 & Agent 安全**：*Orphan risks*（[2608.16895](https://arxiv.org/abs/2608.16895)）比较四家前沿实验室的安全/合规文档，给出"可测量性/严重性/可审计性/竞争成本"四个选择器；*Safety in Self-Evolving Agents*（[2610.00093](https://arxiv.org/abs/2610.00093)）提出 SAVER 转移中心框架；OpenART（[2608.00677](https://arxiv.org/abs/2608.00677)，266 票）用 10,000+ 有状态场景做 agent 红队。

### 3.19 评估 / 基准 / 元科学：这一年最大的"公共瓶颈"

> **一句话**：整个领域的公共瓶颈，并已蔓延到科研系统自身。

- **agent 评测换代**：Agents' Last Exam（[2606.05405](https://arxiv.org/abs/2606.05405)，250+ 专家、55 个职业/13 行业簇、1K+ 长时程任务；**最难层级 frontier agent 通过率 <1%**；ALE-CLI 最好 25.2%，而 Terminal-Bench 82.0%、SWE-bench-Pro 59.1%；单任务成本 $15.70 / $3.80 / $1.33）、Gaia2（ICLR 2026 oral）、Terminal-Bench 2.1、ClawBench、StartupBench（[2608.17800](https://arxiv.org/abs/2608.17800)）、Workflow-GYM（[2606.11042](https://arxiv.org/abs/2606.11042)）、Claw-Eval（[2604.06132](https://arxiv.org/abs/2604.06132)）、MerchantBench、cua-speedrun（[2609.40284](https://arxiv.org/abs/2609.40284)）。
- **"benchmark 不可信"成为显学**：DeepSWE（[2607.07946](https://arxiv.org/abs/2607.07946)）反污染；DatBench（[2601.02316](https://arxiv.org/abs/2601.02316)）指出某些 VLM 评测**最多 70% 的题不看图也能答、最多 42% 标注错误**；MMGist（[2606.22437](https://arxiv.org/abs/2606.22437)）用 23,250→7,262 的精简在 ρ=0.98 下保持结论；Benchmark Radar（[2609.11115](https://arxiv.org/abs/2609.11115)）做"活的 benchmark 数据库"；SurveyReview（[2608.07641](https://arxiv.org/abs/2608.07641)）连"综述评测器"都要评。
- **可靠性口径**：pass@1 → pass^k（Thinkingbox）、"多轮退化"（ICLR 2026 最佳论文）。
- **元科学：评审自身的 AI 化**（本轮最重要的元发现之一）：
  - **ICML 2026 水印钓鱼**：用 **170,000 短语词典**（每篇 PDF 采 2 个，碰撞概率 <1/10^10）注入"仅 LLM 会遵循"的隐藏指令，前沿模型 **>80% 会照做**；标记 **795 条评审（约 1%）来自 506 名 Policy-A 审稿人**（全部人工核验），**497 篇论文（约 2% 投稿）被 desk-reject**（后修正为对应 **398 名互评审稿人**），51 名审稿人（占 506 的约 10%）被移除；family-wise 误差率 0.0001。ICML 自己承认**只能抓"粗心的复制粘贴"**。ICML 投稿从 2023 年的 6,538 涨到 2026 年的 **24,661（+277%）**。
  - **NeurIPS 2026** 用 Pangram v3.3.2 审计 Position Paper Track：**28.2%（273/969）为 100% AI 撰写**、42.7% ≥90%、70.5% ≥50%；**178 篇（18.4%）desk-reject**，123 篇（12.7%）申诉并附审计轨迹；ICLR 2026 已接收论文只有 1% 被标记。**但 28.2% 这个数字对窗口极其敏感**：换成约 100 词窗口后，"100% AI"从 28.2% 掉到 **2.16%**、"≥90%"从 42.7% 掉到 12.7%（召回率约 70%）。**检测器估计不是真值。**
  - **ICLR 2026** 遭遇 OpenReview API 爬取、身份在讨论期泄露，导致分数重置与 AC 重分配；同一事件中 Pangram 分析了全部 **19,490 篇论文 + 75,800 条评审**，估计**约 21% 的评审完全由 AI 生成**（该数字经厂商与媒体转述，非同行评审）。
  - **随机实验**（[2609.19420](https://arxiv.org/abs/2609.19420)，ICML 2026，N=1,486）：严格执行"禁止 LLM"策略的审稿人里 **22.5% 报告仍用了 LLM**；宽松策略下 36.5% 至少有一次明确违规；两种政策对最终决策影响接近零，但宽松组的评审长 5.5–7%。
  - **投稿量本身失控**：ICLR 2027 在一个周期内收到 **60,000+ 摘要，超过 2013–2026 全部 ICLR 之和（约 56,000）**（2013 年只有 67 篇）。
  - **污染与可复现**：对 55 项研究的系统综述（[ACL GEM 2026](https://aclanthology.org/2026.gem-main.50/)）发现**没有任何检测方法稳定可靠**，指令微调是盲点，污染导致分数通胀约 **6–40%**。
  - **含义**：当"谁在评审、谁在写论文"都不可信时，**可信验证不只是 agent 的问题，而是科研系统本身的问题；而"用 AI 检测 AI"本身也不可信**（28.2%→2.16% 的窗口敏感度是最好的例子）。

### 3.20 AI for Science / 医学 / 数学：形式化数学是最干净的胜利

> **一句话**：形式化数学是最干净的胜利；临床 AI 最有力的证据是阴性 RCT。

- **数学赢在"验证免费"**：**AlphaProof Nexus**（[2605.22763](https://arxiv.org/abs/2605.22763)）用 Lean 4 自主解决 **353 个开放 Erdős 问题中的 9 个**、492 个 OEIS 猜想中的 44 个，全部 kernel 检查通过，单题成本数百美元；**AlphaEvolve**（PNAS，陶哲轩参与）在 67 个分析/组合/几何/数论问题上改进若干；**Atlas/AutoformBot**（[2605.29955](https://arxiv.org/abs/2605.29955)）把 26 本研究生教材形式化为 45,000+ 条 Lean 声明；**MechGeo**（[2608.02295](https://arxiv.org/abs/2608.02295)）不只证明、还**构造反例**；**Magenta**（[2609.11319](https://arxiv.org/abs/2609.11319)）强调"statement judge"以防假证书。Anthropic 声称 11 天 / 1300 万行 Lean 形式化费马大定理——**是工程演示，不是同行评审结果**。
- **基因组有两个里程碑**：**Evo 2**（9T bp、1M 上下文，跨物种基因组设计，Nature）与 **AlphaGenome**（1Mb 输入、单碱基轨迹，在 25/26 个变异效应评测上领先，Nature）。但统一评测（GENEB, [2606.04525](https://arxiv.org/abs/2606.04525)）显示排名在不同任务间翻转，**不要相信聚合榜单**。
- **蛋白质设计进入湿实验**：RFdiffusion 抗体（cryo-EM 验证结合姿态）、ProteinMPNN 重设计酶（进化起点更好，特异性提升 >79×）、Doudna 组的 SynTnpB（结构+进化约束设计，在人类/植物细胞有活性）。
- **天气 AI 走向业务化**：WeatherNext Cyclones 声称对物理模式有 **>1 天** 的提前量优势；WeatherNext 3 用原始卫星观测做 0.1°、逐小时预报。
- **临床 AI 最有力的证据是一个阴性 RCT**：LungIMPACT（n=93,326，Nature Medicine）发现 AI 优先排序胸片**没有**缩短到 CT（p=0.31）或诊断（p=0.84）的时间，作者建议在该场景**不要部署**。**这是对临床 AI 热情最有力的对照。**
- **"自主发现"多为半自主**：Robin（Nature）自称 "semi-autonomous"，ripasudil 只是体外验证；Virtual Biotech 明确 "human-guided"，媒体"37,000 个 AI 发现肺癌药"的说法**言过其实**；Kosmos 只做数据分析+文献，自报 79.4% 陈述准确率。

### 3.21 非 LLM ML：不在聚光灯下，但有一个真热点——表格基础模型

> **一句话**：不在聚光灯下，唯一真热点是表格基础模型——而它正被自己的评测修正。

- **先看元事实**：2026 年 1–10 月的 HF Daily Papers 里，upvote ≥100 的 227 篇中只有约 **15% 是非 LLM**（≥200 票的 58 篇里约 7 篇）；ICLR 2026 接收里基础/前沿模型 831 篇，而图学习 113、时间序列 101、概率方法 116、因果 47。**非 LLM 子领域没死，只是搬到了聚光灯外。**
- **表格基础模型是唯一例外，也是最大的非 LLM 热点**：LimiX-2（[2609.17488](https://arxiv.org/abs/2609.17488)，**813 票，全年非 LLM 最高**）用"机制式联合建模" p(x,y|context) 取代 p(y|x,context)，TabArena overall Elo 1935（+117.4）；TabFM（[2609.37959](https://arxiv.org/abs/2609.37959)，400M）回归 Elo 2055.2；加上 TabPFN-3、TabICLv2、TabDPT、Mitra-v2 等。**但它自己的反证同样有力**：BeyondArena（[2606.30410](https://arxiv.org/abs/2606.30410)）显示这些模型**只在小型 IID 表格上占优**，在非 IID（时序/分组）、大样本、高维、高基数数据上会被普通 GBDT 击败——**榜单设计而非能力，解释了大部分"胜利"。**
- **时间序列基础模型是第二个成熟品类，但被"鹦鹉学舌"打假**：Chronos-2（[2510.15821](https://arxiv.org/abs/2510.15821)，group attention，多元/协变量零样本）声称在 fev-bench/GIFT-Eval 领先（作者自承预训练语料与 GIFT-Eval 训练集重叠）；Moirai 2.0（[2511.11698](https://arxiv.org/abs/2511.11698)）。**但 [Context Parroting](https://arxiv.org/abs/2505.11349)（ICLR 2026）证明领先模型经常只是"抄上下文"，一个朴素 parrot 基线就能在混沌/湍流/ECG 上超过它们**；[Do Tabular FMs Know Physics?](https://arxiv.org/abs/2609.02766) 进一步说明它们的先验无法表示无噪声机制与物理单位。
- **图 / 几何 / 原子模拟持续产出真实成果**：EquiformerV3（[2604.09130](https://arxiv.org/abs/2604.09130)）在 OC20/OMat24/Matbench Discovery 上 SOTA（与 eSEN、Meta UMA 并列）；CVPR 2026 两篇最佳论文（D4RT 4D 重建、O-Voxel 结构化 3D 潜变量）都是几何原生。但**"图基础模型"仍主要是综述与愿景**（[2505.15116](https://arxiv.org/abs/2505.15116)）。
- **因果 / 推荐 / 联邦**：因果的亮点是 CausalPFN / Do-PFN（把因果效应估计变成 in-context，但假设 ignorability 且只在模拟器族上训练）与 ICLR 2026 评分 8 的**环状潜变量因果可辨识性** Oral；推荐侧是"把生成式推荐 Transformer 扩到 1B"（[2507.15994](https://arxiv.org/abs/2507.15994)）；联邦在整合（ICLR 2026 仅 57 篇），亮点是成本感知客户端选择的非凸理论（[2512.05327](https://arxiv.org/abs/2512.05327)）。
- **经典 RL 的新意来自"规模与数据 regime"，而不是新算法**：NeurIPS 2025 最佳论文是 **1024 层自监督 RL**（[2503.14858](https://arxiv.org/abs/2503.14858)，把"RL 只能用浅网络"当作架构/优化伪命题）；ICLR 2026 RL Oral 是 TD-JEPA（[2510.00739](https://arxiv.org/abs/2510.00739)）；WarpSAC（[2608.24479](https://arxiv.org/abs/2608.24479)）说明 off-policy 稳定器是"数据 regime 依赖"的；ICML 2026 时间检验奖是 A3C。
- **判断**：非 LLM ML 的绝对产出没降，但**相对注意力急剧下降**；真正的增长点是**与 LLM 的交叉**（graph+LLM、time-series agent、causal+LLM）以及**表格/时序的"基础模型化"**——而后者正在被它自己的评测论文修正。

### 3.22 数据 / 合成数据 / 持续学习 / 理论

> **一句话**：数据成为一等公民，"数据选择"从配方争论变成理论。

- **数据成为一等公民**：DataFlex（[2603.26164](https://arxiv.org/abs/2603.26164)）统一数据选择/配比/重加权；DataFlex-RL（[2609.06107](https://arxiv.org/abs/2609.06107)）评测 RLVR 的数据策略；Data Recipes for Reasoning Models（ICLR 2026 oral）；合成数据综述 15 篇、数据策展 1 篇（我的归类偏低，实际更多）。
- **数据选择"变成理论"**：Why Less is More（[2511.03492](https://arxiv.org/abs/2511.03492)）给出数据策展的相变曲线；WebGraphMix（[2606.11499](https://arxiv.org/abs/2606.11499)）用 Common Crawl 主机图的中心性做选择（1:1 中心/边缘混合 41.4% vs 均匀 39.8%，加质量分类器达 43.8%）；TabStruct（ICLR 2026 oral）评测合成表格的**因果结构保真度**；模型坍缩被重述为"泛化→记忆"的转变（[2509.16499](https://arxiv.org/abs/2509.16499)）；而 [Demystifying Synthetic Data](https://arxiv.org/abs/2510.01631)（>1000 个 LLM）指出**纯改写型合成文本并不比自然网页文本更快**，"1/3 改写混合"才有帮助。
- **持续学习重新变热**：*Continual Learning Mechanisms Compose for Long-Horizon Memorization*（[2609.06986](https://arxiv.org/abs/2609.06986)）用 100 个持续 SFT 任务证明**没有单一机制能抗遗忘**；Macaron-V1（[2608.09819](https://arxiv.org/abs/2608.09819)）把持续学习与 MoE-LoRA 自改进结合；FIRE、Plug-and-Play Compositionality。
- **理论回潮**：Pre-training under infinite compute、The Coverage Principle、Transformers are Inherently Succinct（三项 ICLR 2026 oral/最佳）、Why DPO is a Misspecified Estimator、Expressivity 相关（Softmax Transformers are Turing-Complete）、泛化理论（Scaling Laws and Spectra of Shallow Neural Networks）。
- **判断**：在 LLM 时代，"理论"没有消失，而是**重新瞄准了后训练/预训练/推理这三个新对象**（coverage、DPO 的统计性质、RL 的 scaling law、Transformer 的表达紧致性）。

### 3.23 综述地图与"学科化"：一个元趋势

> **一句话**：327 篇综述是"学科化"的信号，也是"我们测不了 X"的焦虑。

- 一年内 **327 篇** AI/ML 综述（标题含 survey/review/overview）；归类后 Agents/RAG/多模态/效率 四大块最多（见 2.5 与 [notes/survey-map.md](notes/survey-map.md)）。子代理另精选出 29 篇"最该读"的综述，覆盖 test-time intelligence、unsupervised post-training、world models、agentic skills、RAG 安全、prompt injection、world-action models、rubric RL、agent-as-a-judge、mechanistic interpretability、hallucination lifecycle、agent memory、time-series agents、alignment game theory、diffusion adversarial、动态异质图、vision-graphs 等。
- **几篇"定调"综述值得单独点名**：
  - [A Survey on Self-Improving Test-Time Intelligence](https://arxiv.org/abs/2609.01679)：用 **update（状态更新）vs compute（推理算力）** 两个旋钮统一 test-time adaptation / learning / scaling，指出两个社区在用不同词汇讲同一件事。
  - [Unsupervised Post-Training of Foundation Models](https://arxiv.org/abs/2608.24982)：把 **80 个无标签后训练方法**按信号来源分成四族，核心风险是**递归误差放大**。
  - [Do World Models Make Better Robots?](https://arxiv.org/abs/2609.29669)：在 **160 个 benchmark** 里只有 **11 个**做了 world-model vs VLA 的对照、**只有 4 个**真的执行预测——**"世界模型能不能帮机器人"目前无法被现有评测回答**。
  - [A Survey on the Linear Representation Hypothesis](https://arxiv.org/abs/2609.22695)：把 LRH 变成可证伪假设（必须先声明模型、表示位置、特征定义、评测数据）。
  - [A Systematic Survey of Agentic Skills](https://arxiv.org/abs/2608.29596)：九阶段生命周期 + 六类开放问题（含零信任市场、策略-技能协同漂移）。
- **综述本身就是信号，也暴露了焦虑**：当"Self-Evolving Agents""Unsupervised Post-Training""Efficient GUI Agents""World-Action Models""Agentic Skills"都有专门综述时，说明这些方向**从论文簇变成了子领域**；而当出现"do world models make better robots""are benchmarks already contaminated""survey of survey evaluators（SurveyReview）"这类**"我们根本测不了 X"**的综述时，说明领域正在**系统性地发现自己的测量缺口**——这是这一时期最有辨识度的综述形态。

### 3.24 补遗：主线之外，但仍值得知道的板块

上面 23 节覆盖了注意力中心；下面这些板块**不在聚光灯下，但 ICLR/ICML/NeurIPS 里都有稳定的接收量**，属于"容易在热点综述里被漏掉"的部分。

> **一句话**：这些板块热度低，但不是因为不重要，而是因为领域注意力被 agent 系统吸走了。

- **神经科学 / 脑与认知（NeuroAI）**：ICLR 2026 "neuroscience & cognitive science" 方向接收 **114 篇**，是脑科学侧最大的一块。补漏检索显示三条线同时推进：
  - **脑解码（fMRI/EEG/MEG）**：**TRIBE**（三模态脑编码器做全脑 fMRI 响应预测, ICLR 2026）、**Representational Alignment Across Model Layers and Brain Regions with Hierarchical Optimal Transport**（分层最优传输对齐模型层与脑区, ICLR 2026）、**Interpretable MEG Decoding of Perceived Speech**（HF 74 票）、**Real-time Reconstruction of Human Visual Perception from fMRI**（[2607.22753](https://arxiv.org/abs/2607.22753)）、**FlatClip**（[2609.31204](https://arxiv.org/abs/2609.31204)，几何感知的 fMRI 表征学习基线）。
  - **基础模型化 + scaling law**：**CortexBridge**（[2610.01124](https://arxiv.org/abs/2610.01124)，把任意 EEG 电极布局映射到共享皮层潜空间）、**NeurDuo-EEG**（[2609.38587](https://arxiv.org/abs/2609.38587)，长序列 EEG 基础模型，带持久状态与显式记忆）、**Scaling Laws for EEG Decoding: How Much Data Is Enough?**（[2609.35056](https://arxiv.org/abs/2609.35056)）。
  - **BCI 走向语言与语音**：**From Neurons to Conversation: Speech Brain-Computer Interfaces**（[2609.36736](https://arxiv.org/abs/2609.36736)）、**NEUROTOKEN**（[2610.00397](https://arxiv.org/abs/2610.00397)，听觉注意 + 包络解码）、**BrainNet Studio**（[2609.37956](https://arxiv.org/abs/2609.37956)）。
  - **需要保留的怀疑**：把 LLM 当"脑模型"的类比今年被更严格检验——**能接受不同电极配置 ≠ 表征稳定**（[2609.36288](https://arxiv.org/abs/2609.36288)），CLIP 用于脑解码还有对抗鲁棒性问题（[2607.03165](https://arxiv.org/abs/2607.03165)）。**"LLM 和大脑一样"是被过度解读最多的一类结论。**
- **理论的地基：kernel / 高斯过程 / 神经算子 / bandit / 优化 / 量子**。ICLR 2026 学习理论 190 篇、优化 191 篇、概率方法 116 篇——**数量远超几乎任何应用方向，但没有一条热搜**。值得点名：**Feedback-driven recurrent quantum neural network universality**（rating 8）、**Special Unitary Parameterized Estimators of Rotation**（rating 8.5）、**Nesterov Finds GRAAL**（自适应凸优化最优率）、**Cautious Weight Decay**、**Symmetry-Aware Bayesian Optimization via Max Kernels**、**Revisiting Nonstationary Kernel Design for Multi-Output Gaussian Processes**、**Probabilistic Kernel Function for Fast Angle Testing**（rating 8）。bandit 相关标题 28 个、GP 5 个——**安静、高信号，且正在被 LLM 时代重新调用**。补漏检索还抓到：**量子 ML 正从玩具走向可证明结果**（**Fourier Symmetrization for Geometric Quantum Machine Learning** [2610.01874](https://arxiv.org/abs/2610.01874)、**Classical Hardness of Learning Functions of Hamiltonians** [2610.01141](https://arxiv.org/abs/2610.01141)、**The Single-Copy Quantum Bandit Is Classical** [2609.40339](https://arxiv.org/abs/2609.40339)）；bandit 侧有 **Bandits with Multiple Optimal Arms: Minimax Regret and Non-Adaptivity**（[2609.38659](https://arxiv.org/abs/2609.38659)）与 **Learning When to Update: A Near-Optimal Timing Bandit Approach**（[2609.37932](https://arxiv.org/abs/2609.37932)）；kernel 侧有 **Deep kernel hedging**（[2609.34474](https://arxiv.org/abs/2609.34474)）。
- **人本 AI：教育 / 医疗落地 / 社会模拟**。教育侧代表是 **SHAPE**（统一安全、有用性与教学法, [2604.22134](https://arxiv.org/abs/2604.22134)）、**Evaluating LLMs for Answering Student Questions in Introductory Programming**（[2603.28295](https://arxiv.org/abs/2603.28295)）、**教育 tutor 的 prompt injection 防御权衡**（[2605.06669](https://arxiv.org/abs/2605.06669)）；医疗落地侧，除 3.20 的 LungIMPACT 阴性 RCT 外，还有**临床分诊偏见的反事实审计**（[2610.01963](https://arxiv.org/abs/2610.01963)）、**MIMIC-IV 的交叉性公平评估**（[2610.01645](https://arxiv.org/abs/2610.01645)）、**神经符号差分诊断 NSIDDx**（[2609.00256](https://arxiv.org/abs/2609.00256)）、**跨语言临床标注投影**（[2609.11450](https://arxiv.org/abs/2609.11450)）。**社会模拟**是快速升温又快速被质疑的子领域：一边是 StudentSim（[2609.01591](https://arxiv.org/abs/2609.01591)，HF 494 票）、"用 LLM 模拟问卷受访者"，另一边是同期多篇证伪——**LLM 模拟人群会抹平跨文化方差、个体层面预测不成立、marginal fidelity 不等于有效模拟**。**结论：LLM 社会模拟能做群体级相关，不能替代个体级测量。**
- **安全机制与知识控制（与 3.18 互补）**：3.18 讲对齐与评测，这里讲**攻击机制与知识操纵**。
  - **MCP / 工具投毒是最具体的攻击面**：**ShareLock**（[2606.27027](https://arxiv.org/abs/2606.27027)，多工具阈值投毒）、**TRUSTDESC**（[2604.07536](https://arxiv.org/abs/2604.07536)，可信描述生成防御）、**MCP Threat Modeling**（[2603.22489](https://arxiv.org/abs/2603.22489)，用 STRIDE 对 MCP 客户端做威胁建模）、**MCP-ITP**（[2601.07395](https://arxiv.org/abs/2601.07395)，自动化隐式工具投毒）。
  - **Agent 安全已成体系**：**Prompt Injection Threats in LLM Agents**（SoK, [2602.10453](https://arxiv.org/abs/2602.10453)）、**The Attack and Defense Landscape of Agentic AI**（[2603.11088](https://arxiv.org/abs/2603.11088)）、**Connecting the Dots in Agentic AI Security**（[2609.23894](https://arxiv.org/abs/2609.23894)，跨维度威胁分类）、**Aletheia**（[2609.39678](https://arxiv.org/abs/2609.39678)，对 coding-agent 规则做"权限最小性"测试）、**From A2A Attacks to Envelope-Layer Defense**（[2610.00392](https://arxiv.org/abs/2610.00392)，A2A/ACP 协议层间接注入）、**The Innocent Courier**（[2610.01768](https://arxiv.org/abs/2610.01768)，借合法网页抓取做隐蔽外泄）、**Layered LLM Defenses as an Ensemble**（[2608.28327](https://arxiv.org/abs/2608.28327)，指出多层防御只在"不同层在不同输入上失败"时才真正叠加，而文献从不测量这一点）。OpenART（[2608.00677](https://arxiv.org/abs/2608.00677)）与 AgentDoG 1.5（[2605.29801](https://arxiv.org/abs/2605.29801)）提供红队与对齐侧工具。
  - **模型编辑 / 合并是被热点综述漏掉的一块**：ICLR 2026 标题含 merging 的接收论文 24 篇、model editing 9 篇。编辑从"一次性改事实"转向**终身/序列化编辑**：**Generalizable Lifelong Model Editing via Preference Optimization**（[2609.36748](https://arxiv.org/abs/2609.36748)）、**ManiEdit**（[2609.33534](https://arxiv.org/abs/2609.33534)，流形视角的序列化长文本知识编辑）、**ALOE**（[2609.29269](https://arxiv.org/abs/2609.29269)，把编辑同时当作"写"与"寻址"问题）。合并开始研究**几何结构**：**No Task Vector Is an Island**（[2609.39405](https://arxiv.org/abs/2609.39405)，on-policy distillation 得到的任务向量可组合性）、**Orthogonal Yet Coupled**（[2609.37564](https://arxiv.org/abs/2609.37564)，解耦任务向量内部几何分量），并有综述 **From Parameters to Behaviors: A Survey of Model Fusion**（[2609.19553](https://arxiv.org/abs/2609.19553)，背景是 HF 已有 >2M 个模型）；**Unmerge**（[2609.38895](https://arxiv.org/abs/2609.38895)）把任务算术反过来用于遗忘。
  - **watermarking 正从"打水印"转向"溯源基础设施"**（WARP, [2609.40031](https://arxiv.org/abs/2609.40031)；隐频掩蔽可攻破图像水印 [2610.02010](https://arxiv.org/abs/2610.02010)）。
- **检索与推荐**：ICLR 2026 含 retrieval 的接收论文 **78 篇**、recommend 15 篇；工业侧代表是 **Kuaishou Explorer LLM-Rec Challenge 2026**（推理式生成推荐, [2609.39828](https://arxiv.org/abs/2609.39828)）、**Generative End-to-end Ad Retrieval at Douyin**（[2609.39327](https://arxiv.org/abs/2609.39327)）、**On the Complexity of Preference-Based Bandits**（[2609.39351](https://arxiv.org/abs/2609.39351)）。判断：**推荐/检索的学术增量正被 LLM 吸收，而工业侧在"生成式推荐 + 大规模扩展"上继续真实推进**。
- **语音 / 音频理解**（3.11 讲生成，这里补理解与全双工）：Mega-ASR（[2605.19833](https://arxiv.org/abs/2605.19833)）、Realtime-Venus（[2609.13814](https://arxiv.org/abs/2609.13814)）、OmniVChat（[2609.21465](https://arxiv.org/abs/2609.21465)）、AudioSAE（[2606.03086](https://arxiv.org/abs/2606.03086)）。
- **3D / 图形 / 渲染**：ICLR 2026 标题含 "3D" 的接收论文 **135 篇**，CVPR 2026 的 3D/4D/GS 桶 **748 篇**——**规模巨大但范式趋稳**。代表：Utonia（[2603.03283](https://arxiv.org/abs/2603.03283)）、ABot-Earth 0.5（[2606.09967](https://arxiv.org/abs/2606.09967)）、3DROID（[2610.01744](https://arxiv.org/abs/2610.01744)）、Dyna3（[2610.01286](https://arxiv.org/abs/2610.01286)）、BayesianGS-SLAM（[2609.24140](https://arxiv.org/abs/2609.24140)）。**判断：Gaussian splatting 从"范式"变成"工程与数据"，真正的创新迁移到了生成式 3D 与动态 4D。**

---

## 4. 重点论文总表（跨全部板块）

下表是本报告认为最值得读的代表性工作，按板块分组（链接为 arXiv 或 OpenReview / 官方页）。

### 基础模型 / 预训练 / 架构
| 论文 | 为什么值得看 |
|---|---|
| [Kimi K3](https://arxiv.org/abs/2607.24653) | 2.8T MoE、1M 上下文、KDA + Stable LatentMoE，2.5× scaling 效率 |
| [DeepSeek-V4.1-Flash](https://arxiv.org/abs/2609.19969) | 552B MoE + 1M 上下文 + 极限 KV 压缩 |
| [Pre-training under infinite compute](https://openreview.net/forum?id=) | ICLR 2026 oral；数据固定、算力无限下的配方 |
| [Mamba-3](https://openreview.net/forum?id=) | ICLR 2026 oral；SSM 视角的序列建模 |
| [Transformers are Inherently Succinct](https://arxiv.org/abs/2510.19315) | ICLR 2026 最佳论文；为什么 Transformer 仍然赢 |
| [HRM-Text](https://arxiv.org/abs/2605.20613) | 层级递归模型预训练，绕开纯 scaling |
| [BDH-CQ](https://arxiv.org/abs/2608.09888) | 递归潜在推理；ARC-AGI-1 成本-精度新前沿 |
| [MLP 优化器：Muon with Finite Newton-Schulz](https://arxiv.org/abs/2608.26288) | 优化器成为独立热点 |

### 后训练 / RL / 蒸馏 / 推理
| 论文 | 为什么值得看 |
|---|---|
| [T1: Terminal Agent RL](https://arxiv.org/abs/2609.11042) | TBench 2.1 43.8→64.0%；**GRPO 不涨、PPO+critic 涨** |
| [The Art of Scaling RL Compute](https://openreview.net/forum?id=) | ICLR 2026 oral；RL 计算-性能曲线 |
| [Scaling Properties of Same-Family OPD](https://arxiv.org/abs/2609.32722) | OPD 的 √KL 转移律与幂律 |
| [Rethinking On-Policy Distillation](https://arxiv.org/abs/2604.13016) | OPD 成功的两个条件与机制 |
| [On-Policy or Off-Policy?](https://arxiv.org/abs/2609.35259) | 受控实验：rollout policy 未必是关键，KL 方向更重要 |
| [A Survey on Rubric-Guided RL](https://arxiv.org/abs/2608.27505) | 用贝叶斯框架统一 rubric/宪法/过程监督 |
| [Unsupervised Post-Training of Foundation Models](https://arxiv.org/abs/2608.24982) | 80 个 UPT 方法的分类学（无标签后训练） |
| [A Survey on Self-Improving Test-Time Intelligence](https://arxiv.org/abs/2609.01679) | 把 test-time adaptation / learning / scaling 统一 |
| [Is it Thinking or Cheating? (TRACE)](https://openreview.net/forum?id=) | ICLR 2026 oral；隐式 reward hacking 检测 |
| [Reward Hacking Benchmark](https://arxiv.org/abs/2605.02964) | ICML 2026；RL 后训练把 hacking 0.6%→13.9% |
| [The Dark Room in the Reward Channel](https://arxiv.org/abs/2607.21273) | 预注册 74 arms；dense reward 在 GRPO 下反转 |
| [In-Place Test-Time Training](https://openreview.net/forum?id=) | ICLR 2026 oral；推理时更新 fast weights |
| [The Coverage Principle](https://openreview.net/forum?id=) | ICLR 2026 oral；预训练为何能开启后训练 |

### Agent / harness / skills / 长时程
| 论文 | 为什么值得看 |
|---|---|
| [Raven: The Harness of Harnesses](https://arxiv.org/abs/2609.33439) | harness 的自动构造、演化与跨域编排 |
| [StateM](https://arxiv.org/abs/2608.15089) | harness scaling；Terminal-Bench 2.1 声称 95.3% |
| [HarnessDev](https://arxiv.org/abs/2609.01437) | 让 LLM 自己创造并演化 harness |
| [Harness Handbook](https://arxiv.org/abs/2607.13285) | 形式化"行为→代码"定位问题 |
| [Mid-Harness](https://arxiv.org/abs/2609.39982) | 在模型与 harness 之间加验证器分配 test-time compute |
| [DarwinX](https://arxiv.org/abs/2608.07545) | 用自然选择进化 harness |
| [SoL-Pi](https://arxiv.org/abs/2609.20519) | 把 auto-research loop 扩到 production harness |
| [A Systematic Survey of Agentic Skills](https://arxiv.org/abs/2608.29596) | skill 的九阶段生命周期与安全治理 |
| [SkillOpt](https://arxiv.org/abs/2605.23904) | 把 skill 当"冻结 agent 的外部状态"来训练 |
| [Efficient GUI Agents (systems survey)](https://arxiv.org/abs/2609.02309) | GUI agent 的效率系统学 |
| [ComputerRL](https://arxiv.org/abs/2508.14040) | ICLR 2026；OSWorld 48.9%，RL +66% |
| [CompactionRL](https://arxiv.org/abs/2607.05378) | 把上下文压缩训进 RL；进入 GLM-5.2 pipeline |
| [SWE-MILE](https://arxiv.org/abs/2609.32631) | 从运行时势能导出过程监督，无需 reward model |
| [T²PO](https://arxiv.org/abs/2605.02178) | ICML 2026 Spotlight；不确定性引导的多轮探索 |
| [SimpleTIR](https://arxiv.org/abs/2509.02479) | ICLR 2026；过滤 void turns 稳定多轮工具 RL |
| [DeepSWE](https://arxiv.org/abs/2607.07946) | 反污染的长时程编码 benchmark |
| [EdgeBench](https://arxiv.org/abs/2607.05155) | 部署后环境学习的 log-sigmoid 定律（R²=0.998） |
| [Agents' Last Exam](https://arxiv.org/abs/2606.05405) | 250+ 专家、13 行业簇的长时程评测 |
| [Thinkingbox](https://arxiv.org/abs/2608.19741) | pass@1 → pass^20 的可靠性崩塌 |

### RSI / 自改进 / 自动科研
| 论文 | 为什么值得看 |
|---|---|
| [AIDE²](https://arxiv.org/abs/2609.26457) | 最强闭环 RSI；ignition test 是负结果 |
| [AI4AI-Bench](https://arxiv.org/abs/2608.20318) | 最锋利的怀疑测量：290 次提交 124 次更差 |
| [FARS](https://arxiv.org/abs/2606.31651) | 417 小时 / 166 篇论文；均分 3.17/10 |
| [Gödel Forest](https://arxiv.org/abs/2609.36675) | 数据层 RSI，+10.70 分 |
| [Mendel Gödel Machine](https://arxiv.org/abs/2608.07645) | 比较式进化，Polyglot 50.8→93.2 |
| [The Red Queen Gödel Machine](https://arxiv.org/abs/2606.26294) | 让 evaluator 也一起演化 |
| [RSI survey (1,250 papers)](https://arxiv.org/abs/2607.07663) | 验证层级与失败模式分类学 |
| [REUSE](https://arxiv.org/abs/2609.33180) | 复用 benchmark 的假晋升最高 20.7%→0% |
| [More Convincing, Not More Correct](https://arxiv.org/abs/2607.05904) | 自博弈 judge 可被刷：0.716→0.938 而准确率不动 |
| [What is Missing from AI Post-Training AI](https://arxiv.org/abs/2608.19072) | 1,338 条轨迹只有 2.1% 改变策略 |
| [Shadow evaluations](https://arxiv.org/abs/2607.27191) | agent 做未发表论文核心问题，两篇全拒 |
| [ReSAIL](https://arxiv.org/abs/2609.39306) | 迭代自蒸馏的崩溃与修复 |
| [Safety in Self-Evolving Agents](https://arxiv.org/abs/2610.00093) | SAVER：自演化 agent 安全的转移中心框架 |

### 长上下文 / memory / RAG
| 论文 | 为什么值得看 |
|---|---|
| [LLMs Get Lost In Multi-Turn Conversation](https://arxiv.org/abs/2505.06120) | ICLR 2026 最佳论文；-39%、unreliability +112% |
| [Intent Mismatch Causes LLMs to Get Lost](https://arxiv.org/abs/2602.07338) | 2026 跟进；Mediator-Assistant |
| [Cracks in the Foundation](https://arxiv.org/abs/2608.10296) | 26 个 matched 7B；四个"小选择"掉 47 分 |
| [RoPE at the End of Its Rope?](https://arxiv.org/abs/2609.39929) | RoPE 极限可证明/可诊断；重缩放 +20/+25pp |
| [Context Compaction Theory](https://arxiv.org/abs/2608.01326) | 压缩的信息论下界 |
| [Governance Decay](https://arxiv.org/abs/2606.22528) | 压缩删掉安全约束：违规 0%→30% |
| [Retrieval and Multi-Hop Reasoning in 1M Tokens](https://arxiv.org/abs/2605.02173) | 单针 100%，多跳退化 |
| [To Memorize or to Retrieve](https://arxiv.org/abs/2604.00715) | 记忆-检索的 scaling law |
| [DolphinBench](https://arxiv.org/abs/2609.24971) | 动作级 memory benchmark |
| [Continual Learning Mechanisms Compose](https://arxiv.org/abs/2609.06986) | 100 任务长时程记忆；单机制全部失败 |
| [Retrieved But Not Reliable (RAG security)](https://arxiv.org/abs/2608.24977) | RAG 威胁模型与流水线防御 |

### 多模态 / 视觉 / 生成媒体
| 论文 | 为什么值得看 |
|---|---|
| [D4RT](https://arxiv.org/abs/2512.08924) | CVPR 2026 最佳论文；动态 4D 重建 200+ FPS |
| [O-Voxel / TRELLIS.2](https://arxiv.org/abs/2512.14692) | CVPR 2026 最佳学生论文；原生紧凑 3D 潜变量 |
| [SAM 3](https://arxiv.org/abs/2511.16719) | ICLR 2026；概念提示分割 |
| [Depth Anything 3](https://arxiv.org/abs/2511.10647) | ICLR 2026；+35.7% 位姿 / +23.6% 几何 |
| [BabyVision](https://arxiv.org/abs/2601.06521) | ICML 2026；Gemini 3 Pro 49.7 < 六岁儿童 |
| [Video-MME-v2](https://arxiv.org/abs/2604.05015) | 针对"榜单虚高"的视频理解评测 |
| [DatBench](https://arxiv.org/abs/2601.02316) | 某些 VLM 评测最多 70% 不看图可答 |
| [Z-Image](https://arxiv.org/abs/2511.22699) | 6B 模型、314K H800 小时，开源图像生成效率标杆 |
| [SenseNova-U1 / U1.5](https://arxiv.org/abs/2605.12500) | 原生统一理解+生成 |
| [Vidu S2](https://arxiv.org/abs/2609.11638) | 实时 720p 交互式 + **流式视频编辑** |
| [Helios](https://arxiv.org/abs/2603.04379) | 单卡 H100 上 19.5 FPS 的长视频生成 |
| [Physion-Eval](https://arxiv.org/abs/2603.19607) | 83%+ 生成视频有物理错误 |
| [WorldMark](https://arxiv.org/abs/2604.21686) | 世界模型单分数榜单会误导；质量与延迟负相关 |
| [AuK](https://arxiv.org/abs/2609.08936) | 统一语音生成+编辑（编辑 exact-match 仅 13.85%） |
| [Lychee-FD (ACL 2026 Outstanding)](https://aclanthology.org/2026.acl-long.419/) | 全双工语音的声学/语义梯度冲突 |

### 世界模型 / 具身 / 生成建模
| 论文 | 为什么值得看 |
|---|---|
| [Orca: The World is in Your Mind](https://arxiv.org/abs/2606.30534) | 统一 world latent + Next-State-Prediction |
| [Programmable World Model](https://arxiv.org/abs/2609.10540) | 世界状态演化与视觉生成解耦，可编程 |
| [ABot-World-0](https://arxiv.org/abs/2607.19191) | 单张 RTX 5090 上无限 rollout |
| [Astronex-World 1.0](https://arxiv.org/abs/2609.20034) | 开放权重交互式世界模型 |
| [Training Object Permanence in World Models](https://arxiv.org/abs/2609.28654) | 150 认知任务证明世界模型不懂物理 |
| [World-Action Models survey](https://arxiv.org/abs/2609.16074) | WAM 的统一分类学 |
| [Qwen-VLA](https://arxiv.org/abs/2605.30280) | 跨任务/环境/本体的统一 VLA |
| [MolmoAct2](https://arxiv.org/abs/2605.02881) | 全年机器人最高票；面向部署的开放 VLA |
| [Qwen-Drive-1.0](https://arxiv.org/abs/2609.00111) | 自动驾驶 VLM 基础模型 |
| [DiffusionGemma](https://arxiv.org/abs/2608.00146) | 每次前向约 20 token 的扩散 LM |
| [LLaDA MoE v2](https://arxiv.org/abs/2608.03457) | 首个 MoE-dLLM scaling law |
| [LangFlow](https://arxiv.org/abs/2604.11748) | 连续扩散追平离散扩散 |
| [The Flexibility Trap](https://arxiv.org/abs/2601.15165) | ICML 2026 最佳论文；任意顺序并不更优 |

### 效率 / 系统 / 安全 / 科学 / 其它
| 论文 | 为什么值得看 |
|---|---|
| [Why Is Video Still So Expensive?](https://arxiv.org/abs/2609.10355) | 视频/音视频 LLM 推理效率机制综述 |
| [Efficient Video Diffusion Models](https://arxiv.org/abs/2604.15911) | 722 篇加速论文的四范式分类 |
| [MinT](https://arxiv.org/abs/2605.13779) | 管理"百万个 LoRA 策略"的训练与服务 |
| [A Single Neuron Is Sufficient to Bypass Safety](https://arxiv.org/abs/2605.08513) | 单神经元绕过对齐，7 模型 91.7% ASR |
| [The Obfuscation Atlas](https://arxiv.org/abs/2602.15515) | ICML 2026 HM；训练对抗欺骗探针会催生混淆 |
| [Realistic honeypot evaluations](https://arxiv.org/abs/2605.29729) | Gemini 不会无缘无故耍阴谋；评测意识是混淆 |
| [When Behavioral Safety Evaluation Fails](https://arxiv.org/abs/2606.08044) | 通过所有静态审计却在潜在扰动下失守 |
| [Storage Is Not Strategy](https://arxiv.org/abs/2609.37858) | 遗忘学习的方法论危机 |
| [Memorization Is Not Extraction](https://arxiv.org/abs/2608.27782) | 记忆与抽取互不控制；DP 盲点 |
| [Stealing Reasoning Traces from Proprietary LLM APIs](https://arxiv.org/abs/2608.09867) | 加密 CoT 被打穿 |
| [Orphan risks](https://arxiv.org/abs/2608.16895) | 四家实验室安全/合规文档的选择效应 |
| [OpenART](https://arxiv.org/abs/2608.00677) | 10,000+ 有状态场景的 agent 红队 |
| [Use and Effects of LLMs in Peer Review](https://arxiv.org/abs/2609.19420) | ICML 2026 随机实验：禁用组仍 22.5% 用 LLM |
| [AlphaProof Nexus](https://arxiv.org/abs/2605.22763) | Lean 自主解决 9/353 个开放 Erdős 问题 |
| [AlphaEvolve (PNAS)](https://www.pnas.org/doi/10.1073/pnas.2536158123) | 陶哲轩参与；67 个数学问题 |
| [Atlas / AutoformBot](https://arxiv.org/abs/2605.29955) | 26 本教材 → 45,000+ 条 Lean 声明 |
| [MechGeo](https://arxiv.org/abs/2608.02295) | 不只证明，还构造 Lean 验证的反例 |
| [Evo 2](https://www.nature.com/articles/s41586-026-10176-5) | 9T bp、1M 上下文的基因组基础模型 |
| [AlphaGenome](https://www.nature.com/articles/s41586-025-10014-0) | 1Mb 输入、单碱基调控轨迹 |
| [WeatherNext Cyclones](https://www.nature.com/articles/s41586-026-10953-2) | 台风预报 >1 天提前量 |
| [LungIMPACT RCT](https://www.nature.com/articles/s41591-026-04253-5) | n=93,326 的**阴性**临床 AI 试验 |
| [A Survey on the Linear Representation Hypothesis](https://arxiv.org/abs/2609.22695) | 把 LRH 变成可证伪假设 |
| [A Survey on Self-Improving Test-Time Intelligence](https://arxiv.org/abs/2609.01679) | （重复出现，因其为统一视角） |

---

## 5. 全局判断：这一年到底发生了什么

**把 2025Q4–2026Q3 的 AI 研究压缩成一句话：领域从"造更强的模型"转向"造更可靠的系统、并诚实地衡量它"。** 下面是我认为最值得记住的判断，按重要性排序。

1. **后训练是主战场，且正在"系统化"。** RL（GRPO/RLVR）+ on-policy distillation 是增长最快的技术栈；但 2026 的关键不再是"再发明一个 GRPO 变体"，而是**环境、验证器、异步基础设施、上下文/记忆管理**这些系统层要素。T1 的"GRPO 不涨、PPO+critic 涨"和 Dark Room 的"dense reward 被归一化反转"是两个必须知道的机制性结果。
2. **"Agent harness" 是这一年最有辨识度的新概念。** 收益来自**冻结模型外面的可演化执行系统**，而不是模型参数。这解释了为什么 "agent harness" 主题暴涨、为什么 agent 论文都在谈 harness/skills/memory，也解释了为什么"更长上下文"不再是核心。
3. **RSI 从口号变成了有分类学的子领域——但仍是"工程闭环"，不是"复利加速"。** 证据（AIDE² 的负 ignition test、AI4AI-Bench 的 124/290、策略锁死的 2.1%）非常一致：**瓶颈是验证与方向选择，不是生成**。
4. **评估/验证是整个领域的公共瓶颈，而且问题已经蔓延到科研系统自身。** 从 benchmark 污染、pass@1 高估、静态安全审计过度认证，到 ICML 795 条 AI 评审 / NeurIPS 28.2% AI 撰写 / ICLR 数据泄露——**"信不信得过"是 2026 最稀缺的能力**。
5. **On-policy distillation 是被低估的富矿。** weak-to-strong 能超过老师、有 √KL 律与幂律、并分化出多教师/双向/agentic/多模态分支；但它与 RL 的分工还没有定论（"rollout policy 未必是关键"）。
6. **长文本作为"长度军备竞赛"结束，作为"memory/compaction/可靠性"研究非常活跃。** 1M 是标配、单针解决、多跳未解决；compaction 有信息论下界、会删安全约束、正被 RL 训进 agent；多轮可靠性成为最高荣誉。
7. **除 agent 外，最大的能力变量是扩散/并行生成 LM。** DiffusionGemma/LLaDA MoE v2/LangFlow 把 dLLM 推到可用的开放权重规模；同时领域在自我纠偏（The Flexibility Trap）。
8. **多模态的"统一理解+生成"成为默认框架，但证据仍薄**（Tuna-2 四个月内反转了 TUNA 的结论）；**真正的能力跃迁在视频与 3D 几何**（D4RT、O-Voxel、Depth Anything 3）；而**视觉原语仍是瓶颈**（BabyVision：Gemini 3 Pro 49.7）。
9. **生成媒体是最热也最需要怀疑的领域。** 它几乎没有同行评审，而它自己的评测论文反复证明"好看 ≠ 有物理/控制能力"（Physion-Eval、WorldMark、VGI-Bench）。**引用"SOTA"时请当作营销。**
10. **世界模型复兴，但"世界模型"的定义尚未统一，且被自己人打假**（WROP：并不天然具备客体永久性）。它的真实进展是**可交互、实时、可编程、开放权重**。
11. **AI for science：形式化数学是最干净的胜利**（验证免费）；基因组/蛋白质/天气有真正的里程碑；**但"自主发现"多为半自主，临床 AI 最有力的证据是一个 n=93,326 的阴性 RCT**。
12. **安全研究的重心从"对齐方法"转向"证伪评测"。** 单神经元绕过（91.7% ASR）、SAE 干预不可靠、审计 gap、遗忘学习危机、DP 盲点——**这一年的安全进展主要是"发现我们之前高估了安全性"**。
13. **非 LLM ML 没有消失，而是与 LLM 交叉。** 图/时间序列/因果/推荐/表格/联邦/经典 RL 稳定产出（ICML 2026 各约 30–140 标题），新增长点在 "graph+LLM""time-series agent""causal+LLM"。
14. **综述文献爆炸是"学科化"的标志**：327 篇 AI 综述，从 agentic skills 到 linear representation hypothesis，说明领域在**快速自我整理**——也可能说明它正在**从"发现"转向"整合"**。
15. **最该被记住的一句话**：这一年最重要的进展，**一半是"我们真的能做出东西了"（agent/harness、RL 后训练、dLLM、视频、形式化数学），另一半是"我们发现之前骗了自己"（RSI 不加速、RL 增益存疑、benchmark 不可信、安全审计过度认证、生成媒体评测失效）**。成熟的表现不是只有前者。

### 如果只记三件事
- **做系统，不只是做模型**：harness / memory / 环境 / 验证器 / 训练配方比参数更重要。
- **做验证，因为它是所有主线的咽喉**：agent RL、RSI、自动科研、科研评审都被它卡住。
- **对"能力"保持怀疑，用可靠性指标（pass^k、多轮、分布外、闭环）而不是 pass@1 或视觉质量来判断**。

---

## 6. 局限与不确定（以及这一轮补了什么）

> **一句话**：主要瓶颈已从"拿不到数据"变成"口径不统一"；剩下的硬缺口只有 NeurIPS 2026 主赛道与 ACL 关键词。

**这一轮已经补上的（上一版问题 → 现状）：**

| 上一版的局限 | 现在 |
|---|---|
| 年度同比只有 ICLR + NeurIPS 两条曲线 | **四组独立曲线**：ICLR 2024-26、NeurIPS 2024-25（关键词口径）+ **ICML 2024-25-26**（PMLR 官方标题）+ **CVPR 2025-26**（CVPR Open Access 标题） |
| OpenAlex 索引滞后 + 免费额度耗尽 | 年度同比改用 **arXiv API 直接计数 100 个主题 × 两个 12 个月窗口**，并用 cs.LG/CL/AI/CV 总量做份额归一化；OpenAlex 仅作 30 主题的旁证 |
| ICML 2026 只有 418 条 | 用**官方 6,628 个标题**补全，得到 ICML 2024→2025→2026 三点趋势（Reasoning 2.1%→5.1%→9.1%） |
| CVPR 2026 只有 241 条 | 用 **CVPR Open Access 的 4,042 个标题**补全（对照 2025 年的 2,330 个） |
| HF 8–9 月覆盖偏薄（子代理称归档在 2026-07-20 中断） | 我自己的全量抓取**确实覆盖了 8–9 月**（8 月 670 篇、9 月 676 篇），全年 366 天 / 8,511 篇 |
| 只覆盖三条线 | 新增 **3.24 补遗**：神经/BCI、量子 ML、kernel/GP/bandit、教育/医疗/社会模拟、agent 安全、模型编辑与合并、检索推荐、语音理解、3D/图形 |

**剩下的真实局限（不掩饰）：**

- **NeurIPS 2026 无法获取**：官网 virtual 返回 403，OpenReview group 明确写着 **public_submissions = false**，API 需过 challenge。因此 NeurIPS 2026 只有 position-track 的官方统计（28.2% AI 撰写等），**主赛道接收列表与奖项仍缺**。
- **ACL 2024/2025 无关键词**：ACL Anthology 标题可抓，但论文级关键词缺失，因此 **ACL 没有进入同比**（只作为个别引用）。
- **关键词口径 vs 标题口径不可直接比**：ICLR/NeurIPS 用作者关键词（占比偏高、语义更全），ICML/CVPR 用标题（占比偏低）。我只在同一来源内部比较趋势，**不做跨来源绝对值比较**。
- **HF upvote 是注意力，不是质量**：安全、非 LLM、人本 AI 在 HF 上普遍票数低（150–330 vs 模型发布 800+），所以这些板块的排序**没有**依赖 upvote。
- **arXiv 计数有措辞偏差**：如 "long-horizon agent" vs "agentic RL"；100 主题 + 多源三角验证能降低但不能消除单点误差。
- **子代理覆盖**：本轮共 **13 个方向**的深读（9 个主板块 + 4 个补漏板块），每份都在其文件里声明了"读全文 / 只读摘要"的边界；仍可能漏掉非英文、非 arXiv、工业界博客的工作。完整笔记见 [notes/](notes)。
- **时间边界**：覆盖到 2026-10-01 左右；几天前的新 arXiv ID 尚无社区共识。
- **这不是终极结论**：它是"给定数据下的快照与判断"。证据与判断分开书写，读者可只取证据、自下结论。



