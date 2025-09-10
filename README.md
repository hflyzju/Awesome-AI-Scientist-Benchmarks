# 🌟 Awesome AI-Scientist Benchmarks — Expanded Edition

A curated, *English* Markdown list of benchmarks useful for building and evaluating **Proposal2Code** pipelines, **CodeAgents**, and end-to-end AI-scientist capabilities. Each entry includes a compact summary, evaluation focus, datasets / scale (when available), and key findings — with primary paper links cited.

---

## 🎯 Purpose

* Provide a single, well-organized reference of state-of-the-art benchmarks for evaluating systems that **turn research proposals into runnable code and experiments** (Proposal2Code), and for measuring the broader capabilities of **AI research agents**.
* Help prioritize which benchmarks to run for different competence axes (paper understanding, code synthesis, experiment design & execution, data analysis, domain-specific discovery).

---

## 📊 Benchmark Comparison Table

| Benchmark | Focus | Task Type | Scale / Dataset | Main Metrics | Key Insights |
|-----------|-------|-----------|-----------------|--------------|--------------|
| **PaperBench** | Reproducing ML research papers | Paper → Code → Experiment | ~dozens of recent ICML/NeurIPS papers | Implementation accuracy, result matching | Tests practical reproducibility of modern papers |
| **MLEBench** | Kaggle competition performance | Kaggle ML tasks | 100s of Kaggle tasks | Leaderboard score | Measures real-world ML engineering competence |
| **ResearchCodeBench** | Novel idea implementation | Code-level tasks | 100s of challenges from ~20 papers | Unit test correctness | Exposes gaps in translating novel ideas to code |
| **EXP-Bench** | Full experiment automation | Hypothesis → Experiment → Analysis | 461 tasks from 51 papers | Stepwise rubric, success rate | Agents rarely succeed end-to-end (<1%) |
| **MLR-Bench** | Open-ended ML research | Idea → Proposal → Paper | 100s of tasks | LLM+rubric grading | LLMs good at writing, weak at valid experiments |
| **SciReplicate-Bench** | NLP algorithm reproduction | Algorithm → Code | ~100 tasks | Execution, dependency recall | Highlights incomplete paper descriptions |
| **ML-Bench** | Repository-level ML coding | Multi-file repo edits | 1000s of GitHub tasks | Pass@k, execution | Tests repo-scale code reasoning |
| **SUPER** | Repo setup & execution | Env setup + running tasks | Multi-split benchmark | Success of repo execution | Evaluates engineering reliability |
| **AAAR-1.0** | Research assistance | Critical review & math tasks | Multi-domain | Correctness, quality | Can AI help real researchers? |
| **ScienceAgentBench** | Data-driven discovery | Paper → Code | ~100 expert tasks | Program correctness | Agents solve only a minority of tasks |
| **CORE-Bench** | Computational reproducibility | Paper → Result reproduction | 270 tasks from 90 papers | Execution accuracy | Reproducibility automation still immature |
| **Auto-Bench** | Scientific discovery via causal graphs | Interactive interventions | Simulated environments | Graph accuracy | Iterative discovery is very hard |
| **MLGym** | Training RL-style research agents | RL environment | 13 open tasks | Success rate | First gym for AI scientist training |
| **SciCode** | Science-specific coding | Domain problems | 80 problems, 338 subproblems | Pass@k, execution | Extremely low success on real science coding |
| **RE-Bench** | Human vs AI R&D | Open-ended ML research | Human expert 8h baselines | Task completion, quality | Humans still stronger with long budgets |
| **GAIA** | General AI assistant | Tool use, reasoning | 100s of curated Qs | Human-judge accuracy | Good general assistant baseline |
| **SWE-bench** | GitHub issue resolution | Patch generation | 2,294 real issues | Issue resolution % | Tests multi-file, repo-scale reasoning |
| **Humanity’s Last Exam** | Ultimate reasoning | Hard academic Qs | 1,000s of Qs | Accuracy | Current LLMs perform very poorly |
| **Paper2Code** | Paper → runnable repo | CodeAgent pipeline | 100s of ML papers | Repo executability | Direct Proposal2Code evaluation |
| **AlphaGo Moment (Arch Disc.)** | Large-scale architecture search | Automated ML design | Massive compute-scale | Discovered architectures | First “AlphaGo moment” for arch search |
| **BaisBench (omics)** | Biology research | Omics Q&A + annotation | Domain-specific | Task accuracy | Agents underperform domain experts |
| **SciAssess** | Literature analysis | Comprehension & critique | Multi-field | Graded tasks | Bench for survey / paper understanding |
| **BixBench** | Computational biology | Bioinformatics analysis | Multiple scenarios | Answer correctness | Domain-specific reasoning benchmark |
| **ResearchArena** | Research survey workflow | Collect & organize papers | Millions of papers | Retrieval & clustering | Evaluates survey-building agents |
| **DataSciBench** | Data science | Data tasks (open) | Multi-dataset | TFC framework | Tackles ambiguity in data analysis eval |
| **InfiAgent-DABench** | Data analysis | CSV Q&A | 1,000s of queries | Automatic scoring | Tests agent data-analysis accuracy |
| **Tapilot-Crossing** | Interactive data analysis | Multi-turn analysis | Multi-domain | Task success | Focuses on adaptive collaboration |

