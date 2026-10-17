---
name: Bustamante_Matrix_prompting_probing_question_synthesizer
description: "Formulates rigorous probing and verification questions to clarify ambiguities, validate missing preconditions, and establish human-in-the-loop alignment before pipeline execution. Sintetizador de preguntas de sondeo, preguntas de verificación, control de alineación con usuario, aclarar ambigüedad, pausar ejecución ante riesgo alto."
category: prompting
risk: safe
source: c-tocast
date_added: "2026-10-16"
---

# Probing Question Synthesizer


Systematically synthesizes rigorous probing, clarifying, and verification questions (*Probing Questions*) to resolve ambiguities, validate missing preconditions, and align the context with the human operator before executing critical or irreversible steps in the agent pipeline.


## When to Use This Skill


- PCE detects ambiguous requirements, undeclared assumptions, or missing dependencies in the request

- The instruction involves high-risk actions (writing files, deployments, state overwrites)

- The verification check step must be executed prior to a technical investigation or synthesis stage

- The user employs polysemic or imprecise terms that allow for multiple disparate architectures

- Part 4 of PCE’s mandatory five-part diagnostic framework is formulated


## The Probing Question Process


### 1. Identify Ambiguities and Missing Preconditions


First, scan the request for any information gaps or design conflicts:

1. Check for files, schemas, or libraries that are mentioned but not provided

2. Assess whether the user clearly specified the success and termination criteria

3. Detect contradictions between the stated objective and the imposed constraints

4. Classify actions according to their risk matrix (read/explore vs. write/mutate)

5. Formulate the critical questions that must be clarified by the operator


**If the technical gap is evident:**


- Is this a low-risk action where the agent can assume a safe default setting?   
- Is this a high-risk action where the agent MUST pause and consult the user?   
- What is the minimum information required to proceed without making incorrect assumptions?



### 2. Gather Evidence on Risk and Permission Boundaries


Classify uncertainty according to advanced agent workflow guidelines:


**Permission Matrix and Ambiguity Handling:**


```
permission_handling_matrix:

  low_risk_exploratory:

    nature: “Searches, reading existing files, inspecting dependencies”

    action: “Assume reasonable default parameters and report in traces, without blocking unnecessarily”

  high_risk_state_mutation:

    nature: “Overwriting code on disk, changing session variables, executing destructive commands”

    action: “Mandatorily pause execution and ask the user a closed-ended verification question”
```


**Verify Interaction Channels:**


- Does the interaction occur in a Colab interactive cell, a Discord command, or a standalone script?
- Does the environment allow for text-based clarifications without interrupting the execution thread?



### 3. Formulate a Questioning Strategy Hypothesis


Design the optimal type of questioning to resolve ambiguity in a single turn:


```
"To resolve ambiguity in the output format, I will formulate a closed-ended question

with exhaustive options (Option A vs. Option B)"


"To verify the missing source file, I will request confirmation of the physical path

by proposing the default assumption as a direct alternative"
```


### 4. Test Question Precision and Brevity


Review the draft questions to ensure they do not cause additional confusion:


**Question Quality Filter:**

```
question_quality_audit:
  is_direct_and_specific: true
  avoids_philosophical_rambling: true
  provides_clear_options: true
  highlights_impact_of_decision: true
```

### 5. Find the Root Cause of Operational Hesitation


Trace why the misalignment occurred in the original instruction:


Root causes of operational ambiguity:


- Instructions written in vague, colloquial language (“make it work quickly”)
- Lack of definition of the target environment (Linux Colab vs. Windows vs. Docker Server)
- Assumption that the agent knows local environment variables or non-injected API secrets
- Lack of clarification regarding backward compatibility with previous versions of dependencies


### 6. Implement Fix


Write the survey questions using a structured and actionable format:

```
Bad fix (open-ended, philosophical, or overwhelming questions):
What do you think about how we should program this, and which libraries do you prefer?


Good fix (precise verification questions with specific options):
### 4. Probing Questions (Verification and Alignment Check)

1. **Concurrency Context:** Will the final script run in isolation in a Google Colab cell, or should it remain coupled to the Discord bot’s event loop (`discord.py`)?

2. **Missing File Handling Policy:** If a referenced skill does not exist in the local folder, do you prefer to raise an explicit stop error (`INTERVENTION_REQUIRED`) or fall back gracefully to verified heuristics?
```

### 7. Test the Fix


**Verify that the questions allow the decision to be resolved:**

1. Verify that the options cover the main architectural scenarios

2. Verify that a single-word or single-letter response is sufficient to align the pipeline

3. Ensure that the agent states which assumption it will temporarily adopt if the user does not respond

