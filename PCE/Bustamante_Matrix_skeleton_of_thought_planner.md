---
name: prompting-skeleton-of-thought-planner
description: "Deconstructs complex prompt engineering challenges into a structured Skeleton-of-Thought (SoT) skeleton roadmap before writing, balancing computational cost, reasoning depth, latency, and token efficiency for multi-agent workflows. Planificador Skeleton of Thought, descomposición de pensamiento, hoja de ruta de prompts, balance costo precisión, planificación previa de prompts."
category: prompting
risk: safe
source: community
date_added: "2026-10-16"
---
# Skeleton-of-Thought Planner

Systematically breaks down complex prompt engineering problems into an organized preliminary framework (a "Skeleton-of-Thought") before drafting any final instructions, establishing an optimal balance between computational cost, latency, and semantic fidelity in multi-agent environments.

# When to Use This Skill

- PCE receives an extensive, chaotic, or unstructured prompt for optimization

- Planning the architecture of a multi-turn prompt is required before generating text

- Balancing latency, token consumption, and analytical precision for LLM calls needs to be configured

- An agentic workflow is producing erratic responses due to the lack of a prior reasoning map

- Initiating Step 1 of PCE’s mandatory five-part diagnostic framework

## The Planning Process
1. Analyze Prompt Scope and Complexity

First, define the scope of the task and the target language model:

```
- Identify the primary and secondary objectives of the request

- Determine the target foundational model (e.g., Gemini 3 series, Claude Sonnet 5, GPT-5.6)

- Estimate the required context window and the density of the input data

- Determine whether the task requires intensive analytical reasoning or straightforward completion

- Note any constraints regarding response time and system latency
```
If the scope is not evident, gather more information:
- Does the prompt operate in a batch call or in real-time via a chatbot?
- What level of determinism is required for inference?
- Will the end user tolerate additional latency due to internal reasoning phases?

### 2. Gather Evidence on Computational Constraints

Gather inference parameters and platform hardware limits:

**Inspect sampling parameters:**

Sampling_parameters_audit:

```
  temperature: "0.0 for deterministic transformations; 0.3-0.7 for analysis"
  top_p: "0.95 by default to maintain controlled lexical richness"
  top_k: "1 (greedy) for exact data extraction; 3-40 for balanced synthesis"
  max_output_tokens: "Strict budget to avoid abrupt code truncation"
```
**Check the resource balance:**

- Should the agent output its step-by-step reasoning or delegate it to the model’s internal reasoning?
- Can independent subtasks be parallelized to reduce the total time?
- What is the maximum input token budget for the context block?

#### 3. Form a Skeleton Hypothesis


**Design the preliminary intervention skeleton map by structuring the critical nodes:**

```
"For this security audit prompt, the Skeleton-of-Thought must separate

the syntactic scan from the analysis of logical vulnerabilities before generating the patch"


"The optimal skeleton requires: Node 1 (Schema Validation), Node 2 (Fact Extraction),

and Node 3 (Generating a Diagnosis in XML Format)"
```

### 4. Test the Roadmap Feasibility

**Verify that the skeleton solves the task without creating bottlenecks:**

Thought process simulation:

```
skeleton_simulation:

  node_1_ingestion: “Verify that the input contains all necessary files”

  node_2_constraint_audit: “Evaluate logical conflicts and regulatory ambiguities”

  node_3_resolution: “Synthesize the final solution in accordance with standards”

  verification_checkpoint: “Stop execution if node 1 detects missing data”
```

### 5. Find the Root Cause of Structural Bloat

**Investigate why the original prompt failed to generate consistent responses:**

Root causes of disorganization in prompts:


- Indiscriminate mixing of instructions, context, and examples in a single paragraph
- Overload of superfluous instructions that dilute critical guidelines
- Lack of visual delimiters between the analysis and delivery stages
- Insufficient token budget that truncates the output halfway through

### 6. Implement Fix

**Structure the Skeleton-of-Thought as a numbered hierarchical guide:**

Bad fix (vague planning with no prioritization):

```
# Plan: Read the prompt, improve it, and implement it correctly with code.
```

Good fix (hierarchical skeleton with explicit technical balance):