---

## 📚 Core AI-Scientist Benchmarks

### **PaperBench — Evaluating AI’s ability to replicate AI research**.

PaperBench tasks agents with end-to-end replication of published ML work: understanding the paper, creating a codebase, running experiments, and matching reported results. The benchmark focuses on reproducibility rubrics that decompose replication into graded sub-tasks (implementation correctness, experiment setup, result matching). PaperBench samples recent high-impact conference papers (e.g., ICML spotlight/oral items) to measure practical research-engineering competence. ([arXiv][1])

### **MLEBench (MLE-bench) — Measuring ML engineering / Kaggle performance.**

MLEBench collects a curated set of Kaggle competitions (hundreds of real ML engineering tasks) so agents are evaluated on realistic ML engineering workflows: dataset prep, model training, hyperparameter tuning, and leaderboard-quality submissions. It establishes human baselines from existing leaderboards and measures the agent’s ability to “push a leaderboard.” Useful when you want to stress test model selection, pipeline automation, and iterative experiment tuning. ([OpenAI][2])

### **ResearchCodeBench (Stanford) — Implementing novel ML research code.**

A focused coding benchmark that converts novel ML research contributions into fine-grained coding challenges (hundreds of challenges across \~20 recent papers). Each challenge targets core implementation components (model blocks, loss terms, training loops) and includes correctness tests co-developed with domain experts. The benchmark exposes how well LLMs translate *novel* (post-pretraining) research ideas into executable code. ([arXiv][3])

### **EXP-Bench — Can AI conduct AI research experiments?**

**(Detailed — from the paper abstract)**
EXP-Bench is designed to evaluate *end-to-end* experimental capability: given a research question and partially provided starter code, agents must (1) formulate hypotheses, (2) design experimental procedures, (3) implement and execute experiments, and (4) analyze results. To create realistic tasks, the authors build a **semi-autonomous pipeline** that extracts and structures experimental details from papers and their open-source code. EXP-Bench curates **hundreds of real research tasks** (the paper reports *\~461 tasks drawn from 51 papers*) and provides stepwise, gradeable procedures. Evaluations on current LLM-based agents show partial strength on individual aspects (e.g., design or implementation correctness sometimes score \~20–35%), but **the success rate for complete, executable experiments is extremely low (\~0.5%)**, highlighting major gaps in current agents’ ability to run full research experiments. EXP-Bench is explicitly intended to surface the bottlenecks in automating real research experiments (hypothesis→implementation→analysis) and to provide realistic, gradable tasks for improving agents. ([arXiv][4])

### **MLR-Bench — Open-ended machine learning research evaluation.**

MLR-Bench bundles hundreds of open-ended ML research tasks (sourced from workshop papers) and provides an automated judge (MLR-Judge) that mixes LLM reviewers with explicit rubrics. It also ships an agent scaffold (MLR-Agent) to evaluate the full research pipeline (idea → proposal → experiment → paper). Bench results emphasize that while LLMs are strong at generating coherent ideas and prose, *experimental validity* remains a major challenge (many agent outputs contain fabricated or invalid experimental claims). ([arXiv][5])

### **SciReplicate-Bench — Reproducing algorithms from papers (NLP focus).**

SciReplicate extracts algorithm descriptions from recent NLP papers and frames tasks requiring both algorithm comprehension and repository-level coding. The benchmark contains \~100 tasks from dozens of papers, annotated with test cases and dependency metadata; evaluation metrics include execution accuracy, reasoning-graph similarity, and dependency recall. This benchmark highlights problems caused by incomplete or inconsistent algorithm descriptions in papers. ([arXiv][6])

