# Continuity Handoff Test

## Purpose

The Continuity Handoff Test evaluates whether a body of work has become understandable and continuable beyond the people, agents, vendors, and tools that established its current state.

It is the central practical test of Arc Practice.

> **A durable workplace should enable a qualified new participant to orient, distinguish truth from uncertainty, perform bounded useful Work, and leave a coherent Outcome without depending on an undocumented private briefing.**

The test is not a general intelligence benchmark, employee performance review, penetration test, security certification, or proof that the workplace contains every relevant fact.

## Test subject

The subject is one bounded body of work represented through its current public or authorized workplace:

- purpose and scope;
- current Situation;
- accepted state;
- active and completed Work;
- evidence and artifacts;
- authority and acceptance rules;
- known risks and unknowns;
- procedures and valid next moves.

## Participant

The participant may be a qualified human, AI agent, or mixed human-agent team.

The participant should:

- not have established the environment;
- not have participated materially in the tested Work;
- not have access to the practitioner's private conversations or memory;
- possess the baseline domain competence required for the bounded task;
- receive only the interfaces and context a normal successor would receive.

A domain novice should not be used to manufacture a failure. The test measures continuity of the workplace, not whether the workplace can replace all professional competence.

## Practitioner constraint

During the scored portion, the practitioner may:

- resolve documented access failures;
- identify where a published instruction is located;
- answer a formal Decision Request through the same channel available in ordinary Work.

The practitioner should not:

- provide undocumented historical context;
- explain what the participant is “supposed to infer”;
- disclose private conversations;
- perform the task on the participant's behalf;
- silently repair the environment while the test is running;
- convert a missing instruction into an informal briefing.

Necessary interventions must be recorded as test evidence.

## Test Commission

The test should use a real, bounded, non-trivial task. A representative Commission is:

```text
Orient to this body of work from the available environment.

Identify:
- its purpose and current Situation;
- what is accepted, inferred, disputed, stale, missing, or unknown;
- active Work, material risks, and the next valid actions;
- the evidence supporting the most important claims;
- the authority or review required for consequential change.

Then perform one bounded useful task and return:
- a structured Outcome;
- supporting artifacts or evidence;
- limitations and unresolved questions;
- proposed improvements to the workplace for the next participant.
```

The task should be meaningful enough to reveal whether orientation supports action, but safe enough that a failed test does not create an uncontrolled consequential effect.

## Test phases

### Phase 1: Orientation

The participant should determine:

1. What body of work is this?
2. Why does it exist?
3. What is the current Situation?
4. Which materials are canonical, working, historical, or merely proposed?
5. What changed recently?
6. What remains uncertain?

Record time to first accurate orientation and any incorrect assumptions.

### Phase 2: Evidence and truth

The participant should trace at least three material claims to their evidence or attribution and classify each claim appropriately.

The test should include at least one known uncertainty so success does not reward false certainty.

### Phase 3: Authority and valid moves

The participant should identify:

- actions available without additional approval;
- actions requiring verification, domain judgment, approval, or Commit;
- prohibited or unsupported actions;
- how to request clarification without inventing a default.

### Phase 4: Bounded Work

The participant performs the agreed task using the available procedures, tools, and context.

Observe:

- unnecessary reconstruction;
- repeated questions already answered by the workplace;
- inappropriate tool or authority assumptions;
- evidence use;
- ability to recover from ambiguity;
- quality and resource proportionality.

### Phase 5: Outcome and accretion

The participant returns:

- artifacts;
- claims and their evidence class;
- limitations;
- unresolved questions;
- recommended next moves;
- Candidate improvements to the workplace.

The result should not become canonical merely because the participant completed the task.

### Phase 6: Debrief

After the scored portion, compare the participant's understanding with the accepted Situation and underlying evidence.

Classify each issue as one or more of:

```text
participant knowledge gap
missing workplace context
stale or contradictory state
unclear authority
evidence not discoverable
excessive context or noise
missing procedure
tool or interface failure
incorrect accepted state
```

The practitioner should treat workplace defects as actionable outcomes of the test.

## Measures

Minimum measures:

| Measure | Description |
|---|---|
| **Orientation time** | Time until the participant can accurately describe purpose, current Situation, and active Work |
| **Truth accuracy** | Accuracy in separating accepted, evidenced, inferred, disputed, stale, and unknown claims |
| **Evidence traceability** | Ability to locate support for material claims |
| **Authority awareness** | Accuracy in identifying permitted, gated, and prohibited actions |
| **Task completion** | Whether the bounded useful task produced an acceptable Outcome |
| **Private-briefing dependence** | Number and materiality of undocumented practitioner interventions |
| **Reconstruction burden** | Work repeated because prior results or procedures were not legible |
| **Accretive value** | Whether the participant left useful artifacts, questions, procedures, or corrections |
| **Resource proportionality** | Whether time, human attention, inference, and tools were proportionate to the task |

Additional domain-specific measures may be added but should not replace these.

## Suggested outcome classes

```text
PASS
  The participant accurately oriented, respected authority, completed
  the bounded task, and required no material undocumented briefing.

PASS_WITH_FINDINGS
  The task succeeded, but the test exposed material workplace defects
  that should be corrected.

INCONCLUSIVE
  Infrastructure, access, or participant-role mismatch prevented a fair test.

FAIL
  The participant could not accurately orient or continue because essential
  state, evidence, authority, or procedure remained dependent on private context.
```

A pass does not establish production readiness, security, completeness, or fitness for every future participant.

## Evidence bundle

A handoff test should preserve:

```text
test charter and participant profile
starting Situation and source revision
task Commission and Outcome Contract
permitted interfaces and authority
start and end times
questions and formal Decision Requests
undocumented interventions, if any
participant Outcome and artifacts
claim/evidence comparison
measure results
identified workplace defects
accepted remediation decisions
follow-up test requirement
```

Sensitive or private tests may retain this internally. Public projects should publish a sanitized result sufficient for readers to understand the method and limitations.

## Pass criteria

The project or organization should define thresholds before the test begins. At minimum, a pass requires:

- accurate identification of purpose and current Situation;
- no material confusion between accepted state and inference;
- successful tracing of material claims to evidence or explicit unknown status;
- correct recognition of consequential authority boundaries;
- completion of a bounded useful task;
- no material undocumented briefing from the practitioner;
- a structured Outcome with limitations and unresolved questions;
- recorded improvements for the next participant.

## Retest policy

A failed or qualified test should generate Work, not embarrassment.

After material defects are corrected, repeat the test with a new participant or a reset participant who does not receive the missing answers privately.

Repeated testing should become easier and less expensive as the workplace improves.

## First pilot: Attexa Arc Harness repository

The public repository is the first intended pilot.

A fresh participant with no access to the private development conversations should be asked to:

- explain the project thesis and accepted architecture;
- identify the current evidence floor;
- distinguish public source from non-public implementation;
- locate the next release gate;
- identify which claims may and may not be advanced;
- identify when an RFC is required;
- propose one compliant, evidence-bearing next piece of Work;
- report missing, contradictory, or overly implicit instructions.

The pilot should be tracked in a public issue and should not be recorded as a passed milestone until the test has actually been conducted and its results accepted.
