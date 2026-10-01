# Angra-AI-Model-Collaboration-Bridge-.-Bardiya-Shokri-
Open-source bridge for coordinating local AI models across LM Studio and Bionic.

<img width="1024" height="1536" alt="file_000000002fb082438c79119efba2e23b" src="https://github.com/user-attachments/assets/bd28febf-e196-4c1f-a9e4-f7117664eeb7" />


Bardiya Shokri
copy paste file in you "C:\Users\yours"
 ### angra lm studio prompt :
 
 py Angra_lmstudio.py install
angra
angra primary "GPT-OSS-20B"
angra link "GPT-OSS-20B" "DeepSeek-Coder-V2-Lite"
angra allow "DeepSeek-Coder-V2-Lite" --session
angra doctor
angra uninstall

##angra bionic prompt:
py Angra_bionic.py 
angra-bionic models
angra-bionic select       (مدل رو انتخاب و تأیید می‌کنید)
angra-bionic enable       (تخمین منابع، تأیید، لود)
angra-bionic disable
angra-bionic config set max_gpu_budget_gb 6 
angra-bionic test
angra-bionic doctor
angra-bionic status --json
angra-bionic uninstall

ANGRA — AI Model Collaboration Bridge

«Connect models. Coordinate work. Build an AI workforce.»

ANGRA is an open-source AI model collaboration bridge designed to connect and coordinate compatible AI models running through environments such as LM Studio and Bionic.

Instead of treating every model as an isolated endpoint, ANGRA provides an integration and orchestration layer through which multiple models can communicate, exchange task context, take on specialized roles, and cooperate as part of a larger workflow.

ANGRA is not an AI model.
ANGRA is not an LLM.
ANGRA is not a replacement for LM Studio or Bionic.

It is the layer between them.

---

What ANGRA Does

Modern local AI environments make it increasingly practical to run capable models on personal hardware. The problem is that running several models does not automatically make them a team.

One model may be strong at software engineering.

Another may be better at research and information extraction.

Another may be useful for review, validation, planning, or structured reasoning.

Without an orchestration layer, these models usually remain isolated workers.

ANGRA is built around a different idea:

                    USER / TASK
                         │
                         ▼
                ┌─────────────────┐
                │      ANGRA      │
                │ Collaboration   │
                │     Bridge      │
                └────────┬────────┘
                         │
              ┌──────────┼──────────┐
              │          │          │
              ▼          ▼          ▼
          MODEL A     MODEL B     MODEL C
          Research    Coding      Review
              │          │          │
              └──────────┼──────────┘
                         ▼
                 Shared workflow
                         │
                         ▼
                  Verified result

The central concept is simple:

«A model becomes a worker. Multiple coordinated models become a workforce.»

ANGRA is designed to make that workforce possible.

---

Why ANGRA Exists

AI systems are becoming more heterogeneous.

There is no single requirement that says one model must perform every part of a complex task.

A real engineering workflow can instead be decomposed into specialized roles:

Problem
   ↓
Planning
   ↓
Research
   ↓
Implementation
   ↓
Testing
   ↓
Review
   ↓
Final synthesis

Each stage can potentially be handled by a different model or agent environment.

ANGRA is designed to provide the communication layer required to coordinate those stages.

This creates a model of AI collaboration closer to an engineering organization than a single conversational interface:

                ANGRA
                   │
      ┌────────────┼────────────┐
      │            │            │
      ▼            ▼            ▼
   Research     Engineering    Review
    Worker        Worker       Worker
      │            │            │
      └────────────┼────────────┘
                   ▼
                Shared
               workflow

The goal is not to make every model identical.

The goal is to make different models useful together.

---

ANGRA in One Sentence

ANGRA connects AI models running in LM Studio and Bionic so they can communicate, coordinate tasks, and operate as cooperating workers inside a larger AI workflow.

---

Core Concepts

1. Model Workers

ANGRA treats individual models as potential workers within a coordinated system.

A worker is not defined only by the model name.

A useful worker can also have:

- a role
- a capability profile
- a context scope
- task responsibilities
- communication permissions
- input and output requirements
- execution constraints
- verification requirements

Conceptually:

Worker
├── identity
├── model
├── runtime
├── role
├── capabilities
├── context
├── permissions
├── communication
├── task state
└── outputs

This makes it possible to move from:

"Which model should answer?"

toward:

"Which worker should perform this part of the task?"

---