### **ML-Bench — Repository-level ML tasks**.

ML-Bench evaluates LLMs and autonomous agents on real repository tasks (thousands of examples across many GitHub repos). It focuses on repository-scale reasoning (argument selection for routines, multi-file edits, bash/script generation) and provides two modes: LLM (text→code) and agent (sandboxed execution + iterative action). ML-Bench is useful for measuring the agent’s ability to work inside a full research codebase. ([arXiv][7])

### **SUPER — Setting up & executing tasks from research repositories.**

SUPER evaluates an agent’s ability to *set up* research environments (install deps, config, run experiments) and then *execute* tasks from public repositories. SUPER contains multiple splits (Expert, Masked, Auto) to stress different capabilities (full problem, focused subproblems, automatic extraction). This is a practical benchmark for measuring engineering reliability when reproducing papers from GitHub. ([arXiv][8])

### **AAAR-1.0 — Assessing AI’s potential to assist research.**

AAAR-1.0 focuses on research-centric tasks that require deep expertise: equation inference/validation, experiment design, identifying paper weaknesses, and reviewer-style critique. It evaluates whether LLMs can help with the day-to-day intellectual tasks researchers perform and highlights where models do and do not provide reliable outputs for expert audiences. ([arXiv][9])

### **ScienceAgentBench — Language agents for data-driven scientific discovery.**

ScienceAgentBench extracts \~100 real tasks from peer-reviewed papers across multiple disciplines and validates tasks with subject experts. Each task has a canonical Python program as the target output; the benchmark measures program correctness, execution results, and resource costs. Current state-of-the-art agents solve only a minority of tasks, underlining limits in agent-driven data discovery. ([arXiv][10])

### **CORE-Bench — Computational reproducibility at scale.**

CORE-Bench is built to test computational reproducibility: reproduce experiment results using provided code/data across multiple disciplines. It contains hundreds of tasks (e.g., 270 tasks from 90 papers) spanning CS, social sciences, and medicine, with automated evaluation pipelines. Baseline agents show modest success (e.g., low accuracy on hardest tasks), indicating reproducibility automation is still immature. ([arXiv][11])

### **Auto-Bench — Benchmarking LLMs for scientific discovery (causal graphs).**

Auto-Bench frames scientific discovery as interactive causal-graph discovery: agents iteratively propose interventions, observe or query an oracle, and update hypotheses. Settings include simulated chemistry and social networks; the benchmark measures an agent’s ability to discover hidden structures and produce valid justifications. Performance drops quickly as complexity rises, signaling gaps in iterative scientific reasoning. ([arXiv][12])

### **MLGym — A gym for ML research agents.**

MLGym provides an RL-style environment and 13 open-ended research tasks (vision, NLP, RL, game theory). It’s designed to let researchers train agents using reinforcement learning or imitation approaches for research workflows: idea generation, data synthesis, implementation, experimentation, and iteration. Useful if you want to *train* agents to improve over time. ([arXiv][13])

### **SciCode — Scientist-curated coding benchmark (natural sciences).**

SciCode collects realistic, scientist-authored research problems across physical & life sciences and decomposes them into subproblems (e.g., 80 main problems → 338 subproblems). Each subproblem blends domain knowledge, reasoning, and code synthesis; state-of-the-art models solve only a very small fraction in realistic settings — revealing the steep gap between general code generation and research-grade scientific coding. ([arXiv][14])

### **RE-Bench — Comparing AI R\&D agents to human experts**.

RE-Bench provides open-ended ML research engineering environments with human expert runs (real 8-hour attempts) and agent baselines. It offers a realistic, time-budgeted comparison showing agents can be much faster (and sometimes score higher in short time budgets), but humans still scale better with longer time — a nuanced, resource-aware evaluation for “automation risk” analysis. ([arXiv][15])

---

## 🤖 General agent & code-agent benchmarks

### **GAIA — General AI assistant tasks (multi-modal, tool use).**

GAIA is a broad assistant benchmark (hundreds of human-designed questions) that stresses tool use, browsing, multi-modality, and practical reasoning — a good sanity check for general assistant competencies before narrowing to research tasks. (Human vs. model gaps are large on challenging questions.) ([arXiv][16])

### **SWE-bench — Real GitHub issue resolution (software engineering).**

