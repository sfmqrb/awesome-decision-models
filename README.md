# Awesome Decision Models [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Models that answer instead of talk: give them text and typed questions, get back calibrated probabilities in one forward pass. No generated tokens, no JSON to parse.

A curated list of decision models (also called System One models, typed decision models, or "semantic ifs"): TypeSafe's Jev, the open-source Laya, Kev, SemIf, and everything the community has built around them.

## What is a decision model?

A chat LLM writes an answer token by token and your code parses it back into an `if`. A decision model skips the writing: you send text plus typed questions (yes/no, pick one, score) and read each answer straight off the model, with a probability, in one pass. [Longer explanation with an example](docs/what-is-a-decision-model.md).

## Contents

- [Official](#official)
- [Open models and weights](#open-models-and-weights)
- [Runtimes, ports and servers](#runtimes-ports-and-servers)
- [SDKs and libraries](#sdks-and-libraries)
- [Integrations and plugins](#integrations-and-plugins)
  - [Coding agents](#coding-agents)
  - [Browser and computer use](#browser-and-computer-use)
  - [MCP servers](#mcp-servers)
- [Tools and CLIs](#tools-and-clis)
- [Apps, demos and games](#apps-demos-and-games)
- [Robotics and simulation](#robotics-and-simulation)
- [Training and research code](#training-and-research-code)
- [Benchmarks and datasets](#benchmarks-and-datasets)
- [Papers](#papers)
- [Articles and tutorials](#articles-and-tutorials)
- [Discussions](#discussions)
- [Related lists](#related-lists)

## Official

### Jev (TypeSafe AI, hosted)

- [Introducing System One Models and Jev](https://typesafe.ai/blog/introducing-system-one-models-and-jev) - Launch post that introduced the System One model category.
- [TypeSafe docs](https://docs.typesafe.ai) - API reference for Jev's typed decisions.
- [typesafe-sdk-python](https://github.com/typesafe-ai/typesafe-sdk-python) - Official Python SDK.
- [typesafe-sdk-js](https://github.com/typesafe-ai/typesafe-sdk-js) - Official TypeScript/JavaScript SDK.
- [skills](https://github.com/typesafe-ai/skills) - Official agent skills for building with the System One API.
- [system-one-adapter-python](https://github.com/typesafe-ai/system-one-adapter-python) - Drop-in client replacement that answers System One calls with regular LLM APIs.

### Laya (Convai Innovations, open source)

- [Laya](https://github.com/NandhaKishorM/laya) - Open-source, multilingual, non-autoregressive decision engine with a router across checkpoints.
- [Laya docs](https://nandhakishorm.github.io/laya/) - Guides for hooks, schema-driven decisions, Docker and LangChain.
- [Laya website](https://laya.convaiinnovations.com/) - Project site with demos and benchmarks.
- [laya on PyPI](https://pypi.org/project/laya/) - `pip install laya`, with optional server, MCP, LangChain and ONNX extras.
- [Laya demo Space](https://huggingface.co/spaces/convaiinnovations/laya-demo) - Try Laya in the browser.

## Open models and weights

- [convaiinnovations/laya](https://huggingface.co/convaiinnovations/laya) - Laya English checkpoint.
- [convaiinnovations/laya-multilingual](https://huggingface.co/convaiinnovations/laya-multilingual) - Laya checkpoint for 100+ languages with up to 8k context.
- [convaiinnovations/laya-typed-decisions](https://huggingface.co/convaiinnovations/laya-typed-decisions) - Laya fine-tuned on the typed-decisions benchmark.
- [Kev](https://github.com/jaredpalmer/kev) - Family of Jev-like decision models on Qwen3.5/3.8 (0.8B to 27B) with training code and a Jev-compatible server.
- [Kev Space](https://huggingface.co/spaces/jaredpalmer/kev) - Browser demo of Kev-4B and Kev-0.8B.
- [SemIf](https://github.com/TheoLeeCJ/SemIf-OpenJev) - Semantic ifs read from open models' option logits, with a WebGPU demo (formerly OpenJev).
- [Tev1](https://github.com/togethercomputer/tev1) - Open-weight Jev-inspired decision model fine-tuned on Qwen3.5 4B.
- [Decider](https://github.com/Mapika/decider) - System One-style model family fine-tuned from Qwen3.5, including vision variants.
- [Bespoke Nimble](https://github.com/bespokelabsai/nimble) - Data, model and recipe for an open Jev-style model.
- [Von](https://github.com/wfzyx/von) - Open-source, non-autoregressive decision model positioned as a local Jev alternative.
- [Open-Jev](https://github.com/Zefan-Cai/Open-Jev) - Open decision model (27B) returning typed probabilities without generation.
- [OpenJev](https://github.com/razorback16/openjev) - Jev-compatible decision server on DiffusionGemma with image support.
- [AgentJev](https://github.com/malevrigns/agent-jev) - 0.6B decision model tuned for agent state such as diffs, traces and logs.
- [Reflex](https://github.com/kshetrajna12/reflex) - Small open decision model re-creating the System One interface on Qwen3.5.
- [JevK5](https://github.com/allebee/jevk5) - Apache-2.0 open-weight typed decision model.
- [Verdict](https://github.com/Heman10x-NGU/openJev-verdict-2.0) - 151M ModernBERT-based non-autoregressive decision engine.
- [OpenThai-SystemOne](https://github.com/iapp-technology/openthai-systemone) - Thai and English System One decision model (0.8B).
- [Valen](https://github.com/Liuziyu77/Valen) - Train a Jev-like multimodal decision model with vision.
- [laya-vision](https://github.com/r33drichards/laya-vision) - Image inputs for Laya on a SmolVLM-256M backbone.
- [Eikos](https://github.com/caiovicentino/eikos) - Single-pass typed decision models (4B and 27B) for finance.
- [dev-0.4b](https://github.com/mpnikhil/dev-0.4b) - 0.4B bidirectional decision model on ModernBERT-large.
- [Blink](https://github.com/sqliteai/blink) - System One model with an embeddable C runtime and WebAssembly support.

## Runtimes, ports and servers

- [laya-mlx](https://github.com/mizorewww/laya-mlx) - Native MLX runtime for Laya on Apple Silicon.
- [laya-coreml](https://github.com/mizorewww/laya-coreml) - Laya on Core ML and the Apple Neural Engine.
- [laya.cpp](https://github.com/lkarlslund/laya.cpp) - C++ inference for Laya with CUDA, Vulkan, Core ML and CPU backends.
- [receptron/laya](https://github.com/receptron/laya) - Run Laya from Node.js and TypeScript via ONNX Runtime.
- [laya-server](https://github.com/1Panel-dev/laya-server) - Self-hosted API and web UI for Laya, compatible with the Jev API format.
- [laya-apple](https://github.com/tc3oliver/laya-apple) - Heterogeneous Laya runtime using MLX GPU and the Neural Engine.
- [laya-mps](https://github.com/afshinm/laya-mps) - Run typed decisions on a Mac via PyTorch MPS with low RAM use.
- [layaForWeb](https://github.com/vishalmysore/layaForWeb) - Laya running in the browser.
- [open-jev-laya](https://github.com/killkli/open-jev-laya) - Browser-only Laya multilingual demos on Transformers.js.
- [laya-goish](https://github.com/centillex-labs/laya-goish) - Laya GGUF inference and HTTP server.
- [lev](https://github.com/jlt-commons/lev) - Jolt implementation of the Laya decision engine.
- [Arbiter](https://github.com/0xBakeer/arbiter) - Serve Laya or custom decision models on NVIDIA or Apple Silicon behind a Jev-compatible API.
- [Ollaya](https://github.com/ollaya-dev/ollaya) - Pull and serve open decision models (Laya, Decider, NLI) behind a TypeSafe-compatible API.
- [EdgeJev](https://github.com/yzfly/edgejev) - CPU-only ONNX + INT8 inference for Laya, Kev and similar models.
- [openjev-sglang](https://github.com/ekzhang/openjev-sglang) - Jev API server on SGLang with prefill-only open models.
- [djev](https://github.com/mmastrac/djev) - Structured decisions on DiffusionGemma, from a vLLM example server.
- [vllm-jev](https://github.com/mode-io/vllm-jev) - Native vLLM serving for Jev-style decision models.
- [JevFire](https://github.com/kikoncuo/jevfire) - Parallel decisions over one context for CUDA LLMs with a vLLM API.
- [jevmlx](https://github.com/bnsd55/jevmlx) - Parallel constrained decisions for any MLX model.
- [JEV-CPU](https://github.com/leesk212/JEV-CPU) - Run SemIf decisions on CPU with a web UI.
- [jeff](https://github.com/logan-markewich/jeff) - Self-hosted Jev replacement powered by GliFormer.
- [JevCache](https://github.com/hyperspaceai/jevcache) - Decision cache that memoizes repeated calls to Jev-class models.

## SDKs and libraries

- [AnyJev](https://github.com/nokia-applied-research/AnyJev) - Turn any LLM into a Jev-style decision model without training.
- [simple-jev](https://github.com/featherless-ai/simple-jev) - Classification and scoring endpoint over open Hugging Face models via next-token logits.
- [LLM2Jev](https://github.com/Yinsongxu/LLM2Jev) - Structured decisions from local LMs using prefill only, for text and images.
- [rizzo-flow](https://github.com/Rizzo-AI-Academy/rizzo-flow) - Local typed decisions from an LLM without generating tokens.
- [open-jev](https://github.com/nico-martin/open-jev) - Browser-focused TypeScript library for typed decisions.
- [system-one](https://github.com/iamaamir/system-one) - Provider-neutral System One runtime for TypeScript.
- [go-jev](https://github.com/mattn/go-jev) - Go SDK and CLI for Jev.
- [ruby_decision_model](https://github.com/obie/ruby_decision_model) - Ruby client for decision models such as Jev.
- [laya_ex](https://github.com/ChristianAlexander/laya_ex) - Elixir library wrapping Laya.
- [jev-foundation-models](https://github.com/peterfriese/jev-foundation-models) - Swift bridge between Jev and Apple's Foundation Models framework.
- [advocaat](https://github.com/pithings/advocaat) - Small type-safe client for asking questions about your data with Jev.
- [semantic-if](https://github.com/rinat-amanbekov/semantic-if) - SemIf method on vLLM as a Python library, CLI, REST API and MCP server.

## Integrations and plugins

### Coding agents

- [fast-jev-compaction](https://github.com/tamaratran/fast-jev-compaction) - Claude Code plugin that scores tool calls with Jev to drop stale context instead of summarizing.
- [jev-pruner](https://github.com/tamaratran/jev-pruner) - Claude Code plugin that trims long Bash output with Jev.
- [winnow](https://github.com/GhalebDweikat/winnow) - Claude Code context sieve that judges each tool result with a System One model.
- [hermes-jev-skills](https://github.com/kerpopule/hermes-jev-skills) - Jev-powered routing, memory, compaction and skill selection for Hermes, Claude Code and Codex.
- [jev-router](https://github.com/gargpratyush/jev-router) - Route Claude Code tasks to the cheapest capable model.
- [jev-codex-router](https://github.com/0xNatoshi/jev-codex-router) - Per-turn model and reasoning-effort routing for Codex.
- [jev-rules](https://github.com/EliaAlberti/jev-rules) - Select which rules apply to each prompt so Claude only sees relevant ones.
- [skillranker](https://github.com/Dicklesworthstone/skillranker) - Rust CLI that ranks agent skills for the next step, with Claude Code hooks.
- [pi-jev](https://github.com/y0usaf/pi-jev) - Jev decision layer and tool-call gate for the Pi coding agent.
- [jev-review](https://github.com/devagrawal09/jev-review) - Staged code-review workflow with a local dashboard.
- [building-with-jev-skill](https://github.com/dbreunig/building-with-jev-skill) - Agent skill for writing and improving programs that call Jev.
- [keel](https://github.com/codejunkie99/keel) - Local-first macOS coding workspace with local Laya decisions.
- [laya-drift](https://github.com/pythongiant/laya-drift) - OpenCode plugin that monitors agent drift with Laya.
- [jevals](https://github.com/openlayer-ai/jevals) - Agent evals and guardrails as decision calls, runnable locally with Kev or Laya.

### Browser and computer use

- [jev-ultrafast](https://github.com/browser-use/jev-ultrafast) - Browser agent where Jev picks each operation and element from an indexed action space.
- [laya-ultrafast](https://github.com/ipenywis/laya-ultrafast) - jev-ultrafast running on local Laya.
- [laya-browser-agent](https://github.com/ChenneyZhuang/laya-browser-agent) - Local Playwright browser agent driven by Laya.
- [jev-browser-use](https://github.com/wy-coliney/jev-browser-use) - Browser operations where Jev clicks and Codex plans and verifies.
- [fastbrowse](https://github.com/agent-labs-dev/fastbrowse) - Browser agent with page-cited answers; Jev picks actions, an LLM plans.
- [jev-browser](https://github.com/Ying-Kai-Liao/jev-browser) - Browser automation library, CLI and MCP server where an LLM plans and Jev decides.
- [jev-voice-browser](https://github.com/moritzkremb/jev-voice-browser) - Control a real browser by voice.
- [FluidUse](https://github.com/FluidInference/FluidUse) - On-device computer use on macOS with Laya via the Accessibility API.
- [jev-use](https://github.com/savka777/jev-use) - macOS computer-use harness that reads the screen via Accessibility.
- [Jev-cu](https://github.com/Sac-Y/Jev-cu) - Hands Codex Computer Use's next-click choice to Jev.
- [mobile-jev](https://github.com/droidrun/mobile-jev) - Android phone agent with Jev making the decisions.
- [third-hand](https://github.com/shhivv/third-hand) - Computer-use assistant built on decision models.
- [system1-agents](https://github.com/ThinkFlowLab/system1-agents) - Jev, Laya and Cua-S1 as the brain for browser, computer, game and robot agents.
- [unclutter](https://github.com/kitze/unclutter) - Browser extension that removes page clutter with reusable rules.
- [Sedum](https://github.com/sedum-dev/sedum) - Plain-English browser tests on Playwright that use Jev to pick each next action in goal mode, resolve each step's element and judge verify claims.

### MCP servers

- [jev-mcp](https://github.com/jkudish/jev-mcp) - Jev typed judgments as MCP tools.
- [system-one-connector](https://github.com/itsmostafa/system-one-connector) - MCP connector for Jev and open-weight models such as Laya.
- [Jevbridge](https://github.com/tacticocc/Jevbridge) - ACP and MCP adapter bridging Jev with Codex, Claude, Grok and OpenCode.
- [jev-sift](https://github.com/kbhuw/jev-sift) - Agent plugin and MCP tool for batch text classification.

## Tools and CLIs

- [gutcheck](https://github.com/sfmqrb/gutcheck) - grep for meaning: a single-binary CLI that runs Laya locally, with a live explorer, named questions and a log cache.
- [jgrep](https://github.com/keltokhy/jgrep) - grep where the pattern is a description.
- [jev-semgrep](https://github.com/uehaj/jev-semgrep) - Grep by meaning across languages with AND/OR/NOT.
- [jegrep](https://github.com/can1357/jegrep) - Find code by describing it.
- [jevgrep](https://github.com/nassim-arifette/jevgrep) - Semantic code search for coding agents via CLI or MCP.
- [perch](https://github.com/lakeday-org/perch) - Semantic code linting.
- [semdecide](https://github.com/sharziki/semdecide) - Typed semantic decisions for Unix pipelines and CI.
- [webctl](https://github.com/dorkitude/webctl) - Web search CLI for agents.
- [jev-shell-history](https://github.com/mrnugget/jev-shell-history) - zsh history autosuggestions ranked by Jev.
- [pg-jev](https://github.com/realZachi/pg-jev) - PostgreSQL extension to ask tables questions in plain language.
- [docjev](https://github.com/jerryjliu/docjev) - Fast document classifier and splitter.
- [jev-curate](https://github.com/AkashPriyadarshii/jev-curate) - Rust dataset sifter for filtering pretraining and synthetic data.
- [jevcal](https://github.com/abhixhek/jevcal) - Calibrate thresholds and check drift for typed decision models.
- [jeview](https://github.com/andududu/jeview) - Local visualizer for every Jev call your code makes.
- [HA-Jev](https://github.com/AboveColin/HA-Jev) - Home Assistant integration exposing typed answers as sensors.
- [hono-jev-router](https://github.com/yusukebe/hono-jev-router) - Route HTTP requests by meaning in Hono.

## Apps, demos and games

- [laya-playground](https://github.com/wdobry/laya-playground) - Website, games, a benchmark and an agent skill for local Laya.
- [laya-vs-jev](https://github.com/virajbhartiya/laya-vs-jev) - Local Laya and hosted Jev playing T-Rex side by side.
- [laya-vs-jev-arena](https://github.com/PromptEngineer48/laya-vs-jev-arena) - Laya and Jev racing in Snake and fighting in an arena.
- [jev-experiments](https://github.com/dabit3/jev-experiments) - Collection of latency-focused Jev demos.
- [shapeshift](https://github.com/anishfn/shapeshift) - A text box that morphs into the right UI as you type.
- [jev-chat](https://github.com/w3cj/jev-chat) - Tool-calling chatbot built with Jev and no LLM.
- [jevmail](https://github.com/fazlerocks/jevmail) - Gmail inbox triage.
- [jev-search](https://github.com/superagents-lab/jev-search) - Web search with Jev for source selection and ranking.
- [tax-doc-classifier](https://github.com/kyotofin/tax-doc-classifier) - Tax document page classifier.
- [jev-chat-jarvis](https://github.com/jev-chat/jev-chat-jarvis) - Phone chat copilot that reads the screen and suggests replies (Chinese).
- [jev-trader](https://github.com/jarrodwatts/jev-trader) - One trade decision per Monad block.
- [typesafe-mario](https://github.com/fhshaik/typesafe-mario) - Agent that plays Super Mario Bros. from emulator state.
- [minecraft-agent](https://github.com/rmalde/minecraft-agent) - Minecraft planner with a Jev controller.
- [jevpilot](https://github.com/standardagents/jevpilot) - Three.js driving simulator with a Jev autopilot.

## Robotics and simulation

- [quackd](https://github.com/rokbenko/quackd) - CLI to command robots, with a decision model for multiple-choice steps.
- [embodied-jev](https://github.com/FBddcz/embodied-jev) - MuJoCo robot decision workbench.
- [jev-drone](https://github.com/RomanSlack/jev-drone) - Camera-only autonomous drone in MuJoCo with a decision model in the loop.
- [jev-libero](https://github.com/Dimweaker/jev-libero) - Fine-grained robot control on LIBERO tasks.

## Training and research code

- [NanoJev](https://github.com/TianyuCodings/NanoJev) - Nano replica of Jev with an end-to-end training pipeline.
- [Jevlike](https://github.com/vinnylarouge/jevlike) - Train a small model that chooses among a changing list of options.
- [jev-forge](https://github.com/zwliJay/jev-forge) - Training and inference stack for Jev-style models.
- [autojev](https://github.com/denis-pplx/autojev) - Full-weight Qwen decision model with training code and a playground.
- [tinyjev](https://github.com/ankit-aglawe/tinyjev) - Tiny choice/score/noul model in MLX or PyTorch.
- [mini-jev](https://github.com/r-ms/mini-jev) - Preregistered experiment reading option logits from a frozen Qwen3-4B.
- [jev-on-a-laptop](https://github.com/rorshopping/jev-on-a-laptop) - Study of Jev-style decisions on stock 1.5B-8B models on Apple Silicon.
- [sarvam-jev](https://github.com/SAGAR-TAMANG/sarvam-jev) - Generation-free typed decisions on Indic LLMs.
- [JevHarness](https://github.com/TianyuCodings/JevHarness) - LLM-authored task-specific Jev harnesses with GEPA evolution.
- [jev-align](https://github.com/sutro-sh/jev-align) - Build calibrated AI functions from human feedback with Jev and GEPA.

## Benchmarks and datasets

- [typed-decisions](https://huggingface.co/datasets/LocalLLaMA/typed-decisions) - Typed-decisions benchmark dataset used in several model cards, including Laya's.
- [kev-suites](https://huggingface.co/datasets/jaredpalmer/kev-suites) - Frozen evaluation suites from the Kev project.
- [laya-jev-benchmark](https://huggingface.co/datasets/Luni/laya-jev-benchmark) - Head-to-head Laya vs Jev benchmark data.
- [JevBench](https://github.com/fstandhartinger/jevbench) - Benchmark for Jev-class models on accuracy, cost, speed and reliability.
- [jev-benchmarks](https://github.com/AbdelStark/jev-benchmarks) - Calibration, selective risk and latency evaluation for typed decision models.
- [jev_and_laya_benchmarking](https://github.com/pavanjava/jev_and_laya_benchmarking) - Scripts comparing Jev and Laya.
- [JevPokerBench](https://github.com/Prophetlab/JevPokerBench) - Texas Hold'em benchmark and leaderboard for decision models.
- [AIM-Decision](https://aimultiple.com/decision-models) - Independent comparison of Jev, Kev and LLMs.

## Papers

- [SalesRLAgent (arXiv:2503.23303)](https://arxiv.org/abs/2503.23303) - Earlier reinforcement-learning paper by Laya's author, cited as prior work.
- [Confidence-Aware Routing for LLM Reliability Enhancement (arXiv:2510.01237)](https://arxiv.org/abs/2510.01237) - Pre-generation routing paper by Laya's author.
- [Calibrated Decisions at Scale (arXiv:2609.24052)](https://arxiv.org/abs/2609.24052) - Converting police crash narratives into probabilistic variables with Jev.
- [Calibrated Decision Models for Autonomous Penetration-Testing Harnesses (arXiv:2609.28940)](https://arxiv.org/abs/2609.28940) - Jev and Laya as decision layers for pentest agents.

## Articles and tutorials

- [Jev's Architecture Unmasked](https://archerhume.com/posts/jevs-architecture-unmasked/) - Reverse-engineered architecture of Jev that Kev builds on.
- [I Built Non-Autoregressive Decision Models a Year Ago](https://dev.to/nandakishor_m_6cc0adfde9f/i-built-non-autoregressive-decision-models-a-year-ago-then-a-frontier-lab-called-it-a-18me) - Laya's author on the background of the project.
- [A deep dive into Jev](https://flaviocopes.com/jev/) - Walkthrough of the System One model.
- [How to Use Jev](https://dev.to/valyuai/how-to-use-jev-a-practical-guide-to-typesafes-system-one-model-g5e) - Practical guide.
- [A Coding Guide to TypeSafe AI Jev](https://www.marktechpost.com/2026/09/23/a-coding-guide-to-typesafe-ai-jev/) - Typed decisions, confidence and fan-out in code.
- [Building a harness with Jev](https://www.langchain.com/blog/building-a-harness-with-jev) - LangChain's guide to the System One model.
- [Jev: TypeSafe's System One Model](https://www.datacamp.com/blog/system-one-models-jev) - DataCamp explainer.
- [Laya: A 421M Local Decision Model](https://themenonlab.blog/blog/laya-local-system-1-decision-model) - How Laya works under the hood.
- [Laya: The Open-Source Jev Alternative, Benchmarked](https://flowtivity.ai/blog/laya-open-source-jev-alternative/) - Laya benchmarked against Jev.
- [Jev vs Laya](https://wilsonwu.me/en/blog/2026/jev-vs-laya/) - Choosing between closed and open System One models.
- [Jev vs djev vs Laya vs OpenJev vs SemIf](https://huggingface.co/blog/sora-2/jev-ai-vs-djev-vs-laya-vs-openjev-vs-semif-which-d) - Comparison of open decision models.
- [Open-Weights Jev Alternatives](https://rohitraj.tech/notes/jev-alternatives-open-weights-decision-models-2026) - Which open decision model to ship.
- [Best Open Source Jev Alternatives](https://pinggy.io/blog/best_open_source_jev_alternatives_self_hosted_decision_models/) - Self-hosting decision models.
- [Here are 6 Clones of Jev in 2 days](https://www.latent.space/p/ainews-here-are-6-clones-of-jev-in) - Latent Space roundup of the first open clones.
- [TypeSafe AI Releases Jev](https://www.marktechpost.com/2026/09/19/typesafe-ai-releases-jev/) - Launch news coverage.
- [TypeSafe AI's Jev offers an alternative to LLMs](https://www.tomshardware.com/tech-industry/artificial-intelligence/typesafe-ais-jev-offers-an-alternative-to-llms-that-claims-to-be-193x-faster-and-445x-cheaper-system-one-type-model-is-bespoke-for-probabilistic-decision-making) - Tom's Hardware coverage.

## Discussions

- [Kev on Hacker News](https://news.ycombinator.com/item?id=49783999) - Discussion of Kev.
- [Laya author on Hacker News](https://news.ycombinator.com/item?id=49765348) - Discussion of the Laya background post.

## Related lists

- [awesome-jev (yibie)](https://github.com/yibie/awesome-jev) - Projects, integrations and discussions built on Jev.
- [awesome-jev (heyjunpenn)](https://github.com/heyjunpenn/awesome-jev) - Large catalog of open-source projects built with Jev.
- [awesome-jev-tools](https://github.com/v-modal/awesome-jev-tools) - Tools built for Jev.
- [awesome-jev-zh](https://github.com/yzfly/awesome-jev-zh) - Chinese-language list for Jev and System One.

## Contributing

Contributions welcome! Read the [contribution guidelines](contributing.md) first.
