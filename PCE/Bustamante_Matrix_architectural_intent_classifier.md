---

name: prompting-architectural-intent-classifier

description: "Classifies prompt drafts by architectural layer (System Prompt vs. User Prompt vs. Modular Pre-Prompt), assigning a behavioral consistency weight (~70% vs. ~30%) and preventing override risks or boundary leakage. Architectural Intent Classifier, system prompt vs. user prompt, behavioral consistency weight, modular pre-prompts, override protection."

category: prompting

risk: safe

source: community

date_added: “2026-10-16”

---


# Architectural Intent Classifier


Systematically classifies any prompt draft by accurately determining its architectural execution layer (persistent System Prompt, on-demand User Prompt, or modular session-based Pre-Prompt), assigning behavioral consistency weights (~70% vs. ~30%), and shielding the system against scope leakage and attempts to override instructions.


## When to Use This Skill


- PCE receives a prompt and must discern whether it is a permanent system instruction or a one-time task

- A risk is detected that a user’s instructions may violate the system’s security guidelines

- An intermediate modular skill is required to contextualize retrieval-assisted generation (RAG) results

- The developer reports inconsistent behavior throughout a multi-turn conversation

- Part 2 of PCE’s mandatory five-part diagnostic framework is executed