SWE-bench contains thousands of real GitHub issues + PR fixes and asks models to generate patches that resolve issues across multiple files and contexts. It’s a demanding engineering benchmark — the best models historically resolve only a small percentage of realistic issues. Use it to test multi-file reasoning & patch generation. ([arXiv][17])

### **Humanity’s Last Exam (HLE) — Frontier, closed-ended academic questions.**

HLE is a multi-modal, expert-curated benchmark of **thousands** of extremely challenging, closed-ended academic questions (math, science, humanities). It’s intended as a frontier stress-test: current frontier LLMs perform very poorly on HLE, making it a strong evaluation for high-level reasoning and domain mastery. ([arXiv][18])

### **Paper2Code / PaperCoder — from paper → runnable repo.**

Paper2Code (PaperCoder) proposes a multi-agent framework that ingests ML papers and autonomously generates a runnable code repository (planning, implementation, and verification). It directly targets the Proposal2Code workflow and reports strong gains when evaluated on related benchmarks (including PaperBench). This is a practical starting point for a CodeAgent design. ([arXiv][19])

---

## 🧪 Large-scale / architecture discovery

### **AlphaGo Moment for Model Architecture Discovery (ASI-Arch)**

A multi-agent, large-scale system that autonomously searches model architectures (reported large numbers of autonomous experiments and discovered novel architectures). This paper demonstrates the feasibility of highly automated, compute-intensive architecture discovery and provides lessons for scaling Proposal2Code pipelines that include large experimental searches. ([arXiv][20])

---

## 🧬 Domain-specific AI-scientist benchmarks

* **Benchmarking AI scientists in omics / BaisBench** — Data-driven biological discovery (cell type annotation tasks + domain question answering). Highlights how data + domain knowledge are essential and how current agents underperform domain experts. ([arXiv][21])
* **SciAssess** — Benchmarks LLM skill in scientific literature analysis across memorization, comprehension, and analysis tiers (multi-field coverage). Useful for measuring literature-understanding modules in a Proposal2Code stack. ([arXiv][22])
* **BixBench** — LLM-agent benchmark for computational biology — real analysis scenarios + open-answer questions to evaluate multi-step bioinformatics reasoning. ([arXiv][23])

---

## 🔎 Survey / information-collection benchmarks

* **ResearchArena** — Evaluates LLM agents on the *research survey* workflow: discovery → selection → organization (offline corpus of millions of papers). Great for measuring agents that must *collect & synthesize* prior work before proposing experiments. ([arXiv][24])

---

## 📊 Data / interactive analysis benchmarks

* **DataSciBench** — An LLM agent benchmark for data-science tasks with a semi-automated ground-truth pipeline and a Task–Function–Code (TFC) evaluation framework; stresses open-ended data tasks and evaluation ambiguity. ([arXiv][25])
* **InfiAgent-DABench** — Agent evaluation specifically for CSV / data analysis question answering with closed-form conversion to enable automatic scoring; strong baseline of agent frameworks included. ([arXiv][26])
* **Tapilot-Crossing** — Interactive data-analysis benchmark that evaluates multi-turn, human-agent collaboration logics and adaptive strategies (useful for interactive Proposal2Code where a human steers experiments). ([arXiv][27])

---

## ✅ How to use this catalog (practical suggestions)

1. **Map capability → benchmark:**

   * Paper understanding & idea extraction → *ResearchArena, SciAssess, AAAR-1.0*.
   * Codegen for research algorithms → *ResearchCodeBench, SciReplicate, SciCode*.
   * Reproducibility & repo setup → *SUPER, CORE-Bench, ML-Bench*.
   * End-to-end experiment design & execution → *EXP-Bench, MLR-Bench, RE-Bench, PaperBench*.
   * Domain discovery (biology/omics) → *BaisBench, BixBench, SciCode*.

2. **Start small, iterate:** pick a 2–3 benchmark suite matching your goal (e.g., *ResearchCodeBench + EXP-Bench + Paper2Code* for Proposal2Code), run baseline agents, inspect failure modes (missing deps, incomplete implementations, wrong experimental configs), and design targeted improvements (better dependency resolution, iterative test-and-debug loops, sandboxed execution).

3. **Combine automated and human review:** many benchmarks intentionally require subject-expert validation or multi-stage rubrics — mix automated metrics (execution accuracy, pass\@k) with human annotations for robust evaluation.

---

## ♻️ Contributions & license

* PRs / issues welcome — add missing benchmarks or new evaluation notes.
* Suggested license: **MIT**.


