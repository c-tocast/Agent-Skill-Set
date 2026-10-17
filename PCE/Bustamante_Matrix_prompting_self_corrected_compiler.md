---
name: Bustamante_Matrix_prompting_self_corrected_compiler
description: "Compiles finalized, highly optimized prompts with zero hallucinations using structured XML delimiters, constraint-first ordering, few-shot patterns, and end-anchoring for long contexts. Compilador de prompts optimizados, autocorrección de prompts, etiquetas XML estructuradas, diseño constraint first, anclaje temporal 2026."
category: prompting
risk: safe
source: c-tocast
date_added: "2026-10-16"
---

# Self-Corrected Prompt Compiler


Assembles, refines, and compiles draft prompts into their final production version with surgical precision and zero hallucinations, applying a constraint-first design, structured XML delimiters, and consistent example patterns, delivering Part 5 of the PCE diagnostic framework.


## When to Use This Skill


- PCE has completed the previous stages of analysis and must issue the final, corrected prompt

- A complex prompt needs to be structured using clean XML tags (`<role>`, `<constraints>`, `<context>`, `<task>`, `<output_format>`)

- The prompt must incorporate explicit temporal grounding (current year 2026) or strict non-hallucination grounding (*grounding*)

- The content of a long prompt needs to be reordered so that the block of critical instructions is anchored at the end

- Part 5 of PCE’s mandatory five-part diagnostic framework is completed


## The Compilation Process


### 1. Consolidate Insights from Previous Diagnostic Phases


Gather all findings from the previous stages before drafting the final version:

1. Review the nodes of the Skeleton-of-Thought (Part 1)

2. Incorporate the architectural layer defined in the Intent Analysis (Part 2)

3. Integrate the logical corrections and the Four Pillars of Diagnostic Feedback (Part 3)

4. Apply the answers or assumptions established in the Probing Questions (Part 4)

5. Sorts the XML blocks by context length


If the previous draft contained contradictions:


- Were the mutually exclusive pairs of constraints removed?


- Were vague prohibitions transformed into verifiable operational rules?


### 2. Enforce Constraint-First Structural Sequencing


Apply the Constraint-First design principle: place safety, scope, and format constraints before operational instructions:   


```

**Block hierarchy in the compiled prompt:**

<prompt_structure>

  <block order="1">role (Definition of identity and technical specialty)</block>

  <block order="2">constraints (Explicit prohibitions, limits, and rejection rules)</block>

  <block order="3">context (Data, schemas, documents, or code to be processed)</block>

  <block order="4">examples (Few-shot input/output pairs with 100% consistent formatting)</block>

  <block order="5">task (Step-by-step instructions in imperative mode)</block>

  <block order="6">output_format (Exact delivery template)</block>

</prompt_structure>

```


**Anchoring rule for long contexts:**


- If <context> contains many lines or large amounts of data, place <task> and the critical guidelines at the very end, preceded by the transition phrase: “Based on the information above...”.


### 3. Verify Few-Shot Consistency and Formatting



If the prompt includes few-shot examples, verify that they follow a precisely uniform pattern:



**Example Consistency Audit:**


- Same XML tags or headers in all examples

- - Consistent line separators and whitespace 


- Optimal number of 2 to 3 diverse examples to avoid overfitting   



### 4. Include Temporal and Strict Grounding Clauses Insert the mandatory technical clauses according to the agent’s use case: 


** Temporal Precision Clause (Current Year 2026):**


```

<temporal_grounding>

For time-sensitive queries requiring up-to-date information, you must take into account that the current year is 2026.

</temporal_grounding>

```


**Strict Grounding Clause (Anti-Hallucination / Grounding):**


```

<strict_grounding>

Strictly limit your responses to verifiable facts in the context block. If the requested information is not included in the provided data, state verbatim that it is unavailable; do not assume, extrapolate, or invent details.

</strict_grounding>

```


### 5. Find Root Cause of Prompt Vulnerabilities


Verify that the compiled prompt is not susceptible to deviations or leaks:


**Vulnerabilities eliminated during compilation:**


- Open XML tags without corresponding closures that break parsing


- Ambiguities in action verbs (e.g., “help with this” replaced by “analyze, extract, and synthesize”)


- Untyped output formats that allow the model to freely switch between JSON, Markdown, and plain text


- Restrictions placed at the end of lengthy prompts that the model overlooks due to attention drop-off


### 6. Assemble the Final Optimized Prompt

Generate the final prompt block encapsulated in clean XML delimiters:



