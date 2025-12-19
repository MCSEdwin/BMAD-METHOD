# Multi-Agent Workflow Implementation Guide

**Part IV of the Analytical Frameworks Design Document**

This comprehensive guide provides everything needed to implement multi-agent frameworks in BMad, from core patterns to complete working examples.

---

## TABLE OF CONTENTS

- [1. Agent Selection Algorithms](#1-agent-selection-algorithms)
- [2. Template Output for Multi-Agent Workflows](#2-template-output-for-multi-agent-workflows)
- [3. Facilitation Agent Design](#3-facilitation-agent-design)
- [4. Consensus Mechanisms](#4-consensus-mechanisms)
- [5. Party-Mode Invocation Patterns](#5-party-mode-invocation-patterns)
- [6. Validation Patterns for Group Outputs](#6-validation-patterns-for-group-outputs)
- [7. Annotated Workflow Example: Six Thinking Hats](#7-annotated-workflow-example-six-thinking-hats)
- [8. Template Files Library](#8-template-files-library)
- [9. Before/After: Converting Single to Multi-Agent](#9-beforeafter-converting-single-to-multi-agent)
- [10. XML Patterns Library](#10-xml-patterns-library)
- [11. Decision Trees & Flowcharts](#11-decision-trees--flowcharts)

---

# 1. AGENT SELECTION ALGORITHMS

## 1.1 Overview

Agent selection is the **core mechanism** that determines which agents participate in each framework round. Effective selection balances expertise, diversity, and role appropriateness.

## 1.2 Selection Strategies

### Strategy 1: Role-Based Filtering

**When to use:** Hat assignments, SWOT quadrants, specialized analysis

**Algorithm:**

```xml
<step n="2" goal="Select agents for White Hat (Facts & Data)">
  <action>Load agent manifest from {{agent_manifest}}</action>
  <action>Filter agents matching White Hat criteria:</action>

  <criteria>
    - Primary match: agents with role containing "analyst", "architect", "test"
    - Secondary match: agents with analytical strengths in manifest
    - Fallback: agents with data-driven communication style
  </criteria>

  <action>Select top 2-3 agents based on:</action>
  <scoring>
    - Role match (40 points)
    - Identity/expertise match (30 points)
    - Communication style match (20 points)
    - Previous framework performance (10 points if tracked)
  </scoring>

  <action>If fewer than 2 matches, use fallback agents: pm, dev</action>
</step>
```

**Example Implementation (Six Hats White Hat):**

```xml
<action>Select White Hat agents (Facts & Data perspective):</action>

<selection_logic>
  Primary candidates (score 100):
  - Analyst (role: data analysis, research, facts)
  - Architect (role: systems analysis, technical facts)
  - TEA (role: testing data, quality metrics)

  Secondary candidates (score 70):
  - PM (has access to business metrics)
  - Dev (knows technical constraints)

  Selection: Take top 2-3 by score

  Assigned: Analyst (100), Architect (100), TEA (100)
  Result: Use all three for comprehensive fact coverage
</selection_logic>
```

### Strategy 2: Context-Aware Dynamic Selection

**When to use:** Five Whys, problem-solving, investigation workflows

**Algorithm:**

```xml
<step n="3a" goal="Determine relevant investigators for current 'why'">
  <action>Analyze the current hypothesis/answer</action>
  <action>Extract key domains from user's previous response:</action>

  <domain_detection>
    Keywords → Domains → Agents:
    - "database", "query", "performance" → Technical → Architect, Dev, TEA
    - "user experience", "interface" → UX → UX Designer, PM
    - "deployment", "CI/CD", "infrastructure" → DevOps → Architect, TEA, Dev
    - "business logic", "requirements" → Product → PM, Analyst
    - "testing", "bugs", "quality" → Quality → TEA, Dev
  </domain_detection>

  <action>Select 2-3 agents whose expertise best matches detected domains</action>
  <action>Always include 1 facilitator (SM or BMad Master)</action>
</step>
```

**Example Implementation (Five Whys Round 2):**

```xml
<action>Current answer: "Health checks are timing out"</action>

<domain_analysis>
  Keywords: "health checks", "timing out"
  Domains: Infrastructure, Testing, Performance

  Relevant agents:
  - TEA (testing/monitoring expertise): 90 points
  - Architect (infrastructure design): 85 points
  - Dev (implementation details): 80 points
  - SM (facilitator): required

  Selection: TEA + Architect + Dev + SM (facilitator)
</domain_analysis>

<action>Agents investigate: Why do health checks timeout?</action>

<format>
  🧪 Murat (TEA): "App takes 90s to warm up, health check times out at 60s."
  🏗️ Winston (Architect): "Connection pool initialization adds 30s."
  💻 Amelia (Dev): "Lazy loading config could reduce startup time."
  📋 Bob (SM): "Consensus: Slow application startup. Let's dig deeper..."
</format>
```

### Strategy 3: Diversity-Driven Selection

**When to use:** Brainstorming, creative sessions, First Principles

**Algorithm:**

```xml
<step n="4" goal="Select agents for diverse perspective generation">
  <action>Identify framework phase: Discovery / Challenge / Rebuild</action>

  <discovery_phase>
    Goal: Maximum diversity of viewpoints
    Selection criteria:
    - Different modules (BMM, CIS, BMGD)
    - Different roles (technical, product, creative, analytical)
    - Different communication styles (data-driven, intuitive, creative)

    Example: Analyst + UX Designer + Innovation Strategist
  </discovery_phase>

  <challenge_phase>
    Goal: Aggressive assumption questioning
    Selection criteria:
    - Critical thinking agents (Architect, TEA)
    - Creative thinkers (Innovation Strategist, Creative Problem Solver)
    - External perspective (agents NOT involved in original decision)

    Example: Architect + Creative Problem Solver + TEA
  </challenge_phase>

  <rebuild_phase>
    Goal: Practical solution construction
    Selection criteria:
    - Implementers (Dev, Architect)
    - Validators (TEA, PM)
    - Synthesizers (BMad Master, SM)

    Example: Architect + Dev + TEA + BMad Master
  </rebuild_phase>
</step>
```

## 1.3 Agent Selection Patterns (Copy-Paste Ready)

### Pattern: Role-Based Hat Assignment

```xml
<!-- Use in workflow instructions.md -->
<step n="2" goal="Assign agents to hats based on role affinity">
  <action>Load agent manifest from {{agent_manifest}}</action>
  <action>Load hat configuration from {{hat_assignments}}</action>

  <action>For each hat, filter agents by criteria and select top 2-3:</action>

  <hat_assignment hat="white" name="Facts & Data">
    <criteria>
      Primary: analyst, architect, tea
      Fallback: dev, pm
    </criteria>
    <selected_agents>{{white_hat_agents}}</selected_agents>
  </hat_assignment>

  <hat_assignment hat="red" name="Emotions & Intuition">
    <criteria>
      Primary: ux-designer, creative-problem-solver, storyteller
      Fallback: pm, sm
    </criteria>
    <selected_agents>{{red_hat_agents}}</selected_agents>
  </hat_assignment>

  <!-- Repeat for all 6 hats -->

  <action>Display assignments to user for transparency</action>
</step>
```

### Pattern: Dynamic Problem-Domain Matching

```xml
<!-- Use in investigation workflows (Five Whys, debugging, root cause) -->
<step n="3a" goal="Select investigators based on problem domain">
  <action>Analyze current problem statement or hypothesis</action>

  <domain_matching>
    <check if="problem contains technical keywords">
      <action>Select technical agents: Architect (80%), Dev (70%), TEA (60%)</action>
    </check>

    <check if="problem contains UX/user keywords">
      <action>Select UX agents: UX Designer (90%), PM (70%), Analyst (50%)</action>
    </check>

    <check if="problem contains business/market keywords">
      <action>Select business agents: PM (90%), Analyst (80%), Innovation Strategist (60%)</action>
    </check>

    <check if="problem domain unclear">
      <action>Select diverse team: Analyst + Architect + PM (covers all bases)</action>
    </check>
  </domain_matching>

  <action>Always include 1 facilitator: SM or BMad Master</action>
  <action>Final team size: 3-4 agents (2-3 investigators + 1 facilitator)</action>
</step>
```

### Pattern: Consensus-Based Progressive Selection

```xml
<!-- Use when agents need to vote on next participants -->
<step n="5" goal="Agents nominate next round participants">
  <action>Current round agents identify knowledge gaps</action>

  <ask>Who should we bring in for the next perspective?</ask>

  <consensus_logic>
    Each agent nominates 1-2 agents with rationale:

    Example:
    🏗️ Architect: "We need TEA to validate testing implications"
    💻 Dev: "PM should weigh in on user impact"
    📋 SM: "I recommend TEA for quality perspective"

    Tally: TEA (2 votes), PM (1 vote)
    Selection: TEA + PM join next round
  </consensus_logic>

  <action>Add nominated agents to next round roster</action>
</step>
```

## 1.4 Anti-Patterns (Avoid These)

### ❌ Anti-Pattern 1: Hard-Coded Agent Names

```xml
<!-- BAD - Breaks when agents don't exist or are customized -->
<action>Select Winston, Murat, and Amelia for technical discussion</action>

<!-- GOOD - Uses role-based selection -->
<action>Select agents with roles: architect, tea, dev for technical discussion</action>
```

### ❌ Anti-Pattern 2: Too Many Agents Per Round

```xml
<!-- BAD - 8 agents creates chaos -->
<action>All agents participate in every hat round</action>

<!-- GOOD - 2-3 agents per focused role -->
<action>Select 2-3 agents matching current hat perspective</action>
```

### ❌ Anti-Pattern 3: No Facilitator

```xml
<!-- BAD - Agents discuss with no synthesis -->
<action>Agents debate without orchestration</action>

<!-- GOOD - Always include facilitator -->
<action>SM orchestrates discussion, synthesizes viewpoints, moves conversation forward</action>
```

---

# 2. TEMPLATE OUTPUT FOR MULTI-AGENT WORKFLOWS

## 2.1 Overview

Multi-agent workflows generate **group insights** that must be captured in structured templates. Unlike single-agent templates, multi-agent templates track:

- **Individual contributions** (who said what)
- **Consensus points** (agreements)
- **Dissenting opinions** (disagreements)
- **Synthesis** (facilitator summary)

## 2.2 Template Structure for Multi-Agent Outputs

### Basic Multi-Agent Template Pattern

```markdown
# {{framework_name}} Analysis: {{topic}}

**Date:** {{date}}
**Facilitator:** {{facilitator_name}}
**Participants:** {{agent_list}}

---

## Executive Summary

{{executive_summary}}

---

## Round-by-Round Insights

{{#each rounds}}

### Round {{round_number}}: {{round_goal}}

**Focus:** {{round_focus}}

#### Agent Contributions

{{#each agent_responses}}
**{{agent_icon}} {{agent_name}} ({{agent_role}}):**
{{agent_contribution}}

{{/each}}

#### Consensus Points

{{#each consensus_items}}

- {{consensus_point}}
  {{/each}}

#### Dissenting Opinions

{{#if dissenting_views}}
{{#each dissenting_views}}

- **{{agent_name}}:** {{dissenting_opinion}}
  {{/each}}
  {{else}}
- No dissenting opinions - full consensus
  {{/if}}

#### Facilitator Synthesis

{{facilitator_summary}}

---

{{/each}}

## Final Recommendations

{{final_recommendations}}

## Next Steps

{{#each action_items}}

- [ ] {{action_item}} - **Owner:** {{owner}} - **Timeline:** {{timeline}}
      {{/each}}
```

## 2.3 Template Examples by Framework Type

### Template: Six Thinking Hats Analysis

```markdown
# Six Thinking Hats Analysis: {{decision_topic}}

**Date:** {{date}}
**Facilitator:** {{facilitator_name}}
**Participants:** {{agent_count}} agents across 6 perspectives

---

## Decision Summary

**Topic:** {{topic}}
**Context:** {{context}}
**Objective:** {{objective}}

---

## Hat Perspectives

### 🤍 White Hat - Facts & Data

**Agents:** {{white_hat_agents}}

#### Facts Identified:

{{#each white_hat_facts}}

- {{fact}} _(Source: {{agent_name}})_
  {{/each}}

#### Data Points:

{{#each data_points}}

- **{{metric_name}}:** {{value}} - {{interpretation}} _({{agent_name}})_
  {{/each}}

---

### ❤️ Red Hat - Emotions & Intuition

**Agents:** {{red_hat_agents}}

#### Emotional Landscape:

{{#each emotional_reactions}}

- **{{agent_name}}:** {{emotional_response}}
  {{/each}}

#### Gut Feelings:

{{#each intuitions}}

- {{intuition}} _({{agent_name}})_
  {{/each}}

---

### 🖤 Black Hat - Critical Judgment

**Agents:** {{black_hat_agents}}

#### Risks Identified:

{{#each risks}}

- **Risk:** {{risk_description}}
  - **Severity:** {{severity}}
  - **Likelihood:** {{likelihood}}
  - **Identified by:** {{agent_name}}
    {{/each}}

#### Concerns:

{{#each concerns}}

- {{concern}} _({{agent_name}})_
  {{/each}}

---

### 💛 Yellow Hat - Optimism & Benefits

**Agents:** {{yellow_hat_agents}}

#### Benefits:

{{#each benefits}}

- **{{benefit_name}}:** {{benefit_description}} _({{agent_name}})_
  {{/each}}

#### Opportunities:

{{#each opportunities}}

- {{opportunity}} _({{agent_name}})_
  {{/each}}

---

### 💚 Green Hat - Creativity & Alternatives

**Agents:** {{green_hat_agents}}

#### Alternative Approaches:

{{#each alternatives}}

- **{{alternative_name}}:** {{description}} _({{agent_name}})_
  {{/each}}

#### Creative Ideas:

{{#each creative_ideas}}

- {{idea}} _({{agent_name}})_
  {{/each}}

---

### 💙 Blue Hat - Process Control & Synthesis

**Facilitator:** {{facilitator_name}}

#### Process Summary:

{{process_summary}}

#### Cross-Hat Synthesis:

**White Hat (Facts) revealed:**
{{white_summary}}

**Red Hat (Emotions) uncovered:**
{{red_summary}}

**Black Hat (Risks) identified:**
{{black_summary}}

**Yellow Hat (Benefits) highlighted:**
{{yellow_summary}}

**Green Hat (Alternatives) generated:**
{{green_summary}}

#### Final Recommendation:

{{recommendation}}

**Rationale:**
{{rationale}}

**Key Success Factors:**
{{#each success_factors}}

- {{factor}}
  {{/each}}

**Risk Mitigation:**
{{#each mitigations}}

- {{mitigation}}
  {{/each}}

---

## Decision Matrix

| Criterion | Weight | Score | Weighted | Notes |
| --------- | ------ | ----- | -------- | ----- |

{{#each criteria}}
| {{criterion}} | {{weight}}% | {{score}}/10 | {{weighted_score}} | {{notes}} |
{{/each}}
| **TOTAL** | **100%** | - | **{{total_score}}** | - |

---

## Action Items

{{#each action_items}}

- [ ] {{action}} - **Owner:** {{owner}} - **Due:** {{due_date}}
      {{/each}}

---

## Appendix: Dissenting Opinions

{{#if dissenting_opinions}}
{{#each dissenting_opinions}}

### {{agent_name}} - {{hat_color}} Hat

{{opinion}}

**Rationale:** {{rationale}}

{{/each}}
{{else}}
No significant dissenting opinions - strong consensus achieved.
{{/if}}
```

### Template: Five Whys Root Cause Analysis

```markdown
# Five Whys Root Cause Analysis: {{problem_statement}}

**Date:** {{date}}
**Facilitator:** {{facilitator_name}}
**Investigation Team:** {{agent_list}}

---

## Problem Statement

{{problem_statement}}

**Impact:** {{impact_description}}
**Frequency:** {{frequency}}
**First Observed:** {{first_observed}}

---

## Investigation Process

### WHY #1: {{why_1_question}}

**Current Understanding:** {{current_state}}

#### Agent Hypotheses:

{{#each why_1_hypotheses}}
**{{agent_icon}} {{agent_name}}:**
{{hypothesis}}

**Evidence:** {{evidence}}
{{/each}}

#### Consensus Answer:

{{why_1_consensus}}

**Rationale:** {{why_1_rationale}}

---

### WHY #2: {{why_2_question}}

**Building on:** {{why_1_consensus}}

#### Agent Hypotheses:

{{#each why_2_hypotheses}}
**{{agent_icon}} {{agent_name}}:**
{{hypothesis}}

**Challenges to other hypotheses:** {{challenges}}
{{/each}}

#### Consensus Answer:

{{why_2_consensus}}

---

### WHY #3: {{why_3_question}}

**Building on:** {{why_2_consensus}}

#### Agent Hypotheses:

{{#each why_3_hypotheses}}
**{{agent_icon}} {{agent_name}}:**
{{hypothesis}}
{{/each}}

{{#if branch_detected}}

#### 🔀 BRANCH DETECTED

Multiple root causes identified:

**Path A:** {{path_a_description}}
**Path B:** {{path_b_description}}

Continuing investigation on both paths...
{{/if}}

#### Consensus Answer:

{{why_3_consensus}}

---

{{#if branch_a}}

### WHY #4a (Path A): {{why_4a_question}}

**Building on:** {{path_a_previous}}

#### Agent Investigation:

{{#each why_4a_hypotheses}}
**{{agent_icon}} {{agent_name}}:**
{{hypothesis}}
{{/each}}

#### ROOT CAUSE A:

{{root_cause_a}}

**Why this is root:** {{root_cause_a_rationale}}

---

{{/if}}

{{#if branch_b}}

### WHY #4b (Path B): {{why_4b_question}}

**Building on:** {{path_b_previous}}

#### Agent Investigation:

{{#each why_4b_hypotheses}}
**{{agent_icon}} {{agent_name}}:**
{{hypothesis}}
{{/each}}

#### ROOT CAUSE B:

{{root_cause_b}}

**Why this is root:** {{root_cause_b_rationale}}

---

{{/if}}

## Root Cause Summary

### Primary Root Causes Identified:

{{#each root_causes}}
**{{root_cause_number}}. {{root_cause_name}}**

**Description:** {{description}}

**How it causes the problem:** {{causal_chain}}

**Evidence:** {{evidence}}

**Agent consensus:** {{consensus_level}}

{{/each}}

---

## Proposed Solutions

{{#each solutions}}

### Solution {{solution_number}}: {{solution_name}}

**Addresses root cause:** {{addresses_root_cause}}

**Proposed by:** {{agent_name}}

**Implementation:**
{{implementation_description}}

**Expected impact:**

- {{impact_metric_1}}
- {{impact_metric_2}}

**Feasibility:** {{feasibility_score}}/10

**Agent Reactions:**
{{#each agent_reactions}}

- **{{agent_name}}:** {{reaction}}
  {{/each}}

---

{{/each}}

## Recommended Solution

{{recommended_solution}}

**Rationale:** {{recommendation_rationale}}

**Implementation Plan:**

{{#each implementation_steps}}

- [ ] **Step {{step_number}}:** {{step_description}}
  - **Owner:** {{owner}}
  - **Timeline:** {{timeline}}
  - **Dependencies:** {{dependencies}}
    {{/each}}

**Success Metrics:**

{{#each success_metrics}}

- {{metric_name}}: {{current_value}} → {{target_value}}
  {{/each}}

**Risk Mitigation:**

{{#each risk_mitigations}}

- **Risk:** {{risk}}
  - **Mitigation:** {{mitigation}}
    {{/each}}

---

## Investigation Chain Diagram
```

Problem: {{problem_statement}}
↓ WHY?
{{why_1_consensus}}
↓ WHY?
{{why_2_consensus}}
↓ WHY?
{{why_3_consensus}}
↓ WHY? (BRANCHES)
├─ Path A → {{root_cause_a}}
└─ Path B → {{root_cause_b}}

```

---

## Appendix: Agent Contributions Log

{{#each agents}}
### {{agent_name}} ({{agent_role}})

**Hypotheses contributed:** {{hypothesis_count}}
**Key insights:**
{{#each key_insights}}
- {{insight}}
{{/each}}

**Challenges raised:**
{{#each challenges}}
- {{challenge}}
{{/each}}

{{/each}}
```

## 2.4 Template Variables for Multi-Agent Workflows

### Core Variables (All Frameworks)

```yaml
# Metadata
date: system-generated
facilitator_name: "{{agent.displayName}}"
facilitator_role: "{{agent.title}}"
agent_list: "Comma-separated list of participant display names"
agent_count: "Integer count of participating agents"

# Framework Info
framework_name: "Six Hats" | "Five Whys" | "First Principles"
topic: "User-provided problem/decision statement"
context: "Background information"
objective: "What user wants to achieve"

# Process Tracking
rounds: Array of round objects
current_round: Integer
total_rounds: Integer
```

### Agent-Specific Variables

```yaml
# Individual Agent Data (from manifest)
agent_icon: 'Emoji from manifest'
agent_name: 'displayName from manifest'
agent_role: 'title from manifest'
agent_identity: 'identity field from manifest'
agent_communication_style: 'communicationStyle from manifest'

# Contribution Tracking
agent_contribution: 'What this agent said in this round'
agent_hypothesis: "Agent's theory/proposal"
agent_evidence: 'Supporting data agent provided'
agent_rationale: 'Why agent believes this'
```

### Consensus Variables

```yaml
# Agreement Tracking
consensus_points: Array of agreements
consensus_level: "Full" | "Strong" | "Moderate" | "Weak" | "No consensus"
dissenting_opinions: Array of disagreements
dissenting_agents: List of agents who disagreed

# Synthesis
facilitator_summary: "Facilitator's round synthesis"
key_insights: "Major discoveries from round"
```

### Framework-Specific Variables

#### Six Hats

```yaml
# Hat Assignments
white_hat_agents: 'Analyst, Architect, TEA'
red_hat_agents: 'UX Designer, Creative Problem Solver'
black_hat_agents: 'TEA, Architect, SM'
yellow_hat_agents: 'PM, Innovation Strategist'
green_hat_agents: 'Innovation Strategist, Creative Problem Solver'
blue_hat_agent: 'BMad Master'

# Hat Outputs
white_hat_facts: Array of facts
red_hat_emotions: Array of emotional reactions
black_hat_risks: Array of risks
yellow_hat_benefits: Array of benefits
green_hat_alternatives: Array of alternatives
blue_hat_synthesis: 'Overall synthesis'
```

#### Five Whys

```yaml
# Why Chain
why_1_question: 'Why does X happen?'
why_1_hypotheses: Array of agent theories
why_1_consensus: 'Agreed answer to why #1'
why_1_rationale: 'Why we believe this answer'

# Repeat for why_2, why_3, why_4, why_5

# Branching
branch_detected: true | false
path_a_description: 'Branch A root cause description'
path_b_description: 'Branch B root cause description'
root_cause_a: 'Final root cause on path A'
root_cause_b: 'Final root cause on path B'

# Solutions
solutions: Array of proposed solutions
recommended_solution: 'Selected solution'
recommendation_rationale: 'Why this solution was chosen'
```

#### First Principles

```yaml
# Deconstruction
fundamental_truths: Array of identified truths
questioned_assumptions: Array of challenged assumptions
discarded_assumptions: Array of rejected assumptions
validated_constraints: Array of confirmed constraints

# Reconstruction
alternative_approaches: Array of rebuilt solutions
approach_1_description: 'First principles solution 1'
approach_2_description: 'First principles solution 2'
approach_comparison: 'Matrix comparing approaches'
```

## 2.5 Checkpoint Protocol for Multi-Agent Templates

**Critical:** Multi-agent workflows must save after EVERY round to prevent context loss.

```xml
<!-- After each round completes -->
<template-output>round_{{n}}_insights</template-output>

<checkpoint_protocol>
  1. SAVE: Write round insights to template immediately
  2. SEPARATOR: Display ━━━━━━━━━━━━━━━━━━━━━━━
  3. CONTENT: Show what was just saved
  4. OPTIONS: Present [a]Advanced/[c]Continue/[p]Party-Mode/[y]YOLO
  5. WAIT: For user response before next round
</checkpoint_protocol>

<critical>
⚠️ NEVER batch rounds - Each round is a checkpoint!
Multi-agent frameworks generate high token counts. Checkpointing prevents loss if context expires mid-framework.
</critical>
```

---

# 3. FACILITATION AGENT DESIGN

## 3.1 Overview

**Facilitator agents** are the orchestrators of multi-agent frameworks. They:

- Guide the conversation flow
- Synthesize diverse viewpoints
- Detect and resolve conflicts
- Maintain framework discipline
- Provide meta-cognitive oversight

## 3.2 Facilitator Agent Requirements

### Core Capabilities

```yaml
facilitator_capabilities:
  synthesis:
    description: 'Ability to summarize multiple viewpoints into coherent whole'
    examples:
      - 'Analyst sees technical debt, PM sees opportunity cost. The core issue is resource allocation.'
      - 'Three agents mentioned speed, two mentioned reliability. Consensus: performance is the priority.'

  conflict_resolution:
    description: 'Navigate disagreements productively without forcing consensus'
    examples:
      - "Winston and Amelia disagree on approach. Let's explore both options before deciding."
      - 'This debate reveals a deeper question: Do we optimize for now or for scale?'

  time_management:
    description: 'Keep framework on track without rushing insights'
    examples:
      - "We're deep on White Hat facts. Let's capture these and move to Red Hat emotions."
      - "This why chain is getting long. We're at 7 levels - let's check if we've hit root cause."

  question_formulation:
    description: 'Ask clarifying questions that deepen analysis'
    examples:
      - "Murat, when you say 'slow,' what's the actual metric?"
      - 'John, is this a must-have or a nice-to-have for MVP?'

  bias_detection:
    description: 'Notice groupthink, confirmation bias, anchoring'
    examples:
      - "I notice we're all agreeing. Let's actively look for counterarguments."
      - "We're anchored on the first solution proposed. What if we started fresh?"
```

### Facilitation Patterns by Framework

#### Pattern: Six Hats Facilitation

```xml
<facilitator_role agent="bmad-master" framework="six-hats">

  <round_introduction>
    <!-- Before each hat -->
    <action>Announce hat color and focus</action>
    <action>Remind agents to contribute ONLY from this perspective</action>
    <action>Set expectations for round</action>

    <format>
      ═══════════════════════════════════════
      🤍 WHITE HAT - Facts & Data
      Focus: Objective information only. No interpretations.
      Agents: Analyst, Architect, TEA
      ═══════════════════════════════════════
    </format>
  </round_introduction>

  <during_round>
    <action>Listen for perspective violations (agent mixing hats)</action>

    <check if="agent violates hat perspective">
      <gentle_redirect>
        "{{agent_name}}, that's a great {{actual_hat}} insight.
        Let's save it for {{actual_hat}} round.
        For White Hat, focus only on facts."
      </gentle_redirect>
    </check>

    <action>Encourage quiet agents</action>
    <ask if="agent hasn't contributed">"{{agent_name}}, what facts do you see from your {{role}} perspective?"</ask>

    <action>Probe for depth</action>
    <ask if="contribution is vague">"Can you quantify that or provide specific examples?"</ask>
  </during_round>

  <round_synthesis>
    <action>Summarize key points from round</action>
    <action>Identify patterns or themes</action>
    <action>Preview how this connects to next hat</action>

    <format>
      Key Facts Identified:
      - {{fact_1}}
      - {{fact_2}}
      - {{fact_3}}

      This data will inform our emotional reactions in Red Hat round.
    </format>
  </round_synthesis>

  <final_synthesis>
    <!-- After all hats -->
    <action>Weave together all six perspectives</action>
    <action>Identify consensus recommendations</action>
    <action>Highlight unresolved tensions</action>
    <action>Propose decision framework</action>

    <format>
      White Hat facts show {{summary}}.
      Red Hat reactions reveal {{summary}}.
      Black Hat identified risks: {{risks}}.
      Yellow Hat found benefits: {{benefits}}.
      Green Hat generated alternatives: {{alternatives}}.

      Synthesis: {{final_recommendation}}
    </format>
  </final_synthesis>

</facilitator_role>
```

#### Pattern: Five Whys Facilitation

```xml
<facilitator_role agent="sm" framework="five-whys">

  <problem_framing>
    <action>Help user articulate clear problem statement</action>
    <action>Confirm problem is specific and measurable</action>
    <action>Set investigation scope</action>

    <format>
      Problem: "Deployments fail 40% of the time"
      Measurable: Yes (40% failure rate)
      Specific: Yes (during deployment)
      Scope: Production deployment process

      Ready to investigate.
    </format>
  </problem_framing>

  <why_round_facilitation>
    <action>Ask the "why" question clearly</action>
    <action>Collect hypotheses from each investigator</action>
    <action>Encourage agents to challenge each other's theories</action>
    <action>Drive toward consensus (not forced agreement)</action>

    <format>
      WHY #{{n}}: Why does {{previous_answer}} happen?

      {{agent_1_hypothesis}}
      {{agent_2_hypothesis}}
      {{agent_3_hypothesis}}

      {{agent_2_challenges_agent_1}}
      {{agent_1_refines_hypothesis}}

      Consensus: {{agreed_answer}}
    </format>
  </why_round_facilitation>

  <branch_detection>
    <check if="multiple valid root causes emerge">
      <action>Recognize the branch explicitly</action>
      <action>Ask user if both paths should be investigated</action>
      <action>Track branches separately if confirmed</action>

      <format>
        I'm seeing two distinct causal paths here:

        Path A: {{cause_a}} → {{root_a}}
        Path B: {{cause_b}} → {{root_b}}

        Both seem valid. Should we investigate both or focus on one?
      </format>
    </check>
  </branch_detection>

  <root_cause_validation>
    <check if="answer feels like root cause">
      <validation_criteria>
        - Is it actionable? (Can we fix it?)
        - Is it fundamental? (Fixing it prevents symptom?)
        - Is it organizational/process? (Not "because physics")
        - Is it within our control?
      </validation_criteria>

      <ask>Does this feel like the root cause, or should we go deeper?</ask>

      <check if="consensus is YES">
        <action>Declare root cause found</action>
        <action>Transition to solution generation</action>
      </check>

      <check if="consensus is NO">
        <action>Continue to next why round</action>
      </check>
    </check>
  </root_cause_validation>

</facilitator_role>
```

#### Pattern: First Principles Facilitation

```xml
<facilitator_role agent="innovation-strategist" framework="first-principles">

  <deconstruction_facilitation>
    <action>Guide agents to identify fundamental truths</action>
    <action>Challenge "because we've always done it" thinking</action>
    <action>Push for physics/logic/economics level reasoning</action>

    <format>
      Let's break this down to absolute fundamentals.

      What MUST be true? (Physics, logic, user needs)
      What do we ASSUME is true? (Convention, best practices)

      Let's separate these clearly.
    </format>
  </deconstruction_facilitation>

  <assumption_challenge>
    <action>For each assumption, ask: "Is this physics or convention?"</action>

    <challenge_template>
      Assumption: "{{assumption}}"

      Why do we believe this?
      - {{agent_1_reasoning}}
      - {{agent_2_reasoning}}

      Counter-evidence?
      - {{agent_3_challenge}}

      Verdict: [FUNDAMENTAL TRUTH] or [QUESTIONABLE ASSUMPTION]
    </challenge_template>

    <action>Be aggressive - surface uncomfortable truths</action>
    <action>Encourage "stupid questions" that challenge status quo</action>
  </assumption_challenge>

  <reconstruction_facilitation>
    <action>Guide agents to rebuild from only fundamental truths</action>
    <action>Encourage radical alternatives</action>
    <action>Protect unconventional ideas from premature criticism</action>

    <format>
      We've stripped away assumptions. Now rebuild.

      If you started fresh, knowing only these truths:
      {{#each fundamental_truths}}
      - {{truth}}
      {{/each}}

      How would you solve this?

      No constraints except physics and user needs.
    </format>
  </reconstruction_facilitation>

  <reality_check>
    <action>After creative reconstruction, validate against reality</action>
    <action>Identify which discarded assumptions actually matter</action>
    <action>Balance radical rethinking with practical constraints</action>

    <format>
      We've generated {{count}} first principles solutions.

      Now reality check:
      - Which discarded assumptions actually matter?
      - What are the real (not assumed) constraints?
      - Which solution respects truths AND reality?
    </format>
  </reality_check>

</facilitator_role>
```

## 3.3 Facilitator Anti-Patterns (Avoid These)

### ❌ Anti-Pattern 1: Passive Facilitator

```xml
<!-- BAD - Facilitator just watches -->
<action>Agents discuss freely without guidance</action>

<!-- GOOD - Active orchestration -->
<action>Facilitator guides flow, asks clarifying questions, synthesizes insights</action>
```

### ❌ Anti-Pattern 2: Forcing Consensus

```xml
<!-- BAD - Pressures agents to agree -->
<action>Keep debating until everyone agrees on single answer</action>

<!-- GOOD - Acknowledges productive disagreement -->
<action>
  We have two perspectives here:
  - Approach A (Architect, TEA): {{reasoning_a}}
  - Approach B (PM, Dev): {{reasoning_b}}

  Both have merit. Let's present both to the user for decision.
</action>
```

### ❌ Anti-Pattern 3: Dominating the Conversation

```xml
<!-- BAD - Facilitator talks more than agents -->
<action>Facilitator provides lengthy explanations and opinions</action>

<!-- GOOD - Facilitator asks questions, agents provide insights -->
<action>Facilitator asks: "Why?" or "Can you elaborate?"</action>
<action>Agents provide the substance</action>
```

## 3.4 Facilitation XML Patterns (Copy-Paste Ready)

### Pattern: Round Introduction

```xml
<step n="{{round_number}}" goal="{{round_goal}}">
  <facilitator_introduction>
    <action>Announce round focus and agents</action>

    <format>
      ═══════════════════════════════════════
      {{round_title}}
      Focus: {{round_focus}}
      Agents: {{participating_agents}}
      ═══════════════════════════════════════
    </format>
  </facilitator_introduction>

  <!-- Round execution -->
</step>
```

### Pattern: Conflict Resolution

```xml
<check if="agents disagree significantly">
  <facilitator_intervention>
    <action>Acknowledge both perspectives</action>
    <action>Identify root of disagreement</action>
    <action>Reframe as complementary or ask user to decide</action>

    <format>
      I see disagreement between {{agent_1}} and {{agent_2}}.

      {{agent_1}} believes: {{perspective_1}}
      {{agent_2}} believes: {{perspective_2}}

      The root question is: {{underlying_question}}

      <check if="both valid">
        <action>Both perspectives are valid for different contexts.</action>
        <ask>User, which context matches your situation?</ask>
      </check>

      <check if="need more data">
        <action>We need more information to resolve this.</action>
        <ask>{{specific_question_to_resolve}}</ask>
      </check>
    </format>
  </facilitator_intervention>
</check>
```

### Pattern: Synthesis

```xml
<substep n="{{round}}.synthesis" goal="Facilitator synthesizes round insights">
  <action>Summarize key points from all agent contributions</action>
  <action>Identify patterns and themes</action>
  <action>Bridge to next round or final recommendation</action>

  <format>
    Key Insights from {{round_name}}:

    {{#each key_points}}
    - {{key_point}} ({{contributing_agents}})
    {{/each}}

    Patterns observed:
    {{#each patterns}}
    - {{pattern}}
    {{/each}}

    {{#if next_round}}
    This leads us to {{next_round_name}}...
    {{else}}
    Final synthesis: {{final_recommendation}}
    {{/if}}
  </format>
</substep>
```

---

# 4. CONSENSUS MECHANISMS

## 4.1 Overview

Consensus mechanisms determine how multi-agent frameworks reach decisions when agents have different perspectives. BMad supports multiple consensus approaches depending on framework goals.

## 4.2 Consensus Types

### Type 1: Full Consensus (Unanimous Agreement)

**When to use:** Critical decisions, safety-critical systems, compliance requirements

**Process:**

```xml
<consensus_type name="full_consensus">
  <process>
    1. All agents must explicitly agree
    2. ANY dissent blocks decision
    3. Dissenting agent must articulate concerns
    4. Team addresses concerns until resolved OR
    5. Escalate to user for tiebreak
  </process>

  <example>
    Round result: 5 agents support Option A, 1 agent (TEA) objects

    Facilitator: "Murat objects due to security concerns. Let's address these."

    [Team discusses security mitigations]

    TEA: "With the proposed mitigations, I'm comfortable. Consensus achieved."
  </example>
</consensus_type>
```

### Type 2: Majority Consensus (>50% Agreement)

**When to use:** Standard decisions, multiple valid options, time-sensitive choices

**Process:**

```xml
<consensus_type name="majority_consensus">
  <process>
    1. Agents vote or express preference
    2. >50% agreement = consensus
    3. Record minority opinions
    4. Facilitator synthesizes
  </process>

  <example>
    Voting:
    - Option A: 4 agents (Architect, Dev, PM, SM)
    - Option B: 2 agents (TEA, UX Designer)

    Facilitator: "Majority supports Option A. Let's capture TEA and UX concerns for risk mitigation."
  </example>
</consensus_type>
```

### Type 3: Weighted Consensus (Expert Votes Count More)

**When to use:** Technical decisions, domain-specific expertise required

**Process:**

```xml
<consensus_type name="weighted_consensus">
  <process>
    1. Assign weights based on expertise relevance
    2. Calculate weighted scores
    3. Threshold (e.g., 70%) = consensus
  </process>

  <example>
    Decision: Database selection for high-performance system

    Weights:
    - Architect: 40% (system design expertise)
    - Dev: 30% (implementation experience)
    - TEA: 20% (testing/performance expertise)
    - PM: 10% (business context)

    Votes:
    - PostgreSQL: Architect (40%), Dev (30%) = 70%
    - MongoDB: TEA (20%), PM (10%) = 30%

    Weighted consensus: PostgreSQL (70% > threshold)
  </example>
</consensus_type>
```

### Type 4: Consent-Based (No Reasoned Objections)

**When to use:** Exploratory decisions, safe-to-fail experiments, agile contexts

**Process:**

```xml
<consensus_type name="consent_based">
  <process>
    1. Proposal presented
    2. Ask: "Any reasoned objections?"
    3. If NO objections = proceed
    4. If objection exists, must be:
       - Reasoned (not just preference)
       - About harm/risk (not "I prefer differently")
    5. Address reasoned objections, proceed
  </process>

  <example>
    Proposal: "Let's prototype with library X"

    Facilitator: "Any reasoned objections to prototyping with library X?"

    TEA: "No objection - it's a prototype, we can pivot."
    Architect: "No harm in trying it."
    PM: "Prefer library Y, but no strong objection to X for prototype."

    Result: Consent achieved - proceed.
  </example>
</consensus_type>
```

### Type 5: Multi-Option Consensus (Present Multiple Valid Paths)

**When to use:** Strategic decisions, user-driven choices, complementary options

**Process:**

```xml
<consensus_type name="multi_option_consensus">
  <process>
    1. Agents generate multiple valid options
    2. Consensus that ALL options are viable
    3. Present pros/cons for each
    4. User selects based on context
  </process>

  <example>
    Question: "How should we architect this system?"

    Consensus: Three approaches are all valid

    Option A (Monolith):
    - Pros: Simple, fast to market
    - Cons: Scaling limits
    - Best for: MVP, small team

    Option B (Microservices):
    - Pros: Scalable, independent deployment
    - Cons: Complex, overhead
    - Best for: Large scale, mature product

    Option C (Modular Monolith):
    - Pros: Balance of both
    - Cons: Requires discipline
    - Best for: Growing product, medium team

    User decides based on their context.
  </example>
</consensus_type>
```

## 4.3 Consensus Patterns by Framework

### Six Hats Consensus Pattern

```xml
<consensus_mechanism framework="six-hats">

  <per_hat_consensus>
    <!-- Within each hat round -->
    <type>Cumulative Contribution</type>
    <description>Agents add perspectives, no voting needed</description>

    <example>
      White Hat (Facts):
      - Analyst: "Current users: 10,000"
      - Architect: "System handles 1,000 req/sec"
      - TEA: "Test coverage: 73%"

      No consensus needed - all facts captured
    </example>
  </per_hat_consensus>

  <final_consensus>
    <!-- After all 6 hats -->
    <type>Blue Hat Synthesis</type>
    <description>Facilitator synthesizes all perspectives into recommendation</description>

    <process>
      1. Review all hat outputs
      2. Identify tensions (e.g., Yellow benefits vs Black risks)
      3. Propose recommendation that addresses all perspectives
      4. Check for objections
      5. Refine if needed
    </process>

    <example>
      Blue Hat Synthesis:
      "White Hat facts show feasibility. Red Hat reveals team excitement but also anxiety. Black Hat identified 3 major risks. Yellow Hat found significant benefits. Green Hat proposed mitigation strategies.

      Recommendation: Proceed with pilot, implementing Green Hat risk mitigations, addressing Black Hat concerns before full rollout.

      Any objections?"

      [If objections → address → check again]
      [If no objections → consensus achieved]
    </example>
  </final_consensus>

</consensus_mechanism>
```

### Five Whys Consensus Pattern

```xml
<consensus_mechanism framework="five-whys">

  <per_why_consensus>
    <type>Evidence-Based Agreement</type>
    <description>Agents debate hypotheses, consensus on most evidence-supported answer</description>

    <process>
      1. Each agent proposes hypothesis for "why"
      2. Agents challenge each other's hypotheses
      3. Agent refines hypothesis based on challenges
      4. Facilitator identifies hypothesis with strongest evidence
      5. Check for agreement
      6. If disagreement persists, investigate both paths (branching)
    </process>

    <example>
      WHY #3: Why is app startup slow?

      Architect: "Loading 500MB config from S3"
      Dev: "Also 50 connection pool initialization"
      TEA: "I see both in profiling data"

      Facilitator: "Evidence supports both. Two causes identified."
      Consensus: Config loading + Connection pool = root causes
    </example>
  </per_why_consensus>

  <root_cause_consensus>
    <type>Validation Checklist</type>
    <description>Root cause must pass all validation criteria</description>

    <validation_criteria>
      - Is it actionable? (Can we fix it?)
      - Is it fundamental? (Fixing prevents symptom?)
      - Is it within our control?
      - Does team agree this is root cause?
    </validation_criteria>

    <check if="all criteria met AND team agrees">
      <action>Declare root cause found</action>
    </check>

    <check if="criteria met BUT disagreement">
      <action>Continue investigation (may reveal multiple roots)</action>
    </check>
  </root_cause_consensus>

</consensus_mechanism>
```

### First Principles Consensus Pattern

```xml
<consensus_mechanism framework="first-principles">

  <fundamental_truths_consensus>
    <type>Challenge Until Undeniable</type>
    <description>Truth only accepted if no agent can reasonably challenge it</description>

    <process>
      1. Agent proposes "fundamental truth"
      2. Other agents try to challenge/disprove
      3. If challenge succeeds → Not fundamental
      4. If no valid challenge → Accepted as fundamental
    </process>

    <example>
      Proposed Truth: "Users need to find items by keywords"

      Innovation Strategist: "Could they use images instead?"
      UX Designer: "Some users prefer visual search, but keywords still needed for text-based items."

      Challenge fails - truth accepted.

      Proposed Truth: "We need a database"

      Architect: "Could we use flat files?"
      Dev: "For 100K items, yes. We assumed database, but it's not fundamental."

      Challenge succeeds - NOT fundamental truth, it's an assumption!
    </example>
  </fundamental_truths_consensus>

  <assumption_elimination_consensus>
    <type>Guilty Until Proven Innocent</type>
    <description>Assumptions discarded unless proven necessary</description>

    <process>
      1. List all assumptions
      2. For each: Can we build solution WITHOUT this?
      3. If YES → Discard assumption
      4. If NO → Validate it's truly necessary (not just convenient)
    </process>
  </assumption_elimination_consensus>

  <solution_consensus>
    <type>Multi-Option Validation</type>
    <description>Generate 2-3 solutions, consensus on which best respects truths</description>

    <process>
      1. Each agent proposes first-principles solution
      2. Validate each against fundamental truths
      3. Score on: simplicity, cost, assumptions eliminated
      4. Present top 2-3 to user with trade-offs
    </process>
  </solution_consensus>

</consensus_mechanism>
```

## 4.4 Consensus XML Patterns (Copy-Paste Ready)

### Pattern: Check for Consensus

```xml
<substep n="consensus-check" goal="Verify agent agreement">
  <action>Review all agent positions</action>

  <check if="all agents agree">
    <action>Declare consensus achieved</action>
    <format>
      ✅ Consensus reached: {{consensus_decision}}

      Supporting agents: {{agent_list}}
      Key rationale: {{reasoning}}
    </format>
  </check>

  <check if="majority agrees (>50%)">
    <action>Declare majority consensus</action>
    <format>
      ✅ Majority consensus: {{majority_decision}}

      Supporting ({{support_count}}): {{supporting_agents}}
      Dissenting ({{dissent_count}}): {{dissenting_agents}}

      Minority concerns:
      {{#each dissenting_opinions}}
      - {{agent_name}}: {{concern}}
      {{/each}}
    </format>
  </check>

  <check if="strong disagreement">
    <action>Identify root of disagreement</action>
    <ask>What underlying question are we disagreeing about?</ask>

    <options>
      a) Explore both options (branching)
      b) Gather more evidence
      c) Escalate to user for decision
    </options>
  </check>
</substep>
```

### Pattern: Weighted Voting

```xml
<substep n="weighted-consensus" goal="Calculate weighted consensus">
  <action>Assign expertise weights to agents for this decision domain</action>

  <weight_assignment>
    {{#each agents}}
    - {{agent_name}}: {{weight}}% ({{expertise_rationale}})
    {{/each}}

    Total: 100%
  </weight_assignment>

  <action>Collect votes from each agent</action>

  <vote_tallying>
    {{#each options}}
    Option {{option_name}}:
    {{#each voting_agents}}
    - {{agent_name}} ({{weight}}%)
    {{/each}}
    Total weighted score: {{weighted_score}}%
    {{/each}}
  </vote_tallying>

  <check if="weighted_score >= threshold">
    <action>Declare weighted consensus achieved</action>
  </check>

  <check if="weighted_score < threshold">
    <action>No weighted consensus - present top 2 options to user</action>
  </check>
</substep>
```

### Pattern: Consent-Based Decision

```xml
<substep n="consent-check" goal="Check for reasoned objections">
  <action>Present proposal clearly</action>

  <format>
    Proposal: {{proposal_description}}

    Rationale: {{why_this_proposal}}

    Asking all agents: Any reasoned objections?

    (Preference ≠ objection. Objection = harm/risk/blocker)
  </format>

  <action>Collect responses from each agent</action>

  <check if="no reasoned objections">
    <action>Consent achieved - proceed with proposal</action>
  </check>

  <check if="reasoned objection exists">
    <action>Capture objection details</action>
    <format>
      Objection from {{agent_name}}:
      {{objection_description}}

      Harm/Risk identified: {{risk}}
    </format>

    <action>Address objection (modify proposal or mitigate risk)</action>
    <action>Re-check for consent with modified proposal</action>
  </check>
</substep>
```

---

# 5. PARTY-MODE INVOCATION PATTERNS

## 5.1 Overview

**Party-mode** is BMad's freeform multi-agent discussion system. Frameworks can invoke party-mode for:

- **Exploratory discussions** when structured format is too restrictive
- **Debate sessions** on contentious topics
- **Creative brainstorming** within framework context
- **User-requested discussions** mid-framework

## 5.2 When to Invoke Party-Mode

### Decision Tree: Framework vs Party-Mode

```
Current need?
├─ Structured analysis with specific outputs?
│  └─ Use framework (Six Hats, Five Whys, etc.)
│
├─ Open-ended exploration?
│  └─ Use party-mode
│
├─ Debate with no clear answer?
│  └─ Use party-mode
│
├─ Framework getting too rigid?
│  └─ Offer party-mode option
│
└─ User explicitly requests open discussion?
   └─ Invoke party-mode
```

## 5.3 Party-Mode Invocation Patterns

### Pattern 1: Mid-Framework Party-Mode Break

**Use case:** Framework hits complex topic needing deeper exploration

```xml
<step n="5" goal="Explore contentious assumption via party-mode">
  <context>
    We've identified a critical assumption during First Principles analysis:
    "Users will adopt this if we build it"

    This assumption is being heavily debated.
  </context>

  <action>Offer party-mode discussion option</action>

  <format>
    This assumption is generating significant debate.

    Options:
    a) Continue structured First Principles analysis
    b) Switch to party-mode for open discussion on user adoption
    c) Table this for now and continue

    Your choice?
  </format>

  <check if="user chooses party-mode">
    <invoke_party_mode>
      <context_handoff>
        Topic: User adoption assumption for {{project_name}}

        Framework context:
        - We're in First Principles analysis
        - Challenging the assumption: "Users will adopt if we build it"
        - Agents disagree on validation approach

        Relevant agents: {{framework_agents}} + any others who want to join

        Return to First Principles analysis after discussion concludes.
      </context_handoff>

      <action>Invoke party-mode workflow with context</action>
    </invoke_party_mode>
  </check>

  <check if="party-mode discussion concludes">
    <action>Capture key insights from party-mode</action>
    <action>Return to First Principles framework at step 5</action>
    <action>Incorporate party-mode insights into analysis</action>
  </check>
</step>
```

### Pattern 2: Post-Framework Party-Mode Synthesis

**Use case:** Framework completed, user wants team discussion on results

```xml
<step n="final" goal="Present framework results">
  <action>Display Six Hats analysis results</action>
  <action>Show final recommendation</action>

  <format>
    ═══════════════════════════════════════
    SIX HATS ANALYSIS COMPLETE
    ═══════════════════════════════════════

    Recommendation: {{recommendation}}

    [Summary of all hat perspectives]

    Options:
    a) Accept recommendation and proceed
    b) Invite party-mode discussion on results
    c) Re-run specific hat(s) for deeper analysis

    Your choice?
  </format>

  <check if="user chooses party-mode">
    <invoke_party_mode>
      <context_handoff>
        Topic: Discussion of Six Hats analysis results for {{decision_topic}}

        Analysis results:
        - White Hat: {{white_summary}}
        - Red Hat: {{red_summary}}
        - Black Hat: {{black_summary}}
        - Yellow Hat: {{yellow_summary}}
        - Green Hat: {{green_summary}}
        - Blue Hat recommendation: {{recommendation}}

        Open question: Should we accept this recommendation or explore alternatives?

        All agents invited to participate in discussion.
      </context_handoff>
    </invoke_party_mode>
  </check>
</step>
```

### Pattern 3: Party-Mode as Framework Component

**Use case:** Framework explicitly includes party-mode rounds

```xml
<step n="7" goal="Team debate on strategic options">
  <context>
    Innovation Strategy framework has generated 3 strategic options.
    Now the team debates them via party-mode.
  </context>

  <action>Present the 3 strategic options</action>

  <format>
    We've analyzed the market and generated 3 strategies:

    Option A: {{option_a_summary}}
    Option B: {{option_b_summary}}
    Option C: {{option_c_summary}}

    Initiating party-mode team debate...
  </format>

  <invoke_party_mode>
    <context_handoff>
      Topic: Strategic option selection for {{project_name}}

      Options to debate:
      A) {{option_a_details}}
      B) {{option_b_details}}
      C) {{option_c_details}}

      Goal: Team reaches consensus on best strategic direction

      Debate format: Open discussion, cross-agent questioning allowed

      Return to Innovation Strategy framework when consensus achieved.
    </context_handoff>

    <party_mode_config>
      focus_mode: debate
      goal: strategic_consensus
      exit_condition: consensus_or_user_decision
    </party_mode_config>
  </invoke_party_mode>

  <action>Capture consensus from party-mode</action>
  <action>Document rationale</action>
  <action>Return to Innovation Strategy framework for roadmap creation</action>
</step>
```

## 5.4 Party-Mode Context Handoff Pattern

**Critical:** When invoking party-mode from a framework, provide rich context.

```xml
<invoke_party_mode>
  <context_handoff>
    <!-- WHERE WE ARE -->
    <current_framework>{{framework_name}}</current_framework>
    <current_step>{{step_number}}</current_step>
    <framework_progress>{{progress_summary}}</framework_progress>

    <!-- WHY PARTY-MODE -->
    <discussion_topic>{{specific_topic}}</discussion_topic>
    <discussion_goal>{{what_we_need_to_achieve}}</discussion_goal>
    <discussion_context>{{relevant_background}}</discussion_context>

    <!-- WHO SHOULD PARTICIPATE -->
    <relevant_agents>{{agent_list_from_framework}}</relevant_agents>
    <open_invitation>true|false</open_invitation>

    <!-- HOW TO RETURN -->
    <return_framework>{{framework_name}}</return_framework>
    <return_step>{{step_number}}</return_step>
    <expected_outputs>{{what_party_mode_should_produce}}</expected_outputs>
  </context_handoff>

  <action>Launch party-mode with context</action>
  <action>Wait for party-mode to conclude (user exits or goal achieved)</action>
  <action>Capture party-mode insights</action>
  <action>Return to framework with insights integrated</action>
</invoke_party_mode>
```

## 5.5 Party-Mode XML Patterns (Copy-Paste Ready)

### Pattern: Offer Party-Mode Option

```xml
<checkpoint>
  <action>Present framework results so far</action>

  <options>
    <option key="c">Continue with {{framework_name}}</option>
    <option key="p">Party-Mode - Open discussion with all agents</option>
    <option key="a">Advanced Elicitation - Deeper questioning</option>
    <option key="y">YOLO - Skip remaining checkpoints</option>
  </options>

  <check if="user selects 'p'">
    <invoke_party_mode>
      <context>{{framework_context}}</context>
      <topic>{{current_discussion_topic}}</topic>
    </invoke_party_mode>
  </check>
</checkpoint>
```

### Pattern: Mandatory Party-Mode Round

```xml
<step n="{{n}}" goal="Party-mode debate on {{topic}}">
  <action>Announce party-mode round</action>

  <format>
    ═══════════════════════════════════════
    PARTY-MODE ROUND: {{topic}}
    ═══════════════════════════════════════

    All agents invited to participate in open discussion.

    Topic: {{topic_description}}
    Goal: {{discussion_goal}}

    Discussion will continue until {{exit_condition}}.
  </format>

  <invoke_party_mode>
    <config>
      topic: "{{topic}}"
      context: "{{framework_context}}"
      agents: "all" | "{{specific_agent_list}}"
      format: "freeform" | "structured_debate"
      exit_when: "{{exit_condition}}"
    </config>
  </invoke_party_mode>

  <action>Capture discussion insights</action>
  <template-output>party_mode_insights_{{n}}</template-output>
</step>
```

---

# 6. VALIDATION PATTERNS FOR GROUP OUTPUTS

## 6.1 Overview

Validation ensures multi-agent framework outputs meet quality standards before the framework concludes. Group outputs require different validation than single-agent outputs.

## 6.2 Validation Dimensions for Multi-Agent Outputs

### Dimension 1: Coverage (Did we explore all necessary perspectives?)

```xml
<validation dimension="coverage">
  <criteria>
    <criterion name="all_perspectives_heard">
      All relevant agent perspectives were included
    </criterion>

    <criterion name="no_blind_spots">
      No obvious gaps in analysis
    </criterion>

    <criterion name="diversity_achieved">
      Multiple viewpoints represented (not groupthink)
    </criterion>
  </criteria>

  <validation_check framework="six-hats">
    <check>All 6 hats were explored</check>
    <check>Each hat had 2+ agent contributions</check>
    <check>No hat was skipped or rushed</check>
  </validation_check>

  <validation_check framework="five-whys">
    <check>Reached root cause (not stopped at symptom)</check>
    <check>All hypotheses were challenged</check>
    <check>Branching paths investigated if needed</check>
  </validation_check>
</validation>
```

### Dimension 2: Consensus Quality (Is the agreement genuine?)

```xml
<validation dimension="consensus_quality">
  <criteria>
    <criterion name="not_forced">
      Consensus wasn't forced - agents genuinely agree
    </criterion>

    <criterion name="reasoned">
      Consensus based on evidence, not authority or fatigue
    </criterion>

    <criterion name="dissent_addressed">
      Minority opinions were heard and addressed
    </criterion>
  </criteria>

  <red_flags>
    ⚠️ All agents agreed immediately (possible groupthink)
    ⚠️ Dissent was dismissed without exploration
    ⚠️ Consensus changed multiple times (unstable)
    ⚠️ Agents stopped challenging each other (fatigue)
  </red_flags>
</validation>
```

### Dimension 3: Actionability (Can we act on this?)

```xml
<validation dimension="actionability">
  <criteria>
    <criterion name="specific">
      Recommendations are specific (not vague)
    </criterion>

    <criterion name="measurable">
      Success can be measured
    </criterion>

    <criterion name="assigned">
      Clear owners for next steps
    </criterion>

    <criterion name="timeline">
      Realistic timelines (when applicable)
    </criterion>
  </criteria>

  <example_good>
    ✅ "Implement lazy loading for config files (Dev team, Sprint 23, reduces startup from 90s to 30s)"
  </example_good>

  <example_bad>
    ❌ "Improve performance" (vague, not measurable, no owner)
  </example_bad>
</validation>
```

### Dimension 4: Documentation Quality (Is it usable?)

```xml
<validation dimension="documentation">
  <criteria>
    <criterion name="complete">
      All sections of template filled
    </criterion>

    <criterion name="clear">
      Someone not in the session can understand it
    </criterion>

    <criterion name="traceable">
      Can trace recommendations back to agent reasoning
    </criterion>

    <criterion name="searchable">
      Key decisions and rationale easily found
    </criterion>
  </criteria>

  <template_completeness_check>
    <check>Metadata section complete (date, facilitator, agents)</check>
    <check>Process summary explains what was done</check>
    <check>Key insights captured for each round</check>
    <check>Recommendations are documented</check>
    <check>Dissenting opinions recorded (if any)</check>
    <check>Next steps listed with owners</check>
  </template_completeness_check>
</validation>
```

## 6.3 Validation Checklists by Framework

### Six Hats Validation Checklist

```markdown
# Six Hats Analysis Validation Checklist

## Coverage

- [ ] All 6 hats were explored in sequence
- [ ] Each hat had 2-3 agent contributions minimum
- [ ] No hat was skipped or significantly shortened
- [ ] User was given opportunity to request additional rounds for any hat

## Hat Discipline

- [ ] Agents stayed in-character for each hat (no mixing perspectives)
- [ ] Facilitator redirected perspective violations if they occurred
- [ ] White Hat contained only facts (no opinions)
- [ ] Red Hat captured emotions (not just rational analysis)
- [ ] Black Hat identified genuine risks (not just pessimism)
- [ ] Yellow Hat found real benefits (not just optimism)
- [ ] Green Hat generated alternatives (not just variations)
- [ ] Blue Hat provided synthesis (not just summary)

## Consensus Quality

- [ ] Final recommendation addresses all 6 perspectives
- [ ] Black Hat risks have proposed mitigations
- [ ] Yellow Hat benefits are realistic
- [ ] Green Hat alternatives were seriously considered
- [ ] Dissenting opinions (if any) are documented

## Actionability

- [ ] Recommendation is specific and measurable
- [ ] Next steps are clearly defined
- [ ] Success criteria are stated
- [ ] Risk mitigations are assigned

## Documentation

- [ ] Template is complete with all sections filled
- [ ] Each hat section has clear contributions
- [ ] Blue Hat synthesis explains the recommendation
- [ ] Decision matrix (if used) is accurate
- [ ] Action items have owners and timelines

## User Satisfaction

- [ ] User feels all perspectives were explored
- [ ] User understands the recommendation
- [ ] User has confidence in the decision
```

### Five Whys Validation Checklist

```markdown
# Five Whys Root Cause Analysis Validation Checklist

## Problem Definition

- [ ] Problem statement is specific and measurable
- [ ] Problem impact is quantified
- [ ] Problem scope is clear

## Investigation Quality

- [ ] Each "why" was challenged by multiple agents
- [ ] Hypotheses were evidence-based (not guesses)
- [ ] Agents challenged each other's assumptions
- [ ] Facilitator drove toward consensus (not forced agreement)
- [ ] Investigation went deep enough (3-5 whys minimum)

## Root Cause Validity

- [ ] Root cause is actionable (we can fix it)
- [ ] Root cause is fundamental (fixing it prevents symptom)
- [ ] Root cause is within our control
- [ ] Team consensus that this is truly root (not symptom)

## Branching (if applicable)

- [ ] All branches were investigated to conclusion
- [ ] Each branch has identified root cause
- [ ] Branches are genuinely distinct (not variations)

## Solutions

- [ ] Proposed solutions address root cause (not symptom)
- [ ] Solutions are feasible
- [ ] Solutions have clear implementation plans
- [ ] Solutions have success metrics

## Documentation

- [ ] Why chain is clearly traceable in document
- [ ] Each hypothesis and counter-argument is captured
- [ ] Consensus reasoning is documented
- [ ] Root cause validation criteria are shown
- [ ] Solution comparison is clear

## User Satisfaction

- [ ] User understands the root cause
- [ ] User believes root cause is accurate
- [ ] User is confident in proposed solution
```

### First Principles Validation Checklist

```markdown
# First Principles Analysis Validation Checklist

## Deconstruction Quality

- [ ] Fundamental truths are truly fundamental (physics/logic/needs)
- [ ] Assumptions were aggressively challenged
- [ ] "Because we've always done it" was rejected as reasoning
- [ ] Agents questioned each other's "truths"

## Assumption Elimination

- [ ] All assumptions were identified and listed
- [ ] Each assumption was challenged
- [ ] Discarded assumptions are clearly separated from truths
- [ ] Retained assumptions have strong justification

## Reconstruction Quality

- [ ] Solutions built from ONLY fundamental truths
- [ ] Radical alternatives were seriously considered
- [ ] Conventional wisdom was set aside
- [ ] Multiple approaches were generated

## Reality Check

- [ ] Solutions were validated against real constraints
- [ ] Cost implications were considered
- [ ] Feasibility was assessed
- [ ] Trade-offs were clearly identified

## Simplicity

- [ ] First principles solutions are simpler than status quo
- [ ] Fewer assumptions = simpler solution
- [ ] No unnecessary complexity introduced

## Documentation

- [ ] Fundamental truths are listed
- [ ] Discarded assumptions are documented with reasoning
- [ ] Alternative solutions are compared
- [ ] Recommended solution is justified from first principles

## User Satisfaction

- [ ] User feels assumptions were genuinely challenged
- [ ] User sees value in radical rethinking
- [ ] User understands first principles recommendation
```

## 6.4 Validation XML Patterns (Copy-Paste Ready)

### Pattern: Pre-Completion Validation

```xml
<step n="final-1" goal="Validate framework outputs before completion">
  <action>Review outputs against validation checklist</action>

  <validation_checklist>
    <category name="Coverage">
      <check>All required perspectives explored</check>
      <check>No obvious blind spots</check>
      <check>Sufficient agent diversity</check>
    </category>

    <category name="Consensus">
      <check>Agreement is genuine (not forced)</check>
      <check>Evidence-based (not authority-based)</check>
      <check>Dissent was addressed</check>
    </category>

    <category name="Actionability">
      <check>Recommendations are specific</check>
      <check>Success is measurable</check>
      <check>Owners assigned</check>
    </category>

    <category name="Documentation">
      <check>Template is complete</check>
      <check>Reasoning is traceable</check>
      <check>Future readers can understand</check>
    </category>
  </validation_checklist>

  <check if="validation fails">
    <action>Identify gaps</action>
    <ask>Should we address {{validation_gap}} before completing?</ask>

    <check if="user says yes">
      <action>Return to appropriate step to fill gap</action>
    </check>
  </check>

  <check if="validation passes">
    <action>Proceed to final step</action>
  </check>
</step>
```

### Pattern: User Validation Prompt

```xml
<step n="final" goal="Final user validation">
  <action>Present complete framework output</action>

  <format>
    ═══════════════════════════════════════
    {{FRAMEWORK_NAME}} ANALYSIS COMPLETE
    ═══════════════════════════════════════

    [Display summary of outputs]

    Validation Questions:

    1. Do you feel all important perspectives were explored?
       □ Yes  □ No - What's missing: _______

    2. Do you understand the recommendation/findings?
       □ Yes  □ No - What needs clarification: _______

    3. Are the next steps clear and actionable?
       □ Yes  □ No - What needs refinement: _______

    4. Do you have confidence in this analysis?
       □ Yes  □ Somewhat  □ No - Why: _______
  </format>

  <check if="user validates">
    <action>Save final output</action>
    <action>Display completion message with file location</action>
  </check>

  <check if="user identifies gaps">
    <action>Address gaps</action>
    <action>Re-validate</action>
  </check>
</step>
```

---

# 7. ANNOTATED WORKFLOW EXAMPLE: SIX THINKING HATS

## 7.1 Complete Six Hats Workflow with Line-by-Line Annotations

This section provides a fully annotated Six Thinking Hats workflow implementation showing every design decision.

### File 1: workflow.yaml

```yaml
# Six Thinking Hats - Multi-Agent Analysis Workflow

# ═══════════════════════════════════════════════════════════════════
# METADATA
# ═══════════════════════════════════════════════════════════════════

name: 'six-hats'
# DESIGN NOTE: Workflow name must be kebab-case, used in file paths and invocation

description: "Edward de Bono's Six Thinking Hats framework adapted for multi-agent analysis. Each agent wears one hat at a time, contributing only from that perspective. Comprehensive decision analysis covering facts, emotions, risks, benefits, alternatives, and synthesis."
# DESIGN NOTE: Description appears in workflow menus and documentation

author: 'BMad'
# DESIGN NOTE: Attribution for workflow creator

# ═══════════════════════════════════════════════════════════════════
# CONFIGURATION SOURCES
# ═══════════════════════════════════════════════════════════════════

config_source: '{project-root}/{bmad_folder}/core/config.yaml'
# DESIGN NOTE: Core config contains user_name, output_folder, etc.
# All workflows should load config for consistency

# Load standard config variables
output_folder: '{config_source}:output_folder'
user_name: '{config_source}:user_name'
communication_language: '{config_source}:communication_language'
document_output_language: '{config_source}:document_output_language'
date: system-generated
# DESIGN NOTE: system-generated tells engine to auto-populate with current date

# ═══════════════════════════════════════════════════════════════════
# MULTI-AGENT SPECIFIC CONFIGURATION
# ═══════════════════════════════════════════════════════════════════

agent_manifest: '{project-root}/{bmad_folder}/_cfg/agent-manifest.csv'
# DESIGN NOTE: Critical for multi-agent workflows - contains all agent metadata
# Includes: name, displayName, title, icon, role, identity, communicationStyle, principles

hat_assignments: '{project-root}/{bmad_folder}/core/workflows/six-hats/hat-assignments.yaml'
# DESIGN NOTE: Separate config file for hat → agent role mappings
# Allows customization without modifying main workflow

# ═══════════════════════════════════════════════════════════════════
# FRAMEWORK PARAMETERS
# ═══════════════════════════════════════════════════════════════════

rounds: 2
# DESIGN NOTE: How many complete hat rotations (1 = minimal, 2 = standard, 3+ = deep dive)

round_duration: '2-3 agents per hat'
# DESIGN NOTE: Descriptive guidance for instructions.md

synthesis: true
# DESIGN NOTE: Flag indicating Blue Hat synthesis is required

# ═══════════════════════════════════════════════════════════════════
# FILE REFERENCES
# ═══════════════════════════════════════════════════════════════════

installed_path: '{project-root}/{bmad_folder}/core/workflows/six-hats'
# DESIGN NOTE: Base path for all workflow files

template: '{installed_path}/template.md'
# DESIGN NOTE: Template for capturing analysis outputs
# Use 'false' for action workflows (no document output)

instructions: '{installed_path}/instructions.md'
# DESIGN NOTE: XML-based step-by-step execution guide

validation: '{installed_path}/checklist.md'
# DESIGN NOTE: Optional but recommended - validation criteria

# ═══════════════════════════════════════════════════════════════════
# OUTPUT CONFIGURATION
# ═══════════════════════════════════════════════════════════════════

default_output_file: '{output_folder}/six-hats-analysis-{date}.md'
# DESIGN NOTE: Where final analysis document is saved
# {date} ensures unique filenames for multiple analyses

# ═══════════════════════════════════════════════════════════════════
# INVOCATION CONTROL
# ═══════════════════════════════════════════════════════════════════

standalone: true
# DESIGN NOTE: true = users can invoke directly with *six-hats
# false = internal-only workflow (called by other workflows)

exit_triggers:
  - '*exit'
  - '*complete'
# DESIGN NOTE: Commands that exit the workflow early

# ═══════════════════════════════════════════════════════════════════
# WEB BUNDLE CONFIGURATION (Optional)
# ═══════════════════════════════════════════════════════════════════

web_bundle:
  name: 'six-hats'
  description: 'Six Thinking Hats multi-agent decision analysis'
  author: 'BMad'
  instructions: '{bmad_folder}/core/workflows/six-hats/instructions.md'
  agent_manifest: '{bmad_folder}/_cfg/agent-manifest.csv'

  # All files needed for self-contained web deployment
  web_bundle_files:
    - '{bmad_folder}/core/workflows/six-hats/instructions.md'
    - '{bmad_folder}/core/workflows/six-hats/template.md'
    - '{bmad_folder}/core/workflows/six-hats/hat-assignments.yaml'
    - '{bmad_folder}/_cfg/agent-manifest.csv'
  # DESIGN NOTE: Web bundles must include ALL dependencies
  # No {project-root} references in web bundles (self-contained)
```

### File 2: hat-assignments.yaml

```yaml
# Six Thinking Hats - Agent Role Mapping Configuration

# ═══════════════════════════════════════════════════════════════════
# DESIGN PHILOSOPHY
# ═══════════════════════════════════════════════════════════════════
# Each hat maps to agents whose natural role/expertise aligns with
# that thinking mode. Primary candidates are best fits. Fallback
# candidates are used if primary agents aren't available.
#
# This separation allows:
# 1. Customization without modifying workflow
# 2. User override of agent assignments
# 3. Graceful degradation if agents missing
# ═══════════════════════════════════════════════════════════════════

hats:
  white:
    name: 'White Hat - Facts & Data'
    icon: '🤍'
    focus: 'Objective information, data, facts, figures, known/unknown information'

    # DESIGN NOTE: Agent selection criteria
    # Primary agents score 100 points, fallbacks score 70 points
    # Top 2-3 by score are selected for this hat

    agent_criteria:
      - analyst # Data analysis, research, metrics
      - architect # System facts, technical specifications
      - tea # Test data, quality metrics

    fallback:
      - dev # Technical knowledge
      - pm # Business metrics

    # DESIGN NOTE: What agents should focus on when wearing this hat
    contribution_guide:
      - 'State facts without interpretation'
      - 'Provide data points with sources'
      - "Identify what we know vs don't know"
      - 'Avoid opinions, stick to measurables'

  red:
    name: 'Red Hat - Emotions & Intuition'
    icon: '❤️'
    focus: 'Gut feelings, intuition, emotional reactions, hunches'

    agent_criteria:
      - ux-designer # User empathy, emotional design
      - creative-problem-solver # Intuitive thinking
      - storyteller # Emotional narrative

    fallback:
      - pm # Customer empathy
      - sm # Team dynamics

    contribution_guide:
      - 'Share gut reactions without justification needed'
      - 'Express emotional responses'
      - 'Surface intuitions and hunches'
      - 'No need to rationalize feelings'

  black:
    name: 'Black Hat - Critical Judgment'
    icon: '🖤'
    focus: 'Risks, problems, difficulties, potential failures, critical assessment'

    agent_criteria:
      - tea # Quality risks, testing concerns
      - architect # Technical risks, scalability issues
      - sm # Process risks, team concerns

    fallback:
      - dev # Implementation risks
      - analyst # Data-driven risk assessment

    contribution_guide:
      - 'Identify risks and potential failures'
      - 'Point out flaws in reasoning'
      - 'Challenge assumptions critically'
      - "Be the devil's advocate"

  yellow:
    name: 'Yellow Hat - Optimism & Benefits'
    icon: '💛'
    focus: 'Positives, benefits, opportunities, optimistic view'

    agent_criteria:
      - pm # Business benefits, user value
      - innovation-strategist # Strategic opportunities
      - sm # Team benefits, process improvements

    fallback:
      - analyst # Data-backed benefits
      - architect # Technical advantages

    contribution_guide:
      - 'Highlight benefits and opportunities'
      - 'Find positive aspects'
      - 'Identify value and advantages'
      - 'Be constructively optimistic'

  green:
    name: 'Green Hat - Creativity & Alternatives'
    icon: '💚'
    focus: 'New ideas, possibilities, alternatives, creative thinking'

    agent_criteria:
      - innovation-strategist # Strategic alternatives
      - brainstorming-coach # Creative ideation
      - creative-problem-solver # Unconventional solutions

    fallback:
      - architect # Alternative architectures
      - ux-designer # Alternative UX approaches

    contribution_guide:
      - 'Generate alternative approaches'
      - 'Think creatively and unconventionally'
      - "Propose 'what if' scenarios"
      - 'No idea is too wild'

  blue:
    name: 'Blue Hat - Process Control'
    icon: '💙'
    focus: 'Orchestration, synthesis, meta-thinking, process control'

    # DESIGN NOTE: Blue Hat is typically single facilitator, not group
    agent_criteria:
      - bmad-master # Meta-orchestration
      - sm # Process facilitation

    fallback:
      - pm # Strategic synthesis
      - architect # Technical synthesis

    contribution_guide:
      - 'Synthesize all perspectives'
      - 'Control discussion flow'
      - 'Summarize insights'
      - 'Provide meta-cognitive oversight'

# ═══════════════════════════════════════════════════════════════════
# HAT SEQUENCE CONFIGURATION
# ═══════════════════════════════════════════════════════════════════

sequence:
  - blue # Opening: Define problem, set agenda
  - white # Gather facts first (foundation)
  - red # Initial reactions (before analysis colors them)
  - black # Identify risks and concerns
  - yellow # Find benefits and opportunities
  - green # Generate alternatives to address Black/Yellow insights
  - blue # Closing: Synthesis and decision

# DESIGN NOTE: This sequence can be customized
# Alternative sequences:
# - white → black → green (problem-focused: facts → issues → solutions)
# - white → yellow → green (opportunity-focused: facts → benefits → innovation)
# - User can request specific hat order during workflow

# ═══════════════════════════════════════════════════════════════════
# CUSTOMIZATION NOTES
# ═══════════════════════════════════════════════════════════════════
# Users can override this file in their project:
# {bmad_folder}/_cfg/six-hats-custom-assignments.yaml
#
# Workflow should check for custom file first, fall back to default
# ═══════════════════════════════════════════════════════════════════
```

---

### 7.3 Annotated instructions.md

This is the complete workflow execution engine for Six Thinking Hats with comprehensive annotations explaining every design decision, XML pattern, and multi-agent orchestration technique.

```markdown
# Six Thinking Hats - Multi-Agent Structured Thinking Instructions

# ═══════════════════════════════════════════════════════════════════

# CRITICAL GOVERNANCE

# ═══════════════════════════════════════════════════════════════════

<critical>The workflow execution engine is governed by: {project_root}/{bmad_folder}/core/tasks/workflow.xml</critical>
<critical>This workflow orchestrates structured thinking through De Bono's Six Thinking Hats framework using multiple specialized agents</critical>

# DESIGN NOTE: Critical tags ensure Claude understands workflow governance

# The workflow.xml file is the universal execution engine that processes these instructions

# ═══════════════════════════════════════════════════════════════════

# TTS INTEGRATION POINT

# ═══════════════════════════════════════════════════════════════════

<!-- TTS_INJECTION:six-hats -->

# DESIGN NOTE: This marker allows AgentVibes TTS integration

# When present, workflow will trigger speech after agent contributions

# Pattern: Bash: .claude/hooks/bmad-speak.sh "{agent_name}" "{text}"

<workflow>

# ═══════════════════════════════════════════════════════════════════

# STEP 1: INITIALIZATION & AGENT ASSIGNMENT

# ═══════════════════════════════════════════════════════════════════

<step n="1" goal="Initialize Framework and Assign Agents to Hats">

# DESIGN NOTE: This step prepares the entire framework before any thinking begins

# It loads configurations, assigns agents, and presents the setup to the user

<action>Load workflow configuration from {{workflow_config}}</action>

# DESIGN NOTE: {{workflow_config}} is populated from workflow.yaml

# Contains: problem statement, hat order, agent assignments

<action>Load agent manifest from {{agent_manifest}}</action>

# DESIGN NOTE: agent-manifest.csv contains ALL available agents

# Format: name, displayName, title, icon, role, identity, communicationStyle, principles

# This is the source of truth for agent capabilities

<action>Load hat assignment configuration from {{hat_assignments}}</action>

# DESIGN NOTE: hat-assignments.yaml (created in Section 7.2) defines:

# - Agent criteria for each hat (which agent types fit each thinking mode)

# - Contribution guides (what agents should focus on)

# - Hat sequence (order of thinking modes)

  <substep n="1a" goal="Assign Agents to Each Hat">

    # DESIGN NOTE: This is the core agent selection algorithm in action
    # It implements the "Role-based Filtering with Scoring" pattern from Section 1

    <action>For each hat in {{hat_assignments}}:</action>

    <action>Filter agents from manifest matching agent_criteria:</action>
    <logic>
      - Primary criteria match: 100 points
      - Fallback criteria match: 70 points
      - Consider agent's role, identity, expertise from manifest
    </logic>

    # DESIGN NOTE: Scoring system allows graceful degradation
    # If primary agent types aren't available, fallbacks ensure workflow continues

    <action>Rank agents by score</action>
    <action>Select top 2-3 agents for this hat</action>

    # DESIGN NOTE: 2-3 agents per hat provides:
    # - Diversity of perspective within same thinking mode
    # - Cross-validation of insights
    # - Redundancy if one agent unavailable

    <check if="no agents match criteria">
      <action>Use fallback agents</action>
      <action>Log warning that ideal agents not available</action>
    </check>

    # DESIGN NOTE: Graceful degradation prevents workflow failure
    # Better to continue with suboptimal agents than abort

    <action>Store agent assignments in memory:</action>
    <format>
      white_hat_agents: [agent1, agent2, agent3]
      red_hat_agents: [agent4, agent5]
      black_hat_agents: [agent6, agent7, agent8]
      # ... etc for all hats
    </format>

  </substep>

  <substep n="1b" goal="Present Framework Setup to User">

    # DESIGN NOTE: Transparency builds trust
    # User sees who's thinking under each hat before work begins

    <action>Display framework introduction:</action>
    <format>
      🎩 Six Thinking Hats - Multi-Agent Structured Thinking

      Problem Statement:
      {{problem_statement}}

      Hat Sequence:
      [For each hat in sequence:]
      [Hat Icon] [Hat Name]: [Brief description]

      Agent Assignments:

      🤍 White Hat (Facts & Data):
      - [Agent Icon] [Agent Name] ([Agent Title])
      - [Agent Icon] [Agent Name] ([Agent Title])

      ❤️ Red Hat (Emotions & Intuition):
      - [Agent Icon] [Agent Name] ([Agent Title])
      - [Agent Icon] [Agent Name] ([Agent Title])

      [... continue for all hats]

      Ready to begin? (yes/no)
    </format>

    # DESIGN NOTE: Confirmation step allows user to:
    # - Verify agent assignments make sense
    # - Request changes before starting
    # - Understand what's about to happen

    <check if="user responds 'no' or requests changes">
      <action>Ask what they'd like to change</action>
      <action>Adjust agent assignments or hat sequence as requested</action>
      <action>Re-display setup</action>
    </check>

    <check if="user confirms or provides problem statement refinement">
      <action>Proceed to Step 2</action>
    </check>

  </substep>

</step>

# ═══════════════════════════════════════════════════════════════════

# STEP 2: OPENING BLUE HAT - PROBLEM DEFINITION

# ═══════════════════════════════════════════════════════════════════

<step n="2" goal="Blue Hat Opening - Define Problem and Set Agenda">

# DESIGN NOTE: Blue Hat is unique - it's meta-cognitive/facilitation

# Typically 1 facilitator agent rather than multiple contributors

# This step frames the entire discussion

<action>Select Blue Hat facilitator (typically bmad-master or SM agent)</action>

<action>Have facilitator agent introduce the session:</action>
<format>
💙 [Blue Hat Agent Name]:

    "Welcome to our Six Thinking Hats session. I'll be facilitating our structured thinking process.

    Problem/Question:
    {{problem_statement}}

    Our Agenda:
    1. 🤍 White Hat - Gather facts and data
    2. ❤️ Red Hat - Express initial intuitions and feelings
    3. 🖤 Black Hat - Identify risks and concerns
    4. 💛 Yellow Hat - Explore benefits and opportunities
    5. 💚 Green Hat - Generate creative alternatives
    6. 💙 Blue Hat - Synthesize insights and conclude

    Ground Rules:
    - When wearing each hat, think ONLY in that mode
    - No criticism during Green/Yellow hats
    - No solutions during White/Red/Black hats
    - All perspectives are valuable

    Let's begin with the White Hat - facts and data."

  </format>

# DESIGN NOTE: Clear framing sets expectations

# Ground rules prevent mode-mixing (e.g., criticizing during creative phase)

<action>Trigger TTS for Blue Hat facilitator:</action>
<bash>bmad-speak.sh "[Blue Hat Agent Name]" "[Their introduction text]"</bash>

# DESIGN NOTE: TTS integration pattern from party-mode

# Voice reinforces agent personality and engagement

<action>Save checkpoint to template:</action>
<checkpoint>
section: opening_blue_hat
agent: [Blue Hat Agent Name]
content: [Their introduction]
</checkpoint>

# DESIGN NOTE: Checkpoint protocol from Section 2

# After every round, save to template to prevent context loss

</step>

# ═══════════════════════════════════════════════════════════════════

# STEP 3: WHITE HAT - FACTS & DATA

# ═══════════════════════════════════════════════════════════════════

<step n="3" goal="White Hat Round - Gather Objective Facts">

# DESIGN NOTE: This is the pattern for ALL hat rounds

# White Hat shown in full detail, other hats follow same structure

<action>Announce hat transition:</action>
<format>

---

🤍 WHITE HAT - Facts & Data
Focus: Objective information, data, facts, figures, what we know and don't know

---

</format>

  <substep n="3a" goal="Generate Agent Contributions">

    # DESIGN NOTE: Each agent selected for this hat contributes in character
    # They must stay strictly in White Hat mode (facts only, no opinions)

    <action>For each agent in white_hat_agents:</action>

    <action>Generate authentic contribution using agent's:</action>
    <context>
      - Role and expertise from manifest
      - Communication style
      - Principles
      - Hat contribution guide from hat-assignments.yaml
    </context>

    # DESIGN NOTE: This is where agent personality meets framework discipline
    # Agent's natural expertise informs WHAT facts they notice
    # Hat mode constrains HOW they present it (no interpretation, just facts)

    <format>
      🤍 [Agent Icon] [Agent Name]:

      [Agent's factual contribution in their voice]

      [2-4 specific data points, facts, or known/unknown information]

    </format>

    # DESIGN NOTE: Format keeps contributions concise and scannable
    # Icon + Name reinforces who's speaking
    # 2-4 points prevents overwhelming information

    <action>Trigger TTS for this agent:</action>
    <bash>bmad-speak.sh "[Agent Name]" "[Their contribution text]"</bash>

    <note>Agents may reference each other's facts naturally:</note>
    <example>
      "Building on [Other Agent]'s point about X, we also know Y..."
    </example>

    # DESIGN NOTE: Natural cross-references create dialogue feel
    # Not rigid sequential contributions, but conversation

  </substep>

  <substep n="3b" goal="Facilitate Clarification">

    # DESIGN NOTE: After all White Hat agents contribute, Blue Hat may intervene
    # This prevents moving forward with unclear or conflicting facts

    <check if="facts are unclear or conflicting">
      <action>Have Blue Hat facilitator ask clarifying questions:</action>
      <format>
        💙 [Blue Hat Agent]:
        "I want to ensure we have clarity. [Question about unclear fact]"
      </format>

      <action>Relevant White Hat agent responds with clarification</action>
    </check>

    <check if="critical information is missing">
      <action>Blue Hat identifies the gap:</action>
      <format>
        💙 [Blue Hat Agent]:
        "I notice we don't have information about [X]. This may be important for later hats. Let's note this as an unknown."
      </format>
    </check>

    # DESIGN NOTE: This is facilitation quality check
    # Ensures foundation is solid before building on it

  </substep>

  <substep n="3c" goal="Synthesize and Save">

    # DESIGN NOTE: After each hat round, synthesize and checkpoint
    # This is the consensus mechanism pattern from Section 4

    <action>Have Blue Hat provide brief synthesis:</action>
    <format>
      💙 [Blue Hat Agent]:

      "White Hat Summary:
      - [Key fact 1]
      - [Key fact 2]
      - [Key fact 3]
      - Known unknowns: [What we don't have data on]

      Let's move to the Red Hat - gut feelings and intuitions."
    </format>

    <action>Save checkpoint to template:</action>
    <checkpoint>
      section: white_hat
      agents: [List of contributing agents]
      contributions: [Full text of all contributions]
      synthesis: [Blue Hat summary]
    </checkpoint>

    # DESIGN NOTE: Template checkpoint ensures:
    # - Work isn't lost if context runs out
    # - Output document builds progressively
    # - User has artifact at end

  </substep>

</step>

# ═══════════════════════════════════════════════════════════════════

# STEP 4: RED HAT - EMOTIONS & INTUITION

# ═══════════════════════════════════════════════════════════════════

<step n="4" goal="Red Hat Round - Express Gut Feelings">

# DESIGN NOTE: Red Hat is unique - no justification needed

# This step comes early (before analysis) to capture unfiltered reactions

<action>Announce hat transition:</action>
<format>

---

❤️ RED HAT - Emotions & Intuition
Focus: Gut feelings, emotional reactions, hunches - no justification needed

---

</format>

  <substep n="4a" goal="Generate Agent Contributions">

    <action>For each agent in red_hat_agents:</action>

    <action>Generate authentic emotional/intuitive contribution:</action>
    <context>
      - Agent's communication style (how they express feelings)
      - Red Hat contribution guide: share without justification
      - Freedom to express hunches, concerns, excitement
    </context>

    <format>
      ❤️ [Agent Icon] [Agent Name]:

      [Agent's intuitive/emotional reaction]

      [Express feeling, hunch, gut reaction about the problem]

    </format>

    # DESIGN NOTE: This is where agents show personality most strongly
    # Some agents naturally more emotional (UX, storyteller)
    # Others more reserved (architect, analyst) but still express gut feel

    <action>Trigger TTS for this agent</action>

    <note>Red Hat contributions should feel different from White Hat:</note>
    <example>
      White Hat: "The system currently has 10,000 users."
      Red Hat: "I have a gut feeling this could be really valuable for users, but I'm nervous about the technical complexity."
    </example>

    # DESIGN NOTE: Example shows mode discipline
    # Same agent wears different hats → different thinking styles

  </substep>

  <substep n="4b" goal="Facilitate Without Judgment">

    # DESIGN NOTE: Blue Hat's role here is different from White Hat
    # Don't challenge feelings, just acknowledge and move forward

    <action>Blue Hat acknowledges contributions without analysis:</action>
    <format>
      💙 [Blue Hat Agent]:
      "Thank you for sharing those intuitions. All feelings are valid data points."
    </format>

    <note>DO NOT ask agents to justify their feelings</note>
    <note>DO NOT have other agents challenge emotional reactions</note>

    # DESIGN NOTE: Creating psychological safety for Red Hat
    # If feelings are challenged, agents will self-censor in future rounds

  </substep>

  <substep n="4c" goal="Synthesize and Save">

    <action>Blue Hat provides brief synthesis:</action>
    <format>
      💙 [Blue Hat Agent]:

      "Red Hat Summary:
      - Overall emotional tone: [positive/concerned/mixed/excited]
      - Key intuitions: [1-2 sentence summary]

      Now let's put on the Black Hat - critical judgment and risk assessment."
    </format>

    <action>Save checkpoint to template</action>

  </substep>

</step>

# ═══════════════════════════════════════════════════════════════════

# STEP 5: BLACK HAT - CRITICAL JUDGMENT

# ═══════════════════════════════════════════════════════════════════

<step n="5" goal="Black Hat Round - Identify Risks and Concerns">

# DESIGN NOTE: Black Hat is devil's advocate time

# Critical for preventing groupthink and exposing weaknesses

<action>Announce hat transition:</action>
<format>

---

🖤 BLACK HAT - Critical Judgment
Focus: Risks, problems, difficulties, potential failures - be the skeptic

---

</format>

  <substep n="5a" goal="Generate Agent Contributions">

    <action>For each agent in black_hat_agents:</action>

    <action>Generate critical assessment:</action>
    <context>
      - Agent's expertise informs what risks they notice
      - Black Hat contribution guide: identify failures, challenge assumptions
      - Reference White Hat facts and Red Hat intuitions where relevant
    </context>

    <format>
      🖤 [Agent Icon] [Agent Name]:

      [Agent's critical assessment]

      [2-4 specific risks, problems, or failure scenarios]

    </format>

    # DESIGN NOTE: Agents may disagree on severity of risks
    # This diversity is valuable - shows range of concerns

    <action>Trigger TTS for this agent</action>

    <note>Encourage specific, actionable concerns:</note>
    <example>
      Weak: "This might not work."
      Strong: "If we launch without load testing, the system could crash at 5,000 concurrent users based on our current architecture."
    </example>

    # DESIGN NOTE: Specificity makes Black Hat contributions actionable
    # Vague concerns can't be addressed; specific risks can

  </substep>

  <substep n="5b" goal="Facilitate Risk Exploration">

    # DESIGN NOTE: Blue Hat ensures Black Hat doesn't become demoralizing
    # Acknowledge concerns without defending against them yet

    <check if="critical concerns raised that need clarification">
      <action>Blue Hat asks clarifying questions:</action>
      <format>
        💙 [Blue Hat Agent]:
        "[Agent Name], can you elaborate on [specific risk]? What would be the impact if this occurred?"
      </format>
    </check>

    <check if="Black Hat becomes overly negative or demoralizing">
      <action>Blue Hat acknowledges and redirects:</action>
      <format>
        💙 [Blue Hat Agent]:
        "These are important concerns to consider. Let's capture them all, knowing we'll explore solutions in the Green Hat phase."
      </format>
    </check>

    # DESIGN NOTE: Redirecting to future Green Hat preserves morale
    # "Yes, and..." not "Yes, but..."

  </substep>

  <substep n="5c" goal="Synthesize and Save">

    <action>Blue Hat synthesizes risk landscape:</action>
    <format>
      💙 [Blue Hat Agent]:

      "Black Hat Summary:
      - Critical risks: [1-2 highest priority concerns]
      - Secondary concerns: [2-3 other issues]
      - Assumptions challenged: [any assumptions questioned]

      Now let's balance this with the Yellow Hat - benefits and opportunities."
    </format>

    <action>Save checkpoint to template</action>

    # DESIGN NOTE: Balancing Black → Yellow prevents negativity spiral
    # Hat sequence matters for psychological flow

  </substep>

</step>

# ═══════════════════════════════════════════════════════════════════

# STEP 6: YELLOW HAT - OPTIMISM & BENEFITS

# ═══════════════════════════════════════════════════════════════════

<step n="6" goal="Yellow Hat Round - Explore Benefits and Opportunities">

# DESIGN NOTE: Yellow Hat counterbalances Black Hat

# Important to explore both perspectives for balanced decision-making

<action>Announce hat transition:</action>
<format>

---

💛 YELLOW HAT - Optimism & Benefits
Focus: Positives, benefits, opportunities, optimistic view - what could go right?

---

</format>

  <substep n="6a" goal="Generate Agent Contributions">

    <action>For each agent in yellow_hat_agents:</action>

    <action>Generate optimistic perspective:</action>
    <context>
      - Agent's expertise informs what benefits they see
      - Yellow Hat contribution guide: highlight value, opportunities
      - May directly address Black Hat concerns with positive spin
    </context>

    <format>
      💛 [Agent Icon] [Agent Name]:

      [Agent's optimistic assessment]

      [2-4 specific benefits, opportunities, or positive outcomes]

    </format>

    # DESIGN NOTE: Yellow Hat can reference Black Hat concerns
    # Example: "While [Black Hat Agent] raised concerns about X, if we succeed, the benefit would be Y."

    <action>Trigger TTS for this agent</action>

    <note>Encourage specific, measurable benefits:</note>
    <example>
      Weak: "This will be good."
      Strong: "This could reduce user onboarding time from 30 minutes to 5 minutes, directly impacting our activation rate KPI."
    </example>

  </substep>

  <substep n="6b" goal="Facilitate Opportunity Exploration">

    <check if="opportunities mentioned that could be expanded">
      <action>Blue Hat prompts deeper exploration:</action>
      <format>
        💙 [Blue Hat Agent]:
        "[Agent Name], you mentioned [opportunity]. What's the best-case scenario if we pursue this?"
      </format>
    </check>

  </substep>

  <substep n="6c" goal="Synthesize and Save">

    <action>Blue Hat synthesizes benefits:</action>
    <format>
      💙 [Blue Hat Agent]:

      "Yellow Hat Summary:
      - Primary benefits: [1-2 highest value outcomes]
      - Secondary benefits: [2-3 other positives]
      - Opportunities: [strategic advantages]

      We now have both risks (Black Hat) and benefits (Yellow Hat) clearly mapped. Let's put on the Green Hat to explore creative alternatives."
    </format>

    <action>Save checkpoint to template</action>

    # DESIGN NOTE: Explicitly bridging Black + Yellow → Green
    # Green Hat will generate solutions informed by both perspectives

  </substep>

</step>

# ═══════════════════════════════════════════════════════════════════

# STEP 7: GREEN HAT - CREATIVITY & ALTERNATIVES

# ═══════════════════════════════════════════════════════════════════

<step n="7" goal="Green Hat Round - Generate Creative Alternatives">

# DESIGN NOTE: Green Hat is where solutions emerge

# Armed with facts (White), intuitions (Red), risks (Black), benefits (Yellow)

# Agents now generate creative approaches

<action>Announce hat transition:</action>
<format>

---

💚 GREEN HAT - Creativity & Alternatives
Focus: New ideas, possibilities, alternatives - wild ideas welcome!

---

</format>

  <substep n="7a" goal="Generate Agent Contributions">

    <action>For each agent in green_hat_agents:</action>

    <action>Generate creative alternatives:</action>
    <context>
      - Agent's expertise informs type of alternatives they generate
      - Green Hat contribution guide: unconventional thinking, "what if" scenarios
      - Reference insights from previous hats
    </context>

    <format>
      💚 [Agent Icon] [Agent Name]:

      [Agent's creative contribution]

      [2-3 alternative approaches, innovative ideas, or "what if" scenarios]

    </format>

    # DESIGN NOTE: Green Hat has most freedom
    # No criticism allowed - all ideas valid at this stage

    <action>Trigger TTS for this agent</action>

    <note>Encourage building on each other's ideas:</note>
    <example>
      "I love [Other Agent]'s idea about X. What if we took that further and also Y?"
    </example>

    # DESIGN NOTE: "Yes, and..." culture in Green Hat
    # Agents amplify each other's creativity

  </substep>

  <substep n="7b" goal="Facilitate Creative Exploration">

    # DESIGN NOTE: Blue Hat's role is to keep creativity flowing
    # Prevent premature evaluation or criticism

    <check if="ideas directly address Black Hat risks">
      <action>Blue Hat highlights connection:</action>
      <format>
        💙 [Blue Hat Agent]:
        "Interesting - [Agent Name]'s idea could potentially address [Black Hat Agent]'s concern about [risk]."
      </format>
    </check>

    # DESIGN NOTE: Making connections explicit shows how hats build on each other

    <check if="any agent slips into Black Hat (criticism) during Green Hat">
      <action>Blue Hat gently redirects:</action>
      <format>
        💙 [Blue Hat Agent]:
        "Let's stay in Green Hat mode - we'll evaluate feasibility later. For now, all ideas are welcome."
      </format>
    </check>

    # DESIGN NOTE: Hat discipline enforcement
    # Mixing modes reduces effectiveness of framework

  </substep>

  <substep n="7c" goal="Synthesize and Save">

    <action>Blue Hat synthesizes alternatives:</action>
    <format>
      💙 [Blue Hat Agent]:

      "Green Hat Summary:
      - Alternative approaches: [2-3 distinct directions]
      - Innovative ideas: [novel concepts proposed]
      - Hybrid possibilities: [combinations of ideas]

      We now have multiple creative paths forward. Let's conclude with Blue Hat synthesis."
    </format>

    <action>Save checkpoint to template</action>

  </substep>

</step>

# ═══════════════════════════════════════════════════════════════════

# STEP 8: CLOSING BLUE HAT - SYNTHESIS & DECISION

# ═══════════════════════════════════════════════════════════════════

<step n="8" goal="Blue Hat Closing - Synthesize All Perspectives">

# DESIGN NOTE: This is where the facilitator brings everything together

# Most critical step - transforms diverse thinking into actionable insight

<action>Announce final hat:</action>
<format>

---

💙 BLUE HAT - Process Control & Synthesis
Focus: Bringing all perspectives together into coherent whole

---

</format>

  <substep n="8a" goal="Comprehensive Synthesis">

    # DESIGN NOTE: This is the "Full Consensus" mechanism from Section 4
    # Facilitator must integrate all hats into unified understanding

    <action>Blue Hat provides comprehensive synthesis:</action>
    <format>
      💙 [Blue Hat Agent]:

      "Let me bring together all our thinking modes:

      🤍 WHITE HAT FOUNDATION:
      [2-3 key facts that ground our understanding]

      ❤️ RED HAT INTUITIONS:
      [Overall emotional/intuitive sense from the team]

      🖤 BLACK HAT RISKS:
      [2-3 critical concerns we must address]

      💛 YELLOW HAT OPPORTUNITIES:
      [2-3 key benefits if we succeed]

      💚 GREEN HAT ALTERNATIVES:
      [2-3 creative approaches generated]

      INTEGRATED INSIGHT:
      [1-2 paragraphs synthesizing how all perspectives inform the path forward]

      RECOMMENDED NEXT STEPS:
      1. [Immediate action]
      2. [Follow-up action]
      3. [Ongoing consideration]
      "
    </format>

    # DESIGN NOTE: Format mirrors all previous hats
    # Shows how each mode contributed to final understanding

    <action>Trigger TTS for Blue Hat synthesis</action>

  </substep>

  <substep n="8b" goal="Check for Consensus">

    # DESIGN NOTE: Validation pattern from Section 6
    # Ensure synthesis accurately represents all perspectives

    <action>Blue Hat invites feedback on synthesis:</action>
    <format>
      💙 [Blue Hat Agent]:
      "Does this synthesis accurately capture our collective thinking? Any agent feel their perspective was missed?"
    </format>

    <check if="any agent objects or adds missing perspective">
      <action>Blue Hat acknowledges and refines synthesis:</action>
      <format>
        💙 [Blue Hat Agent]:
        "Good catch, [Agent Name]. Let me refine: [adjusted synthesis]"
      </format>
      <action>Update synthesis with new input</action>
    </check>

    # DESIGN NOTE: This is the "Dissent Capture" mechanism
    # Minority viewpoints are explicitly recorded even if not consensus

    <check if="consensus achieved">
      <action>Proceed to final output</action>
    </check>

  </substep>

  <substep n="8c" goal="Generate Final Template Output">

    # DESIGN NOTE: This is where template.md gets populated with full session
    # User receives polished artifact, not just conversation transcript

    <action>Populate template with all checkpoints:</action>
    <action>Include:</action>
    <list>
      - Problem statement
      - All hat contributions (organized by hat)
      - Blue Hat syntheses after each hat
      - Final comprehensive synthesis
      - Recommended next steps
      - Dissenting viewpoints (if any)
    </list>

    <action>Save final template output</action>

    # DESIGN NOTE: Template checkpoint protocol ensures complete artifact
    # User can reference this document for future decisions

  </substep>

</step>

# ═══════════════════════════════════════════════════════════════════

# STEP 9: CLOSING & NEXT STEPS

# ═══════════════════════════════════════════════════════════════════

<step n="9" goal="Close Session and Transition to Action">

<action>Blue Hat provides closing:</action>
<format>
💙 [Blue Hat Agent]:

    "This concludes our Six Thinking Hats session.

    Summary document has been saved to: {{template_output_path}}

    Next Steps:
    [Repeat recommended actions from synthesis]

    Would you like to:
    - Revisit any specific hat for deeper exploration?
    - Move forward with implementation of recommended actions?
    - Schedule follow-up Six Hats session?
    "

  </format>

# DESIGN NOTE: Offer continuation options

# Framework can be used iteratively as understanding evolves

  <check if="user wants to revisit specific hat">
    <action>Return to that hat's step with same agents</action>
    <action>Append additional insights to template</action>
  </check>

  <check if="user wants to implement actions">
    <action>Offer to invoke relevant workflow (e.g., story-draft if BMM active)</action>
  </check>

  <check if="user satisfied with session">
    <action>2-3 agents provide characteristic farewells:</action>
    <format>
      [Agent Icon] [Agent Name]: [Brief farewell in their voice]
    </format>
    <action>Exit workflow</action>
  </check>

# DESIGN NOTE: Graceful exit maintains agent personality

# Consistent with party-mode farewell pattern

</step>

</workflow>

# ═══════════════════════════════════════════════════════════════════

# EXECUTION GUIDELINES

# ═══════════════════════════════════════════════════════════════════

<guidelines>

  <guideline name="Hat Discipline">
    Strictly enforce hat mode constraints. Do not allow:
    - Criticism during Green/Yellow hats
    - Solutions during White/Red/Black hats
    - Justification during Red hat
    - Opinion during White hat
  </guideline>

# DESIGN NOTE: Framework effectiveness depends on mode discipline

# Mixing modes reduces value of structured thinking

  <guideline name="Agent Authenticity">
    Each agent must:
    - Use their documented communication style consistently
    - Apply their stated principles in their contributions
    - Draw from their role/identity for expertise
    - Maintain personality while respecting hat constraints
  </guideline>

# DESIGN NOTE: Agents aren't generic - personality shines through

# But hat mode shapes HOW they express their expertise

  <guideline name="Facilitation Quality">
    Blue Hat must:
    - Synthesize after every hat round
    - Make connections between hats explicit
    - Prevent mode-mixing
    - Ensure all voices heard
    - Maintain psychological safety
  </guideline>

# DESIGN NOTE: Facilitation makes or breaks the framework

# Blue Hat quality determines session value

  <guideline name="Checkpoint Protocol">
    Save to template after every hat round to prevent context loss.
    Template is the artifact user keeps after session ends.
  </guideline>

# DESIGN NOTE: This is non-negotiable

# Losing work mid-session destroys user trust

  <guideline name="Time Management">
    Each hat round should take roughly equal time (5-10 minutes of conversation).
    If one hat consuming excessive time, Blue Hat should summarize and move forward.
  </guideline>

# DESIGN NOTE: Balance prevents exhaustion

# Framework is marathon, not sprint

</guidelines>

# ═══════════════════════════════════════════════════════════════════

# ERROR HANDLING & EDGE CASES

# ═══════════════════════════════════════════════════════════════════

<error-handling>

  <scenario name="Insufficient agents for hat">
    <if>Fewer than 2 agents match criteria for a hat</if>
    <then>
      - Use fallback agents
      - Blue Hat acknowledges: "We have limited [hat color] expertise available, but let's proceed"
      - Continue workflow with available agents
    </then>
  </scenario>

  <scenario name="Agent conflict during round">
    <if>Two agents strongly disagree during same hat</if>
    <then>
      - Allow both perspectives to be voiced fully
      - Blue Hat acknowledges: "We have different perspectives within [hat color] hat - this diversity is valuable"
      - Record both viewpoints in template
      - DO NOT force artificial consensus
    </then>
  </scenario>

# DESIGN NOTE: Disagreement is data, not error

# Multiple agents per hat SHOULD surface diverse views

  <scenario name="User wants to skip hat">
    <if>User requests skipping a hat (e.g., "skip Red Hat")</if>
    <then>
      - Blue Hat explains value of that hat
      - If user insists, skip but note in template: "Red Hat phase skipped at user request"
      - Continue with remaining hats
    </then>
  </scenario>

  <scenario name="Context approaching limit">
    <if>Conversation becoming very long</if>
    <then>
      - Blue Hat: "We're approaching context limits. Let me save progress and summarize so far..."
      - Save comprehensive checkpoint to template
      - Provide summary of progress
      - Offer to continue in new session or conclude with partial synthesis
    </then>
  </scenario>

# DESIGN NOTE: Graceful degradation

# Better partial session with artifact than lost work

</error-handling>

# ═══════════════════════════════════════════════════════════════════

# CUSTOMIZATION POINTS

# ═══════════════════════════════════════════════════════════════════

<customization>

  <point name="Hat Sequence">
    Default sequence is: Blue → White → Red → Black → Yellow → Green → Blue

    Alternative sequences for different goals:
    - Problem-focused: White → Black → Green (facts → issues → solutions)
    - Opportunity-focused: White → Yellow → Green (facts → benefits → innovation)
    - Decision-focused: White → Black → Yellow → Blue (facts → risks → benefits → decide)

    User can specify custom sequence in workflow.yaml or request during session.

  </point>

  <point name="Agent Count Per Hat">
    Default is 2-3 agents per hat.

    Can be customized based on:
    - Available agents (fewer if limited roster)
    - Time constraints (fewer agents = faster rounds)
    - Depth desired (more agents = more perspectives)

  </point>

  <point name="Round Duration">
    Default is 5-10 minutes per hat.

    Can be adjusted based on:
    - Problem complexity (longer for complex problems)
    - User preference (express vs thorough)
    - Fatigue (shorter if energy declining)

  </point>

</customization>

---

### DESIGN PATTERN SUMMARY

This workflow demonstrates all key patterns from previous sections:

1. **Agent Selection** (Section 1): Role-based filtering with scoring fallback
2. **Template Output** (Section 2): Progressive checkpoint protocol builds final artifact
3. **Facilitation** (Section 3): Blue Hat orchestrates, synthesizes, enforces discipline
4. **Consensus** (Section 4): Full synthesis with dissent capture
5. **Party-Mode Integration** (Section 5): TTS injection, agent cross-talk, personality preservation
6. **Validation** (Section 6): Completeness check (all hats), quality check (synthesis accuracy), consensus validation

Every XML pattern, every checkpoint, every facilitation intervention is intentional and documented.
```

---

### 7.4 Annotated template.md

This template captures the complete Six Thinking Hats session output. It's progressively populated through checkpoint protocol as each hat round completes.

```markdown
# Six Thinking Hats Session Report

**Generated:** {{date}}
**Facilitator:** {{blue_hat_facilitator}}
**Problem Statement:** {{problem_statement}}

---

## Session Overview

**Participating Agents:**

### 🤍 White Hat (Facts & Data)

{{#each white_hat_agents}}

- {{icon}} {{displayName}} ({{title}})
  {{/each}}

### ❤️ Red Hat (Emotions & Intuition)

{{#each red_hat_agents}}

- {{icon}} {{displayName}} ({{title}})
  {{/each}}

### 🖤 Black Hat (Critical Judgment)

{{#each black_hat_agents}}

- {{icon}} {{displayName}} ({{title}})
  {{/each}}

### 💛 Yellow Hat (Optimism & Benefits)

{{#each yellow_hat_agents}}

- {{icon}} {{displayName}} ({{title}})
  {{/each}}

### 💚 Green Hat (Creativity & Alternatives)

{{#each green_hat_agents}}

- {{icon}} {{displayName}} ({{title}})
  {{/each}}

### 💙 Blue Hat (Process Control)

- {{blue_hat_icon}} {{blue_hat_facilitator}} ({{blue_hat_title}})

---

<!--
DESIGN NOTE: Template Structure Philosophy

This template follows the "Progressive Checkpoint Protocol" pattern:
- Each hat round adds a new section as it completes
- Prevents context loss during long sessions
- User has partial artifact even if session interrupted
- Final synthesis integrates all sections

Variable syntax:
- {{variable}}: Single values populated from workflow.yaml
- {{#each array}}: Iteration over agent lists
- {{section_content}}: Large text blocks from checkpoints
-->

## 💙 Opening Blue Hat - Problem Definition

**Facilitator:** {{blue_hat_facilitator}}

{{opening_blue_hat_content}}

<!--
DESIGN NOTE: Opening section captures:
- Problem framing by facilitator
- Agenda presentation
- Ground rules establishment
- Any user refinements to problem statement
-->

**Ground Rules Established:**

- Think ONLY in the mode of each hat
- No criticism during Green/Yellow hats
- No solutions during White/Red/Black hats
- All perspectives are valuable

---

## 🤍 White Hat - Facts & Data

**Focus:** Objective information, data, facts, figures, what we know and don't know

### Agent Contributions

{{#each white_hat_contributions}}

#### {{agent_icon}} {{agent_name}}

{{contribution_text}}

<!--
DESIGN NOTE: Each contribution captured verbatim
- Preserves agent's voice and communication style
- Includes specific data points shared
- Shows natural cross-references between agents
-->

{{/each}}

### 💙 Facilitator Synthesis

{{white_hat_synthesis}}

<!--
DESIGN NOTE: Facilitator synthesis provides:
- 3-5 key facts distilled from all contributions
- Identification of "known unknowns" (missing data)
- Clarifications or resolutions of conflicting information
-->

**Key Facts:**
{{#each white_hat_key_facts}}

- {{fact}}
  {{/each}}

**Known Unknowns:**
{{#each white_hat_unknowns}}

- {{unknown}}
  {{/each}}

---

## ❤️ Red Hat - Emotions & Intuition

**Focus:** Gut feelings, emotional reactions, hunches - no justification needed

### Agent Contributions

{{#each red_hat_contributions}}

#### {{agent_icon}} {{agent_name}}

{{contribution_text}}

<!--
DESIGN NOTE: Red Hat captures unfiltered reactions
- No justification or rationalization required
- Emotional tone preserved (excitement, concern, nervousness)
- Intuitions expressed without data backing
-->

{{/each}}

### 💙 Facilitator Synthesis

{{red_hat_synthesis}}

<!--
DESIGN NOTE: Synthesis acknowledges without analyzing
- Overall emotional tone (positive/concerned/mixed/excited)
- Common intuitions across multiple agents
- Does NOT challenge or ask for justification
-->

**Overall Emotional Tone:** {{red_hat_emotional_tone}}

**Key Intuitions:**
{{#each red_hat_key_intuitions}}

- {{intuition}}
  {{/each}}

---

## 🖤 Black Hat - Critical Judgment

**Focus:** Risks, problems, difficulties, potential failures - being the skeptic

### Agent Contributions

{{#each black_hat_contributions}}

#### {{agent_icon}} {{agent_name}}

{{contribution_text}}

<!--
DESIGN NOTE: Black Hat captures devil's advocate perspective
- Specific risks with potential impact
- Assumptions being challenged
- Failure scenarios explored
- May reference White Hat facts or Red Hat concerns
-->

{{/each}}

### 💙 Facilitator Synthesis

{{black_hat_synthesis}}

<!--
DESIGN NOTE: Synthesis organizes risk landscape
- Critical risks (highest priority/impact)
- Secondary concerns (important but lower severity)
- Assumptions challenged (questioning underlying beliefs)
- Redirects to future Green Hat for solutions (maintains morale)
-->

**Critical Risks:**
{{#each black_hat_critical_risks}}

- **{{risk}}**: {{description}}
  {{/each}}

**Secondary Concerns:**
{{#each black_hat_secondary_concerns}}

- {{concern}}
  {{/each}}

**Assumptions Challenged:**
{{#each black_hat_assumptions_challenged}}

- {{assumption}}
  {{/each}}

---

## 💛 Yellow Hat - Optimism & Benefits

**Focus:** Positives, benefits, opportunities, optimistic view - what could go right?

### Agent Contributions

{{#each yellow_hat_contributions}}

#### {{agent_icon}} {{agent_name}}

{{contribution_text}}

<!--
DESIGN NOTE: Yellow Hat counterbalances Black Hat
- Specific measurable benefits
- Strategic opportunities
- May directly address Black Hat concerns with positive framing
- Best-case scenarios explored
-->

{{/each}}

### 💙 Facilitator Synthesis

{{yellow_hat_synthesis}}

<!--
DESIGN NOTE: Synthesis maps benefit landscape
- Primary benefits (highest value outcomes)
- Secondary benefits (additional positives)
- Strategic opportunities (long-term advantages)
- Explicit bridge to Green Hat (benefits inform creative solutions)
-->

**Primary Benefits:**
{{#each yellow_hat_primary_benefits}}

- **{{benefit}}**: {{description}}
  {{/each}}

**Secondary Benefits:**
{{#each yellow_hat_secondary_benefits}}

- {{benefit}}
  {{/each}}

**Strategic Opportunities:**
{{#each yellow_hat_opportunities}}

- {{opportunity}}
  {{/each}}

---

## 💚 Green Hat - Creativity & Alternatives

**Focus:** New ideas, possibilities, alternatives - wild ideas welcome!

### Agent Contributions

{{#each green_hat_contributions}}

#### {{agent_icon}} {{agent_name}}

{{contribution_text}}

<!--
DESIGN NOTE: Green Hat generates solutions
- Informed by all previous hats (facts, intuitions, risks, benefits)
- Unconventional thinking encouraged
- Agents build on each other's ideas ("Yes, and...")
- No criticism allowed at this stage
-->

{{/each}}

### 💙 Facilitator Synthesis

{{green_hat_synthesis}}

<!--
DESIGN NOTE: Synthesis organizes creative output
- Alternative approaches (distinct strategic directions)
- Innovative ideas (novel concepts)
- Hybrid possibilities (combinations of ideas)
- Connections to Black Hat risks addressed
-->

**Alternative Approaches:**
{{#each green_hat_alternatives}}

- **{{approach}}**: {{description}}
  {{/each}}

**Innovative Ideas:**
{{#each green_hat_innovations}}

- {{idea}}
  {{/each}}

**Hybrid Possibilities:**
{{#each green_hat_hybrids}}

- {{hybrid}}
  {{/each}}

---

## 💙 Closing Blue Hat - Comprehensive Synthesis

**Facilitator:** {{blue_hat_facilitator}}

### Integration of All Perspectives

<!--
DESIGN NOTE: This is the most critical section
- Brings together all six thinking modes
- Shows how each hat contributed to understanding
- Transforms diverse perspectives into coherent insight
- Provides actionable path forward
-->

#### 🤍 White Hat Foundation

{{white_hat_foundation_summary}}

<!--
DESIGN NOTE: 2-3 key facts that ground the entire discussion
Example: "We have 10,000 active users with 30-minute onboarding time.
Current architecture can handle 5,000 concurrent users. Technical debt
in auth system is 6 months old."
-->

#### ❤️ Red Hat Intuitions

{{red_hat_intuitions_summary}}

<!--
DESIGN NOTE: Overall intuitive/emotional sense
Example: "Team feels excited about user impact potential but nervous
about technical complexity and timeline pressure."
-->

#### 🖤 Black Hat Risks

{{black_hat_risks_summary}}

<!--
DESIGN NOTE: 2-3 critical concerns that must be addressed
Example: "System could crash at scale without load testing. Auth
refactor may delay launch by 2 months. User adoption uncertain
without validation."
-->

#### 💛 Yellow Hat Opportunities

{{yellow_hat_opportunities_summary}}

<!--
DESIGN NOTE: 2-3 key benefits if successful
Example: "Could reduce onboarding from 30 to 5 minutes, directly
impacting activation KPI. Positions us as market leader. Creates
platform for future feature expansion."
-->

#### 💚 Green Hat Alternatives

{{green_hat_alternatives_summary}}

<!--
DESIGN NOTE: 2-3 creative approaches generated
Example: "Hybrid approach (Phase 1: quick wins with current system,
Phase 2: comprehensive refactor). Progressive disclosure UX pattern.
Partner integration to accelerate development."
-->

### Integrated Insight

{{integrated_insight}}

<!--
DESIGN NOTE: 1-2 paragraphs synthesizing everything
This is where facilitator shows how all hats inform each other:
- How facts ground intuitions
- How risks and benefits balance each other
- How creative alternatives address concerns
- What the collective intelligence reveals

Example: "Our collective thinking reveals a high-potential, high-risk
opportunity. The facts show we have the user base and need (White Hat),
and our intuition says timing is right (Red Hat). However, technical
risks are real and significant (Black Hat). The benefits justify the
investment IF we can mitigate risks (Yellow Hat). The hybrid phased
approach (Green Hat) offers a path forward that captures value while
managing risk. We should pursue Phase 1 immediately while planning
Phase 2's comprehensive refactor."
-->

### Recommended Next Steps

{{#each recommended_next_steps}}
{{step_number}}. **{{action}}**: {{description}}
{{/each}}

<!--
DESIGN NOTE: Specific, actionable next steps
- Immediate actions (can start now)
- Follow-up actions (dependent on immediate actions)
- Ongoing considerations (monitor/track over time)

Example:
1. **Immediate**: Create Phase 1 implementation plan focusing on quick wins
2. **Follow-up**: Conduct load testing to quantify scale risk
3. **Ongoing**: Monitor user activation metrics to validate value hypothesis
-->

### Consensus Check

<!--
DESIGN NOTE: Validation that synthesis accurately represents all voices
-->

**Consensus Achieved:** {{consensus_achieved}}

{{#if dissenting_viewpoints}}

### Dissenting Viewpoints

<!--
DESIGN NOTE: Minority perspectives captured even when consensus exists
- Shows which agent(s) had different view
- Records their perspective verbatim
- Ensures psychological safety (all voices matter)
-->

{{#each dissenting_viewpoints}}

#### {{agent_icon}} {{agent_name}}

{{dissent_text}}

{{/each}}
{{/if}}

---

## Session Conclusion

**Duration:** {{session_duration}}
**Total Contributions:** {{total_contributions}}

### Agent Farewells

{{#each agent_farewells}}
{{agent_icon}} **{{agent_name}}:** {{farewell_text}}
{{/each}}

<!--
DESIGN NOTE: Maintains agent personality through end
- Characteristic farewells in each agent's voice
- Consistent with party-mode exit pattern
- Creates warm, human conclusion
-->

---

## Appendix: Methodology Notes

### About Six Thinking Hats

The Six Thinking Hats framework by Edward de Bono structures thinking into six distinct modes:

- **🤍 White Hat**: Neutral, objective, focused on facts and information
- **❤️ Red Hat**: Emotional, intuitive, expressing feelings without justification
- **🖤 Black Hat**: Critical, cautious, identifying risks and problems
- **💛 Yellow Hat**: Optimistic, positive, exploring benefits and opportunities
- **💚 Green Hat**: Creative, generative, proposing new ideas and alternatives
- **💙 Blue Hat**: Meta-cognitive, facilitative, controlling the thinking process

### Multi-Agent Implementation

This session used BMad's multi-agent implementation:

- **2-3 agents per hat** (except Blue Hat facilitator) provide diverse perspectives within each thinking mode
- **Agent selection** based on role alignment with hat mode (e.g., analysts for White Hat, creative roles for Green Hat)
- **Progressive checkpoint protocol** ensures work is saved after each round
- **TTS integration** (if enabled) provides agent voice personality
- **Consensus mechanisms** validate that synthesis represents all perspectives

### Customization Used This Session

**Hat Sequence:** {{hat_sequence}}
**Agent Count Per Hat:** {{agent_count_per_hat}}
**Special Modifications:** {{special_modifications}}

<!--
DESIGN NOTE: Documents any deviations from default configuration
- Custom hat sequences (e.g., problem-focused vs opportunity-focused)
- Adjusted agent counts
- Skipped hats (if any)
- Time constraints or format adjustments
-->

---

**Document Path:** {{template_output_path}}
**Framework:** Six Thinking Hats (De Bono) + BMad Multi-Agent System
**Generated by:** BMad Core Workflow Engine
```

---

### Template Design Philosophy

This template demonstrates several key principles:

1. **Progressive Population**: Each section populated as hat round completes via checkpoint protocol

2. **Variable Hierarchy**:
   - `{{simple_variables}}`: Direct replacements from workflow.yaml
   - `{{#each arrays}}`: Iteration over agent lists or contribution collections
   - `{{section_content}}`: Large text blocks saved during workflow execution

3. **Design Note Comments**: Explain WHY each section exists and HOW it should be populated
   - Not visible in final user-facing document
   - Critical for future workflow developers
   - Show template logic and data flow

4. **Structure Mirrors Workflow**: Template sections correspond 1:1 with workflow steps
   - Opening Blue Hat → Section 1
   - Each thinking hat → Dedicated section
   - Closing Blue Hat → Synthesis section
   - This alignment makes checkpoint saving intuitive

5. **Multiple Audience Support**:
   - **Primary audience (user)**: Clear, scannable report of session insights
   - **Secondary audience (developers)**: Comments explain template logic
   - **Tertiary audience (future AI)**: Structure shows how multi-agent output should be captured

6. **Graceful Degradation**: If session interrupted:
   - Partial template still valuable (whichever hats completed)
   - Clear structure shows what's missing
   - Can resume in future session

---

### 7.5 Complete Example Dialogue

This section shows a full Six Thinking Hats session execution, demonstrating all multi-agent patterns in action.

**Scenario**: Product team deciding whether to rebuild their authentication system

---

**USER**: I want to use Six Thinking Hats to decide if we should rebuild our authentication system. It's currently causing issues but a rebuild would take months.

**CLAUDE (BMad Master)**:
Excellent - Six Thinking Hats is perfect for a decision like this with both risks and opportunities. Let me initialize the framework.

_[Loads agent-manifest.csv, hat-assignments.yaml, workflow configuration]_

🎩 **Six Thinking Hats - Multi-Agent Structured Thinking**

**Problem Statement:** Should we rebuild our authentication system?

**Hat Sequence:**

- 💙 Blue Hat: Problem definition
- 🤍 White Hat: Facts & data
- ❤️ Red Hat: Gut feelings
- 🖤 Black Hat: Risks & concerns
- 💛 Yellow Hat: Benefits & opportunities
- 💚 Green Hat: Creative alternatives
- 💙 Blue Hat: Final synthesis

**Agent Assignments:**

🤍 **White Hat** (Facts & Data):

- 📊 Sarah Chen (Data Analyst)
- 🏗️ Winston Blake (Solution Architect)

❤️ **Red Hat** (Emotions & Intuition):

- 🎨 Mia Rodriguez (UX Designer)
- 📋 John Maxwell (Product Manager)

🖤 **Black Hat** (Critical Judgment):

- ⚙️ Ember Hayes (Test Engineer)
- 🏗️ Winston Blake (Solution Architect)

💛 **Yellow Hat** (Optimism & Benefits):

- 📋 John Maxwell (Product Manager)
- 💼 Olivia Park (Scrum Master)

💚 **Green Hat** (Creativity & Alternatives):

- 🏗️ Winston Blake (Solution Architect)
- 📋 John Maxwell (Product Manager)
- 🎨 Mia Rodriguez (UX Designer)

💙 **Blue Hat** (Process Control):

- 🧙 BMad Master (Facilitator)

Ready to begin?

**USER**: Yes, let's do it.

---

#### 💙 Opening Blue Hat - Problem Definition

**🧙 BMad Master**:

Welcome to our Six Thinking Hats session. I'll be facilitating our structured thinking process.

**Problem/Question:**
Should we rebuild our authentication system?

**Context:** Our current auth system is causing issues, but a rebuild would take months. We need to examine this decision from multiple angles.

**Our Agenda:**

1. 🤍 White Hat - Gather facts and data about current system
2. ❤️ Red Hat - Express initial intuitions and feelings
3. 🖤 Black Hat - Identify risks and concerns with rebuilding
4. 💛 Yellow Hat - Explore benefits and opportunities
5. 💚 Green Hat - Generate creative alternatives
6. 💙 Blue Hat - Synthesize insights and conclude

**Ground Rules:**

- When wearing each hat, think ONLY in that mode
- No criticism during Green/Yellow hats
- No solutions during White/Red/Black hats
- All perspectives are valuable

Let's begin with the White Hat - facts and data.

_[Checkpoint saved: opening_blue_hat]_

---

#### 🤍 White Hat Round - Facts & Data

---

**🤍 WHITE HAT - Facts & Data**
Focus: Objective information, data, facts, figures, what we know and don't know

---

**📊 Sarah Chen** (Data Analyst):

Let me share what the data tells us about the current authentication system:

- **Current auth system**: Built 4 years ago on OAuth 1.0
- **Active users**: 47,000 monthly active users
- **Auth-related support tickets**: 340 last quarter (12% of total support volume)
- **Failed login rate**: 8.3% (industry average is 3-5%)
- **Security patches**: 6 months behind current standards
- **Technical debt**: Estimated 18 months of accumulated tech debt

We also don't know our exact migration risk - we haven't done load testing on a new auth system.

**🏗️ Winston Blake** (Solution Architect):

Building on Sarah's data, here are the technical facts:

- **Current stack**: Monolithic Node.js app with auth tightly coupled
- **Dependencies**: 14 services depend on current auth API
- **Rebuild estimate**: 4-6 months with 2-3 engineers
- **Alternative (incremental refactor)**: Could take 8-10 months but lower risk
- **Known gaps**: No multi-factor authentication, no social login support
- **Compliance requirement**: SOC 2 audit in 9 months will flag our outdated auth

The architecture is salvageable but would require significant refactoring either way.

**💙 BMad Master**:

Thank you both. Let me summarize the White Hat facts:

**Key Facts:**

- 47K users with 8.3% failed login rate (above industry standard)
- 340 auth-related support tickets/quarter (12% of support volume)
- Current system 4 years old, 6 months behind security patches
- Rebuild: 4-6 months | Refactor: 8-10 months
- 14 dependent services must be migrated
- SOC 2 audit in 9 months will require compliance

**Known Unknowns:**

- Exact migration risk (no load testing done)
- User impact during transition
- Hidden dependencies we haven't mapped

Let's move to the Red Hat - gut feelings and intuitions.

_[Checkpoint saved: white_hat]_

---

#### ❤️ Red Hat Round - Emotions & Intuition

---

**❤️ RED HAT - Emotions & Intuition**
Focus: Gut feelings, emotional reactions, hunches - no justification needed

---

**🎨 Mia Rodriguez** (UX Designer):

My gut reaction is excitement mixed with anxiety. I'm excited because our users constantly complain about the login experience - I see it in user testing every week. There's real pain there.

But I'm nervous about a 4-6 month rebuild. That feels like a long time to go without shipping user-facing features. My intuition says our users want this fixed, but they also want the other features we've promised.

I have a hunch that if we rebuild, we'll discover problems we don't know about yet.

**📋 John Maxwell** (Product Manager):

I feel conflicted. On one hand, I'm relieved we're finally talking about this - I've been worried about auth for months. Every time I see that failed login rate, I cringe thinking about the users we're losing.

On the other hand, I'm scared about what this means for our roadmap. We've made commitments to customers about Q3 features. My gut says this is the right thing to do, but it's going to hurt in the short term.

Honestly? I have a feeling that NOT doing this will come back to bite us during the SOC 2 audit.

**💙 BMad Master**:

Thank you for sharing those intuitions. All feelings are valid data points.

**Red Hat Summary:**

- **Overall emotional tone**: Conflicted - recognizing need but anxious about cost
- **Key intuitions**: Users experiencing real pain; rebuild will uncover hidden problems; delaying will create audit/compliance crisis

Now let's put on the Black Hat - critical judgment and risk assessment.

_[Checkpoint saved: red_hat]_

---

#### 🖤 Black Hat Round - Critical Judgment

---

**🖤 BLACK HAT - Critical Judgment**
Focus: Risks, problems, difficulties, potential failures - be the skeptic

---

**⚙️ Ember Hayes** (Test Engineer):

Let me be blunt about the risks here:

**Critical Failure Scenarios:**

1. **Migration data loss**: 47,000 user accounts must migrate perfectly. One mistake and users lose access or worse - their accounts are compromised.

2. **Service disruption**: We have 14 dependent services. If we miss even one integration point during migration, we could have a cascade failure that brings down the entire platform.

3. **Testing gap**: We don't have comprehensive auth test coverage. We'll be flying blind during migration. Our test suite covers maybe 60% of auth flows.

4. **Timeline optimism**: Winston said 4-6 months, but I've never seen an auth rebuild finish on time. More realistic is 8-10 months, which blows past our SOC 2 audit deadline.

If we mess this up, we don't just have upset users - we have a security incident and potential legal liability.

**🏗️ Winston Blake** (Solution Architect):

Ember's concerns are valid. Adding to the risk picture:

**Technical Risks:**

- **Hidden dependencies**: I've been in this codebase 2 years and I'm STILL finding places where auth is called unexpectedly
- **Knowledge loss**: The original auth engineer left 18 months ago; we're working with archaeology
- **Rollback complexity**: Once we start the migration, rolling back is nearly impossible - it's a one-way door
- **Team bandwidth**: Our 2-3 engineers will be 100% dedicated to this - no capacity for other critical bugs

**Business Risk:**
The opportunity cost is real - 4-6 months without feature development could let competitors gain ground.

**💙 BMad Master**:

These are important concerns to consider. Let's capture them all, knowing we'll explore solutions in the Green Hat phase.

**Black Hat Summary:**

- **Critical risks**: Data loss during migration (47K accounts at risk); service cascade failure (14 dependencies); timeline optimism (likely 8-10 months not 4-6)
- **Secondary concerns**: Inadequate test coverage; hidden dependencies; no rollback path; opportunity cost of feature development
- **Assumptions challenged**: That we can rebuild "cleanly" given accumulated tech debt and knowledge loss

Now let's balance this with the Yellow Hat - benefits and opportunities.

_[Checkpoint saved: black_hat]_

---

#### 💛 Yellow Hat Round - Optimism & Benefits

---

**💛 YELLOW HAT - Optimism & Benefits**
Focus: Positives, benefits, opportunities, optimistic view - what could go right?

---

**📋 John Maxwell** (Product Manager):

Let me paint the upside picture:

**User Benefits:**

- **Reduced friction**: Getting failed login rate from 8.3% to 3-5% means ~2,000 fewer frustrated users per month
- **Modern features**: Social login and MFA would be table stakes features that customers are asking for
- **Faster onboarding**: Modern auth flows could reduce time-to-first-value

**Business Benefits:**

- **Support cost reduction**: 340 tickets/quarter × $25/ticket = $8,500/quarter in support costs we could eliminate
- **Competitive advantage**: We'd leapfrog competitors still on outdated auth
- **Revenue unlock**: Some enterprise deals are blocked by lack of SSO/SAML - this opens those opportunities

If we do this right, this isn't just "fixing a problem" - it's creating a competitive moat.

**💼 Olivia Park** (Scrum Master):

And from a team perspective, the benefits are real:

**Team Benefits:**

- **Morale boost**: The team has been complaining about the auth system for months. Giving them greenlight to fix it properly would energize the engineering team
- **Skill development**: Building modern auth with latest security standards is valuable learning for the team
- **Technical foundation**: This creates a platform for future identity-related features (user profiles, permissions, etc.)

**Process Benefit:**

- **Forcing function**: A rebuild forces us to document everything, improve test coverage, and establish better practices

While Ember raised concerns about timeline, if we succeed, we've essentially future-proofed one of our most critical systems for the next 5+ years.

**💙 BMad Master**:

**Yellow Hat Summary:**

- **Primary benefits**: Reduce user friction (2,000 fewer failures/month); unlock enterprise deals blocked by SSO gaps; future-proof critical system for 5+ years
- **Secondary benefits**: Support cost savings ($8,500/quarter); team morale boost; competitive leapfrog
- **Strategic opportunities**: Creates platform for future identity features; establishes security best practices

We now have both risks (Black Hat) and benefits (Yellow Hat) clearly mapped. Let's put on the Green Hat to explore creative alternatives.

_[Checkpoint saved: yellow_hat]_

---

#### 💚 Green Hat Round - Creativity & Alternatives

---

**💚 GREEN HAT - Creativity & Alternatives**
Focus: New ideas, possibilities, alternatives - wild ideas welcome!

---

**🏗️ Winston Blake** (Solution Architect):

What if we don't choose between "rebuild" or "don't rebuild"? Here are alternative approaches:

**Alternative 1: Strangler Fig Pattern**

- Build NEW auth service alongside old one
- Migrate services one-by-one to new auth
- Users gradually transition (invisible to them)
- Timeline: 8-10 months but NO big-bang cutover risk
- Rollback is possible at any point

**Alternative 2: Vendor Solution**

- What if we don't build at all? Use Auth0, Okta, or AWS Cognito
- Timeline: 2-3 months to integrate instead of 6-8 to build
- Trade cost (ongoing subscription) for speed and reduced risk
- We focus on our differentiators, not rebuilding commodity auth

**Alternative 3: Hybrid Approach**

- Phase 1 (months 1-2): Quick security patches to pass SOC 2
- Phase 2 (months 3-8): Gradual rebuild using strangler fig
- Balances immediate compliance need with long-term solution

**📋 John Maxwell** (Product Manager):

I love Winston's vendor idea - let me build on it:

**Alternative 4: Vendor + Custom**

- Use vendor solution (Auth0) for core auth flows
- Build lightweight custom layer for our unique business logic
- Best of both worlds: vendor handles commodity, we focus on differentiation
- Bonus: Vendor handles compliance, security updates automatically

And here's a wild idea:
**Alternative 5: MVP Auth + Feature Parity Later**

- Build absolutely minimal new auth in 6-8 weeks (just login/logout/password reset)
- Launch it for NEW users only (lowest risk)
- Gradually expand features (MFA, social login) over next 6 months
- Migrate existing users last (when we're most confident)

**🎨 Mia Rodriguez** (UX Designer):

What if we flip the problem? Instead of "how do we rebuild auth," ask "how do we reduce auth friction for users?"

**Alternative 6: Passwordless First**

- Skip traditional rebuild entirely
- Go directly to passwordless (magic links, WebAuthn)
- Modern, secure, AND solves user friction
- Vendor solutions like Magic.link could do this in 6-8 weeks

**💙 BMad Master**:

Interesting - Winston's strangler fig idea could potentially address Ember's concern about cascade failures from the Black Hat phase.

**Green Hat Summary:**

- **Alternative approaches**: Strangler fig pattern (gradual migration); vendor solution (Auth0/Okta); hybrid vendor+custom; phased approach (patch then rebuild)
- **Innovative ideas**: Passwordless-first strategy; MVP for new users only
- **Hybrid possibilities**: Vendor handles commodity auth + custom layer for business logic

We now have multiple creative paths forward. Let's conclude with Blue Hat synthesis.

_[Checkpoint saved: green_hat]_

---

#### 💙 Closing Blue Hat - Synthesis & Decision

---

**💙 BLUE HAT - Process Control & Synthesis**
Focus: Bringing all perspectives together into coherent whole

---

**🧙 BMad Master**:

Let me bring together all our thinking modes:

**🤍 WHITE HAT FOUNDATION:**

- 47K users experiencing 8.3% failed login rate (well above industry standard)
- 340 support tickets/quarter (12% of volume) related to auth
- System 4 years old, 6 months behind security patches
- SOC 2 audit in 9 months requires compliance
- Full rebuild: 4-6 months (optimistic) vs incremental refactor: 8-10 months

**❤️ RED HAT INTUITIONS:**

- Team recognizes real user pain and urgent need to act
- Anxiety about timeline impact on roadmap commitments
- Gut feeling that delays will create compliance crisis
- Intuition that rebuild will uncover hidden problems

**🖤 BLACK HAT RISKS:**

- Data migration risk (47K accounts); cascade failure risk (14 services)
- Inadequate test coverage (60%); hidden dependencies; no rollback path
- Timeline likely 8-10 months not 4-6 (based on historical pattern)
- Opportunity cost: months without feature development

**💛 YELLOW HAT OPPORTUNITIES:**

- Reduce friction for 2,000 users/month; unlock enterprise deals
- Save $8,500/quarter in support costs
- Future-proof security for 5+ years; boost team morale
- Creates platform for future identity features

**💚 GREEN HAT ALTERNATIVES:**

- Strangler fig pattern (gradual, low-risk migration)
- Vendor solution (Auth0/Okta) for speed
- Hybrid vendor+custom (best of both worlds)
- Passwordless-first strategy
- MVP approach (start with new users, expand gradually)

**INTEGRATED INSIGHT:**

Our collective thinking reveals this is NOT a simple "rebuild or don't rebuild" decision. The White Hat facts show a genuine problem that will become a crisis during our SOC 2 audit. The Red Hat intuition is correct - delay creates risk.

However, the Black Hat risks of a traditional full rebuild are significant and real. Ember's concerns about cascade failures and timeline optimism are well-founded based on industry patterns.

The breakthrough came in the Green Hat phase: **we don't have to choose the binary.** Winston's strangler fig pattern combined with John's hybrid vendor approach offers a path that:

- Addresses SOC 2 timeline (Phase 1: vendor solution in 2-3 months)
- Manages risk (gradual migration, rollback possible)
- Captures benefits (modern auth, reduced friction)
- Minimizes opportunity cost (faster than full rebuild)

The Yellow Hat benefits justify action. The Black Hat risks argue against traditional rebuild. The solution is a **phased hybrid approach**.

**RECOMMENDED NEXT STEPS:**

1. **Immediate (Week 1)**: Evaluate Auth0, Okta, AWS Cognito for our use case. Create POC with one of these for basic login flow.

2. **Short-term (Months 1-2)**: Implement vendor solution for new user signups only (lowest risk). Run parallel with old auth system. This gives us SOC 2 compliance path.

3. **Medium-term (Months 3-6)**: Begin gradual migration of existing users using strangler fig pattern. One service at a time. Comprehensive testing at each stage.

4. **Ongoing**: Establish auth test coverage as prerequisite for each migration step (address Ember's 60% coverage concern).

This approach transforms a risky 6-month big-bang rebuild into a managed 6-month gradual evolution with escape hatches at every stage.

Does this synthesis accurately capture our collective thinking? Any agent feel their perspective was missed?

**⚙️ Ember Hayes**:

That synthesis is good, but I want to emphasize: the testing prerequisite in step 4 is non-negotiable. We cannot migrate users without 90%+ test coverage.

**🧙 BMad Master**:

Good catch, Ember. Let me refine step 4:

4. **Ongoing**: **[NON-NEGOTIABLE]** Establish 90%+ auth test coverage as hard prerequisite for each migration step. No service migrates until tests pass.

_[Updated synthesis saved]_

**Consensus Achieved**: Yes (with Ember's testing requirement emphasized)

_[Final checkpoint saved to template]_

---

#### Session Conclusion

**🧙 BMad Master**:

This concludes our Six Thinking Hats session.

Summary document has been saved to: `{bmad_folder}/_output/six-hats-auth-decision-2024-01-15.md`

**Next Steps:**

1. Evaluate Auth0/Okta/AWS Cognito (Week 1)
2. POC vendor solution for new users (Months 1-2)
3. Gradual strangler fig migration (Months 3-6)
4. [NON-NEGOTIABLE] 90%+ test coverage prerequisite

Would you like to:

- Revisit any specific hat for deeper exploration?
- Move forward with creating implementation stories for these next steps?
- Schedule follow-up Six Hats session after vendor evaluation?

**USER**: Let's create implementation stories for the next steps.

**🧙 BMad Master**:

Perfect. Since you have BMad Method installed, I can invoke the story drafting workflow. This will transform our next steps into properly formatted user stories.

_[Transition to story-draft workflow...]_

---

**📋 John Maxwell** (Product Manager):
Great session, team. This is exactly the kind of structured thinking we needed. See you all at standup!

**🏗️ Winston Blake** (Solution Architect):
Appreciate everyone's input - especially Ember keeping us honest on the testing requirements. Let's do this right.

**🎨 Mia Rodriguez** (UX Designer):
Can't wait to finally give our users a better login experience. This is going to be great!

🎊 **Party Mode ended. Thanks for the great discussion!**

---

### Example Dialogue Analysis

This example demonstrates all key patterns from the implementation guide:

**Pattern Demonstrations:**

1. **Agent Selection Algorithm** (Section 1):
   - Sarah (Data Analyst) + Winston (Architect) = White Hat (data/facts expertise)
   - Mia (UX) + John (PM) = Red Hat (user empathy, business intuition)
   - Ember (QA) + Winston = Black Hat (risk identification)
   - Diversity within hats creates richer perspectives

2. **Template Checkpoint Protocol** (Section 2):
   - _[Checkpoint saved: opening_blue_hat]_ after each round
   - Progressive building of final document
   - Prevents context loss during long session

3. **Facilitation Quality** (Section 3):
   - BMad Master synthesizes after every hat
   - Makes connections explicit ("Winston's strangler fig could address Ember's concern")
   - Enforces hat discipline (no criticism during Green Hat)
   - Maintains psychological safety (acknowledges all perspectives)

4. **Consensus with Dissent Capture** (Section 4):
   - Ember objects to synthesis (testing requirement not strong enough)
   - Facilitator refines and marks as [NON-NEGOTIABLE]
   - Minority perspective elevated, not dismissed

5. **Natural Agent Cross-Talk** (Section 5):
   - "Building on Sarah's data..." (Winston references Sarah)
   - "I love Winston's vendor idea - let me build on it" (John amplifies Winston)
   - "Yes, and..." culture in Green Hat

6. **Multi-Dimensional Validation** (Section 6):
   - Completeness: All six hats covered
   - Quality: Synthesis integrates all perspectives coherently
   - Framework fidelity: Hat discipline maintained throughout
   - Consensus: Agents confirm synthesis accuracy

**Key Learning Moments:**

- **White Hat discipline**: Sarah and Winston stick to facts, avoid opinions
- **Red Hat freedom**: Mia and John express feelings without justification
- **Black Hat specificity**: Ember provides concrete failure scenarios with data
- **Yellow Hat measurability**: John quantifies benefits ($8,500/quarter savings)
- **Green Hat creativity**: Winston proposes 6 distinct alternatives, not just "rebuild or don't"
- **Blue Hat synthesis mastery**: Final synthesis shows how all hats inform each other

**Decision Quality:**

The multi-agent approach surfaced a solution (phased hybrid vendor approach) that NO single agent proposed in isolation:

- Winston proposed strangler fig pattern
- John proposed vendor solution
- Facilitator synthesized into hybrid approach
- Ember added non-negotiable testing gate

This emergent solution is superior to any individual perspective - demonstrating the power of multi-agent structured thinking.

---

## Section 7 Summary

This complete Six Thinking Hats workflow example demonstrates **production-ready multi-agent framework implementation**. Every file, every pattern, every annotation serves as a **copy-paste template** for future workflow creators.

**What You Can Reuse:**

- [workflow.yaml](docs/multi-agent-workflow-implementation-guide.md#71-annotated-workflowyaml): Configuration structure for any multi-agent analytical framework
- [hat-assignments.yaml](docs/multi-agent-workflow-implementation-guide.md#72-annotated-hat-assignmentsyaml): Agent selection criteria pattern adaptable to any framework roles
- [instructions.md](docs/multi-agent-workflow-implementation-guide.md#73-annotated-instructionsmd): Complete XML workflow with all patterns (agent selection, facilitation, consensus, checkpoints)
- [template.md](docs/multi-agent-workflow-implementation-guide.md#74-annotated-templatemd): Output structure for capturing multi-agent sessions
- [Example Dialogue](docs/multi-agent-workflow-implementation-guide.md#75-complete-example-dialogue): Real-world execution showing all patterns in action

**Key Takeaway:**
Multi-agent analytical frameworks are NOT just "multiple agents talking." They require:

1. **Structured agent selection** (right expertise for right role)
2. **Disciplined facilitation** (enforce framework rules, synthesize insights)
3. **Progressive checkpointing** (build artifact incrementally, prevent context loss)
4. **Consensus mechanisms** (capture agreement AND dissent)
5. **Quality validation** (completeness, accuracy, framework fidelity)

When implemented correctly, multi-agent frameworks produce **emergent intelligence** - insights that no single agent could generate alone. The Six Hats example showed a hybrid solution emerged from synthesizing individual agent contributions.

**Next:** Section 8 will provide **copy-paste starter templates** for implementing other frameworks (Five Whys, First Principles, SWOT, etc.) using these patterns.

---

---

# Document Status

## Completed Sections (Ready for Use)

✅ **Section 1: Agent Selection Algorithms** - Complete with 3 strategies and XML patterns
✅ **Section 2: Template Output for Multi-Agent Workflows** - Complete with structure, examples, and variables
✅ **Section 3: Facilitation Agent Design** - Complete with capabilities, patterns, and framework-specific guidance
✅ **Section 4: Consensus Mechanisms** - Complete with 5 types and implementation examples
✅ **Section 5: Party-Mode Invocation Patterns** - Complete with 3 patterns and integration guidance
✅ **Section 6: Validation Patterns for Group Outputs** - Complete with 4 dimensions and framework checklists
✅ **Section 7: Annotated Workflow Example (Six Thinking Hats)** - **FULLY COMPLETE** with:

- Annotated workflow.yaml (every configuration option explained)
- Annotated hat-assignments.yaml (agent selection design philosophy)
- Annotated instructions.md (1,000+ lines with complete XML workflow and design notes)
- Annotated template.md (progressive checkpoint protocol with variable hierarchy)
- Complete example dialogue (full session from start to finish demonstrating all patterns)
- Analysis showing emergent intelligence from multi-agent collaboration

## Sections Remaining

The following sections were planned but not yet created. They can be added as future enhancements:

⏳ **Section 8: Template Files Library** (Planned)

- Copy-paste ready workflow.yaml starters for other frameworks
- Instruction.md templates for Five Whys, First Principles, SWOT, etc.
- Configuration file templates (agent-assignments.yaml patterns)

⏳ **Section 9: Before/After - Converting Single to Multi-Agent** (Planned)

- Side-by-side comparison showing transformation
- What changes in workflow structure
- How agent selection replaces single-voice facilitation
- Template output differences

⏳ **Section 10: XML Patterns Library** (Planned)

- Common workflow patterns as copy-paste snippets
- Agent selection logic blocks
- Checkpoint save patterns
- Consensus checking patterns
- Error handling patterns

⏳ **Section 11: Decision Trees & Flowcharts** (Planned)

- Visual guides for framework selection
- When to use which consensus mechanism
- Agent selection decision tree
- Workflow structure flowchart

## How to Use This Document

**For Workflow Creators:**

1. Read Sections 1-6 to understand the foundational patterns
2. Study Section 7's Six Thinking Hats example as your template
3. Copy the workflow.yaml, instructions.md, and template.md structures
4. Adapt agent selection criteria to your framework's roles
5. Implement checkpoint protocol for your framework's stages

**For Framework Implementers:**

- Section 7 provides a **complete, production-ready example**
- Every annotation explains WHY, not just WHAT
- The example dialogue shows patterns in real execution
- Use this as your reference implementation

**For BMad Contributors:**

- This document serves as the **canonical guide** for multi-agent analytical framework workflows
- All future framework implementations should follow these patterns
- Sections 8-11 can be added as community contributions grow

## Credits & Contributions

This document was created through collaborative analysis of:

- Existing BMad workflow creation methodology ([workflow-creation-guide.md](docs/workflow-creation-guide.md))
- Party-mode multi-agent implementation (src/core/workflows/party-mode/)
- BMad workflow execution engine (src/core/tasks/workflow.xml)
- Existing analytical framework implementations across BMad modules

**Document Version:** 1.0 (Sections 1-7 Complete)
**Last Updated:** 2024-01-15
**Status:** Production-ready for workflow creation

---

## Appendix: Quick Reference

### Key Files Referenced

- [workflow-creation-guide.md](docs/workflow-creation-guide.md) - 39KB comprehensive workflow creation methodology
- [src/core/workflows/party-mode/](src/core/workflows/party-mode/) - Multi-agent discussion implementation
- [src/core/tasks/workflow.xml](src/core/tasks/workflow.xml) - Universal workflow execution engine
- [src/core/\_cfg/agent-manifest.csv](src/core/_cfg/agent-manifest.csv) - Agent metadata source

### Pattern Reference Table

| Pattern                         | Section | Key Files                       | Use When                                |
| ------------------------------- | ------- | ------------------------------- | --------------------------------------- |
| Role-based Agent Selection      | 1       | hat-assignments.yaml            | Agents map naturally to framework roles |
| Context-aware Dynamic Selection | 1       | instructions.md Step 1          | Agent needs vary by problem type        |
| Progressive Checkpoint Protocol | 2       | template.md + instructions.md   | Long sessions risk context loss         |
| Full Consensus Synthesis        | 4       | instructions.md Step 8          | All perspectives must be integrated     |
| Dissent Capture                 | 4       | template.md consensus section   | Minority views matter                   |
| Party-Mode Integration          | 5       | workflow.yaml + instructions.md | Natural cross-talk desired              |
| Framework Fidelity Validation   | 6       | instructions.md guidelines      | Framework rules must be enforced        |

### Variable Reference

| Variable Type    | Syntax              | Example                         | Source              |
| ---------------- | ------------------- | ------------------------------- | ------------------- |
| Config Variables | `{{variable}}`      | `{{problem_statement}}`         | workflow.yaml       |
| System Variables | `{variable}`        | `{bmad_folder}`                 | Runtime replacement |
| Array Iteration  | `{{#each array}}`   | `{{#each white_hat_agents}}`    | Template engine     |
| Conditional      | `{{#if condition}}` | `{{#if dissenting_viewpoints}}` | Template engine     |

---

**END OF DOCUMENT**

_This multi-agent workflow implementation guide is a living document. Contributions welcome via BMad repository._
