<div align="center">

# Angra Kythons

**Local-first observability and model-to-model coordination for LM Studio and Bionic.**
<img width="1024" height="1536" alt="file_00000000b61482108f0418ab8ff96ee5" src="https://github.com/user-attachments/assets/6751ff44-5cd0-4efc-9351-bdfb037de923" />

*Observe. Analyze. Verify. Challenge. Reconstruct. Coordinate.*

![Python](https://img.shields.io/badge/python-3-blue)
![Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen)
![Runs](https://img.shields.io/badge/runs-100%25%20local-orange)
![Status](https://img.shields.io/badge/status-alpha-yellow)

[Quick start](#quick-start) · [Features](#features) · [How it works](#how-it-works) · [Commands](#commands) · [Roadmap](#roadmap) · [Security](#security-model) · [Contributing](#contributing)

<!-- Add a demo GIF here: docs/assets/demo.gif -->

</div>

---

## What is ANGRA?

Running several local models does not automatically make them a team, and it
does not tell you what they are actually doing.

ANGRA is a single-file Python tool that sits **between** your local model
runtimes and you:

1. **See** what your local models are doing in real time (LM Studio).
2. **Let models work together** through explicit, scoped links instead of
   copy-pasting between chats (LM Studio and Bionic).

> Models should not only exchange answers. They should exchange **evidence**.

ANGRA is **not** a model, **not** an LLM, and **not** a replacement for
LM Studio or Bionic. It is the layer around them.

<img width="1536" height="1024" alt="file_000000002dac82109879474e5a09ecdf" src="https://github.com/user-attachments/assets/0e333f63-e3b3-416c-913e-1198200cd0d9" />


## Features

### Real-time observability (LM Studio)

- Model lifecycle monitoring (load / unload / active model)
- Streaming generation tracking
- Generation metrics: **tokens, latency, time to first token (TTFT), tokens/second**
- Context and performance analysis
- Tool-call visibility, where the runtime exposes it
- Reasoning events, **only when explicitly exposed** by the model or interface
- Resource monitoring

### Model collaboration

- Designate a **primary** model and **link** other models to it
- Grant link permissions **per session** (nothing is permanent by default)
- Relay structured evidence between models: verify, challenge, reconstruct
- Bionic integration with resource estimation and a configurable GPU budget

### Engineering principles

- **Zero dependencies.** Python standard library only. No `pip install`.
- **Single file per integration.** Copy it, run it, delete it.
- **Local-first.** Your prompts and outputs stay on your machine unless you
  deliberately configure otherwise.
- **Reversible.** Setup is idempotent, and `uninstall` removes what `install` added.
- **Safe defaults.** Automatic features are off until you turn them on.

## Quick start
<img width="1536" height="1024" alt="file_00000000f11c8210946039a017d7a3fd (1)" src="https://github.com/user-attachments/assets/47bfc8ac-41e7-46bf-a1c5-b95c3eb45782" />

### Requirements

- [LM Studio](https://lmstudio.ai) and/or Bionic installed
- Python 3
- At least one local model downloaded

### LM Studio

```bash
# 1. Put Angra_lmstudio.py in your user folder (e.g. C:\Users\<you>)
# 2. Install the `angra` command
py Angra_lmstudio.py install

# 3. Check that everything is wired correctly
angra doctor

# 4. Set a primary model and link a second one to it
angra primary "GPT-OSS-20B"
angra link "GPT-OSS-20B" "DeepSeek-Coder-V2-Lite"

# 5. Allow the link for this session only
angra allow "DeepSeek-Coder-V2-Lite" --session
```
<img width="1320" height="1080" alt="angra_10_safety_limits" src="https://github.com/user-attachments/assets/5546e233-d011-435b-a58c-37ba273804df" />

### Bionic

```bash
py Angra_bionic.py

angra-bionic models                        # list available models
angra-bionic select                        # choose a model and confirm
angra-bionic enable                        # estimate resources, confirm, load
angra-bionic config set max_gpu_budget_gb 6
angra-bionic test
angra-bionic doctor
```

## Commands
<img width="1320" height="780" alt="angra_12_latency_model" src="https://github.com/user-attachments/assets/46fc6314-6004-4a8a-8658-05eb99d90ec8" />

### `angra` (LM Studio)

| Command | What it does |
| --- | --- |
| `install` | Installs the `angra` command (reversible) |
| `doctor` | Diagnoses setup, connectivity and permissions |
| `primary "<model>"` | Sets the primary model |
| `link "<A>" "<B>"` | Links model B to model A |
| `allow "<model>" --session` | Allows a link for the current session only |
| `uninstall` | Removes everything `install` added |

### `angra-bionic` (Bionic)

| Command | What it does |
| --- | --- |
| `models` | Lists available models |
| `select` | Choose a model and confirm |
| `enable` / `disable` | Estimate resources, confirm, load / unload |
| `config set <key> <value>` | Changes a setting, e.g. `max_gpu_budget_gb 6` |
| `test` | Runs a self-test |
| `status --json` | Machine-readable status |
| `doctor` | Diagnoses setup |
| `uninstall` | Removes everything it added |

## How it works
<img width="1320" height="1080" alt="angra_10_safety_limits" src="https://github.com/user-attachments/assets/fc53e820-6764-4c2e-b310-49ac0a707d27" />

```mermaid
flowchart LR
    U[You] --> A{{ANGRA}}
    A -->|observe| LM[LM Studio<br/>local models]
    A -->|coordinate| BI[Bionic<br/>agent environment]
    LM -->|events and metrics| A
    BI -->|results| A
    A --> D[Dashboard and logs]
```

ANGRA does not run inference. It watches the runtime you already use,
records what happens, and relays structured context between models you have
explicitly linked.

A relayed message separates identity, task, context, constraints and result,
instead of forwarding an entire chat transcript:

```json
{
  "sender": "primary",
  "recipient": "reviewer",
  "type": "task_context",
  "objective": "Review the proposed fix",
  "context": [],
  "constraints": [],
  "status": "ready"
}
```

## Security model

Connecting models is a security boundary, not just a convenience.

- Access to a model does **not** imply access to files, a shell, the network,
  secrets or other models. Capabilities are scoped and explicit.
- Links are **session-scoped by default** (`--session`).
- Never expose an AI runtime directly to an untrusted network.
- Report vulnerabilities privately; see [SECURITY.md](SECURITY.md).

## Status

ANGRA is **alpha**. Interfaces may change between versions. Pin a specific
release for reproducible setups, and treat any feature not listed under
"Features" as experimental.

## Roadmap
<img width="1680" height="900" alt="angra_07_code_metrics" src="https://github.com/user-attachments/assets/95dea4cb-d5b7-446c-9727-69ebac05066f" />

- [x] LM Studio integration (`Angra_lmstudio.py`)
- [x] Bionic integration (`Angra_bionic.py`)
- [ ] Unified single-file build with live dashboard (Tkinter)
- [ ] Session storage (sqlite3 / JSON) and exportable reports
- [ ] Evaluation engine and anomaly levels (NORMAL / WATCH / WARNING / ANOMALY)
- [ ] Automated tests and CI
- [ ] Tagged releases with checksums
- [ ] Cross-machine workers (authenticated and encrypted)

<img width="1024" height="1536" alt="file_00000000117c82109da9b4390ce1e909" src="https://github.com/user-attachments/assets/f07d6507-1666-42c3-bc12-a97ca393515b" />


## Contributing

Issues and pull requests are welcome. Good first areas: tests, Linux and
macOS support, docs and examples. Please read [CONTRIBUTING.md](CONTRIBUTING.md)
first.

## License

See [LICENSE](LICENSE).

## Author
https://shokribardiya.github.io/Oblivions0.github.io/
https://shokribardiya.github.io/OblivionStudioDev/
Built by **Bardiya Shokri** ([@shokribardiya](https://github.com/shokribardiya))
under the Oblivion project.
Website: <https://shokribardiya.github.io/Angra_AI/>

## Citation

If ANGRA helps your work, please cite it (see `CITATION.cff`).
<img width="1024" height="1536" alt="file_00000000b61482108f0418ab8ff96ee5" src="https://github.com/user-attachments/assets/8cf50f78-f3b2-45d1-88e7-72cd9b75a3db" />
<img width="1560" height="1080" alt="angra_17_consult_sequence" src="https://github.com/user-attachments/assets/1bb42b29-db48-4c3c-a018-7a2e70b70002" />
<img width="1024" height="686" alt="angra_03_permission_states" src="https://github.com/user-attachments/assets/a2b7d68b-bbf6-43e1-bc3b-816bc1f4b1ee" />
<img width="1944" height="874" alt="angra_06_install_flow" src="https://github.com/user-attachments/assets/f8b5ed3e-d6a6-42d6-899d-db228ec11269" />
<img width="1901" height="459" alt="angra_04_topology_rules" src="https://github.com/user-attachments/assets/61752069-0fe7-4bf3-9574-e9280e477d9f" />

# ANGRA

**User chooses. LM Studio runs the models. Angra connects them.**

Angra is a small, dependency-free control tool that lets one model already loaded in [LM Studio](https://lmstudio.ai) (the *primary*) ask a second, already-loaded model (the *helper*) a focused question, under rules you set and can revoke at any time.

Angra never loads, downloads, unloads, switches or routes models. It never performs inference and never starts a server. All inference is done by LM Studio.

![Architecture](docs/img/architecture.png)

---

## Contents

1. [What it is (and is not)](#what-it-is-and-is-not)
2. [Requirements](#requirements)
3. [Quick start](#quick-start)
4. [Commands](#commands)
5. [How a consultation works](#how-a-consultation-works)
6. [Permissions](#permissions)
7. [Connection graph rules](#connection-graph-rules)
8. [Safety limits](#safety-limits)
9. [What to expect from it](#what-to-expect-from-it)
10. [Security model](#security-model)
11. [Code structure](#code-structure)
12. [Diagnostics and repair](#diagnostics-and-repair)
13. [Uninstall](#uninstall)
14. [Known limitations](#known-limitations)

---

## What it is (and is not)

Angra is two products in one file:

| | Product A: `Angra.py` | Product B: `angra-bridge` plugin |
|---|---|---|
| Language | Python, standard library only | TypeScript, generated from templates inside `Angra.py` |
| Runs on | Your Python (3.8+) | LM Studio's own Node runtime, using `@lmstudio/sdk` |
| Job | Installer, CLI, owner of state | Exposes four tools to the primary model |
| Touches models? | Never | Only calls `respond()` on an already-loaded helper |

**Angra is:** a permissioned, auditable bridge for one-question-at-a-time consultation.

**Angra is not:** a model router, an agent framework, a load balancer, or a way to merge two models into one. It does not make the primary stronger in general; it lets the primary delegate a small sub-question.

---
<img width="1430" height="780" alt="angra_delta_strong_hw" src="https://github.com/user-attachments/assets/459a03c3-67da-4c15-bdda-c5f81e66345e" />
in strong hardware ^
<img width="1430" height="780" alt="angra_delta-1" src="https://github.com/user-attachments/assets/58d73105-3c34-4fb3-be81-6df701d1be20" />

## Requirements

- Windows (install, PATH and launcher are Windows-only; read-only commands such as `models`, `loaded`, `doctor`, `self-test` run elsewhere)
- Python 3.8 or newer
- LM Studio with the `lms` CLI available (start LM Studio once, then run `lms bootstrap` if needed)
- A version of `lms` that supports `lms dev --install`
- At least two models loaded by you in LM Studio

---

## Quick start

```bat
py Angra.py install
```

Open a **new** Command Prompt (PATH changes apply to new windows), then:

```bat
angra doctor
angra models
angra primary "my-primary-model"
angra link "my-primary-model" "my-helper-model"
angra allow "my-helper-model" --session
angra links
```

Then ask your primary model something hard in LM Studio. It can call `angra_consult_model` when it decides a helper is useful.

State lives in `%LOCALAPPDATA%\Angra` (override with the `ANGRA_HOME` environment variable).

---

## Commands

| Command | What it does |
|---|---|
| `angra` | Dashboard and interactive shell |
| `status`, `models`, `loaded` | Show state, all models, loaded models |
| `primary "<model>"` | Record your primary (does **not** switch LM Studio) |
| `link "<primary>" "<helper>"` | Create a primary -> helper link (helper must be loaded) |
| `unlink "<primary>" "<helper>"` | Remove a link |
| `connect "<model>"` | Link a model to your declared primary |
| `disconnect "<model>"` | Remove its links and revoke its permission |
| `allow "<model>" [--once \| --session]` | Authorize a helper (default: enabled until denied) |
| `deny "<model>"` | Revoke authorization |
| `permissions`, `links` | Show permissions and the connection graph |
| `doctor`, `self-test` | Diagnostics; no inference is ever performed |
| `install`, `repair`, `uninstall` | Lifecycle |
| `version`, `help`, `exit` | Misc |

Flags: `--no-color`, `--ascii`.

![Command / resource matrix](docs/img/command_resource_matrix.png)

No command writes to a model. `uninstall` has the largest write surface (state, plugin, launcher, PATH entry).

---

## How a consultation works
<img width="924" height="1760" alt="angra_08_call_graph" src="https://github.com/user-attachments/assets/dd56b6d5-6e0e-47b8-aede-185f36046515" />

The primary model sees four tools:

| Tool | Purpose | Side effects |
|---|---|---|
| `angra_status` | Primary, links, permissions, safety limits | none |
| `angra_list_loaded_models` | Loaded models with roles and authorization | none |
| `angra_list_connections` | Each link and whether it is usable | none |
| `angra_consult_model` | Ask **one** helper **one** question | one helper inference |

![Sequence](docs/img/consult_sequence.png)

Before anything is sent, 11 guards run in order and fail closed. Every denial has a specific reason code.

![Guard pipeline](docs/img/consult_pipeline.png)

The helper receives a fixed system prompt ("answer only the specific task, concisely, do not ask questions back") plus the task and optional minimal context. It returns text only. The primary writes the final answer.

---
<img width="1680" height="720" alt="angra_13_montecarlo_gain" src="https://github.com/user-attachments/assets/207c2c8a-0e9e-43e6-af3e-aa1fb73026c7" />

## Permissions

Each helper has its own permission. Nothing is allowed by default.

![Permission states](docs/img/permission_states.png)

| Mode | Behavior |
|---|---|
| `off` | Calls are denied |
| `once` | One call, then automatically set to `off` (consumed before the call; fails closed if it cannot be consumed) |
| `session` | Valid until a TTL expires (`session_ttl_hours`, default 4) |
| `enabled` | Valid until you `deny` or `disconnect` |

A link is reported in one of three states:

![Link states](docs/img/link_states.png)

---
<img width="952" height="748" alt="local_frontier_profile-1" src="https://github.com/user-attachments/assets/07a8e3d0-4a1d-43ca-a0ae-f67bfa8f151c" />
<img width="952" height="748" alt="local_frontier_profile-2" src="https://github.com/user-attachments/assets/d607e57e-0610-418e-b43d-4ef47ff747c4" />

## Connection graph rules

Angra enforces a flat graph: one level of delegation, no loops.

![Topology rules](docs/img/topology_rules.png)

- A model cannot be its own helper.
- A helper cannot also be a primary, and a primary cannot also be a helper (no chains).
- Cycles are rejected (explicit check as defense in depth).
- One primary may have several helpers linked, and a helper may be shared by several primaries; the plugin still only uses the declared primary's links and consults one helper per answer.

---

## Safety limits

Stored in `state.json` under `safety`. Values are clamped on load, and four invariants are forced regardless of what the file says.

![Safety limits](docs/img/safety_limits.png)

| Setting | Default | Range |
|---|---|---|
| `max_helper_context` (tokens) | 4096 | 256 - 32768 |
| `max_helper_output` (tokens) | 512 | 16 - 4096 |
| `timeout_seconds` | 90 | 5 - 600 |
| `cooldown_seconds` | 5 | 0 - 600 |

Fixed in v1: `max_active_helpers = 1`, `parallel_helpers = false`, `max_helper_calls_per_response = 1`, `recursive_delegation = false`.

The input cap is enforced in characters (`max_helper_context x 4`) and oversized requests are rejected, not truncated. The helper's reply is cut at `max_helper_output x 8` characters.

![Information funnel](docs/img/information_funnel.png)

---
<img width="1430" height="1430" alt="angra_radar_strong_hw" src="https://github.com/user-attachments/assets/1f563008-f4ef-4d90-8247-d4d5d53ea631" />
<img width="1088" height="647" alt="vision_benchmark_snapshot-2" src="https://github.com/user-attachments/assets/42416137-b579-4ab6-97f9-4ec3f35a4bf1" />
<img width="1088" height="647" alt="text_agent_benchmark_snapshot-1" src="https://github.com/user-attachments/assets/f78e87f6-96fa-4262-a511-00c7f01dc439" />
<img width="1430" height="1430" alt="angra_radar_after-1" src="https://github.com/user-attachments/assets/00a3f6b7-38b4-49fb-b594-ce7a5a9680d7" />
<img width="1440" height="1280" alt="angra_radar_after" src="https://github.com/user-attachments/assets/b616419b-017b-4ae8-b1f3-ae76a250ef0b" />

## What to expect from it

Because of the limits above, the bridge is a narrow pipe: one question, small context, short answer, text only.

- **Helps most** when a weaker primary delegates a well-scoped sub-problem (a code review of a short snippet, a math step, a second opinion) to a stronger helper.
- **Helps little** when the primary is already the stronger model.
- **Does not change** vision (images cannot cross a text-only bridge), long-context capacity (the primary's window governs), or tool use (only the primary has tools).
- **Costs** extra memory (two models loaded) and extra time (calls are sequential).

> The figures below are **models and simulations with stated assumptions, not benchmarks.** Measure on your own hardware and tasks before relying on them.

![Latency model](docs/img/latency_model.png)

![Monte Carlo](docs/img/montecarlo_gain.png)

The simulation shows the gain depends on two things at once: how much better the helper is, and how reliably the primary knows when to ask. A primary that rarely delegates gains little even with a strong helper.

Suggested evaluation: run a fixed set of tasks with the model alone and with `angra_consult_model` enabled, then compare accuracy and wall-clock time.

---

## Security model

Principles: explicit consent, least data, no autonomy over models, fail closed.

![Security matrix](docs/img/security_matrix.png)

- **Consent:** no helper call without a link **and** a valid permission.
- **No model control:** the plugin enumerates loaded models first and never calls a load operation. `self-test` scans the generated plugin for forbidden calls (`.load(`, `.model(`, `unload(`, `lms load`, `load_new_instance`, `downloadModel`).
- **Single flight:** a busy flag blocks parallel calls; cooldown spaces sequential ones.
- **Bounded:** input cap, output cap, timeout with abort (also follows the host's abort signal).
- **Logging:** metadata only (event, model, mode, character count). Task text, context and answers are not logged.
- **Files:** state is written atomically; changed files are backed up before overwrite; Angra refuses to overwrite a plugin folder it does not own (marker file `.angra-owned`) and only deletes inside its own roots.

Residual risk: the prompt tells the primary to send only minimal context, but the primary model decides what to put in `task` and `context`. The size cap limits how much can leave, not what it contains. Only authorize helpers you trust with the data in your conversation.

---

## Code structure

`Angra.py` is about 2,050 lines. The largest block is the embedded TypeScript plugin.

![Code regions](docs/img/code_regions.png)

Install flow:

![Install flow](docs/img/install_flow.png)

Call graph of the Python side (95 functions, 224 internal call edges):

![Call graph](docs/img/call_graph.png)

Complexity hotspots (approximate cyclomatic complexity, computed with `ast`): `run_self_test` (43), `discover` (34), `run_doctor`, `cmd_install`, `cmd_uninstall` (29 each). These are the first candidates for refactoring.

![Code metrics](docs/img/code_metrics.png)

Pure, unit-testable logic is kept separate from I/O: `perm_effective`, `graph_add_error`, `sanitize_safety`, `migrate_state`, `link_state`.

---

## Diagnostics and repair

```bat
angra doctor      :: environment and installation health
angra self-test   :: state IO, plugin generation, permissions, graph rules, safety invariants
angra repair      :: regenerate Angra-owned files and re-register the plugin
```

Six `doctor` checks can report `FAIL` (Windows, Python, `lms`, model discovery, filesystem, PATH access); the rest report `WARN`.

![Doctor severity](docs/img/doctor_severity.png)

If the plugin does not appear in LM Studio, run `lms dev` inside the plugin folder (`%LOCALAPPDATA%\Angra\plugin\angra-bridge`) as the development-mode fallback.

---

## Uninstall

```bat
angra uninstall
```

Removes only Angra-owned items: the registered plugin copy, the generated plugin project, the launcher, the PATH entry Angra added, and Angra's state, config, logs and backups. LM Studio, your models and other plugins are not touched. You must type `YES` to confirm.

---

## Known limitations

- Install and PATH handling are Windows-only.
- Helpers receive text only; images and files cannot be forwarded.
- One helper call per answer; no parallel or chained delegation (by design in v1).
- The helper has no tools and cannot see the conversation.
- The `busy` flag and cooldown live in the plugin process memory; they reset if the plugin restarts.
- No documented plugin uninstall command was verified, so uninstall removes the exact registered copy that matches Angra's owner/name manifest.
- Performance and gain figures in this document are estimates, not measurements.

---

*Version 1.0.0 (state schema 1).*
<img width="1320" height="840" alt="angra_16_doctor_severity" src="https://github.com/user-attachments/assets/983384fb-50dc-4d87-9c18-42b7d3b33afa" />