2. Model Collaboration

ANGRA is designed around cooperation rather than isolated inference.

A workflow may look like:

Task
  │
  ▼
Planner
  │
  ├───────────────┐
  ▼               ▼
Researcher      Analyst
  │               │
  └───────┬───────┘
          ▼
       Engineer
          │
          ▼
        Reviewer
          │
          ▼
        Result

The models do not have to be identical.

Different workers can be selected for different responsibilities.

---

3. Communication Bridge

ANGRA provides the conceptual middle layer between model environments.

┌──────────────────────────────────────────────┐
│                  ANGRA                       │
│                                              │
│  Discovery → Routing → Messaging → Context  │
│        → Coordination → Verification         │
│                                              │
└───────────────┬──────────────────────────────┘
                │
       ┌────────┴────────┐
       │                 │
       ▼                 ▼
  LM Studio          Bionic

The purpose of the bridge is to reduce isolation between otherwise separate model execution environments.

Instead of manually copying information:

Model A → human → copy → Model B → human → copy

ANGRA is intended to enable machine-mediated communication:

Model A
   │
   │ structured message
   ▼
 ANGRA
   │
   │ routed context
   ▼
Model B
   │
   │ result
   ▼
 ANGRA
   │
   ▼
Model C

---

LM Studio + Bionic

ANGRA is designed to work across the two environments that form an important part of its initial ecosystem.

LM Studio

LM Studio provides an environment for working with local AI models and their runtime.

ANGRA does not replace that runtime.

Instead:

LM Studio
    │
    ▼
Local model
    │
    ▼
ANGRA

ANGRA can treat compatible models as workers in a larger coordinated workflow.

Bionic

Bionic is a separate AI-agent environment designed for working with open models, including local and remote model execution. It is particularly focused on agentic work such as coding, research, files, and documents.

ANGRA does not attempt to redefine Bionic.

Instead:

Bionic
  │
  ▼
Agent / model
  │
  ▼
ANGRA

The long-term objective is interoperability between these environments rather than forcing every worker into one application.

---

The AI Workforce Model

ANGRA uses an organizational analogy because the analogy reflects the intended architecture.

A conventional AI application may look like:

User
  ↓
One model
  ↓
One answer

A coordinated system can instead look like:

                       ANGRA
                         │
        ┌────────────────┼────────────────┐
        │                │                │
        ▼                ▼                ▼
   Researcher        Engineer          Reviewer
        │                │                │
        └────────────────┼────────────────┘
                         ▼
                   Final synthesis

Each worker may have different responsibilities.

For example:

Role| Responsibility
Planner| Decompose a large objective into executable tasks
Researcher| Gather and structure relevant information
Engineer| Implement or modify software
Analyst| Compare outputs and identify inconsistencies
Reviewer| Validate quality, constraints, and correctness
Synthesizer| Combine verified outputs into the final result

These are architectural roles, not claims that every deployment must use this exact topology.

---

Communication Model

A collaboration bridge needs more than model inference.

It needs structured communication.

A conceptual ANGRA message can be represented as:

{
  "sender": "research-worker",
  "recipient": "engineering-worker",
  "type": "task_context",
  "task_id": "task-001",
  "objective": "Implement the requested feature",
  "context": [],
  "artifacts": [],
  "constraints": [],
  "status": "ready"
}

The important principle is separation between:

identity
task
context
instructions
artifacts
permissions
status
result

Rather than treating every interaction as an unstructured chat transcript.

---

Task Routing

A coordinated AI workforce requires routing decisions.

Conceptually:

                  TASK
                    │
                    ▼
              Capability scan
                    │
          ┌─────────┼─────────┐
          ▼         ▼         ▼
       Worker A  Worker B  Worker C
          │         │         │
        score     score     score
          └─────────┼─────────┘
                    ▼
               Route task

Routing can consider factors such as:

- available model
- runtime
- role
- capabilities
- context requirements
- current workload
- task type
- latency constraints
- execution permissions
- verification requirements

ANGRA should therefore be understood as an orchestration layer rather than merely a model selector.

---

Context Handoff

One of the hardest problems in multi-model systems is transferring useful context without transferring unnecessary conversation history.

ANGRA is designed around explicit context exchange.

A context handoff can conceptually contain:

Task objective
      +
Relevant findings
      +
Required constraints
      +
Referenced artifacts
      +
Previous result
      +
Verification state

