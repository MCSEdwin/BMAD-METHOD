# Analytical Frameworks for Multi-Agent Conversations

This document catalogs BMad's comprehensive framework ecosystem and proposes enhancements for multi-agent structured analysis.

## Executive Summary

BMad contains **9 major analytical frameworks** with **150+ specific methodologies** spanning creative, strategic, diagnostic, and collaborative thinking. This document:

1. **Catalogs existing frameworks** - What's already built and how to use them
2. **Proposes multi-agent enhancements** - How to add Six Hats, 5 Whys, First Principles with party-mode orchestration
3. **Identifies integration opportunities** - How frameworks can work together

---

## TABLE OF CONTENTS

- [Part I: Existing Framework Ecosystem](#part-i-existing-framework-ecosystem)
- [Part II: Proposed Multi-Agent Frameworks](#part-ii-proposed-multi-agent-frameworks)
- [Part III: Integration & Enhancement Strategies](#part-iii-integration--enhancement-strategies)

---

# PART I: EXISTING FRAMEWORK ECOSYSTEM

BMad already includes comprehensive analytical frameworks across three modules:

## Quick Reference: Existing Frameworks

| Framework               | Module | Methodologies   | Primary Agent | Use When                       |
| ----------------------- | ------ | --------------- | ------------- | ------------------------------ |
| **Brainstorming**       | Core   | 36 techniques   | Carson        | Need creative ideas            |
| **Design Thinking**     | CIS    | 31 methods      | Maya          | Human-centered design          |
| **Problem-Solving**     | CIS    | 31 methods      | Dr. Quinn     | Systematic troubleshooting     |
| **Innovation Strategy** | CIS    | 31 frameworks   | Victor        | Business model innovation      |
| **Storytelling**        | CIS    | 25 frameworks   | Sophia        | Narrative creation             |
| **Research**            | BMM    | 3 tracks        | Analyst       | Market/technical investigation |
| **Retrospective**       | BMM    | 12-step process | Bob (SM)      | Post-epic review               |
| **Party-Mode**          | Core   | Multi-agent     | All agents    | Group discussion               |

---

## 1. Core Brainstorming Workflow

**Location:** `src/core/workflows/brainstorming/`

**What it is:** Interactive facilitation using 36 creative techniques across 7 categories

**36 Techniques Organized by Category:**

### Structured (5 techniques)

- SCAMPER (Substitute, Combine, Adapt, Modify, Put to other use, Eliminate, Reverse)
- Six Thinking Hats
- Mind Mapping
- Resource Constraints
- Attribute Listing

### Creative (6 techniques)

- What If Scenarios
- Analogical Thinking
- Reversal Inversion
- First Principles
- Forced Relationships
- Time Shifting

### Collaborative (4 techniques)

- Yes And Building
- Brain Writing
- Random Stimulation
- Role Playing

### Deep (5 techniques)

- Five Whys
- Morphological Analysis
- Provocation Technique
- Assumption Reversal
- Question Storming

### Theatrical (5 techniques)

- Time Travel Talk Show
- Alien Anthropologist
- Dream Fusion Lab
- Emotion Orchestra
- Parallel Universe Cafe

### Wild (4 techniques)

- Chaos Engineering
- Guerrilla Gardening
- Pirate Code
- Zombie Apocalypse Planning

### Introspective Delight (5 techniques)

- Inner Child Conference
- Shadow Work
- Values Archaeology
- Future Self Interview
- Body Wisdom

**How to use:**

```
Load Carson (Brainstorming Coach)
*brainstorm

Choose approach:
1. User-Selected Techniques
2. AI-Recommended (context-based)
3. Random Technique Selection
4. Progressive Technique Flow
```

**Outputs:** Session results with generated ideas, themes, action items

**Note:** Already includes Six Thinking Hats, Five Whys, and First Principles as selectable techniques!

---

## 2. Design Thinking Workflow (CIS)

**Location:** `src/modules/cis/workflows/design-thinking/`

**What it is:** Human-centered design methodology with 31 methods across 5 phases

**5-Phase Structure:**

### Phase 1: Empathize

- User interviews
- Empathy mapping
- Shadowing
- Journey mapping
- Diary studies

### Phase 2: Define

- Problem framing
- How Might We questions
- Point of View statements
- Affinity clustering
- Jobs to be Done

### Phase 3: Ideate

- Brainstorming
- Crazy 8s
- SCAMPER
- Provotype Sketching
- Analogous Inspiration

### Phase 4: Prototype

- Paper prototyping
- Role playing
- Wizard of Oz
- Storyboarding
- Physical mockups

### Phase 5: Test

- Usability testing
- Feedback capture
- A/B testing
- Assumption testing
- Iteration

**How to use:**

```
Load Maya (Design Thinking Maestro)
*design-thinking-session

Maya selects 3-5 methods per phase based on your context
```

**Outputs:** Design challenge, user insights, POV statement, HMW questions, prototypes, testing insights

---

## 3. Problem-Solving Workflow (CIS)

**Location:** `src/modules/cis/workflows/problem-solving/`

**What it is:** Systematic diagnostic methodology with 31 methods across 9 steps

**9-Step Process:**

### Step 1: Define Problem

- Problem Refinement
- Stakeholder Analysis
- Scope Definition

### Step 2: Diagnose

- Is/Is Not Analysis
- Timeline Analysis
- Problem Boundaries

### Step 3: Root Cause Analysis

- Five Whys
- Fishbone Diagram
- Systems Thinking
- Failure Mode Analysis

### Step 4: Force Field Analysis

- Driving Forces
- Restraining Forces
- Constraint Identification

### Step 5: Solution Generation

- TRIZ (40 Inventive Principles)
- Lateral Thinking
- Morphological Analysis
- Biomimicry
- Synectics

### Step 6: Evaluation

- Decision Matrix
- Cost-Benefit Analysis
- Risk Assessment
- Feasibility Analysis

### Step 7: Implementation Planning

- PDCA Cycle
- Gantt Charts
- Stakeholder Mapping
- Change Management

### Step 8: Monitoring & Validation

- Metrics Definition
- Validation Plans
- Risk Mitigation

### Step 9: Lessons Learned

- Process Reflection
- Knowledge Capture

**How to use:**

```
Load Dr. Quinn (Creative Problem Solver)
*problem-solving

Dr. Quinn guides you through all 9 steps
```

**Outputs:** Problem statement, root causes, system dynamics, solution options, evaluation matrix, implementation plan

---

## 4. Innovation Strategy Workflow (CIS)

**Location:** `src/modules/cis/workflows/innovation-strategy/`

**What it is:** Strategic business model analysis with 31 frameworks across 9 steps

**31 Frameworks in 6 Categories:**

### Disruption Frameworks (5)

- Disruptive Innovation Theory
- Jobs to be Done
- Blue Ocean Strategy
- Crossing the Chasm
- Platform Revolution

### Business Model Frameworks (5)

- Business Model Canvas
- Value Proposition Canvas
- Business Model Patterns
- Revenue Model Innovation
- Cost Innovation

### Market Analysis Frameworks (5)

- TAM SAM SOM
- Porter's Five Forces
- PESTLE Analysis
- Market Timing
- Competitive Positioning

### Strategic Frameworks (5)

- Three Horizons
- Lean Startup
- Innovation Ambition Matrix
- Strategic Intent
- Scenario Planning

### Value Chain Frameworks (5)

- Value Chain Analysis
- Unbundling
- Platform Design
- Make vs Buy
- Partnership Strategy

### Technology Frameworks (5)

- Technology Adoption Lifecycle
- S-Curve Analysis
- Tech Roadmapping
- Open Innovation
- Digital Transformation

**How to use:**

```
Load Victor (Innovation Oracle)
*innovation-strategy

Victor conducts strategic analysis and provides 3 options
```

**Outputs:** Market landscape, competitive dynamics, disruption vectors, 3 strategic options, recommended strategy, 3-phase roadmap

---

## 5. Storytelling Workflow (CIS)

**Location:** `src/modules/cis/workflows/storytelling/`

**What it is:** Narrative development with 25 story frameworks across 5 categories

**25 Story Frameworks:**

### Transformation Stories (5)

- Hero's Journey
- Pixar Story Spine
- Customer Journey
- Challenge Overcome
- Character Arc

### Strategic Stories (5)

- Brand Story
- Vision Narrative
- Origin Story
- Positioning Story
- Culture Story

### Persuasive Stories (5)

- Pitch Narrative
- Sales Story
- Change Story
- Fundraising Story
- Advocacy Story

### Analytical Stories (5)

- Data Storytelling
- Case Study Narrative
- Research Narrative
- Insight Story
- Process Story

### Emotional Stories (5)

- Hook-Driven Story
- Conflict Resolution
- Empathy Story
- Human Interest
- Vulnerable Story

**How to use:**

```
Load Sophia (Master Storyteller)
*storytelling

Sophia helps you craft narratives using proven frameworks
```

**Outputs:** Complete story with narrative structure, emotional arc, delivery guidance

---

## 6. Research Workflow (BMM)

**Location:** `src/modules/bmm/workflows/1-analysis/research/`

**What it is:** Adaptive research router supporting 3 specialized tracks

**3 Research Tracks:**

### Market Research

- Competitive landscape
- Customer segmentation
- Market sizing
- Trend analysis

### Technical Research

- Architecture evaluation
- Technology selection
- Feasibility assessment
- Performance benchmarking

### Deep Prompt Research

- Comprehensive analysis
- Multi-source synthesis
- Critical evaluation

**Features:**

- Web research enabled
- Citation tracking (minimum 2 sources)
- Fact-checking
- Source URL tracking

**How to use:**

```
Load Analyst
*research

Analyst routes to appropriate research type
```

**Outputs:** Research report with citations, key findings, recommendations

---

## 7. Retrospective Workflow (BMM)

**Location:** `src/modules/bmm/workflows/4-implementation/retrospective/`

**What it is:** Epic completion review with party-mode facilitation

**12-Step Process:**

1. Epic Discovery
2. Deep Story Analysis
3. Previous Epic Integration
4. Next Epic Preview
5. Retrospective Initialization
6. Epic Review Discussion (What went well/challenges/patterns)
7. Next Epic Preparation
8. Action Items (SMART with owners)
9. Significant Change Detection
10. Critical Readiness Exploration
11. Retrospective Closure
12. Documentation & Update

**Key Features:**

- Uses Party-Mode format with multiple agents
- Psychological safety protocols
- Previous retrospective continuity
- Change detection system
- Readiness verification

**How to use:**

```
Load Bob (Scrum Master)
*retrospective

Multi-agent discussion facilitated by Bob
```

**Outputs:** Retrospective report, action items, preparation tasks, readiness assessment

---

## 8. Party-Mode Workflow (Core)

**Location:** `src/core/workflows/party-mode/`

**What it is:** Multi-agent group discussion with all installed agents

**Structure:**

1. Load agent manifest (all agents)
2. Initialize party mode
3. Orchestrate discussion:
   - Select 2-3 relevant agents per response
   - Generate in-character responses
   - Enable natural cross-talk
   - Handle questions
4. Exit with farewells

**Key Features:**

- Personality preservation
- Natural disagreement
- Emotional authenticity
- Optional TTS (AgentVibes)

**How to use:**

```
Load any agent
*party-mode

All agents join the discussion
```

**Outputs:** Group discussion transcript

---

# PART II: PROPOSED MULTI-AGENT FRAMEWORKS

The following frameworks enhance BMad's existing ecosystem with multi-agent structured analysis:

---

## 1. Six Thinking Hats Framework

### Overview

Edward de Bono's Six Thinking Hats method assigns each agent a specific thinking mode (hat color). Agents contribute only from their hat's perspective, enabling comprehensive analysis without conflict.

### Implementation Design

**File Structure:**

```
src/core/workflows/six-hats/
├── workflow.yaml
├── instructions.md
├── template.md (optional - analysis output)
└── hat-assignments.yaml
```

**workflow.yaml:**

```yaml
name: 'six-hats'
description: 'Six Thinking Hats framework - structured multi-perspective analysis'
author: 'BMad'

agent_manifest: '{project-root}/{bmad_folder}/_cfg/agent-manifest.csv'
hat_assignments: '{project-root}/{bmad_folder}/core/workflows/six-hats/hat-assignments.yaml'

template: true
output_path: '{project-root}/{bmad_folder}/_output/six-hats-analysis-{timestamp}.md'
instructions: '{project-root}/{bmad_folder}/core/workflows/six-hats/instructions.md'

# Framework configuration
rounds: 2 # How many complete hat rotations
round_duration: '2-3 agents per hat'
synthesis: true # Final synthesis round

exit_triggers:
  - '*exit'
  - '*complete'

standalone: true
```

**hat-assignments.yaml:**

```yaml
# Six Thinking Hats - Agent Role Mapping
# Dynamically assigns agents to hats based on their expertise

hats:
  white:
    name: 'White Hat - Facts & Data'
    focus: 'Objective information, data, facts, figures'
    agent_criteria:
      - analyst
      - architect
      - tea # Test Engineer Architect
    fallback: [dev, pm]

  red:
    name: 'Red Hat - Emotions & Intuition'
    focus: 'Gut feelings, intuition, emotional reactions'
    agent_criteria:
      - ux-designer
      - creative-problem-solver
      - storyteller
    fallback: [pm, sm]

  black:
    name: 'Black Hat - Critical Judgment'
    focus: 'Risks, problems, why it might fail'
    agent_criteria:
      - tea
      - architect
      - sm # Scrum Master knows risks
    fallback: [dev, analyst]

  yellow:
    name: 'Yellow Hat - Optimism & Benefits'
    focus: 'Positives, benefits, why it will work'
    agent_criteria:
      - pm
      - innovation-strategist
      - sm
    fallback: [analyst, architect]

  green:
    name: 'Green Hat - Creativity & Alternatives'
    focus: 'New ideas, possibilities, alternatives'
    agent_criteria:
      - innovation-strategist
      - brainstorming-coach
      - creative-problem-solver
    fallback: [architect, ux-designer]

  blue:
    name: 'Blue Hat - Process Control'
    focus: 'Orchestration, synthesis, next steps'
    agent_criteria:
      - bmad-master
      - sm
    fallback: [pm, architect]

# Hat rotation sequence (can be customized)
sequence:
  - blue # Opening - define problem
  - white # Gather facts
  - red # Initial reactions
  - black # Identify risks
  - yellow # Find benefits
  - green # Generate alternatives
  - blue # Synthesis & decision
```

**instructions.md:**

```markdown
# Six Thinking Hats - Multi-Agent Analysis

<critical>This workflow orchestrates six rounds of focused thinking using de Bono's Six Hats method</critical>
<critical>Each agent wears ONE hat per round and contributes ONLY from that perspective</critical>

<workflow>

<step n="1" goal="Initialize Six Hats Session">
  <action>Load agent manifest from {{agent_manifest}}</action>
  <action>Load hat assignments from {{hat_assignments}}</action>
  <action>Prompt user for analysis topic/problem</action>

  <format>
    🎩 SIX THINKING HATS ANALYSIS 🎩

    We'll analyze your topic from six distinct perspectives.
    Each agent will "wear" a specific thinking hat and contribute only from that viewpoint.

    What would you like to analyze?

  </format>

<action>Capture user's topic</action>
<action>Initialize analysis document with topic and timestamp</action>
</step>

<step n="2" goal="Assign Agents to Hats">
  <action>For each hat in sequence:</action>
  <substep n="2a">
    <action>Find agents matching hat's criteria from agent_manifest</action>
    <action>Select 2-3 best-matching agents based on role/identity</action>
    <action>If no match, use fallback agents</action>
    <action>Store assignments for this round</action>
  </substep>

<action>Display hat assignments to user:</action>
<format>
Hat Assignments:
🤍 White (Facts): Winston, Murat
❤️ Red (Emotions): Sally, Carson
🖤 Black (Risks): Murat, Bob
💛 Yellow (Benefits): John, Innovation Strategist
💚 Green (Creativity): Carson, Innovation Strategist
💙 Blue (Process): BMad Master, Bob
</format>
</step>

<step n="3" goal="Execute Hat Rounds" repeat="for-each-hat">
  <action>For each hat in sequence:</action>

  <substep n="3a" goal="Announce Hat Round">
    <format>
      ═══════════════════════════════════════
      {{hat.color}} {{hat.name}}
      Focus: {{hat.focus}}
      ═══════════════════════════════════════
    </format>
  </substep>

  <substep n="3b" goal="Agent Contributions">
    <action>For each agent assigned to this hat:</action>

    <constraint>Agent MUST contribute ONLY from hat's perspective</constraint>
    <constraint>NO mixing of perspectives (e.g., no risks while wearing Yellow Hat)</constraint>
    <constraint>Use agent's communication style but filtered through hat lens</constraint>

    <format>
      [Icon] [Agent Name] (wearing {{hat.color}} hat):
      [Their contribution strictly from hat's focus]

      [Next Agent] (wearing {{hat.color}} hat):
      [Their contribution from same perspective]
    </format>

    <example>
      🤍 WHITE HAT - Facts & Data

      🏗️ Winston (wearing White Hat):
      "Current system handles 1,000 requests/second. Database size: 500GB. Average response time: 120ms. Tech stack: Node.js, PostgreSQL, Redis."

      🧪 Murat (wearing White Hat):
      "Test coverage: 73%. P95 latency: 250ms. 12 known bugs in backlog. Last security audit: 3 months ago. Uptime: 99.2%."
    </example>

  </substep>

  <substep n="3c" goal="Capture Round Insights">
    <action>After all agents contribute, pause briefly</action>
    <action>Ask user: "Any questions about this perspective before we move to the next hat?"</action>
    <action>Allow brief clarifications (still from hat perspective only)</action>
    <action>Document insights in analysis template</action>
  </substep>
</step>

<step n="4" goal="Blue Hat Synthesis">
  <action>Blue Hat agents (BMad Master, SM) lead synthesis:</action>

  <format>
    ═══════════════════════════════════════
    💙 BLUE HAT - Synthesis & Decision
    ═══════════════════════════════════════

    🧙 BMad Master (wearing Blue Hat):
    "Let me synthesize what we've learned..."

    [Summary of key insights from each hat]

    White Hat revealed: [facts summary]
    Red Hat reactions: [emotional landscape]
    Black Hat concerns: [risk list]
    Yellow Hat benefits: [opportunity list]
    Green Hat ideas: [alternative approaches]

    Recommended path forward:
    [Synthesis based on all perspectives]

  </format>

<action>Present synthesis to user</action>
<action>Ask: "Would you like to do another round focusing on specific hats, or conclude?"</action>
</step>

<step n="5" goal="Optional Second Round">
  <check if="user requests deeper dive">
    <action>Ask which hats to revisit</action>
    <action>Run those hat rounds again with same or different agents</action>
    <action>Update synthesis</action>
  </check>

  <check if="user is satisfied">
    <goto step="6">Finalize Analysis</goto>
  </check>
</step>

<step n="6" goal="Finalize Analysis">
  <action>Generate complete analysis document using template.md</action>
  <action>Include all hat perspectives</action>
  <action>Include Blue Hat synthesis</action>
  <action>Include recommended actions</action>
  <action>Save to {{output_path}}</action>

  <format>
    ✅ Six Hats Analysis Complete!

    Analysis saved to: {{output_path}}

    Summary:
    - {{count}} perspectives explored
    - {{count}} risks identified (Black Hat)
    - {{count}} benefits identified (Yellow Hat)
    - {{count}} alternatives generated (Green Hat)

    Next steps: [from Blue Hat synthesis]

  </format>
</step>

</workflow>

## Critical Constraints

<constraints>
  <constraint>Agents MUST NOT break character from their assigned hat</constraint>
  <constraint>No agent can contribute from multiple perspectives in same round</constraint>
  <constraint>If agent tries to mix hats, Blue Hat gently redirects</constraint>
  <constraint>Each hat round is complete before moving to next</constraint>
  <constraint>User can interrupt to ask clarifying questions</constraint>
</constraints>

## Hat Switching Protocol

<hat-switching>
  <rule>When hat changes, agents COMPLETELY shift perspective</rule>
  <rule>Same agent can wear different hats in different rounds</rule>
  <rule>Example: Winston wearing Black Hat focuses ONLY on risks, NOT architecture benefits</rule>
  <rule>Example: Winston wearing Yellow Hat focuses ONLY on benefits, NOT technical concerns</rule>
</hat-switching>

## Example Dialogue Flow

<example-flow>
Topic: "Should we migrate from monolith to microservices?"

🤍 WHITE HAT - Facts
Winston: "Current monolith: 200K LOC, 8 developers, deploys take 30 minutes."
Murat: "P95 latency 450ms, 15 services would be needed based on domain analysis."

❤️ RED HAT - Emotions
Sally: "The team feels constrained. Every deploy creates anxiety."
Carson: "Gut says this is the right time - momentum is building."

🖤 BLACK HAT - Risks
Murat: "Distributed tracing will be complex. Network failures become app failures."
Bob: "Team has no k8s experience. 6-month learning curve minimum."

💛 YELLOW HAT - Benefits
John: "Faster deploys mean faster customer value delivery."
Innovation Strategist: "Independent scaling saves 40% infrastructure cost."

💚 GREEN HAT - Alternatives
Carson: "What about modular monolith first? Get benefits with less risk."
Innovation Strategist: "Strangler fig pattern - migrate one service at a time."

💙 BLUE HAT - Synthesis
BMad Master: "Green Hat's strangler pattern addresses Black Hat's risks while achieving Yellow Hat's benefits. White Hat data supports feasibility. Red Hat confirms team readiness. Recommendation: Pilot with one service."
</example-flow>
```

---

## 2. Five Whys Framework

### Overview

Iterative root cause analysis where agents ask "why" five times to drill down to fundamental causes.

### Implementation Design

**File Structure:**

```
src/core/workflows/five-whys/
├── workflow.yaml
├── instructions.md
└── template.md
```

**workflow.yaml:**

```yaml
name: 'five-whys'
description: 'Five Whys root cause analysis with multi-agent investigation'
author: 'BMad'

agent_manifest: '{project-root}/{bmad_folder}/_cfg/agent-manifest.csv'

template: true
output_path: '{project-root}/{bmad_folder}/_output/five-whys-{timestamp}.md'
instructions: '{project-root}/{bmad_folder}/core/workflows/five-whys/instructions.md'

# Framework configuration
max_depth: 5 # Standard 5 Whys
min_depth: 3 # Minimum before synthesis
allow_branches: true # Multiple root causes

# Agent role preferences
investigator_agents:
  - analyst
  - architect
  - tea
facilitator_agents:
  - sm
  - bmad-master
challenger_agents:
  - dev
  - pm

standalone: true
```

**instructions.md:**

```markdown
# Five Whys - Multi-Agent Root Cause Analysis

<critical>Iteratively ask "why" to drill from symptom to root cause</critical>
<critical>Agents collaborate to challenge assumptions and find true underlying issues</critical>

<workflow>

<step n="1" goal="Define Problem Statement">
  <action>Prompt user to state the problem symptom</action>

  <format>
    🔍 FIVE WHYS ROOT CAUSE ANALYSIS 🔍

    We'll investigate the root cause by asking "why" five times.
    Multiple agents will challenge assumptions and explore alternatives.

    What problem are you investigating?

  </format>

<action>Capture initial problem statement</action>
<action>Have SM or BMad Master rephrase for clarity</action>
<action>Confirm with user</action>
</step>

<step n="2" goal="Initialize Investigation">
  <action>Select 3-4 investigator agents (Analyst, Architect, TEA, DEV)</action>
  <action>Select 1 facilitator (SM or BMad Master)</action>

  <format>
    Investigation Team:
    🔬 Lead Investigator: {{analyst.name}}
    🏗️ Systems Expert: {{architect.name}}
    🧪 Quality Expert: {{tea.name}}
    📋 Facilitator: {{sm.name}}

    Problem Statement: {{problem}}

    Let's begin...

  </format>
</step>

<step n="3" goal="Why Loop" repeat="5 times or until root cause found">
  <substep n="3a" goal="Ask Why - Round {{n}}">
    <format>
      ═══════════════════════════════════════
      WHY #{{n}}: {{current_answer}}
      ═══════════════════════════════════════
    </format>

    <action>Facilitator asks: "Why does this happen?"</action>
    <action>2-3 investigator agents propose different reasons:</action>

    <format>
      🔬 {{analyst.name}}:
      "Hypothesis: {{their reasoning based on data/patterns}}"

      🏗️ {{architect.name}}:
      "Alternative view: {{their systems-level explanation}}"

      🧪 {{tea.name}}:
      "From testing perspective: {{their quality-focused cause}}"
    </format>

  </substep>

  <substep n="3b" goal="Challenge and Validate">
    <action>Other agents challenge each hypothesis:</action>

    <format>
      💻 {{dev.name}}:
      "{{analyst.name}}, but what about {{counterpoint}}?"

      🔬 {{analyst.name}}:
      "Good catch. That suggests {{refined hypothesis}}"
    </format>

    <action>Facilitator synthesizes: "So the most likely reason is: {{consensus}}"</action>
    <action>Ask user: "Does this match your understanding?"</action>
    <action>Allow user to redirect or confirm</action>

  </substep>

  <substep n="3c" goal="Detect Branches">
    <check if="multiple valid root causes emerge">
      <action>Facilitator: "I'm seeing two paths here:"</action>
      <format>
        Path A: {{cause_a}}
        Path B: {{cause_b}}

        Should we explore both, or focus on one?
      </format>

      <action>If user chooses both, fork investigation</action>
      <action>Track separate Why chains for each path</action>
    </check>

  </substep>

  <substep n="3d" goal="Check for Root Cause">
    <check if="answer is actionable and fundamental">
      <action>Facilitator: "This feels like a root cause because:"</action>
      <checklist>
        - It's within our control to fix
        - Fixing this would prevent the symptom
        - Going deeper becomes philosophical/organizational
        - Team consensus this is actionable
      </checklist>

      <check if="consensus is YES">
        <goto step="4">Synthesize Findings</goto>
      </check>
      <check if="consensus is NO">
        <action>Continue to next Why round</action>
      </check>
    </check>

  </substep>
</step>

<step n="4" goal="Synthesize Findings">
  <action>Facilitator leads synthesis with all agents contributing:</action>

  <format>
    ═══════════════════════════════════════
    ROOT CAUSE ANALYSIS COMPLETE
    ═══════════════════════════════════════

    Problem: {{initial_problem}}

    Why Chain:
    1. {{problem}} → WHY?
    2. {{answer_1}} → WHY?
    3. {{answer_2}} → WHY?
    4. {{answer_3}} → WHY?
    5. {{answer_4}} → WHY?

    ROOT CAUSE: {{root_cause}}

    {{#if branches}}
    Alternative Root Causes:
    - Path A: {{root_cause_a}}
    - Path B: {{root_cause_b}}
    {{/if}}

  </format>

<action>Agents propose solutions:</action>

  <format>
    Proposed Solutions:

    🏗️ {{architect.name}}:
    "{{architectural solution}}"

    💻 {{dev.name}}:
    "{{implementation approach}}"

    📋 {{pm.name}}:
    "{{product strategy}}"

  </format>
</step>

<step n="5" goal="Action Items">
  <action>SM facilitates action item creation:</action>

  <format>
    Next Steps:
    1. {{action_1}} - Owner: {{owner}} - Timeline: {{timeline}}
    2. {{action_2}} - Owner: {{owner}} - Timeline: {{timeline}}
    3. {{action_3}} - Owner: {{owner}} - Timeline: {{timeline}}

    Success Metrics:
    - {{metric_1}}
    - {{metric_2}}

  </format>

<action>Save analysis to {{output_path}}</action>
<action>Confirm user has what they need</action>
</step>

</workflow>

## Example Five Whys Session

<example>
Problem: "Production deployments are failing 40% of the time"

WHY #1: Why are deployments failing?
🔬 Analyst: "Database migrations fail during deploy."
🏗️ Architect: "Health checks timeout before app is ready."
📋 Facilitator: "Consensus: Health checks timing out."

WHY #2: Why do health checks timeout?
🧪 TEA: "App takes 90 seconds to warm up, health check times out at 60s."
💻 Dev: "Also seeing connection pool initialization delays."
📋 Facilitator: "Root: Slow application startup."

WHY #3: Why is app startup slow?
��️ Architect: "Loading 500MB of config on startup from S3."
💻 Dev: "Plus establishing 50 database connections upfront."
📋 Facilitator: "Two causes: config loading + connection pooling."

BRANCH DETECTED:
Path A: Config loading
Path B: Connection pooling

WHY #4a: Why load all config on startup?
🔬 Analyst: "Original design decision - simpler than lazy loading."
💻 Dev: "No one ever questioned it as system grew."
📋 Facilitator: "ROOT CAUSE A: No config caching strategy."

WHY #4b: Why establish all connections upfront?
🧪 TEA: "Framework default - we never tuned it."
🏗️ Architect: "Connection pool minimum set to 50 from day one."
📋 Facilitator: "ROOT CAUSE B: Untuned connection pool."

SYNTHESIS:
Root Causes:

1. No config caching (load 500MB on every deploy)
2. Oversized connection pool (50 connections on startup)

Solutions:
🏗️ Architect: "Implement config service with local cache. Lazy-load connections."
💻 Dev: "Tune pool: min=5, max=50, acquire on demand."
📋 PM: "Priority this for next sprint - 40% failure rate is unacceptable."
</example>
```

---

## 3. First Principles Framework

### Overview

Deconstruct problem to fundamental truths, question all assumptions, rebuild solution from scratch.

### Implementation Design

**File Structure:**

```
src/core/workflows/first-principles/
├── workflow.yaml
├── instructions.md
└── template.md
```

**workflow.yaml:**

```yaml
name: 'first-principles'
description: 'First Principles thinking - deconstruct to fundamental truths and rebuild'
author: 'BMad'

agent_manifest: '{project-root}/{bmad_folder}/_cfg/agent-manifest.csv'

template: true
output_path: '{project-root}/{bmad_folder}/_output/first-principles-{timestamp}.md'
instructions: '{project-root}/{bmad_folder}/core/workflows/first-principles/instructions.md'

# Framework phases
phases:
  - deconstruct # Break down to fundamentals
  - challenge # Question all assumptions
  - reconstruct # Rebuild from truths

# Agent role preferences
challenger_agents:
  - analyst
  - architect
  - innovation-strategist
builder_agents:
  - architect
  - dev
  - creative-problem-solver
validator_agents:
  - tea
  - pm

standalone: true
```

**instructions.md:**

```markdown
# First Principles - Multi-Agent Fundamental Analysis

<critical>Strip away assumptions, identify fundamental truths, rebuild from scratch</critical>
<critical>Agents aggressively challenge "because we've always done it this way"</critical>

<workflow>

<step n="1" goal="State the Problem">
  <format>
    🔬 FIRST PRINCIPLES ANALYSIS 🔬

    We'll break down your problem to fundamental truths,
    challenge every assumption, and rebuild the solution from scratch.

    This is Elon Musk-style thinking: question everything.

    What problem or decision are you analyzing?

  </format>

<action>Capture problem statement</action>
<action>Capture current approach (if any)</action>
</step>

<step n="2" goal="Deconstruct to Fundamentals">
  <action>Analyst and Architect lead deconstruction:</action>

  <format>
    ═══════════════════════════════════════
    PHASE 1: DECONSTRUCTION
    ═══════════════════════════════════════

    🔬 {{analyst.name}}:
    "Let's break this down. What are we REALLY trying to achieve?"

    {{user_answer}}

    🏗️ {{architect.name}}:
    "Forget the current solution. What are the fundamental components?"

  </format>

<action>Agents collaboratively identify:</action>
<checklist> - What is the true goal? (Not how, but what) - What are the physics/logic constraints? - What are the immutable truths? - What are we taking for granted?
</checklist>

  <format>
    Fundamental Truths Identified:
    1. {{truth_1}} (physics/logic/economics)
    2. {{truth_2}} (customer need/market reality)
    3. {{truth_3}} (resource constraint)
  </format>
</step>

<step n="3" goal="Challenge All Assumptions">
  <action>Innovation Strategist leads assumption challenge:</action>

  <format>
    ═══════════════════════════════════════
    PHASE 2: ASSUMPTION CHALLENGE
    ═══════════════════════════════════════

    💡 {{innovation_strategist.name}}:
    "Now let's challenge EVERY assumption about the current approach."

  </format>

  <substep n="3a" goal="List Assumptions">
    <action>Agents identify hidden assumptions in current/proposed approach:</action>

    <format>
      Assumptions Found:

      🏗️ {{architect.name}}:
      "Assumption: We need a database."
      "Is this true? Or just how we've always done it?"

      💻 {{dev.name}}:
      "Assumption: Users need instant results."
      "What if async is actually better UX?"

      💡 {{innovation_strategist.name}}:
      "Assumption: We must build this ourselves."
      "Why not compose existing solutions?"
    </format>

  </substep>

  <substep n="3b" goal="Validate Each Assumption">
    <action>For each assumption, ask: "Is this a fundamental truth or inherited wisdom?"</action>

    <format>
      Assumption: {{assumption}}

      🔬 {{analyst.name}}: "Challenge: {{counter_evidence}}"
      🏗️ {{architect.name}}: "Alternative: {{different_approach}}"

      VERDICT: [FUNDAMENTAL TRUTH] or [QUESTIONABLE ASSUMPTION]
    </format>

  </substep>

<action>Compile list of:</action>
<checklist> - ✅ Fundamental Truths (keep these) - ❌ Questionable Assumptions (discard these) - ⚠️ Constraints to Validate (research these)
</checklist>
</step>

<step n="4" goal="Reconstruct from First Principles">
  <action>Architect and Creative Problem Solver lead rebuild:</action>

  <format>
    ═══════════════════════════════════════
    PHASE 3: RECONSTRUCTION
    ═══════════════════════════════════════

    🏗️ {{architect.name}}:
    "If we started fresh, knowing only our fundamental truths, how would we solve this?"

    Fundamental Truths (our constraints):
    {{#each truths}}
    - {{this}}
    {{/each}}

    Everything else is negotiable.

  </format>

<action>Agents brainstorm radically different approaches:</action>

  <format>
    🎨 {{creative_problem_solver.name}}:
    "Crazy idea: {{unconventional_approach}}"

    🏗️ {{architect.name}}:
    "Actually... that respects our truths and ignores false assumptions. Viable."

    💡 {{innovation_strategist.name}}:
    "Building on that: {{refined_approach}}"

  </format>

<action>Develop 2-3 first-principles solutions</action>
<action>Each solution must ONLY depend on fundamental truths</action>
<action>Each solution ignores "how we've always done it"</action>
</step>

<step n="5" goal="Validate Against Reality">
  <action>PM and TEA validate solutions against real-world constraints:</action>

  <format>
    ═══════════════════════════════════════
    VALIDATION
    ═══════════════════════════════════════

    📋 {{pm.name}}:
    "Solution A: {{solution_a}}"
    "Market validation: {{customer_perspective}}"
    "Business viability: {{economic_analysis}}"

    🧪 {{tea.name}}:
    "Technical feasibility: {{engineering_assessment}}"
    "Risk profile: {{risk_analysis}}"

  </format>

<action>Rank solutions by:</action>
<checklist> - How many assumptions eliminated? - Simplicity (fewer moving parts = better) - Cost (first principles often cheaper) - Novelty (different from status quo) - Viability (can we actually build this)
</checklist>
</step>

<step n="6" goal="Synthesis and Recommendation">
  <action>BMad Master synthesizes findings:</action>

  <format>
    ═══════════════════════════════════════
    FIRST PRINCIPLES ANALYSIS COMPLETE
    ═══════════════════════════════════════

    Original Problem: {{problem}}
    Current Approach: {{current_approach}}

    Fundamental Truths:
    {{#each truths}}
    ✅ {{this}}
    {{/each}}

    Discarded Assumptions:
    {{#each assumptions}}
    ❌ {{this}} → Replaced with: {{alternative}}
    {{/each}}

    First Principles Solutions:

    OPTION 1: {{solution_1}}
    - Assumptions eliminated: {{count}}
    - Simplicity: {{rating}}
    - Cost: {{estimate}}
    - Feasibility: {{assessment}}

    OPTION 2: {{solution_2}}
    - Assumptions eliminated: {{count}}
    - Simplicity: {{rating}}
    - Cost: {{estimate}}
    - Feasibility: {{assessment}}

    RECOMMENDED: {{recommendation}}
    RATIONALE: {{reasoning}}

  </format>

<action>Save analysis to {{output_path}}</action>
</step>

</workflow>

## Example First Principles Session

<example>
Problem: "We need to add search functionality to our app"
Current Approach: "Install Elasticsearch, set up cluster, index data"

DECONSTRUCTION:
🔬 Analyst: "What's the fundamental goal?"
User: "Let users find relevant items quickly."
🏗️ Architect: "Fundamental truths:

1. Users type queries
2. We match queries to items
3. We return ranked results
   That's it. Everything else is implementation detail."

CHALLENGE ASSUMPTIONS:
💡 Innovation Strategist: "Assumption: We need a search engine."
🔬 Analyst: "Wait - what if we just use PostgreSQL full-text search?"
💻 Dev: "Assumption: Search must be instant."
📋 PM: "Actually, users are fine with 200ms. We're over-optimizing."
🏗️ Architect: "Assumption: We index everything."
💡 Innovation Strategist: "What if we only index what users actually search for?"

FUNDAMENTAL TRUTHS:
✅ Users need to find items by keywords
✅ Results should be relevance-ranked
✅ Sub-200ms response time is acceptable
✅ We have 100K items, growing 10%/year

DISCARDED ASSUMPTIONS:
❌ "Need Elasticsearch" → False. Postgres can handle 100K items.
❌ "Must index everything" → False. Selective indexing is smarter.
❌ "Real-time indexing" → False. Batch indexing nightly is fine.
❌ "Complex relevance algorithm" → False. tf-idf is good enough.

FIRST PRINCIPLES SOLUTION:
🏗️ Architect: "Use Postgres full-text search with GIN index. Batch index nightly. Add query analytics to refine later."

💻 Dev: "Cost: $0 (using existing DB). Complexity: Low. Maintenance: Minimal."

🧪 TEA: "Performance: 50ms avg on 100K items. Scales to 1M before we need to revisit."

📋 PM: "This ships in 1 week vs 6 weeks for Elasticsearch. Let's validate with users first."

RECOMMENDATION: Use Postgres full-text search.
RATIONALE: Respects all fundamental truths, eliminates all questionable assumptions, 6x faster to ship, $0 cost, 10x simpler.
</example>

## Critical Guidelines

<guidelines>
  <guideline>Be ruthless about challenging "best practices" - they're often cargo cult</guideline>
  <guideline>Physics/logic/economics are fundamental. Everything else is negotiable.</guideline>
  <guideline>Simpler solutions built on fewer assumptions are usually better</guideline>
  <guideline>User needs are fundamental. Implementation preferences are not.</guideline>
  <guideline>If you can't explain WHY something is necessary from first principles, discard it</guideline>
</guidelines>
```

---

## 4. Implementation Roadmap

### Phase 1: Core Framework (Week 1-2)

- [ ] Create workflow structure for Six Hats
- [ ] Implement hat assignment logic
- [ ] Test with BMM agents
- [ ] Add TTS support for hat transitions

### Phase 2: Investigation Tools (Week 3-4)

- [ ] Build Five Whys workflow
- [ ] Add branching logic for multiple root causes
- [ ] Test with real bug investigation

### Phase 3: Innovation Framework (Week 5-6)

- [ ] Implement First Principles workflow
- [ ] Create assumption challenge mechanics
- [ ] Test with architectural decisions

### Phase 4: Integration (Week 7)

- [ ] Add to BMad Master menu
- [ ] Create web bundles
- [ ] Write documentation
- [ ] User testing

---

## 5. Agent Manifest Enhancements

To support analytical frameworks, enhance agent-manifest.csv:

```csv
name,displayName,title,icon,role,identity,communicationStyle,principles,module,path,analyticalStrengths
pm,John,Product Manager,📋,...,...,...,...,bmm,/agents/pm.md,"yellow-hat,facilitator"
architect,Winston,Architect,🏗️,...,...,...,...,bmm,/agents/architect.md,"white-hat,first-principles,systems-thinking"
analyst,Sarah,Business Analyst,🔬,...,...,...,...,bmm,/agents/analyst.md,"white-hat,five-whys,data-driven"
```

Add new field: **analyticalStrengths** (comma-separated tags)

---

## 6. Benefits of This Approach

### Six Hats

- **Reduces conflict**: Agents can disagree without ego (it's just the hat)
- **Comprehensive analysis**: Forces exploration of all angles
- **Clear structure**: User knows what to expect each round
- **Multi-agent strength**: Different agents excel at different hats

### Five Whys

- **Root cause**: Gets past symptoms to real issues
- **Collaborative**: Multiple perspectives prevent groupthink
- **Branching**: Handles complex problems with multiple causes
- **Actionable**: Always ends with concrete fixes

### First Principles

- **Innovation**: Breaks free from "how we've always done it"
- **Cost reduction**: Simple solutions usually cheaper
- **Simplicity**: Fewer assumptions = fewer moving parts
- **Validation**: Forces clear thinking about what's actually necessary

---

## 7. Technical Implementation Notes

### Dynamic Agent Selection

Use agent-manifest.csv with new `analyticalStrengths` field:

```javascript
// In workflow instruction parsing
const agents = loadAgentManifest();
const whiteHatAgents = agents.filter(
  (a) => a.analyticalStrengths.includes('white-hat') || a.role.includes('analyst') || a.role.includes('architect'),
);
```

### Hat Assignment Algorithm

```javascript
function assignHats(agents, hatConfig) {
  const assignments = {};

  for (const [hatColor, config] of Object.entries(hatConfig)) {
    // Find agents matching criteria
    const matches = agents.filter((a) => config.agent_criteria.some((role) => a.name.includes(role)));

    // Select top 2-3 based on role fit
    assignments[hatColor] = matches.slice(0, 3);

    // Use fallback if needed
    if (assignments[hatColor].length < 2) {
      const fallbacks = agents.filter((a) => config.fallback.some((role) => a.name.includes(role)));
      assignments[hatColor].push(...fallbacks);
    }
  }

  return assignments;
}
```

### Workflow State Management

Each framework needs to track state across rounds:

```yaml
# Internal state (not exposed to user)
workflow_state:
  current_hat: 'white'
  round: 1
  insights:
    white: ['fact 1', 'fact 2']
    red: ['emotion 1']
  synthesis: ''
```

---

# PART III: INTEGRATION & ENHANCEMENT STRATEGIES

## Framework Integration Matrix

### How Existing Frameworks Can Work Together

| Combination                            | When to Use                        | Flow                                                    | Output                              |
| -------------------------------------- | ---------------------------------- | ------------------------------------------------------- | ----------------------------------- |
| **Research → Six Hats**                | Strategic decisions requiring data | Research gathers facts → Six Hats analyzes perspectives | Informed multi-perspective analysis |
| **Brainstorming → Five Whys**          | Creative ideas need validation     | Generate ideas → Drill into feasibility                 | Validated creative concepts         |
| **Problem-Solving → First Principles** | Systemic issues                    | Root cause analysis → Challenge assumptions             | Fundamental solutions               |
| **Design Thinking → Storytelling**     | Product launches                   | Build solution → Craft narrative                        | Compelling product story            |
| **Innovation Strategy → Party-Mode**   | Strategic alignment                | Framework creates options → Team debates                | Consensus on direction              |
| **Retrospective → Problem-Solving**    | Recurring issues                   | Identify patterns → Systematic fix                      | Lasting improvements                |

### Workflow Chaining Examples

#### Example 1: Complete Product Discovery

```
1. Innovation Strategy (Victor) → Identifies market opportunity
2. Design Thinking (Maya) → Validates with users, creates prototype
3. Research (Analyst) → Validates market assumptions
4. Six Hats (Multi-agent) → Comprehensive go/no-go decision
5. Storytelling (Sophia) → Crafts launch narrative
```

#### Example 2: Complex Bug Investigation

```
1. Problem-Solving (Dr. Quinn) → Diagnose and scope issue
2. Five Whys (Multi-agent) → Find root cause
3. First Principles (Multi-agent) → Question current architecture
4. Brainstorming (Carson) → Generate fix alternatives
5. Research (Analyst) → Validate technical approaches
```

#### Example 3: Strategic Pivot

```
1. Retrospective (Bob) → Why current strategy isn't working
2. Research (Analyst) → Market/competitor analysis
3. Innovation Strategy (Victor) → Generate 3 strategic options
4. Six Hats (Multi-agent) → Evaluate each option
5. Party-Mode → Full team alignment discussion
```

---

## Enhancement Opportunities for Existing Frameworks

### 1. Add Multi-Agent Mode to Single-Agent Workflows

**Current State:** Most CIS workflows are single-agent facilitated
**Enhancement:** Add optional multi-agent mode for richer perspectives

#### Example: Design Thinking with Multi-Agent

```yaml
# In design-thinking/workflow.yaml
mode:
  - solo # Current: Maya facilitates alone
  - multi-agent # New: Maya + PM + Dev + UX discuss each phase

multi_agent_config:
  empathize:
    agents: [ux-designer, pm, analyst]
    format: 'party-mode'
  ideate:
    agents: [creative-problem-solver, innovation-strategist, architect]
    format: 'brainstorming'
```

**Benefits:**

- PM brings business perspective to empathy phase
- Dev brings technical feasibility to ideate phase
- Richer insights from diverse viewpoints

### 2. Add Framework Templates to Party-Mode

**Current State:** Party-mode is freeform discussion
**Enhancement:** Add optional structure templates

```yaml
# In party-mode/workflow.yaml
discussion_templates:
  - freeform # Current default
  - six-hats # Structured hat rotation
  - swot # Strengths/Weaknesses/Opportunities/Threats
  - pros-cons # Debate format
  - round-robin # Each agent speaks in turn
```

**Usage:**

```
*party-mode --template=six-hats
```

### 3. Create Framework Recommendation Engine

**Concept:** Agent that suggests which framework(s) to use based on user's problem

```markdown
Load BMad Master
\*recommend-framework

BMad Master: "Tell me about your challenge..."

User: "We need to decide whether to rebuild our monolith as microservices"

BMad Master: "I recommend this sequence:

1. First Principles (2 hours) - Challenge the assumption you need to change
2. If change confirmed: Six Hats (1 hour) - Multi-perspective analysis
3. Innovation Strategy (3 hours) - Evaluate alternative architectures
4. Party-Mode - Final team alignment"
```

### 4. Add Agent Specialization Tags

**Enhancement:** Tag agents with framework strengths in manifest

```csv
# agent-manifest.csv (enhanced)
name,displayName,title,icon,...,frameworkStrengths
architect,Winston,Architect,🏗️,...,"six-hats:white,first-principles,five-whys"
ux-designer,Sally,UX Designer,🎨,...,"six-hats:red,design-thinking,storytelling"
pm,John,Product Manager,📋,...,"six-hats:yellow,innovation-strategy,swot"
tea,Murat,Test Architect,🧪,...,"six-hats:black,five-whys,problem-solving"
```

**Benefits:**

- Auto-assign agents to optimal framework roles
- Track agent performance per framework
- User visibility into agent expertise

### 5. Framework Completion Tracking

**Enhancement:** Track which frameworks were used for which projects

```yaml
# {bmad_folder}/_cfg/framework-history.yaml
frameworks_used:
  - timestamp: '2025-01-15T10:30:00Z'
    framework: 'innovation-strategy'
    agent: 'Victor'
    project: 'Mobile App Redesign'
    output: '{bmad_folder}/_output/innovation-strategy-2025-01-15.md'
    outcome: 'Selected Option 2: Progressive Web App'

  - timestamp: '2025-01-16T14:00:00Z'
    framework: 'five-whys'
    agents: ['Analyst', 'Architect', 'TEA']
    problem: 'Deploy failures'
    root_cause: 'Untuned connection pool'
    resolution: 'Implemented lazy loading'
```

**Benefits:**

- Historical record of decision-making
- Framework effectiveness analysis
- Searchable organizational knowledge

---

## New Framework Proposals

### 1. SWOT Analysis (Multi-Agent)

**Structure:**

- 4 agent teams assigned to each quadrant
- **Strengths team:** Architect, PM, Dev
- **Weaknesses team:** TEA, Security (if exists), SM
- **Opportunities team:** Innovation Strategist, PM, Creative Problem Solver
- **Threats team:** Analyst, Architect, Risk specialist (if exists)

**Flow:**

1. Problem/opportunity statement
2. Parallel quadrant analysis (4 teams work simultaneously)
3. Cross-quadrant synthesis
4. Strategy formulation

**Location:** `src/core/workflows/swot/`

### 2. Decision Matrix (Multi-Agent)

**Structure:**

- Agents collaboratively define criteria and weights
- Each agent scores options independently
- System calculates weighted scores
- Discussion of disagreements
- Final recommendation

**Example:**

```
Criteria (weighted by multi-agent consensus):
- Cost (25%): PM + Architect
- Time to market (30%): PM + Dev
- Technical debt (20%): Architect + TEA
- User impact (25%): UX Designer + PM

Options:
A. Rebuild from scratch
B. Incremental refactor
C. Buy SaaS solution

[Agents score each option 1-10 per criterion]
[System calculates weighted totals]
[Agents discuss score discrepancies]
```

**Location:** `src/core/workflows/decision-matrix/`

### 3. Pre-Mortem Analysis (Multi-Agent)

**Concept:** Imagine project failed, work backwards to identify risks

**Structure:**

1. Project success criteria defined
2. Time travel: "It's 6 months from now, project failed spectacularly"
3. Agents brainstorm WHY it failed (no holds barred)
4. Risk categorization
5. Mitigation planning

**Agent Roles:**

- **Black Hat agents** (TEA, Risk): Identify technical failures
- **PM agents**: Identify market/business failures
- **SM agents**: Identify process/team failures
- **Dev agents**: Identify implementation failures

**Location:** `src/core/workflows/pre-mortem/`

### 4. Assumption Testing (Multi-Agent)

**Concept:** Surface and validate critical assumptions before committing

**Structure:**

1. Agents list ALL assumptions in plan/design
2. Categorize: Must be true / Should validate / Nice to have
3. Design cheap tests for "must be true" assumptions
4. Execute tests
5. Revise plan based on findings

**Example:**

```
Assumption: "Users will pay $99/month for this feature"

🔬 Analyst: "Test: Landing page with pricing, measure signups"
📋 PM: "Test: Survey current users with pricing tiers"
🎨 UX Designer: "Test: Prototype with pricing, observe reactions"

[Execute cheapest test first]
[If fails, assumption was wrong - pivot]
```

**Location:** `src/core/workflows/assumption-testing/`

---

## Multi-Agent Framework Best Practices

### 1. Optimal Agent Count by Framework Type

| Framework Type       | Ideal Agent Count                         | Rationale                                         |
| -------------------- | ----------------------------------------- | ------------------------------------------------- |
| **Six Hats**         | 12-18 (2-3 per hat)                       | Each hat needs multiple perspectives              |
| **Five Whys**        | 4-5 (investigative + facilitator)         | Enough to challenge, not too many to confuse      |
| **First Principles** | 5-6 (challengers + builders + validators) | Need aggressive challengers + creative rebuilders |
| **SWOT**             | 8-12 (2-3 per quadrant)                   | Parallel quadrant work                            |
| **Decision Matrix**  | 5-7 (criteria definers + scorers)         | Enough perspectives, avoid decision paralysis     |

### 2. Facilitation Agent Requirements

All multi-agent frameworks need a **facilitator agent** with these capabilities:

```yaml
facilitator_requirements:
  synthesis: 'Ability to summarize multiple viewpoints'
  conflict_resolution: 'Navigate disagreements productively'
  time_management: 'Keep framework on track'
  question_formulation: 'Ask clarifying questions'
  bias_detection: 'Notice groupthink or confirmation bias'
```

**Best Facilitator Agents:**

- BMad Master (meta-orchestration)
- Scrum Master (process expertise)
- Innovation Strategist (strategic thinking)

### 3. Framework Selection Guide

**Decision Tree:**

```
Need to make a decision?
├─ Yes → Need multiple perspectives?
│  ├─ Yes → Complex analysis needed?
│  │  ├─ Yes → Six Hats (comprehensive)
│  │  └─ No → Decision Matrix (structured scoring)
│  └─ No → Single expert sufficient
│     ├─ Technical → Architect or TEA
│     ├─ Business → PM or Innovation Strategist
│     └─ Creative → Brainstorming Coach
│
└─ No → Investigating a problem?
   ├─ Root cause unknown → Five Whys
   ├─ Symptoms only → Problem-Solving workflow
   └─ Need to innovate → First Principles
```

### 4. Framework Output Templates

All frameworks should produce **structured outputs** for downstream use:

```markdown
# [Framework Name] Output Template

## Metadata

- Date: {timestamp}
- Framework: {name}
- Facilitator: {agent}
- Participants: {agent_list}
- Topic: {problem_statement}

## Process Summary

[How the framework was executed]

## Key Insights

[Organized by framework phases/rounds]

## Recommendations

[Actionable next steps]

## Dissenting Opinions

[Minority viewpoints that weren't consensus]

## Follow-up Required

[Open questions, validation needed]

## Related Outputs

[Links to other framework outputs, research, etc.]
```

---

## Technical Implementation Roadmap

### Phase 1: Foundation (Weeks 1-2)

- [ ] Create framework selection guide document
- [ ] Add `frameworkStrengths` to agent-manifest.csv
- [ ] Implement framework history tracking
- [ ] Design output template standards

### Phase 2: Multi-Agent Enhancements (Weeks 3-5)

- [ ] Build Six Hats workflow with hat assignment logic
- [ ] Build Five Whys with branching support
- [ ] Build First Principles with assumption challenge mechanics
- [ ] Add multi-agent mode to Design Thinking

### Phase 3: New Frameworks (Weeks 6-8)

- [ ] Implement SWOT Analysis workflow
- [ ] Implement Decision Matrix workflow
- [ ] Implement Pre-Mortem workflow
- [ ] Implement Assumption Testing workflow

### Phase 4: Integration (Weeks 9-10)

- [ ] Framework recommendation engine
- [ ] Workflow chaining examples
- [ ] Party-mode template system
- [ ] Documentation and user guides

### Phase 5: Testing & Refinement (Weeks 11-12)

- [ ] User testing with real scenarios
- [ ] Agent performance tracking
- [ ] Framework effectiveness metrics
- [ ] Iteration based on feedback

---

## Success Metrics

### Framework Effectiveness Metrics

```yaml
metrics:
  usage:
    - frameworks_per_project: 'Average number of frameworks used'
    - most_used_frameworks: 'Top 5 by frequency'
    - framework_combinations: 'Common chaining patterns'

  quality:
    - decision_confidence: 'User ratings of decision quality'
    - insight_depth: 'Novel insights generated'
    - action_item_completion: '% of framework outputs implemented'

  efficiency:
    - time_to_decision: 'Framework duration vs value'
    - agent_relevance: '% of agent contributions rated useful'
    - rework_reduction: "Decisions that didn't need revision"
```

### Agent Performance Metrics

```yaml
agent_metrics:
  framework_participation:
    - frameworks_joined: 'Which frameworks this agent participated in'
    - contribution_quality: "User ratings of agent's insights"
    - specialization_match: '% working in strength areas'

  impact:
    - key_insights_contributed: 'Insights attributed to this agent'
    - disagreements_productive: 'Challenges that improved outcome'
    - synthesis_quality: 'For facilitator agents only'
```

---

## Conclusion

BMad's framework ecosystem is **already comprehensive** with 150+ methodologies spanning:

### Existing Strengths

✅ **Creative:** 36 brainstorming techniques, storytelling frameworks
✅ **Strategic:** 31 innovation frameworks, business model analysis
✅ **Diagnostic:** 31 problem-solving methods, research workflows
✅ **Collaborative:** Party-mode, retrospectives

### Proposed Enhancements

🎯 **Multi-Agent Structured Analysis:** Six Hats, Five Whys, First Principles
🎯 **Additional Frameworks:** SWOT, Decision Matrix, Pre-Mortem, Assumption Testing
🎯 **Integration:** Framework chaining, recommendation engine, cross-workflow orchestration
🎯 **Agent Optimization:** Specialization tags, performance tracking, auto-assignment

### Key Insight

**BMad already has Six Hats, Five Whys, and First Principles** as single-facilitator techniques within the Brainstorming workflow!

The opportunity is to **elevate these to full multi-agent orchestrated workflows** where:

- Multiple agents wear different hats (not just Carson facilitating)
- Multiple agents challenge each "why" (not just Carson asking)
- Multiple agents challenge assumptions (not just Carson guiding)

This transforms single-facilitator techniques into **true multi-agent collaborative frameworks** that leverage BMad's agent diversity.

### Implementation Priority

1. **Quick Win:** Add multi-agent mode to existing Six Hats/Five Whys/First Principles in brainstorming
2. **High Impact:** Build standalone Six Hats workflow (most visual, easiest to understand)
3. **Practical Value:** Build standalone Five Whys workflow (immediate debugging value)
4. **Innovation:** Build standalone First Principles workflow (highest strategic impact)
5. **Expand:** Add SWOT, Decision Matrix, Pre-Mortem as new workflows
6. **Integrate:** Framework chaining, recommendation engine, cross-module orchestration

The comprehensive framework ecosystem positions BMad as the **definitive multi-agent analytical platform** for structured thinking, creative problem-solving, and strategic decision-making.