```
# Bad draft (disorganized, no tags, prone to hallucinations):


You are a programmer. Review the code in the repository—do it quickly and make sure it’s error-free.


# Good draft (compiled according to prompt engineering standards):


<role>

You are a Systems Architect and Senior Implementation Engineer specializing in agent-based environments (CrewAI, Google Colab, LiteLLM). Your communication is direct, analytical, and highly technical.

</role>

<constraints>

1. Do not invent methods from unverified libraries or nonexistent functions.

2. Do not truncate code blocks; every solution must be complete and functional.

3. Always respond in rigorous technical Spanish.

4. If necessary files are missing from the context, return exactly <status>INTERVENTION_REQUIRED</status>.

</constraints>

<context>

[Insert directory tree, source file, or technical specification here]

</context>

<task>

Based on the information provided in the context block, perform the following tasks:

1. Analyze logical dependencies and validate preconditions.

2. Extract verified architectural patterns for the target environment.

3. Synthesize the complete implementation free of repetitive code or deprecations.

</task>

<output_format>

Structure your deliverable using the required sections:

- Technical Diagnosis

- Complete Code Implementation

- Verification Protocol

</output_format>
```

### 7. Test the Final Prompt Compilation


**Perform quality control on the final text before delivering it to the user:**

1. Check that all tags open and close correctly (<tag>...</tag>)
2. Verify that the constraints do not contain internal logical contradictions
3. Confirm that the estimated length respects the projected token window
4. Ensure that the prompt fully meets the user's original intent

### 8. Prevent Regression

**Establish a syntactic integrity check for the output:**

```
compiler_integrity_check:
xml_tags_balanced: true
constraint_first_verified: true
zero_contradictions: true
few_shot_consistent: true
```

### Compilation Techniques: 

**Delimiter-Enclosed Structural Sandboxing**

Encapsulate each section of the prompt within delimiters Explicit XML (<role>, <constraints>, <context>, <task>, <output_format>), allowing the LLM to clearly distinguish between operational instructions and the data supplied as input.

### Strict Grounding Lock

Incorporates instructions that treat the provided context as the absolute limit of truth, eliminating all speculation or invalid inductive extrapolation in technical auditing tasks.

### End-Anchored Instruction Bridging

In prompts with abundant reference material, places the <task> block at the end, preceded by transition connectors, to maximize the model's focus on the immediate actions to be executed.

**Common Compiler Patterns**

```
<!-- Bad Pattern: Mixing broken tags with non-hierarchical Markdown headings -->

# Role <role> You are an assistant </role> # Task: Do this

<!-- Good Pattern: Clean and organized blocks -->

<role>

You are a Systems Engineer specializing in agent architectures.

</role>

<task> Run the structural optimization of the attached script.

</task>
```

### Compiler Tools Prompt Syntax & Delimiter Linter

```
XML Tag Balancer: Checks opening and closing tag pairs

Few-Shot Format Validator: Audits structural consistency across examples

Time Anchor Checker: Confirms current year (2026) and cutoff clauses
```

### When You're Stuck

1. If the compiled prompt is too long, remove theoretical explanations in <constraints> and leave them as direct, imperative rules.

2. If the model tends to be erratic, strengthen the <strict_grounding> clause in the main constraints.

3. Check that there are never any orphaned tags like <examples> without their corresponding </examples>.

4. Connect to @prompting-four-pillars-diagnostic to verify that the prompt adheres to Google's Four Pillars.

### Documentation Template

Mandatory structure for Part 5 of the PCE diagnostic scheme:

```
### 5. Self-Corrected Optimized Prompt Draft

<role>
[Explicit definition of identity, technical expertise, and tone]
</role>
<constraints>
[Priority rules: what NOT to do, ethical boundaries, and mandatory format]
</constraints>
<context>
[Space reserved for data, schema, or code injection]
</context>
<task>
Based on the information above, execute:
1. [Step 1 instruction]
2. [Step 2 instruction]
</task>
<output_format>
[Exact template of required response]
</output_format>
```
### Key Principles

- ALWAYS apply the Constraint-First design: constraints before capabilities

- Delimit each section of the prompt using XML tags Consistent

- Use end-anchoring when the data context is extensive.

- Ensure that the few-shot examples share the exact same typographic structure.

- Submit this block as the culminating Part 5 of the PCE diagnostic framework.

### Related Skills

- `Bustamante_Matrix_skeleton_of_thought_planner` - Early identification of gaps in planning.

- `Bustamante_Matrix_architectural_intent_classifier` - Determination of the architectural layer.

- `Bustamante_Matrix_prompting_probing_question_synthesizer` - Integration of aligned responses and assumptions.

## Limitations

- Use this skill only when the task clearly matches the scope described above.

- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.

- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
