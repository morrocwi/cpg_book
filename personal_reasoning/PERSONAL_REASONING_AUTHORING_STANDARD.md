# Personal Reasoning Foundation and Protocol — Authoring Standard

## 1. Purpose

This standard defines how to write a Personal Reasoning Foundation that preserves a person's recurring reasoning principles without turning the file into a workflow, skill, persona, or operational controller.

The foundation is an interpretive reference. It may help humans and multiple AI systems understand the same person coherently, but it does not represent the whole person and has no execution authority.

## 2. Required files

1. `00_PERSONAL_REASONING_FOUNDATION_AND_PROTOCOL.yaml`
   - The actual foundation.
   - Contains philosophical basis, equations, principles, distinctions, examples, and revision protocol.

2. `personal_reasoning_foundation.schema.yaml`
   - Machine-validatable JSON Schema written in YAML.
   - Enforces required sections, ID patterns, limits, and non-operational role.

3. Optional extension files
   - `domains/*.yaml`
   - `examples/*.yaml`
   - `cases/*.yaml`
   - `history/CHANGELOG.yaml`

Extensions may interpret the foundation but must not silently change its core principles.

## 3. Recommended size

- Main foundation: 1,500–3,500 words.
- Roughly 180–450 lines.
- Roughly 12–35 KB.
- 6–15 active principles.
- 3–10 equations.
- 3–12 concise application examples.

When the main file exceeds 4,500 words or 500 lines, move domain material and long cases into extension files.

The foundation must remain small enough to:
- be read in one review session,
- fit into AI context without dominating the task,
- be versioned and compared,
- remain understandable to humans,
- avoid becoming a hidden knowledge base.

## 4. Writing method

### Step 1 — Collect experiences
Record situations, decisions, outcomes, mistakes, and corrections.

### Step 2 — Find recurrence
Do not create a principle from one isolated event unless it is clearly marked experimental.

### Step 3 — Write the principle
One principle should contain one main claim.

Bad:
> Be ethical, accurate, kind, safe, complete, fast, and always follow all rules.

Better:
> A claim must not be stronger than its supporting evidence.

### Step 4 — Add rationale
Explain why the principle matters and what failure it prevents.

### Step 5 — Add scope
State where it applies. Prefer domain-neutral principles in the main file.

### Step 6 — Add a counterexample
Show a recognizable misuse or failure.

### Step 7 — Add a revision trigger
State what evidence or event would justify reconsidering the principle or its scope.

### Step 8 — Assign stability
- `constitutional`: foundational distinction; rarely changed.
- `high`: strongly supported across contexts.
- `medium`: useful but context-sensitive.
- `experimental`: new or weakly tested.

## 5. Equations

Equations clarify relationships. They are not scientific proof.

Good uses:
- `ClaimStrength <= EvidenceStrength`
- `PR_(t+1) = Revise(PR_t, NewEvidence, Critique, Outcome)`
- `PR_t != Person`

Avoid:
- arbitrary numerical weights without evidence,
- equations that merely decorate prose,
- formulas that imply false precision,
- action-routing formulas disguised as reasoning.

Every equation must include:
- stable ID,
- name,
- expression,
- term definitions,
- plain-language meaning.

## 6. Pseudocode

Pseudocode may describe reflection and interpretation only.

It may:
- identify relevant principles,
- expose assumptions,
- identify uncertainty,
- map conceptual tensions,
- produce evaluation criteria.

It must not:
- select a workflow,
- assign an agent,
- call a tool,
- mutate a database,
- send a message,
- make a binding decision.

The final instruction should return a reasoning reference, not execute an action.

## 7. YAML format

- UTF-8.
- Two-space indentation.
- Never use tabs.
- Use `snake_case` keys.
- Use stable IDs such as `PR-001` and `EQ-PRF-01`.
- Use ISO dates: `YYYY-MM-DD`.
- Prefer lines under 100 characters.
- Quote values with `:`, `#`, ambiguous booleans, or leading special characters.
- Use folded text (`>`) for long prose.
- Use literal text (`|`) for pseudocode or text whose line breaks matter.
- Comments are for navigation only; normative content belongs in fields.

## 8. Separation from adjacent artifacts

| Artifact | Main question |
|---|---|
| Personal Reasoning | How does this person tend to interpret, judge, and revise? |
| Prompt | What is requested now? |
| Workflow | What sequence of work should occur? |
| Skill | What bounded capability can perform a task? |
| Memory | What facts, preferences, and events are stored? |
| Persona | How should expression sound or appear? |
| Policy | What conduct is institutionally permitted or required? |
| Knowledge base | What domain content and sources are available? |

A Personal Reasoning principle must still make sense when no workflow, tool, or AI agent is named.

## 9. Review standard

Before activation, verify:
- no hidden operational command,
- no claim that the file is the person,
- no private chain-of-thought,
- no unnecessary sensitive data,
- clear distinction between principle and policy,
- visible uncertainty and revision conditions,
- examples do not become universal rules,
- multiple AI systems can interpret the principle without being forced into identical output.

## 10. Validation

Python example:

```python
import yaml
from jsonschema import Draft202012Validator

with open("00_PERSONAL_REASONING_FOUNDATION_AND_PROTOCOL.yaml", encoding="utf-8") as f:
    document = yaml.safe_load(f)

with open("personal_reasoning_foundation.schema.yaml", encoding="utf-8") as f:
    schema = yaml.safe_load(f)

Draft202012Validator(schema).validate(document)
print("Valid")
```

Schema validation confirms structure, not philosophical quality. Human review remains necessary.
