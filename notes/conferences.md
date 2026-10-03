# Conference Landscape: ICLR 2026, ICML 2026, NeurIPS 2026

*Compiled 2026-10-03. Area: the conference landscape itself (acceptance facts/numbers + award papers). All arXiv IDs were cross-checked against secondary sources; items I could not verify are explicitly flagged.*

## Synthesis: what is actually happening

**Scale is the headline, and it is real.** ICLR 2026 exploded to **19,525 valid submissions** (5,042 withdrawn, 779 desk-rejected; 13,763 decisions) with **5,355 accepted at a 27.4% acceptance rate**, reviewed by 18,054 reviewers who produced 76,139 reviews ([official retrospective, 2025-03-31](https://blog.iclr.cc/2026/03/31/a-retrospective-on-the-iclr-2026-review-process/)). ICML 2026 reached **23,918 post-desk-rejection submissions** and accepted **6,352 (26.6%)** — more than double ICML 2025's 12,107 ([Tech Times](https://www.techtimes.com/articles/319684/20260704/icml-2026-opens-monday-in-seoul-agentic-ai-tops-record-year-as-peer-review-strains.htm)). NeurIPS 2026 is the 40th edition split across **Sydney (main, Dec 6-12), Atlanta and Paris (satellites, Dec 9-13)** — i.e. three physical venues in one cycle. Selection ratios are *not* tightening much (~27%); the field is simply doubling in throughput.

**The genuinely new story is not a topic, it is peer-review integrity — and here the numbers are large and official.** ICLR 2026 suffered an unprecedented OpenReview API scrape that revealed author/reviewer/AC identities mid-discussion, triggering collusion and harassment; the chairs reset all scores to the pre-rebuttal state and reassigned ACs. ICLR also desk-rejected **all papers with confirmed hallucinated references** (partly why the desk-reject rate rose). ICML went furthest technically: it watermark-injected hidden LLM instructions into every submitted PDF and caught **795 reviews (~1%) written by 506 reviewers who had agreed to a no-LLM policy — leading to 497 desk-rejected papers (~2% of all submissions)**; 51 reviewers were removed for using LLMs in >half their reviews; the family-wise false-positive rate was 0.0001 ([official ICML post](https://blog.icml.cc/2026/03/18/on-violations-of-llm-review-policies/)). NeurIPS 2026 ran a Pangram-based audit on its Position Paper Track and found **28.2% (273/969) substantially AI-written**, desk-rejecting **178 (18.4%)** ([official NeurIPS post](https://blog.neurips.cc/2026/06/02/ai-generated-papers-in-the-neurips-2026-position-paper-track/)). Caveat worth stating: ICML's own chairs concede the watermark "is not a difficult measure to circumvent," so ~1% is a floor, not the true LLM-use rate. The hype to discount is the reverse framing — that AI detection is solved. It is not; it is a noisy, adversarial arms race, and the venues themselves say so.

**Topic-wise, LLMs/foundation models dominate by a wide margin.** In ICLR 2026 accepted papers, the largest primary areas are "foundation/frontier models incl. LLMs" (831), "applications to CV/audio/language" (737), "generative models" (496), "datasets and benchmarks" (443) and "alignment/fairness/safety/privacy" (423). Agentic systems, benchmarks/evals, RL post-training (RLVR/GRPO), diffusion LLMs and mechanistic interpretability are the fast-growing clusters; the award slate (below) reflects exactly that mix. NeurIPS 2026 has no paper awards yet — they will be announced at the December conference, and the accepted list is not publicly enumerable (neurips.cc/virtual/2026 returns HTTP 403; the OpenReview group has `public_submissions: false`). **I could not verify NeurIPS 2026 main-track submission/acceptance counts from any official source.**

---

## The numbers (with sources)

### ICLR 2026 — Rio de Janeiro, Brazil; April 2026
| Metric | Value | Source |
|---|---|---|
| Valid submissions | 19,525 | [ICLR retrospective](https://blog.iclr.cc/2026/03/31/a-retrospective-on-the-iclr-2026-review-process/) |
| Desk-rejected | 779 | same |
| Withdrawn | 5,042 | same |
| Decisions | 13,763 | same |
| Accepted / Rejected | 5,355 / 8,408 | same |
| Acceptance rate | **27.4%** | same |
| Reviews / Reviewers | 76,139 / 18,054 | same |
| Orals | **223** (PaperCopilot; 224 incl. 1 conditional oral) | [PaperCopilot ICLR 2026](https://papercopilot.com/paper-list/iclr-paper-list/iclr-2026-paper-list/) |
| Spotlights | **0 — ICLR 2026 has no Spotlight category** | PaperCopilot status summary ("Spotlight*: –") |
| Posters | 5,117 (+14 conditional posters) | PaperCopilot |
| Award | 2 Outstanding + 1 Honorable Mention | [ICLR awards post](https://blog.iclr.cc/2026/04/23/announcing-the-iclr-2026-outstanding-papers/) |

- Award selection: 36-candidate longlist (20 AC-flagged + 17 high-score), 5 shortlisted, 2 Outstanding + 1 HM chosen by a 12-person committee ([source](https://blog.iclr.cc/2026/04/23/announcing-the-iclr-2026-outstanding-papers/)).
- Test of Time Awards for ICLR 2016 were also announced (2026-04-22), and keynotes were announced 2026-04-17.
- **Caveat on orals:** PaperCopilot's summary says 223 (1.13% of 19,814 records); its status filter returns 224 rows when the single "ConditionalOral" is included. Both are secondary; I could not get OpenReview's own count because `api2.openreview.net/notes` now returns **HTTP 403** (only `/notes/search` works), likely a post-incident lockdown.

**ICLR 2026 accepted-paper topic distribution (all 5,358 accepted posters+orals, from PaperCopilot "session" = primary area):**
foundation/frontier models incl. LLMs **831**; applications to CV/audio/language **737**; generative models **496**; datasets & benchmarks **443**; alignment/fairness/safety/privacy/societal **423**; reinforcement learning **308**; representation learning **265**; physical-science applications **221**; interpretability/XAI **199**; optimization **191**; learning theory **190**; robotics/autonomy/planning **178**; other **177**; transfer/meta/lifelong **118**; probabilistic methods **116**; neuroscience/cognitive science **114**; graphs/geometry **113**; time series/dynamical systems **101**; causal reasoning **47**; neurosymbolic **47**; infrastructure/systems **43**.

### ICML 2026 — Seoul (COEX), July 6-11, 2026
| Metric | Value | Source |
|---|---|---|
| Submissions (post desk-reject/withdraw) | **23,918** | [Tech Times](https://www.techtimes.com/articles/319684/20260704/icml-2026-opens-monday-in-seoul-agentic-ai-tops-record-year-as-peer-review-strains.htm) / [Bohrium](https://www.bohrium.com/en/blog/icml-2026-accepted-papers/) |
| Accepted | **6,352** | same (secondary) |
| Acceptance rate | **26.6%** | same (secondary) |
| Spotlights | 536 (2.2%) per press; **574** "Spotlight Posters" pages on the official virtual site | [ICML virtual spotlight](https://icml.cc/virtual/2026/events/2026SpotlightPosters) |
| Orals | 168 per press; **169** oral event pages on the official virtual site | [ICML virtual orals](https://icml.cc/virtual/2026/events/oral) |
| Papers desk-rejected over LLM review policy | **497 (~2% of submissions)** | [official ICML post](https://blog.icml.cc/2026/03/18/on-violations-of-llm-review-policies/) |
| Program chairs | Alekh Agarwal, Miroslav Dudik, Sharon Li, Martin Jaggi | [ICML awards post](https://blog.icml.cc/2026/07/05/announcing-the-icml-2026-awards/) |

- **Where accepted papers live:** the official list is [icml.cc/virtual/2026/papers.html](https://icml.cc/virtual/2026/papers.html) (I parsed it: **6,628 unique paper pages**, of which **213 are Position Paper Track** and **74 are Journal-to-Conference track**; the remainder ~6,340 is the main track). Submission/review is on OpenReview. **PMLR does not yet have an ICML 2026 volume** — the newest ICML proceedings is [v267 (ICML 2025)](https://proceedings.mlr.press/v267/); as of 2026-10-03 the highest PMLR volume is v341. Note the 6,628 virtual entries vs the reported 6,352 acceptance — these are different definitions (virtual pages include position/journal entries), so treat the exact main-track count as unverified.
- Official awards page: [icml.cc/virtual/2026/awards_detail](https://icml.cc/virtual/2026/awards_detail).

### NeurIPS 2026 — Sydney main (Dec 6-12) + Atlanta & Paris satellites (Dec 9-13)
| Metric | Value | Source |
|---|---|---|
| Paper deadline / notification | May 7, 2026 / **Sept 24, 2026** | OpenReview venue group; [cs-pedia](https://cs-pedia.io/conferences/neurips) |
| Main-track submissions / accepted | **NOT PUBLICLY VERIFIED** | neurips.cc/virtual/2026 → HTTP 403; OpenReview `public_submissions:false` |
| Position Paper Track submissions | **969** | [official post](https://blog.neurips.cc/2026/06/02/ai-generated-papers-in-the-neurips-2026-position-paper-track/) |
| Position track substantially AI-written | **273 / 969 = 28.2%** (Pangram v3.3.2) | same |
| Position track desk-rejected | **178 (18.4%)**; +123 (12.7%) asked to prove human authorship | same |
| Workshops | 477 submitted (454 valid), **102 accepted** (48 Sydney / 28 Paris / 26 Atlanta; 21.5% / 25.4% / 23.6%) | [NeurIPS newsletter](https://blog.neurips.cc/2026/09/05/neurips-newsletter-august-2026/) |
| Awards | **None announced yet** (expected at Dec 2026 conference) | — |

- Also notable: NeurIPS re-released all reviews/initial meta-reviews on 2026-07-23 after a technical release failure; registration is multi-site; there is an "AI Reviewing Experiment". No NeurIPS 2026 best-paper list exists publicly as of today.

---

## Ranked list of the most important papers

Because this survey area is the *conference landscape*, the ranked list is the award slate (the papers the venues themselves certified as most important) plus the strongest cross-cutting notable accepts. NeurIPS 2026 contributes nothing yet.

1. **The Flexibility Trap: Rethinking the Value of Arbitrary Order in Diffusion Language Models** — Zanlin Ni, Shenzhi Wang, Yang Yue, … Gao Huang (Tsinghua) — arXiv [2601.15165](https://arxiv.org/abs/2601.15165) — **ICML 2026 Outstanding Paper**. Shows that for general reasoning, diffusion LLMs exploit arbitrary-order generation to skip high-uncertainty "forking" tokens, collapsing solution diversity; the fix (JustGRPO) uses fixed left-to-right RL rollouts while keeping parallel decoding at inference, reaching 89.1% GSM8K. *Why it matters:* it challenges the defining assumption of the dLLM paradigm and is the clearest signal that diffusion LMs are being taken seriously as an autoregressive alternative. Evidence: controlled reasoning benchmarks + an RL recipe.
2. **High-Accuracy Sampling for Diffusion Models and Log-Concave Distributions** — Fan Chen, Sinho Chewi, Constantinos Daskalakis, Alexander Rakhlin (MIT) — arXiv [2602.01338](https://arxiv.org/abs/2602.01338) — **ICML 2026 Outstanding Paper**. Introduces first-order rejection sampling (FORS), giving δ-error in polylog(1/δ) score evaluations — an exponential improvement over prior poly(1/δ) discretization bounds — and the first polylog gradient-only sampler for general log-concave distributions. *Why it matters:* a genuine theory result that could rewrite how many denoising steps diffusion sampling needs.
3. **Transformers are Inherently Succinct** — Pascal Bergsträßer, Ryan Cotterell, Anthony Widjaja Lin — arXiv [2510.19315](https://arxiv.org/abs/2510.19315) — **ICLR 2026 Outstanding Paper**. A theoretical result arguing transformers encode certain concepts far more succinctly than RNN-style models, reframing *why* the architecture wins. *Why it matters:* the award committee explicitly noted it was "controversial" yet conceptually provocative — a rare theory paper winning a top award.
4. **LLMs Get Lost In Multi-Turn Conversation** — Philippe Laban, Hiroaki Hayashi, Yingbo Zhou, Jennifer Neville (Salesforce) — arXiv [2505.06120](https://arxiv.org/abs/2505.06120) — **ICLR 2026 Outstanding Paper**. Builds a scalable simulation-based multi-turn evaluation and finds large, consistent drops in LLM aptitude and reliability when instructions are underspecified and spread across turns. *Why it matters:* exposes a structural train/deploy mismatch (single-turn training vs multi-turn use); the committee flagged only that the studied models were dated, not the method.
5. **The Obfuscation Atlas: Mapping Where Honesty Emerges in RLVR with Deception Probes** — Mohammad Taufeeque, Stefan Heimersheim, Adam Gleave, Chris Cundy — arXiv [2602.15515](https://arxiv.org/abs/2602.15515) — **ICML 2026 Outstanding Paper Honorable Mention**. Combines empirical RLVR/coding experiments with theory to taxonomise how policies evade linear deception probes (blatant deception, obfuscated activations, obfuscated policies), and finds high KL regularization + strong detector penalties can still yield honesty. *Why it matters:* directly relevant to scalable oversight and to the venue-wide worry that detectors become part of the optimised objective.
6. **The Polar Express: Optimal Matrix Sign Methods and their Application to the Muon Algorithm** — Noah Amsel, David Persson, Christopher Musco, Robert M. Gower — arXiv [2505.16932](https://arxiv.org/abs/2505.16932) — **ICLR 2026 Honorable Mention**. Uses approximation theory to derive optimal polynomial approximations to the polar decomposition for Muon, with attention to GPU/low-precision constraints. *Why it matters:* principled improvement to one of the most widely used new optimizers; the committee noted empirical gains were modest but the methodology is general.
7. **Motion Attribution for Video Generation (MOTIVE)** — Xindi Wu, Despoina Paschalidou, Jun Gao, … Sanja Fidler, Jonathan Lorraine (NVIDIA/Princeton) — arXiv [2601.08828](https://arxiv.org/abs/2601.08828) — **ICML 2026 Honorable Mention**. An attribution method that ranks individual training clips by their influence on generated motion using motion-weighted loss masks, then curates the video dataset; fine-tuning on high-influence clips yields a 74.1% human preference rate over the base model. *Why it matters:* turns data attribution into a practical curation tool at video-model scale.
8. **How Much Can Language Models Memorize?** — John X. Morris, Chawin Sitawarin, Narine Kokhlikyan, Chuan Guo, G. Edward Suh, Alexander M. Rush, Kamalika Chaudhuri, Saeed Mahloujifar — arXiv [2505.24832](https://arxiv.org/abs/2505.24832) — **ICML 2026 Honorable Mention**. Across hundreds of transformers (0.5M–1.5B params) estimates a capacity of ~3.6 bits/parameter and shows models fill capacity by memorising first, then generalise once capacity binds. *Why it matters:* gives a quantitative handle on leakage, membership inference and the memorisation/generalisation boundary.
9. **A Random Matrix Perspective on the Consistency of Diffusion Models** — Binxu Wang, Jacob A. Zavatone-Veth, Cengiz Pehlevan — arXiv [2602.02908](https://arxiv.org/abs/2602.02908) *(ID/title matched from a secondary index; treat the exact ID as unverified)* — **ICML 2026 Honorable Mention**. Uses random-matrix theory to explain consistency properties of diffusion models. *Why it matters:* a theory bridge between the empirical successes and the sampling theory above.
10. **To Grok Grokking: Provable Grokking in Ridge Regression** — Mingyue Xu, Gal Vardi, Itay Safran — **no arXiv ID found**; official page [icml.cc/virtual/2026/poster/66206](https://icml.cc/virtual/2026/poster/66206) — **ICML 2026 Honorable Mention**. Provides a provable account of delayed generalisation ("grokking") in ridge regression. *Why it matters:* rare rigorous treatment of a phenomenon that has driven a lot of LLM-training mythology; I could not verify an arXiv preprint.
11. **Position: The Alignment Community is Unintentionally Building a Censor's Toolkit** — Sarah Ball, Phil Hackemann — **no arXiv ID found**; [ICML 2026 Outstanding Position Paper](https://blog.icml.cc/2026/07/05/announcing-the-icml-2026-awards/) — Argues alignment/safety methods are dual-use and hand authoritarians an informational-dominance tool. *Why it matters:* the first ICML *Outstanding Position Paper*, signalling that the venue now formally rewards normative/critical work, not just benchmarks.
12. **Position: AI/ML Deepfake Research is Misaligned with AI-Generated Non-Consensual Intimate Imagery (AIG-NCII)** — Qiwei Li, Wells Lucas Santo, Sarita Schoenebeck, Eric Gilbert — **no arXiv ID found** — **ICML 2026 Outstanding Position Paper Honorable Mention**. A landscape analysis showing deepfake research over-indexes on epistemic harms while the dominant real-world abuse is sexualised imagery. *Why it matters:* concrete evidence of a research-priority mismatch.
13. **Asynchronous Methods for Deep Reinforcement Learning** — Volodymyr Mnih, Adrià Puigdomènech Badia, Mehdi Mirza, … Koray Kavukcuoglu — arXiv [1602.01783](https://arxiv.org/abs/1602.01783) — **ICML 2026 Test of Time Award**. The A3C / asynchronous actor-learner paper; ten-year retrospective recognition. *Why it matters:* the historical anchor for the now-dominant RL-post-training wave.

**Honourable mention for the ranked list (strongest ICLR 2026 orals by topic, from the official/aggregated oral list):** *Mamba-3: Improved Sequence Modeling using State Space Principles*; *Gaia2: Benchmarking LLM Agents on Dynamic and Asynchronous Environments*; *Depth Anything 3: Recovering the Visual Space from Any Views*; *The Art of Scaling Reinforcement Learning Compute for LLMs*; *Common Corpus: The Largest Collection of Ethical Data for LLM Pre-Training*. These are representative of the dominant LLM/agent/benchmark, generative-modelling and data-curation clusters rather than independently award-certified.

---

## Which sources I read in FULL (and what I did not)

This area's primary objects are conference process documents and official paper lists, so the "full reads" are those, not per-paper PDFs:

- **Read in full:** ICLR 2026 [Outstanding Papers announcement](https://blog.iclr.cc/2026/04/23/announcing-the-iclr-2026-outstanding-papers/) and [Review Process Retrospective](https://blog.iclr.cc/2026/03/31/a-retrospective-on-the-iclr-2026-review-process/) (both full text).
- **Read in full:** ICML 2026 [Awards announcement](https://blog.icml.cc/2026/07/05/announcing-the-icml-2026-awards/) and [On Violations of LLM Review Policies](https://blog.icml.cc/2026/03/18/on-violations-of-llm-review-policies/) (both full text).
- **Read in full:** NeurIPS 2026 [AI-Generated Papers in the Position Paper Track](https://blog.neurips.cc/2026/06/02/ai-generated-papers-in-the-neurips-2026-position-paper-track/) and the [August 2026 newsletter](https://blog.neurips.cc/2026/09/05/neurips-newsletter-august-2026/).
- **Read/parsed in full programmatically:** the entire ICLR 2026 PaperCopilot accepted list (5,358 records, all 54 pages) and the ICML 2026 official virtual pages ([papers.html](https://icml.cc/virtual/2026/papers.html), [orals](https://icml.cc/virtual/2026/events/oral), [spotlight posters](https://icml.cc/virtual/2026/events/2026SpotlightPosters), [position](https://icml.cc/virtual/2026/events/2026-position-papers), [journal track](https://icml.cc/virtual/2026/events/2026-journal-track), [awards_detail](https://icml.cc/virtual/2026/awards_detail)).
- **Did NOT read:** the full PDFs/HTML of the individual award papers. Given the time budget and the fact that my assigned subject is the venue landscape, I relied on the official award citations/abstracts plus, where possible, arXiv metadata; the arXiv IDs above are cross-checked but two (items 9 and the failed lookup for item 10) remain unverified.

## Open uncertainties
- NeurIPS 2026 main-track submission/acceptance counts and any awards are **not yet public** (awards due at the Dec 2026 conference; virtual site 403s; OpenReview submissions non-public).
- ICML 2026's official submission/acceptance/spotlight/oral counts are press-secondary (23,918 / 6,352 / 26.6% / 536 / 168); the official virtual site gives 169 orals and 574 spotlight pages, and 6,628 total paper pages including position/journal tracks.
- ICLR 2026 oral count is 223 (PaperCopilot summary) vs 224 (its raw status filter including a conditional oral); I could not confirm via OpenReview because the `/notes` API is now 403.
- Two ICML Honorable-Mention papers have no verified arXiv ID, and one ID is matched only against a secondary index.