This creates a much cleaner boundary than blindly forwarding an entire conversation.

The result is a workflow in which workers receive the information required for their role.

---

<img width="1024" height="1536" alt="file_0000000001ec821088a7be36dcaaf94b" src="https://github.com/user-attachments/assets/c17ae029-262e-4278-b038-f4a0473e7459" />



Verification

Multiple models do not automatically produce reliable results.

A collaboration system therefore needs explicit verification paths.

Example:

Research Worker
      │
      ▼
Research result
      │
      ▼
Analysis Worker
      │
      ▼
Implementation Worker
      │
      ▼
Review Worker
      │
      ├── PASS ───────► Continue
      │
      └── FAIL ───────► Return for revision

This creates a feedback loop:

work
 ↓
inspect
 ↓
verify
 ↓
revise
 ↓
verify again

The exact verification strategy depends on the task and the implementation.

---

Networked AI Workers

A major direction of ANGRA is enabling model workers to communicate over a network rather than requiring every model to run inside the same process.

Conceptually:

        DEVICE A
┌──────────────────────┐
│ LM Studio            │
│ Model A              │
└──────────┬───────────┘
           │
           │ network
           ▼
        ANGRA
           │
           │ network
           ▼
┌──────────────────────┐
│ DEVICE B             │
│ Bionic               │
│ Model B              │
└──────────────────────┘

This creates the possibility of distributing AI workers across machines.

A future topology may therefore look like:

                ANGRA
                  │
       ┌──────────┼──────────┐
       │          │          │
       ▼          ▼          ▼
    Machine A  Machine B  Machine C
       │          │          │
      LLM        LLM        Agent

Network topology, authentication, authorization, transport security, and exposure boundaries must be explicitly designed and configured for the deployment.

ANGRA should never be interpreted as permission to expose an AI runtime directly to an untrusted network.

---

Local-First Architecture

One of the most important design goals is preserving control over where inference occurs.

ANGRA is intended to coordinate existing model environments rather than requiring every model to be moved into a centralized hosted system.

Conceptually:

Your hardware
     │
     ├── Model A
     ├── Model B
     ├── Model C
     └── Agent runtime
          │
          ▼
        ANGRA

This architecture can be useful for developers who want to experiment with local AI, heterogeneous model stacks, and networked model workflows.

Actual privacy characteristics depend on the deployment, network configuration, models, applications, and external services being used.

---

Architecture

At a high level:

┌─────────────────────────────────────────────────┐
│                    ANGRA                        │
│                                                 │
│  Integration                                    │
│      │                                          │
│      ├── Environment adapters                   │
│      │                                          │
│      ├── Worker registry                        │
│      │                                          │
│      ├── Capability discovery                   │
│      │                                          │
│      ├── Task routing                           │
│      │                                          │
│      ├── Message transport                      │
│      │                                          │
│      ├── Context handoff                        │
│      │                                          │
│      ├── Workflow coordination                 │
│      │                                          │
│      ├── Verification                           │
│      │                                          │
│      └── Observability                          │
│                                                 │
└───────────────┬─────────────────┬───────────────┘
                │                 │
                ▼                 ▼
          LM Studio           Bionic
                │                 │
                ▼                 ▼
           AI workers         AI workers

The implementation is expected to evolve.

The repository should therefore keep environment-specific integration code separated from the coordination core.

---

Design Principles

ANGRA is built around several principles.

Interoperability

Models should not have to belong to one vendor, one model family, or one runtime in order to participate in a workflow.

Explicit coordination

Communication should be a first-class architectural operation.

Role-based execution

A worker should be selected because it is appropriate for a task, not simply because it exists.

Context efficiency

Workers should receive relevant information rather than arbitrary amounts of unrelated history.

Observable workflows

Important actions should be inspectable through task state, events, logs, and outputs.

Controlled networking

Connecting models across machines introduces new attack surfaces and must be treated as an infrastructure problem, not merely a convenience feature.

Human control

The system should make it possible for operators to inspect, interrupt, modify, and review workflows.

---

What ANGRA Is Not

ANGRA is deliberately different from several common categories.

Category| ANGRA
AI model| No
LLM| No
Chatbot| No
Model provider| No
Replacement for LM Studio| No
Replacement for Bionic| No
Integration layer| Yes
Communication bridge| Yes
Orchestration layer| Yes
Multi-model coordination system| Yes
AI workforce infrastructure| Yes

The distinction matters.