[1]: https://arxiv.org/pdf/2504.01848?utm_source=chatgpt.com "Evaluating AI's Ability to Replicate AI Research - PaperBench"
[2]: https://openai.com/index/mle-bench/?utm_source=chatgpt.com "MLE-bench: Evaluating Machine Learning Agents on ..."
[3]: https://arxiv.org/html/2506.02314v1?utm_source=chatgpt.com "Benchmarking LLMs on Implementing Novel Machine ..."
[4]: https://arxiv.org/abs/2505.24785?utm_source=chatgpt.com "EXP-Bench: Can AI Conduct AI Research Experiments?"
[5]: https://arxiv.org/abs/2505.19955?utm_source=chatgpt.com "MLR-Bench: Evaluating AI Agents on Open-Ended Machine Learning Research"
[6]: https://arxiv.org/abs/2504.00255?utm_source=chatgpt.com "SciReplicate-Bench: Benchmarking LLMs in Agent-driven Algorithmic Reproduction from Research Papers"
[7]: https://arxiv.org/abs/2311.09835?utm_source=chatgpt.com "ML-Bench: Evaluating Large Language Models and Agents for Machine Learning Tasks on Repository-Level Code"
[8]: https://arxiv.org/abs/2409.07440?utm_source=chatgpt.com "Evaluating Agents on Setting Up and Executing Tasks from ..."
[9]: https://arxiv.org/abs/2410.22394?utm_source=chatgpt.com "AAAR-1.0: Assessing AI's Potential to Assist Research"
[10]: https://arxiv.org/abs/2410.05080?utm_source=chatgpt.com "ScienceAgentBench: Toward Rigorous Assessment of Language Agents for Data-Driven Scientific Discovery"
[11]: https://arxiv.org/abs/2409.11363?utm_source=chatgpt.com "CORE-Bench: Fostering the Credibility of Published Research Through a Computational Reproducibility Agent Benchmark"
[12]: https://arxiv.org/abs/2502.15224?utm_source=chatgpt.com "Auto-Bench: An Automated Benchmark for Scientific Discovery in LLMs"
[13]: https://arxiv.org/abs/2502.14499?utm_source=chatgpt.com "MLGym: A New Framework and Benchmark for Advancing AI Research Agents"
[14]: https://arxiv.org/abs/2407.13168?utm_source=chatgpt.com "SciCode: A Research Coding Benchmark Curated by Scientists"
[15]: https://arxiv.org/abs/2411.15114?utm_source=chatgpt.com "RE-Bench: Evaluating frontier AI R&D capabilities of language model agents against human experts"
[16]: https://arxiv.org/abs/2311.12983?utm_source=chatgpt.com "[2311.12983] GAIA: a benchmark for General AI Assistants - arXiv"
[17]: https://arxiv.org/abs/2310.06770?utm_source=chatgpt.com "SWE-bench: Can Language Models Resolve Real-World GitHub Issues?"
[18]: https://arxiv.org/html/2501.14249v1 "Humanity’s Last Exam"
[19]: https://arxiv.org/abs/2504.17192?utm_source=chatgpt.com "[2504.17192] Paper2Code: Automating Code Generation ..."
[20]: https://arxiv.org/abs/2507.18074?utm_source=chatgpt.com "AlphaGo Moment for Model Architecture Discovery"
[21]: https://arxiv.org/abs/2505.08341?utm_source=chatgpt.com "Benchmarking AI scientists in omics data-driven biological research"
[22]: https://arxiv.org/abs/2403.01976?utm_source=chatgpt.com "SciAssess: Benchmarking LLM Proficiency in Scientific Literature Analysis"
[23]: https://arxiv.org/abs/2503.00096?utm_source=chatgpt.com "BixBench: a Comprehensive Benchmark for LLM-based ..."
[24]: https://arxiv.org/abs/2406.10291?utm_source=chatgpt.com "ResearchArena: Benchmarking Large Language Models' Ability to Collect and Organize Information as Research Agents"
[25]: https://arxiv.org/abs/2502.13897?utm_source=chatgpt.com "DataSciBench: An LLM Agent Benchmark for Data Science"
[26]: https://arxiv.org/abs/2401.05507?utm_source=chatgpt.com "InfiAgent-DABench: Evaluating Agents on Data Analysis Tasks"
[27]: https://arxiv.org/abs/2403.05307?utm_source=chatgpt.com "Tapilot-Crossing: Benchmarking and Evolving LLMs Towards Interactive Data Analysis Agents"