4. Confirm that the wording maintains the role’s authoritative and professional tone



### 8. Prevent Regression


**Set a limit on the number of questions to avoid overwhelming the user:**

### 6. Implement Fix


Write probing questions using a structured and actionable format:


```
# Bad fix (open-ended, philosophical, or overwhelming questions):


What do you think about how we should program this, and which libraries do you like best?


# Good fix (precise verification questions with specific options):


### 4. Probing Questions (Verification and Alignment Check)

1. **Concurrency Environment:** Will the final script run in isolation in a Google Colab cell, or should it remain coupled to the Discord bot’s event loop (`discord.py`)?

2. **Missing File Handling Policy:** If a referenced skill does not exist in the local folder, do you prefer to throw an explicit stop error (`INTERVENTION_REQUIRED`) or fall back gracefully to verified heuristics?

```


### 7. Test the Fix


**Verify that the questions allow the decision to be resolved:**



1. Verify that the options cover the main architectural scenarios

2. Verify that a single-word or single-letter response is sufficient to align the pipeline

3. Ensure that the agent declares which assumption it will temporarily adopt if the user does not respond

4. Confirm that the phrasing respects the role’s authoritative and professional tone



### 8. Prevent Regression


**Set a question limit rule to avoid overwhelming the user:**


```
probing_invariants:

  max_questions_per_turn: 3

  mandatory_options_provided: true

  default_fallback_declared: true
```

### Questioning Techniques


**Forced-Choice Alternative Framing**


Instead of open-ended questions, pose well-defined technical dilemmas (“Do you prefer Approach A [higher speed] or Approach B [total isolation]?”), allowing the user to decide with minimal effort.   


**Default Assumption Declaration**


Accompany each question with the operational assumption that the system will adopt by default if no immediate feedback is received, ensuring that the workflow does not reach an indefinite deadlock.


**Risk-Tiered Triggering**


Reserve blocking questions exclusively for architectural decisions that change the system’s behavior or involve high-risk state changes.


## Common Questioning Patterns



**Over-Questioning on Trivialities**


```

# Bad Pattern: Asking about every optional or low-risk parameter

bad_behavior: “Ask the user which auxiliary variable name they prefer for an iterator”


# Good Pattern: Assume low-risk parameters and ask only about structural decisions

good_behavior: “Assume standard names in code and ask only about the XML contract format”

```


### Questioning Tools


**Ambiguity and Permission Scanner**


```

Operational Risk Analyzer: Distinguishes exploratory reads from state mutations


Technical Dilemma Generator: Transforms functional gaps into closed-ended questions (A vs. B)


Assumption Declarer: Documents the default operational hypothesis for each uncertainty

```




### When You're Stuck


1. If the instruction has too many unknowns, don't ask 10 questions: select the 2 most critical ones that determine the rest.

2. Always provide a recommended or suggested answer from the system engineering team.

3. If the user asks, “Do what you think is best,” assume the safest standard, document it explicitly, and proceed.

4. Remember that in the role of PCE, this section constitutes the formal Part 4 of your exit plan.

5. In Gus, combine these questions with a Socratic tone to address pedagogical inconsistencies.

6. In Dustin, if the missing precondition is absolute, issue <status>INTERVENTION_REQUIRED</status> instead of a simple free-text question.

7. Connect to @prompting-self-corrected-compiler once the user responds or the default assumption is set.


### Documentation Template


**Required structure for Part 4 of the PCE diagnostic framework:**


```

### 4. Probing Questions (User Verification Control Step)

1. **[Critical Axis 1 - Permissions / Environment]:** [Closed-ended question with options A vs. B]

   - *Default operational assumption:* [Action to be taken if no clarification is provided]

2. **[Critical Axis 2 - Format / Success Criteria]:** [Question regarding key restrictions or validations]

   - *Default operational assumption:* [Action to be taken if no clarification is provided]

```


### Key Principles


- ALWAYS ask questions regarding high-risk decisions, state changes, or critical architectural gaps   


- Avoid endless open-ended questions; offer closed-ended, verified alternatives


- Explicitly state which operational assumption will be adopted by default if the user tacitly approves. Limit questions to a maximum of 2 or 3 per interaction to prevent user fatigue


- Present this section as the mandatory Part 4 of the PCE diagnostic framework



### Related Skills

`Bustamante_Matrix_prompting_intent_classifier` - Classification of the prompt’s intent 
`Bustamante_Matrix_skeleton_of_thought_planner.md` - Early identification of gaps in planning
`Bustamante_Matrix_prompting_self_corrected_compiler` - Compilation of the optimized final prompt

### Limitations

- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.