```
### 1. Skeleton-of-Thought

- **Intervention Nodes:**

  1. Identification and isolation of input data vs. role instructions.

  2. Detection of logical conflicts between constraints and functional goals.

  3. Reorganization according to canonical order: Long context -> Constraints -> Task.

- **Cost/Accuracy Balance:**

  - Verbosity level: High technical density, removal of conversational prose.

  - Determinism: Set to low for structural consistency.

  - Token savings: Removal of duplicate guidelines and lexical compaction.
```
### 7. Test the Fix: Verify that the skeleton guides the agent’s subsequent steps: 

1. Verify that each node in the skeleton addresses a dimension of the original problem

2. Verify that the order of the nodes respects logical dependencies

3. Verify that the projected token consumption remains within limits

4. Confirm that the skeleton is immediately understandable to the operator

8. Prevent RegressionSet the skeleton as the invariant startup contract for the pipeline:

```
   skeleton_invariant:

  mandatory_nodes: [“scope_decomposition”, ‘inference_parameters’, “phase_sequence”]

  enforce_before_generation: true
```

- Planning Techniques: Layered Dependency Mapping—Organize reasoning nodes so that normative requirements and input preconditions are always evaluated before creative synthesis or code design begins. 
- Cost-Accuracy Trade-off Sizing: Explicitly determines whether the query warrants the consumption of additional tokens in deep analytical reasoning or whether it should be resolved using high-speed, direct zero-shot patterns. 
- Parallel Skeleton Branching: Identifies subtasks within the prompt that lack mutual causal dependencies so they can be processed in a conceptually decoupled manner.

### Common Planning Patterns
**Unstructured Monolithic Prompt**

```
# Bad Pattern: Approaching the prompt without a preliminary skeleton

approach: “Generate the final response directly, expecting the model to infer the order”


# Good Pattern: Preliminary modular skeleton

approach: “First generate the Skeleton-of-Thought (Part 1) to map out the execution flow”
```

### Planning Tools
**Inference Configuration Profiler**

```
Token Budget Calculator: Estimates the input-to-output ratio (100 tokens ~ 60–80 words)

Parameter Selector: Sets safe combinations of temperature, top_p, and stop_sequences

SoT Node Auditor: Verifies full coverage of requirements before drafting
```

### When You're Stuck

1. If the user’s instruction is too vague, split the skeleton into two conditional branches (Scenario A vs. Scenario B).
2. Remember that Gemini 3 and advanced models automatically generate internal reasoning; the Skeleton-of-Thought should plan the prompt’s structure, not narrate trivial thoughts.
3. Always prioritize providing context before the specific task when processing lengthy documents.
4. If latency is critical, eliminate intermediate cosmetic formatting steps and focus on the functional core.
5. Verify that the skeleton includes an explicit node for formulating verification questions.
6. Consult `Bustamante_Matrix_prompting_intent_classifier` to determine the prompt layer before finalizing the plan.
7. Connect to `Bustamante_Matrix_prompting_self_corrected_compiler` to compile the final draft following the skeleton’s nodes.

### Mandatory Structure for Part 1 of the PCE Diagnostic Framework:Markdown
### 1. Skeleton-of-Thought

- **Structural Intervention Nodes:**

  1. [Node 1: Analysis of Dependencies and Inputs]

  2. [Node 2: Identification of Constraints and Failures]

  3. [Node 3: Formulation of the Output Contract]

- **Cost/Accuracy Balance:**

  - *Latency and Tokens:* [High compactness / Limited technical verbosity]

  - *Determinism:* [Suggested temperature and hallucination control]

### Key Principles:

1. Always map out the skeletal structure before writing or modifying a prompt.
2. Consciously balance computational cost and analytical fidelity. Respect the hierarchy of dependencies: validate inputs first, then synthesize.
3. Eliminate conversational filler to maximize information density per token.
4. Deliver this analysis as the essential Part 1 of the PCE diagnostic framework.

### Related Skills
`Bustamante_Matrix_prompting_intent_classifier` - Classification of the prompt’s intent 
`Bustamante_Matrix_prompting_probing_question_synthesizer` - Formulation of verification questions
`Bustamante_Matrix_prompting_self_corrected_compiler` - Compilation of the optimized final prompt

### Limitations

Use this skill only when the task clearly matches the scope described above. Do not treat the output as a substitute for environment-specific validation, testing, or expert review. Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