The intelligence comes from the models and agents participating in the system.

ANGRA is the infrastructure that helps them work together.

---

Example Workflow

Consider a software engineering task:

"Investigate the bug, determine the root cause,
implement a fix, and review the change."

A coordinated workflow could become:

                    USER TASK
                        │
                        ▼
                    PLANNER
                        │
          ┌─────────────┼─────────────┐
          ▼             ▼             ▼
      RESEARCH       ANALYSIS      REPOSITORY
       WORKER         WORKER         WORKER
          │             │             │
          └─────────────┼─────────────┘
                        ▼
                    ENGINEER
                        │
                        ▼
                     TESTER
                        │
                        ▼
                    REVIEWER
                        │
                ┌───────┴───────┐
                │               │
              PASS             FAIL
                │               │
                ▼               ▼
              RESULT         REVISE

ANGRA's role is to coordinate the communication and state transitions that connect those workers.

---

Multi-Model Workflow Example

Another deployment could assign different models to different tasks:

Model A
Research
   │
   ▼
ANGRA
   │
   ▼
Model B
Reasoning
   │
   ▼
ANGRA
   │
   ▼
Model C
Coding
   │
   ▼
ANGRA
   │
   ▼
Model D
Verification

The models do not need to be the same size, architecture, provider, or runtime.

They simply need an interface that ANGRA can coordinate.

---

Installation

ANGRA is distributed through the project releases and integration packages.

The repository's releases are the authoritative location for versioned release artifacts.

Requirements

Your exact requirements depend on the ANGRA integration being used.

At a minimum, a deployment may require:

- a compatible operating system
- the corresponding ANGRA package
- a supported LM Studio or Bionic installation
- one or more compatible AI models
- network access when using distributed workers

Compatibility information should always be taken from the release notes for the specific ANGRA version.

---

Downloads

Official ANGRA packages are distributed separately for the supported environments.

LM Studio Package

Use the ANGRA release asset intended for LM Studio.

Bionic Package

Use the ANGRA release asset intended for Bionic.

«Release assets, filenames, version numbers, and checksums are intentionally documented only when the corresponding release has actually been published.»

See the repository's Releases page for the current artifacts.

---

Compatibility

ANGRA operates at the intersection of multiple software environments.

That means compatibility is not determined by ANGRA alone.

A compatibility matrix should therefore be maintained for:

ANGRA version
     ×
integration version
     ×
runtime version
     ×
model interface
     ×
operating system

Example:

Component| Compatibility
ANGRA| Defined per release
LM Studio| Defined per integration release
Bionic| Defined per integration release
Model| Depends on supported interface
Network mode| Deployment-dependent

No compatibility claim should be made unless it has been tested and documented.

---

Repository Structure

The project is intended to keep integrations, core coordination logic, documentation, and tests separated.

angra-ai/
│
├── src/
│   ├── core/
│   ├── bridge/
│   ├── workers/
│   ├── routing/
│   ├── networking/
│   ├── protocols/
│   └── verification/
│
├── integrations/
│   ├── lm-studio/
│   └── bionic/
│
├── docs/
│   ├── architecture/
│   ├── integrations/
│   ├── networking/
│   ├── security/
│   └── examples/
│
├── examples/
├── tests/
├── .github/
│   ├── workflows/
│   ├── ISSUE_TEMPLATE/
│   └── PULL_REQUEST_TEMPLATE.md
│
├── README.md
├── ARCHITECTURE.md
├── CONTRIBUTING.md
├── SECURITY.md
├── ROADMAP.md
└── CHANGELOG.md

The actual structure may evolve with the implementation.

---

Documentation

The repository is intended to document ANGRA at several levels.

Concepts

Explain what model collaboration, worker roles, routing, communication, and orchestration mean.

Integration

Explain how ANGRA connects to each supported environment.

Architecture

Explain the internal components and boundaries.

Networking

Explain how distributed workers communicate and what security boundaries are required.

Examples

Show small, reproducible workflows rather than only abstract diagrams.

Operations

Document logs, diagnostics, state, errors, recovery, and deployment behavior.

This separation is intentional: a developer searching for an installation problem should not have to read the entire architecture specification.

---

Security Model

Connecting AI workers across applications or machines changes the threat model.

ANGRA should therefore treat networking as a security boundary.

Important considerations include:

Identity
   ↓
Authentication
   ↓
Authorization
   ↓
Transport
   ↓
Message validation
   ↓
Capability restrictions
   ↓
Execution policy
   ↓
Auditability

A worker should not automatically inherit every capability of another worker.

For example, access to a model does not automatically imply access to:

- a filesystem
- a shell
- arbitrary network destinations
- secrets
- credentials
- other workers
- administrative operations

Capabilities should be explicitly scoped by the deployment and integration.

See "SECURITY.md" for the project's security reporting process and threat model.

---

Reliability

Distributed model workflows introduce failure modes that do not exist in ordinary single-model applications.

Examples include:

model unavailable
runtime disconnected
network timeout
malformed response
incompatible model interface
partial task completion
worker disagreement
stale context
duplicated execution
verification failure

A production-oriented orchestration layer therefore needs explicit state transitions.

Conceptually:

PENDING
   ↓
DISPATCHED
   ↓
RUNNING
   ↓
WAITING
   ↓
COMPLETED
   │
   └──► VERIFIED

or

RUNNING
   ↓
FAILED
   ↓
RETRY
   ↓
RUNNING

The actual state machine is implementation-specific.

---

Observability

A system composed of multiple workers becomes difficult to debug if only the final answer is visible.

ANGRA is therefore designed around observable execution.

Useful events include:

worker discovered
worker selected
task created
task dispatched
message sent
message received
context attached
worker completed
verification started
verification failed
retry requested
workflow completed

A future production deployment may expose this as logs, structured events, traces, or a graphical workflow view.

---

Research Direction

ANGRA is primarily an engineering project focused on a practical question:

«How can independently running AI models cooperate as coordinated workers rather than remaining isolated interfaces?»

Areas of ongoing exploration include:

- model-to-model communication
- capability-aware routing
- context handoff
- role-based worker systems
- distributed AI workflows
- local model interoperability
- networked model coordination
- task graphs
- verification loops
- human-in-the-loop control
- execution observability
- failure recovery
- model specialization

The project is expected to evolve as practical experimentation reveals which coordination patterns are useful.

---

Roadmap

The roadmap is intentionally capability-driven rather than date-driven.

Foundation

- [ ] Stable ANGRA core
- [ ] Worker abstraction
- [ ] Message model
- [ ] Task model
- [ ] Configuration system
- [ ] Logging and diagnostics

Integrations

- [ ] LM Studio integration
- [ ] Bionic integration
- [ ] Environment capability discovery
- [ ] Cross-environment worker registration

Coordination

- [ ] Worker selection
- [ ] Task routing
- [ ] Context handoff
- [ ] Multi-step workflow execution
- [ ] Verification paths
- [ ] Retry and recovery

Networking

- [ ] Remote worker discovery
- [ ] Authentication
- [ ] Authorization
- [ ] Secure transport
- [ ] Network policy controls
- [ ] Distributed observability

Ecosystem

- [ ] Developer documentation
- [ ] Integration SDK
- [ ] Examples
- [ ] Testing framework
- [ ] Community contributions
- [ ] Additional AI environments

Roadmap items may change as the architecture and supported environments mature.

---

Current Project Status

ANGRA is an actively developed Oblivion project.

The project is being developed around a concrete engineering objective:

«Connect AI models running in different environments and allow them to cooperate as specialized workers.»

Functionality, compatibility, interfaces, and release artifacts should always be considered version-specific.

Experimental capabilities should not be interpreted as stable production guarantees unless explicitly marked as such.

---

Design Philosophy

ANGRA follows a simple architectural idea:

One model
     ↓
One capability

Several models
     ↓
Several capabilities

Coordinated models
     ↓
A system

A network of coordinated models
     ↓
A workforce

The project is therefore less about creating another model and more about creating the infrastructure that lets models work together.

---

Frequently Asked Questions

Is ANGRA an AI model?

No.

ANGRA is a bridge and orchestration layer for coordinating AI models.

Does ANGRA replace LM Studio?

No.

LM Studio remains the model/runtime environment. ANGRA is designed to integrate with it.

Does ANGRA replace Bionic?

No.

Bionic is a separate agent environment. ANGRA is intended to provide coordination and communication between supported workers and environments.

Can different models work together?

That is the central purpose of the project.

The goal is to allow compatible models to operate as specialized workers inside the same larger workflow.

Does every worker need to run on the same machine?

No.

ANGRA is being designed with networked and distributed worker scenarios in mind. Exact support depends on the implementation and release.

Is ANGRA itself an agent?

ANGRA should not be reduced to a single-agent identity.

Its primary role is the infrastructure around communication, coordination, routing, and collaboration between participating AI workers and environments.

Is ANGRA a model router?

Routing is one possible function, but it is not the complete definition.

ANGRA is intended to coordinate workers, context, tasks, messages, workflows, and verification.

Is ANGRA fully autonomous?

The project's architecture is focused on coordination infrastructure. The level of autonomy depends on the workers, integrations, policies, and workflow configuration used by a deployment.

Can I use local models?

ANGRA is specifically oriented toward environments capable of running or connecting to local models, including LM Studio and Bionic.

Can I connect models running on different machines?

Distributed operation is a major architectural direction of the project. Network support and security requirements are release-dependent.

---

Who Is ANGRA For?

ANGRA is intended for people building systems around AI models rather than simply chatting with one model.

Potential users include:

- AI and ML engineers
- software developers
- agent-system researchers
- local-LLM users
- automation developers
- infrastructure engineers
- researchers experimenting with multi-model workflows
- developers building AI worker networks

---

Contributing

ANGRA is intended to become a collaborative engineering project.

Contributions are welcome in areas such as:

- integration development
- protocols
- model adapters
- routing
- networking
- testing
- documentation
- developer tooling
- observability
- security engineering
- examples

Please read "CONTRIBUTING.md" before opening a pull request.

A good contribution should ideally include:

Problem
   ↓
Design
   ↓
Implementation
   ↓
Tests
   ↓
Documentation

---

Reporting Security Issues

Please do not disclose potentially sensitive security vulnerabilities in public issues.

See "SECURITY.md" for the appropriate reporting process.

---

Project Principles

ANGRA is developed with the following principles:

Interoperability
Local control
Explicit communication
Modular architecture
Observable execution
Security boundaries
Human oversight
Reproducibility
Engineering over hype

The project intentionally avoids presenting experimental infrastructure as a magical autonomous intelligence.

---

Terminology

To reduce ambiguity, ANGRA uses the following terminology:

ANGRA
The integration, communication, and orchestration layer.

Worker
A model or agent environment participating in a coordinated workflow.

Model
The underlying AI model used by a worker.

Runtime
The environment responsible for executing the model.

Bridge
The communication layer connecting supported environments.

Orchestration
The coordination of tasks, workers, messages, and workflow state.

Task
A unit of work assigned to one or more workers.

Context handoff
The structured transfer of relevant information between workers.

Workflow
A sequence or graph of coordinated tasks.

Verification
A mechanism used to evaluate whether a result satisfies the required conditions.

---

Why This Project Is Different

The central question behind ANGRA is not:

«"How do we build another AI model?"»

It is:

«"How do we make the models we already have work together?"»

That distinction changes the architecture.

Instead of:

Model → Chat

ANGRA explores:

Model
  ↕
Worker
  ↕
ANGRA
  ↕
Worker
  ↕
Model

and ultimately:

                   ANGRA
      ┌─────────────┼─────────────┐
      │             │             │
   Research      Engineering    Review
    Worker          Worker       Worker
      │             │             │
      └─────────────┼─────────────┘
                    │
               Shared state
                    │
                    ▼
                Final result

The goal is a practical foundation for cooperative AI systems composed of multiple models and agent environments.

---

Built by Oblivion

ANGRA is developed by Oblivion, an independent software and AI engineering team exploring practical systems built around local AI, software engineering, automation, and intelligent infrastructure.

ANGRA represents one part of that work.

The repository focuses specifically on the problem of AI model interoperability and collaboration.

---

Status

Development

ANGRA is evolving.

Interfaces, integrations, protocols, release artifacts, and compatibility information may change between versions.

For reproducible deployments, pin a specific ANGRA release and consult the corresponding release documentation.

---

In Development

LM Studio integration
        │
        ▼
      ANGRA
        │
        ▼
 Bionic integration
        │
        ▼
Model collaboration
        │
        ▼
Networked workers
        │
        ▼
Cooperative AI systems

---

License

The repository license is defined by the "LICENSE" file included with the project.

Use, modification, and redistribution are governed by that license.

---

Citation

If ANGRA contributes to research, engineering work, experiments, or publications, use the repository's "CITATION.cff" file when available.

---

Final Principle

«AI does not have to be one model.

A useful AI system can be a network of specialized models that know how to work together.

ANGRA is the bridge.»
