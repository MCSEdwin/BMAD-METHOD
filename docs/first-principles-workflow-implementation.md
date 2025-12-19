# First Principles Thinking - Multi-Agent Workflow Implementation Guide

**Version:** 1.0
**Status:** Production-Ready
**Framework:** First Principles Thinking (Aristotelian reasoning from fundamental truths)
**Multi-Agent Pattern:** Challenge-Rebuild Cycle with Socratic Questioning

---

## Table of Contents

1. [Overview](#1-overview)
2. [Framework Philosophy](#2-framework-philosophy)
3. [Multi-Agent Architecture](#3-multi-agent-architecture)
4. [Complete Workflow Files](#4-complete-workflow-files)
   - [4.1 Annotated workflow.yaml](#41-annotated-workflowyaml)
   - [4.2 Annotated agent-assignments.yaml](#42-annotated-agent-assignmentsyaml)
   - [4.3 Annotated instructions.md](#43-annotated-instructionsmd)
   - [4.4 Annotated template.md](#44-annotated-templatemd)
5. [Complete Example Dialogue](#5-complete-example-dialogue)
6. [Implementation Guide](#6-implementation-guide)
7. [Comparison: First Principles vs Other Frameworks](#7-comparison-first-principles-vs-other-frameworks)

---

## 1. Overview

### What is First Principles Thinking?

First Principles thinking is the practice of **actively questioning every assumption** you think you know about a problem, then **reconstructing solutions from the ground up** using only fundamental truths.

**Origin:** Aristotle defined a first principle as "the first basis from which a thing is known."

**Modern Application:** Elon Musk popularized this approach: "Boil things down to their fundamental truths and reason up from there."

### Why Multi-Agent?

Traditional single-facilitator First Principles sessions have limitations:

- **Echo chamber:** One facilitator may miss assumptions they unconsciously share
- **Incomplete challenge:** Single perspective can't challenge all angles
- **Weak reconstruction:** Building new solutions needs diverse expertise

**Multi-agent approach solves this:**

- **Challenger agents** aggressively question every assumption from different angles
- **Subject matter agents** defend (or abandon) assumptions with evidence
- **Builder agents** reconstruct solutions using validated fundamentals
- **Validator agents** verify the new solution doesn't reintroduce old assumptions

### When to Use This Workflow

✅ **Use First Principles when:**

- You're stuck with legacy solutions that "feel wrong"
- Industry conventions seem limiting
- Incremental improvements aren't working
- You need breakthrough innovation
- Cost constraints demand radically different approach
- Current architecture has fundamental flaws

❌ **Don't use First Principles when:**

- Time-sensitive decisions (it's slow and thorough)
- Problem is well-solved by existing patterns
- Stakes are low (overkill for minor decisions)
- Team lacks expertise to validate fundamentals

### Key Differences from Other Frameworks

| Framework         | Purpose                    | Output                 | First Principles Difference                               |
| ----------------- | -------------------------- | ---------------------- | --------------------------------------------------------- |
| **Six Hats**      | Multi-perspective analysis | Balanced decision      | FP _discards_ perspectives that rest on false assumptions |
| **Five Whys**     | Root cause diagnosis       | Problem source         | FP _rebuilds_ from scratch, not just fixes root cause     |
| **Brainstorming** | Generate ideas             | Creative options       | FP _constrains_ to fundamental truths, not free ideation  |
| **SWOT**          | Strategic analysis         | Situational assessment | FP _questions_ whether strengths/threats are real         |

**First Principles is the most radical framework** - it assumes current thinking may be entirely wrong and rebuilds from zero.

---

## 2. Framework Philosophy

### The Three-Phase Cycle

```
┌─────────────────────────────────────────────────────────┐
│  PHASE 1: DECONSTRUCT (Challenge Every Assumption)     │
│  • Surface ALL assumptions in current approach          │
│  • Categorize: Fundamental truth vs inherited belief    │
│  • Aggressively challenge each assumption               │
│  • Discard assumptions that can't be defended           │
└─────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────┐
│  PHASE 2: VALIDATE (Identify True Fundamentals)        │
│  • For each "fundamental," ask: Is this REALLY true?    │
│  • Demand evidence, not convention                      │
│  • Physics/math/economics trumps "best practice"        │
│  • Establish bedrock truths we CANNOT violate           │
└─────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────┐
│  PHASE 3: RECONSTRUCT (Rebuild from Fundamentals)      │
│  • Start with ONLY validated fundamental truths         │
│  • Build new solution constrained to fundamentals       │
│  • Verify solution doesn't reintroduce old assumptions  │
│  • Compare: Old approach vs First Principles approach   │
└─────────────────────────────────────────────────────────┘
```

### Core Principles of the Framework

**1. Assumption Hostility**

- Default stance: Every assumption is guilty until proven innocent
- "We've always done it this way" is NOT evidence
- Industry standards are NOT fundamental truths

**2. Evidence Hierarchy**

```
HIGHEST: Physics, mathematics, thermodynamics (laws of nature)
HIGH: Economics, biology (strong empirical patterns)
MEDIUM: Engineering constraints, material properties
LOW: Best practices, conventions, industry norms
LOWEST: "Everyone does it this way," gut feelings
```

**3. Socratic Method**

- Facilitator uses relentless questioning, not assertions
- Agents must defend assumptions with evidence, not authority
- "Why?" asked repeatedly until hitting bedrock or assumption crumbles

**4. Rebuild Constraint**

- New solution can ONLY use validated fundamentals
- No "and then we add X because it's standard"
- If it wasn't proven fundamental, it's not allowed

### Multi-Agent Roles

**Challengers (2-3 agents):**

- **Goal:** Destroy assumptions mercilessly
- **Mindset:** "Prove it or lose it"
- **Best agents:** TEA (test mindset), Architect (technical depth), Innovation Strategist (business assumptions)
- **Permission:** Be aggressive, interrupt, demand evidence

**Defenders (2-3 agents):**

- **Goal:** Defend assumptions WITH EVIDENCE or abandon them
- **Mindset:** "Can I back this up or should I let it go?"
- **Best agents:** PM (business knowledge), Dev (implementation reality), Analyst (data)
- **Permission:** Say "I can't defend this" is success, not failure

**Builders (2-3 agents):**

- **Goal:** Reconstruct solution using only proven fundamentals
- **Mindset:** "What's the simplest solution that respects physics/economics?"
- **Best agents:** Architect (design), Creative Problem Solver (innovation), PM (feasibility)
- **Permission:** Propose radical departures from current approach

**Facilitator (1 agent):**

- **Goal:** Orchestrate challenge-defend-rebuild cycle, synthesize insights
- **Mindset:** "What's a fundamental truth vs inherited assumption?"
- **Best agents:** BMad Master (meta-orchestration), Innovation Strategist (strategic thinking)
- **Permission:** Interrupt groupthink, force deeper questioning

### Success Criteria

**Good First Principles Session:**

- ✅ 60%+ of initial assumptions discarded or significantly revised
- ✅ New solution differs substantially from starting approach
- ✅ Every element of new solution traceable to validated fundamental
- ✅ Team can articulate WHY old approach was suboptimal
- ✅ Cost, complexity, or performance dramatically improved

**Bad First Principles Session:**

- ❌ New solution looks like old solution with tweaks
- ❌ Assumptions defended with "best practice" not evidence
- ❌ Team uncomfortable with aggressive challenging
- ❌ Facilitator accepts "that's just how it works" without proof
- ❌ No radical insights emerge

---

## 3. Multi-Agent Architecture

### Agent Selection Algorithm

First Principles requires **THREE distinct agent cohorts** working in sequence:

```yaml
phase_1_challengers:
  selection_criteria:
    - agent.role contains ["test", "quality", "security", "risk"]
    - agent.principles contains "questioning" OR "critical thinking"
    - agent.communicationStyle contains "direct" OR "analytical"
  scoring:
    role_match: 40 points
    challenging_personality: 30 points
    technical_depth: 20 points
    domain_expertise: 10 points
  count: 2-3

phase_2_defenders:
  selection_criteria:
    - agent.role contains ["pm", "dev", "analyst", "architect"]
    - agent.identity contains deep domain knowledge
    - agent has implementation experience
  scoring:
    domain_expertise: 40 points
    evidence_based_thinking: 30 points
    practical_experience: 20 points
    communication_clarity: 10 points
  count: 2-3

phase_3_builders:
  selection_criteria:
    - agent.role contains ["architect", "innovation", "creative"]
    - agent.principles contains "innovation" OR "simplicity"
    - agent has cross-domain knowledge
  scoring:
    creative_capability: 40 points
    technical_design_skill: 30 points
    systems_thinking: 20 points
    pragmatism: 10 points
  count: 2-3

facilitator:
  selection_criteria:
    - agent.role contains ["master", "strategist", "coach"]
    - agent has synthesis capability
  count: 1
```

### Interaction Pattern

**Unlike Six Hats (sequential hats) or Five Whys (linear drilling), First Principles uses ITERATIVE CYCLES:**

```
Round 1: Challengers surface assumptions
         ↓
Round 2: Defenders attempt to defend with evidence
         ↓
Round 3: Facilitator categorizes (fundamental vs discarded)
         ↓
Round 4: Repeat for next assumption cluster
         ↓
         ... (multiple cycles until all assumptions processed)
         ↓
Round N: Builders propose new solution using fundamentals
         ↓
Round N+1: Challengers verify no old assumptions crept back in
         ↓
Round N+2: Facilitator synthesizes old vs new approach
```

**Key Pattern Differences:**

- **NOT debate:** Defenders aren't trying to "win," they're testing assumptions
- **NOT consensus:** If assumption can't be defended, it's discarded regardless of popularity
- **NOT collaborative building:** Builders work AFTER assumptions cleared, not during

### Checkpoint Protocol

First Principles sessions risk context loss due to length and complexity:

```yaml
checkpoint_frequency: after_each_assumption_cluster
checkpoint_contents:
  - assumption_text
  - challenger_questions
  - defender_responses
  - facilitator_verdict (fundamental | discarded | needs_more_evidence)
  - evidence_provided
  - revised_assumption (if applicable)

cumulative_checkpoint: after_phase_completion
phase_checkpoints:
  - phase_1_assumptions_list (with verdicts)
  - phase_2_validated_fundamentals (bedrock truths)
  - phase_3_reconstructed_solution (new approach)
  - comparison_table (old vs new)
```

### Consensus Mechanism

First Principles uses **EVIDENCE-BASED CONSENSUS**, not democratic voting:

```yaml
consensus_rules:
  assumption_validity:
    method: "challenger satisfied"
    requirement: "Challengers agree evidence is sufficient OR defenders concede"
    not_valid: "Majority vote" (popularity doesn't make something fundamental)

  fundamental_truth:
    method: "cannot be further reduced"
    requirement: "Resists all Socratic questioning"
    verification: "Multiple agents with different expertise agree"

  solution_approval:
    method: "validator verification"
    requirement: "No discarded assumptions reintroduced"
    check: "Every component traceable to validated fundamental"
```

---

## 4. Complete Workflow Files

### 4.1 Annotated workflow.yaml

```yaml
# First Principles Thinking - Multi-Agent Workflow Configuration

# ═══════════════════════════════════════════════════════════════════
# METADATA
# ═══════════════════════════════════════════════════════════════════

name: 'first-principles'
description: 'Challenge every assumption and rebuild solutions from fundamental truths using multi-agent Socratic questioning'
author: 'BMad'
version: '1.0'

# DESIGN NOTE: First Principles is the most radical analytical framework
# It assumes current thinking may be entirely wrong and rebuilds from scratch
# This is NOT incremental improvement - it's fundamental rethinking

# ═══════════════════════════════════════════════════════════════════
# CRITICAL DATA SOURCES
# ═══════════════════════════════════════════════════════════════════

agent_manifest: '{project-root}/{bmad_folder}/_cfg/agent-manifest.csv'

# DESIGN NOTE: Agent manifest contains ALL available agents
# Format: name, displayName, title, icon, role, identity, communicationStyle, principles
# First Principles needs diverse agents: challengers, defenders, builders, facilitator

agent_assignments: '{project-root}/{bmad_folder}/core/workflows/first-principles/agent-assignments.yaml'

# DESIGN NOTE: Separate configuration file for agent selection criteria
# Allows customization without modifying workflow logic
# Defines which agent types map to challenger/defender/builder roles

date: system-generated

# ═══════════════════════════════════════════════════════════════════
# WORKFLOW CONFIGURATION
# ═══════════════════════════════════════════════════════════════════

# This is an interactive action workflow with structured output
template: '{project-root}/{bmad_folder}/core/workflows/first-principles/template.md'

# DESIGN NOTE: Template captures the complete session:
# - Initial problem/approach
# - All assumptions identified and challenged
# - Validated fundamental truths
# - Reconstructed solution
# - Comparison: old approach vs first principles approach

instructions: '{project-root}/{bmad_folder}/core/workflows/first-principles/instructions.md'

# DESIGN NOTE: Instructions govern the three-phase cycle:
# Phase 1: Deconstruct (challenge assumptions)
# Phase 2: Validate (identify fundamentals)
# Phase 3: Reconstruct (rebuild from fundamentals)

# ═══════════════════════════════════════════════════════════════════
# WORKFLOW PARAMETERS
# ═══════════════════════════════════════════════════════════════════

phases:
  - deconstruct # Challenge every assumption
  - validate # Identify true fundamentals
  - reconstruct # Rebuild from scratch

# DESIGN NOTE: Three-phase structure is fundamental to framework
# Cannot skip phases - each builds on previous
# Deconstruct without validate = just criticism
# Validate without reconstruct = analysis paralysis
# Reconstruct without deconstruct = incremental thinking

challenge_intensity:
  default: 'aggressive'
  options:
    - gentle # For teams new to framework
    - moderate # Standard Socratic questioning
    - aggressive # Relentless challenge (recommended)

# DESIGN NOTE: Aggressive is default because:
# - Gentle challenges don't expose deep assumptions
# - People defend assumptions unless forced to provide evidence
# - Framework only works if assumptions truly questioned

evidence_standards:
  highest_tier:
    - 'laws of physics'
    - 'mathematical proof'
    - 'thermodynamic constraints'
  high_tier:
    - 'economic principles'
    - 'biological/chemical constraints'
    - 'empirical data (reproducible)'
  medium_tier:
    - 'engineering constraints'
    - 'material properties'
    - 'regulatory requirements'
  low_tier:
    - 'industry best practices'
    - 'competitor behavior'
    - 'historical precedent'
  insufficient:
    - "that's how it's always done"
    - 'everyone does it this way'
    - 'gut feeling'

# DESIGN NOTE: Evidence hierarchy guides facilitator verdicts
# Only highest/high tier evidence can establish fundamentals
# Low tier evidence suggests inherited assumptions, not truths

# ═══════════════════════════════════════════════════════════════════
# EXIT CONDITIONS
# ═══════════════════════════════════════════════════════════════════

exit_triggers:
  - '*exit'
  - '*quit'

# DESIGN NOTE: First Principles sessions are LONG (2-4 hours typical)
# Users may need to pause and resume
# Template checkpoint protocol ensures work isn't lost

# ═══════════════════════════════════════════════════════════════════
# MULTI-AGENT CONFIGURATION
# ═══════════════════════════════════════════════════════════════════

multi_agent:
  challengers:
    count: 2-3
    role: 'Challenge assumptions aggressively'
    selection_criteria: 'agent-assignments.yaml:challengers'

  defenders:
    count: 2-3
    role: 'Defend assumptions with evidence or concede'
    selection_criteria: 'agent-assignments.yaml:defenders'

  builders:
    count: 2-3
    role: 'Reconstruct solution using only fundamentals'
    selection_criteria: 'agent-assignments.yaml:builders'

  facilitator:
    count: 1
    role: 'Orchestrate challenge-defend-rebuild cycle, render verdicts'
    selection_criteria: 'agent-assignments.yaml:facilitator'

# DESIGN NOTE: Three distinct cohorts work in sequence, not parallel
# Challengers go first, defenders respond, builders come last
# This prevents premature solution-building before assumptions cleared

interaction_pattern: 'iterative-cycles'

# DESIGN NOTE: Unlike Six Hats (sequential) or Five Whys (linear),
# First Principles uses iterative cycles:
# Challenge → Defend → Verdict → Next Assumption → Repeat

# ═══════════════════════════════════════════════════════════════════
# OUTPUT CONFIGURATION
# ═══════════════════════════════════════════════════════════════════

output:
  format: 'markdown'
  location: '{project-root}/{bmad_folder}/_output/first-principles-{problem-slug}-{date}.md'

  # DESIGN NOTE: Output is comprehensive artifact showing:
  # - Journey from assumptions to fundamentals to new solution
  # - Evidence trail for all verdicts
  # - Comparison table: old vs new approach
  # - Rationale for why new approach is superior

sections:
  - problem_statement
  - initial_approach_description
  - assumptions_identified
  - challenge_defend_rounds
  - validated_fundamentals
  - reconstructed_solution
  - comparison_analysis
  - implementation_considerations

# ═══════════════════════════════════════════════════════════════════
# OPTIONAL FEATURES
# ═══════════════════════════════════════════════════════════════════

optional:
  tts_enabled: false # AgentVibes text-to-speech integration
  visualization: false # Assumption tree diagram
  reference_links: true # Link to evidence sources

# DESIGN NOTE: TTS useful for long sessions to maintain engagement
# Visualization helpful for complex assumption hierarchies
# Reference links critical for evidence verification

# ═══════════════════════════════════════════════════════════════════
# STANDALONE CONFIGURATION
# ═══════════════════════════════════════════════════════════════════

standalone: true

# DESIGN NOTE: This workflow can be invoked directly
# User can type: *first-principles
# Or: Load BMad Master → *first-principles

# ═══════════════════════════════════════════════════════════════════
# WEB BUNDLE CONFIGURATION (for ChatGPT/Claude/Gemini)
# ═══════════════════════════════════════════════════════════════════

web_bundle:
  name: 'first-principles'
  description: 'Multi-agent First Principles thinking workflow - challenge assumptions and rebuild from fundamental truths'
  author: 'BMad'
  instructions: '{bmad_folder}/core/workflows/first-principles/instructions.md'
  agent_manifest: '{bmad_folder}/_cfg/agent-manifest.csv'
  agent_assignments: '{bmad_folder}/core/workflows/first-principles/agent-assignments.yaml'
  web_bundle_files:
    - '{bmad_folder}/core/workflows/first-principles/instructions.md'
    - '{bmad_folder}/core/workflows/first-principles/agent-assignments.yaml'
    - '{bmad_folder}/core/workflows/first-principles/template.md'
    - '{bmad_folder}/_cfg/agent-manifest.csv'
# DESIGN NOTE: Web bundle allows First Principles to work in:
# - ChatGPT Custom GPTs
# - Claude Projects
# - Gemini with uploaded context
# All required files bundled for portability
```

---

### 4.2 Annotated agent-assignments.yaml

```yaml
# First Principles Thinking - Agent Role Assignment Configuration

# ═══════════════════════════════════════════════════════════════════
# DESIGN PHILOSOPHY
# ═══════════════════════════════════════════════════════════════════
# First Principles requires THREE distinct agent cohorts with different mindsets:
#
# 1. CHALLENGERS: Destroy assumptions mercilessly
#    - Default stance: "Prove it or lose it"
#    - Permission: Be aggressive, interrupt, demand evidence
#
# 2. DEFENDERS: Defend with evidence or concede gracefully
#    - Default stance: "Can I back this up?"
#    - Permission: Saying "I can't defend this" is SUCCESS, not failure
#
# 3. BUILDERS: Reconstruct using only validated fundamentals
#    - Default stance: "What's simplest solution respecting constraints?"
#    - Permission: Propose radical departures from current approach
#
# 4. FACILITATOR: Orchestrate cycle and render evidence-based verdicts
#    - Default stance: "What's fundamental truth vs inherited assumption?"
#    - Permission: Interrupt groupthink, force deeper questioning
# ═══════════════════════════════════════════════════════════════════

# ═══════════════════════════════════════════════════════════════════
# PHASE 1: CHALLENGERS (Deconstruct Assumptions)
# ═══════════════════════════════════════════════════════════════════

challengers:
  name: "Assumption Challengers"
  icon: "⚔️"
  phase: "deconstruct"
  mindset: "Every assumption is guilty until proven innocent with evidence"

  # DESIGN NOTE: Challengers need aggressive questioning capability
  # Best agents: Quality mindset (TEA), critical thinking (Architect),
  # business assumption challenge (Innovation Strategist)

  agent_criteria:
    primary:
      - "test"           # TEA: Quality mindset, finds edge cases
      - "quality"        # QA roles: Skeptical by nature
      - "security"       # Security: Threat modeling mindset
      - "risk"           # Risk analyst: Identifies vulnerabilities
      - "innovation"     # Innovation Strategist: Challenges conventions

    secondary:
      - "architect"      # Technical depth to challenge architecture
      - "analyst"        # Data-driven challenge capability
      - "researcher"     # Evidence evaluation skills

  # DESIGN NOTE: Scoring system prioritizes challenging personality
  # Role match alone insufficient - need aggressive questioning style

  scoring:
    role_match: 40          # Primary criteria roles
    challenging_style: 30   # Communication style: direct, analytical, questioning
    technical_depth: 20     # Depth to understand what they're challenging
    domain_expertise: 10    # Context helps but not required

  # DESIGN NOTE: 2-3 challengers provides:
  # - Multiple questioning angles (technical, business, user, security)
  # - Cross-validation of challenges
  # - Prevents single challenger being dismissed as "too negative"

  optimal_count: 2-3

  fallback:
    - "architect"      # Can challenge technical assumptions
    - "pm"             # Can challenge business assumptions
    - "analyst"        # Can challenge data assumptions

  # DESIGN NOTE: What challengers focus on during Phase 1
  contribution_guide:
    - "Challenge EVERY assumption, even obvious ones"
    - "Demand evidence: physics, data, math - not 'best practice'"
    - "Ask 'Why?' repeatedly until hitting bedrock or assumption crumbles"
    - "Interrupt if defender appealing to authority/convention"
    - "Be aggressive - this is NOT a time for politeness"
    - "If you can imagine an alternative, the assumption isn't fundamental"

  # DESIGN NOTE: Example challenges by assumption type
  challenge_patterns:
    technical:
      - "Why must we use a database? Can we keep it all in memory?"
      - "Why three-tier architecture? What law of physics requires it?"
      - "Why async? What's the ACTUAL constraint - not what's conventional?"

    business:
      - "Why must users pay monthly? What prevents one-time payment?"
      - "Why need sales team? Can't users just... buy it themselves?"
      - "Why compete on features? Can we compete on radically lower price instead?"

    process:
      - "Why need approval workflow? What breaks if person just does it?"
      - "Why meetings? What information transfer can't happen asynchronously?"
      - "Why estimates? Can we just start building and see how long it takes?"

  # DESIGN NOTE: Permission statements empower aggressive challenging
  permissions:
    - "Interrupt defenders if they appeal to convention"
    - "Reject 'best practice' as evidence (it's not fundamental)"
    - "Demand physics, economics, or data - nothing less"
    - "Be comfortable with tension - challenging is your job"

# ═══════════════════════════════════════════════════════════════════
# PHASE 1-2: DEFENDERS (Defend Assumptions with Evidence)
# ═══════════════════════════════════════════════════════════════════

defenders:
  name: "Evidence Providers"
  icon: "🛡️"
  phase: "deconstruct-validate"
  mindset: "Can I defend this with evidence? If not, I concede gracefully."

  # DESIGN NOTE: Defenders need deep domain knowledge AND willingness to concede
  # Best agents: PM (business knowledge), Dev (implementation reality),
  # Analyst (data), Architect (technical constraints)

  agent_criteria:
    primary:
      - "pm"             # Product Manager: Business logic, user needs
      - "dev"            # Developer: Implementation reality, technical constraints
      - "analyst"        # Data Analyst: Evidence and data
      - "architect"      # Solution Architect: Technical design constraints

    secondary:
      - "ux-designer"    # User experience constraints
      - "sm"             # Scrum Master: Process reasoning
      - "researcher"     # Research depth

  # DESIGN NOTE: Defenders need domain expertise AND communication clarity
  # Must articulate WHY assumption exists, not just that it does

  scoring:
    domain_expertise: 40      # Deep knowledge of subject matter
    evidence_based: 30        # Thinks in data/facts, not opinions
    practical_experience: 20  # Has implemented similar solutions
    communication_clarity: 10 # Can articulate reasoning clearly

  optimal_count: 2-3

  fallback:
    - "dev"           # Always have implementation perspective
    - "architect"     # Technical reasoning
    - "pm"            # Business reasoning

  # DESIGN NOTE: What defenders focus on during Phase 1
  contribution_guide:
    - "Defend assumptions ONLY with evidence: data, physics, economics"
    - "If you can't provide evidence, CONCEDE GRACEFULLY (this is success!)"
    - "'Everyone does it' is NOT evidence"
    - "'Best practice' is NOT evidence unless you can cite the underlying reason"
    - "Physics > Economics > Engineering > Convention"
    - "Saying 'I can't defend this' helps the team - don't fight unwinnable battles"

  # DESIGN NOTE: Types of acceptable evidence
  evidence_hierarchy:
    highest:  # Can establish fundamental truth
      - "Laws of physics (gravity, thermodynamics, etc.)"
      - "Mathematical proof"
      - "Economic laws (supply/demand, opportunity cost)"
      - "Reproducible empirical data"

    high:  # Strong evidence but not absolute
      - "Material properties (metals, bandwidth limits)"
      - "Biological constraints (human attention span, reaction time)"
      - "Regulatory requirements (must comply with law)"

    medium:  # Context-dependent evidence
      - "Engineering trade-offs (can be optimized differently)"
      - "Historical data (patterns but not laws)"
      - "User research (specific to context)"

    low:  # Weak evidence, often convention
      - "Industry best practices (may be cargo cult)"
      - "Competitor behavior (may all be wrong)"
      - "Historical precedent (we've always done it)"

    insufficient:  # Not evidence at all
      - "That's how it's always done"
      - "Everyone does it this way"
      - "It feels right"
      - "My experience suggests..."

  # DESIGN NOTE: Successful defense examples
  defense_examples:
    strong:
      - "We need a database because data exceeds RAM (128GB available, 500GB needed) - physics constraint"
      - "Need async processing because users won't wait >3sec (measured: 40% abandon at 3sec) - user behavior data"
      - "Must encrypt because GDPR requires it (legal regulation) - regulatory constraint"

    weak:
      - "We need microservices because that's best practice" (REJECTED - not evidence)
      - "Need approvals because that's how enterprises work" (REJECTED - convention)
      - "Should use React because everyone uses React" (REJECTED - bandwagon)

  # DESIGN NOTE: Permission to concede
  permissions:
    - "Concede if you can't provide evidence - this HELPS the team"
    - "It's okay to say 'I thought this was fundamental but it's not'"
    - "Challenging your own assumptions is valuable contribution"
    - "If defense is 'best practice,' say so and move on"

# ═══════════════════════════════════════════════════════════════════
# PHASE 3: BUILDERS (Reconstruct from Fundamentals)
# ═══════════════════════════════════════════════════════════════════

builders:
  name: "Solution Architects"
  icon: "🏗️"
  phase: "reconstruct"
  mindset: "Build the simplest solution that respects validated fundamental truths"

  # DESIGN NOTE: Builders need creative problem-solving AND pragmatism
  # Best agents: Architect (design), Innovation Strategist (novel approaches),
  # Creative Problem Solver (unconventional thinking)

  agent_criteria:
    primary:
      - "architect"              # Technical design expertise
      - "innovation-strategist"  # Novel approach generation
      - "creative-problem-solver" # Unconventional thinking
      - "dev"                    # Implementation pragmatism

    secondary:
      - "pm"             # Business viability
      - "ux-designer"    # User-centered design
      - "researcher"     # Research-backed approaches

  # DESIGN NOTE: Builders need creativity AND technical feasibility judgment

  scoring:
    creative_capability: 40     # Can imagine radically different approaches
    technical_design: 30        # Can actually design workable solutions
    systems_thinking: 20        # See whole system, not just parts
    pragmatism: 10              # Balance innovation with implementability

  optimal_count: 2-3

  fallback:
    - "architect"      # Technical design always needed
    - "dev"            # Pragmatic implementation view
    - "pm"             # Business viability check

  # DESIGN NOTE: What builders focus on during Phase 3
  contribution_guide:
    - "Use ONLY validated fundamental truths from Phase 2"
    - "Start from scratch - don't modify old solution"
    - "Simplicity is goal - fewest components respecting constraints"
    - "If old solution had X and you can't defend it from fundamentals, DON'T include X"
    - "Propose radical departures - this is where breakthrough happens"
    - "Ask: 'What's the dumbest/simplest thing that could work?'"

  # DESIGN NOTE: Reconstruction patterns
  reconstruction_strategies:
    cost_optimization:
      - "If cost is fundamental constraint, ask: What's cheapest possible solution?"
      - "Example: Battery too expensive → Rethink: Do we need battery at all?"
      - "Example: Cloud costs high → Rethink: Can we use user's device instead?"

    performance_optimization:
      - "If speed is fundamental constraint, ask: What's fastest physically possible?"
      - "Example: Network latency → Rethink: Can we avoid network entirely (local-first)?"
      - "Example: Computation slow → Rethink: Can we precompute or eliminate computation?"

    complexity_reduction:
      - "If simplicity is goal, ask: What can we delete?"
      - "Example: 10 microservices → Rethink: What if one service?"
      - "Example: Complex workflow → Rethink: What if no workflow (direct action)?"

  # DESIGN NOTE: Validation during reconstruction
  validation_checks:
    - "Does this solution use validated fundamentals ONLY?"
    - "Did we reintroduce any discarded assumptions?"
    - "Is this SIMPLER than old approach?"
    - "Can we explain WHY this is better using evidence?"

  # DESIGN NOTE: Permission to be radical
  permissions:
    - "Propose ideas that sound crazy - that's the point"
    - "Challenge conventional architecture/business models"
    - "If it respects fundamentals, it's valid even if unprecedented"
    - "Don't self-censor based on 'that's not how it's done'"

# ═══════════════════════════════════════════════════════════════════
# ALL PHASES: FACILITATOR (Orchestrate and Synthesize)
# ═══════════════════════════════════════════════════════════════════

facilitator:
  name: "Socratic Facilitator"
  icon: "🧠"
  phase: "all"
  mindset: "What's a fundamental truth vs inherited assumption? Drive to bedrock."

  # DESIGN NOTE: Facilitator needs meta-cognitive ability and synthesis skill
  # Best agents: BMad Master (orchestration), Innovation Strategist (strategic thinking)

  agent_criteria:
    primary:
      - "bmad-master"           # Meta-orchestration capability
      - "innovation-strategist" # Strategic thinking, pattern recognition
      - "sm"                    # Scrum Master: Process facilitation

    secondary:
      - "coach"          # Facilitation skills
      - "architect"      # Technical synthesis
      - "pm"             # Business synthesis

  # DESIGN NOTE: Facilitator renders verdicts, not just moderates

  scoring:
    synthesis_capability: 40   # Can integrate multiple viewpoints
    questioning_skill: 30      # Socratic method mastery
    evidence_evaluation: 20    # Can judge evidence quality
    group_facilitation: 10     # Keep discussion productive

  optimal_count: 1  # Single facilitator prevents confusion

  fallback:
    - "bmad-master"    # Always best choice if available
    - "sm"             # Second choice: process expertise

  # DESIGN NOTE: Facilitator responsibilities by phase
  phase_responsibilities:
    phase_1_deconstruct:
      - "Surface ALL assumptions (explicit and hidden)"
      - "Ensure challengers are aggressive enough"
      - "Ensure defenders provide evidence, not opinion"
      - "Render verdicts: Fundamental | Discarded | Needs more evidence"
      - "Maintain evidence hierarchy (physics > convention)"
      - "Prevent groupthink or premature consensus"

    phase_2_validate:
      - "For each 'fundamental,' ask: Is this REALLY fundamental?"
      - "Apply Socratic questioning until hitting bedrock"
      - "Distinguish: Laws of nature vs engineering tradeoffs"
      - "Create list of validated fundamental truths"
      - "These truths constrain Phase 3 reconstruction"

    phase_3_reconstruct:
      - "Ensure builders use ONLY validated fundamentals"
      - "Challenge if discarded assumptions reappear"
      - "Synthesize multiple builder proposals"
      - "Compare old vs new approach"
      - "Articulate WHY new approach is superior"

  # DESIGN NOTE: Socratic questioning patterns
  socratic_patterns:
    - "Why do you believe that?"
    - "What evidence supports that claim?"
    - "Is that a law of nature or a choice?"
    - "Can you imagine an alternative? Then it's not fundamental."
    - "If we started from scratch, would we choose this?"
    - "What would have to be true for this assumption to be false?"

  # DESIGN NOTE: Verdict criteria
  verdict_criteria:
    fundamental_truth:
      - "Cannot be further reduced by questioning"
      - "Supported by physics, math, or strong empirical data"
      - "Multiple experts with different perspectives agree"
      - "Alternative approaches would violate this constraint"

    discarded_assumption:
      - "Defender cannot provide evidence (only convention/practice)"
      - "Revealed to be choice, not constraint"
      - "Inherited from past context that no longer applies"
      - "Can imagine viable alternatives"

    needs_more_evidence:
      - "Plausible but insufficient data"
      - "Need to research or test"
      - "Treat as assumption for now, validate later"

  # DESIGN NOTE: Permission to interrupt
  permissions:
    - "Interrupt if discussion drifts from evidence"
    - "Cut off defender appealing to authority"
    - "Force 'why?' one more level when answer seems surface"
    - "Declare verdict even if unpopular"

# ═══════════════════════════════════════════════════════════════════
# CUSTOMIZATION NOTES
# ═══════════════════════════════════════════════════════════════════

customization:
  user_overrides:
    # Users can create custom assignment file to override defaults
    # Location: {bmad_folder}/_cfg/first-principles-custom-assignments.yaml
    # Workflow checks for custom file first, falls back to this default

  challenge_intensity:
    # Can adjust how aggressive challengers are:
    # - gentle: "Could you explain your reasoning?" (not recommended)
    # - moderate: "What evidence supports that?" (standard)
    # - aggressive: "Prove it or lose it" (recommended)
    default: "aggressive"

  agent_count:
    # Can adjust agents per cohort based on:
    # - Available agent roster size
    # - Time constraints (fewer = faster)
    # - Problem complexity (more = deeper analysis)
    challengers: "2-3"
    defenders: "2-3"
    builders: "2-3"
    facilitator: "1"

# ═══════════════════════════════════════════════════════════════════
# INTEGRATION WITH AGENT MANIFEST
# ═══════════════════════════════════════════════════════════════════

# Workflow loads agent-manifest.csv and scores each agent against criteria above
# Selection algorithm (from multi-agent-workflow-implementation-guide.md Section 1):
#
# For each cohort (challengers, defenders, builders):
#   1. Filter agents by role criteria (primary = 100pts, secondary = 70pts)
#   2. Score each agent using weighted criteria
#   3. Rank agents by total score
#   4. Select top N agents for that cohort
#   5. If insufficient agents, use fallback criteria
#
# Example scoring for TEA agent in challenger role:
#   - role_match (test): 40 points
#   - challenging_style (direct): 30 points
#   - technical_depth (high): 20 points
#   - domain_expertise (quality): 10 points
#   - TOTAL: 100 points (excellent challenger)
```

---

### 4.3 Annotated instructions.md

Due to length, this section is approximately 2,500+ lines. I'll create the complete file with all phases, substeps, and design notes:

```markdown
# First Principles Thinking - Multi-Agent Workflow Instructions

# ═══════════════════════════════════════════════════════════════════

# CRITICAL GOVERNANCE

# ═══════════════════════════════════════════════════════════════════

<critical>The workflow execution engine is governed by: {project_root}/{bmad_folder}/core/tasks/workflow.xml</critical>
<critical>This workflow orchestrates First Principles thinking through three-phase challenge-rebuild cycle using multiple specialized agents</critical>

# DESIGN NOTE: Critical tags ensure Claude understands workflow governance

# workflow.xml is the universal execution engine processing these instructions

# ═══════════════════════════════════════════════════════════════════

# TTS INTEGRATION POINT

# ═══════════════════════════════════════════════════════════════════

<!-- TTS_INJECTION:first-principles -->

# DESIGN NOTE: AgentVibes TTS integration marker

# When present, workflow triggers speech after agent contributions

# Pattern: Bash: .claude/hooks/bmad-speak.sh "{agent_name}" "{text}"

# Long sessions benefit from audio to maintain engagement

<workflow>

# ═══════════════════════════════════════════════════════════════════

# STEP 1: INITIALIZATION & AGENT ASSIGNMENT

# ═══════════════════════════════════════════════════════════════════

<step n="1" goal="Initialize First Principles Framework and Assign Agent Cohorts">

# DESIGN NOTE: First Principles requires careful setup

# Must establish:

# - Current approach/problem

# - Three agent cohorts (challengers, defenders, builders)

# - Ground rules for evidence-based discourse

<action>Load workflow configuration from {{workflow_config}}</action>

# DESIGN NOTE: workflow.yaml contains challenge intensity, evidence standards

<action>Load agent manifest from {{agent_manifest}}</action>

# DESIGN NOTE: CSV with all available agents: name, role, identity, principles

<action>Load agent assignment criteria from {{agent_assignments}}</action>

# DESIGN NOTE: agent-assignments.yaml defines criteria for each cohort

  <substep n="1a" goal="Assign Agents to Three Cohorts">

    # DESIGN NOTE: Three distinct cohorts, not overlapping
    # Same agent can be challenger AND defender if roster limited,
    # but ideally separate agents for clean separation of concerns

    <action>Assign CHALLENGERS (2-3 agents):</action>
    <logic>
      - Filter agents matching challenger criteria (test, quality, security, risk, innovation)
      - Score using weighted criteria (role 40, style 30, depth 20, domain 10)
      - Select top 2-3 agents
      - Fallback: architect, pm, analyst if insufficient
    </logic>

    # DESIGN NOTE: Challengers need aggressive questioning capability
    # TEA (test engineer) often best - quality mindset, finds edge cases
    # Innovation Strategist good - challenges business conventions
    # Architect good - technical depth to challenge architecture

    <action>Assign DEFENDERS (2-3 agents):</action>
    <logic>
      - Filter agents matching defender criteria (pm, dev, analyst, architect)
      - Score using weighted criteria (domain 40, evidence-based 30, experience 20, clarity 10)
      - Select top 2-3 agents
      - Fallback: dev, architect, pm if insufficient
    </logic>

    # DESIGN NOTE: Defenders need domain expertise AND willingness to concede
    # PM good - business logic knowledge
    # Dev good - implementation reality check
    # Analyst good - data-driven thinking

    <action>Assign BUILDERS (2-3 agents):</action>
    <logic>
      - Filter agents matching builder criteria (architect, innovation-strategist, creative-problem-solver)
      - Score using weighted criteria (creative 40, design 30, systems 20, pragmatic 10)
      - Select top 2-3 agents
      - Fallback: architect, dev, pm if insufficient
    </logic>

    # DESIGN NOTE: Builders need creativity AND technical feasibility judgment
    # Architect best - can design radically different solutions
    # Innovation Strategist good - novel business model thinking
    # Creative Problem Solver good - unconventional approaches

    <action>Assign FACILITATOR (1 agent):</action>
    <logic>
      - Filter for bmad-master, innovation-strategist, sm
      - Score synthesis capability highest
      - Select single best facilitator
      - Fallback: bmad-master always if available
    </logic>

    # DESIGN NOTE: Facilitator renders evidence-based verdicts
    # BMad Master ideal - meta-orchestration capability
    # Must judge: fundamental truth vs inherited assumption

    <check if="insufficient agents for cohorts">
      <action>Use fallback criteria</action>
      <action>Allow agent overlap between cohorts if necessary</action>
      <action>Log warning about suboptimal agent availability</action>
    </check>

    # DESIGN NOTE: Graceful degradation if limited agent roster
    # Better to continue with overlap than abort workflow

    <action>Store cohort assignments in memory:</action>
    <format>
      challengers: [agent1, agent2, agent3]
      defenders: [agent4, agent5, agent6]
      builders: [agent7, agent8, agent9]
      facilitator: agent10
    </format>

  </substep>

  <substep n="1b" goal="Present Framework Setup and Problem Statement">

    # DESIGN NOTE: Transparency about approach and agent roles
    # User understands what's about to happen before diving in

    <action>Display framework introduction:</action>
    <format>
      🧠 First Principles Thinking - Multi-Agent Challenge-Rebuild Cycle

      Problem/Current Approach:
      {{problem_statement}}

      Three-Phase Process:
      1. DECONSTRUCT: Challenge every assumption in current approach
      2. VALIDATE: Identify what's truly fundamental (physics, economics, data)
      3. RECONSTRUCT: Rebuild solution using ONLY validated fundamentals

      Agent Cohorts:

      ⚔️ CHALLENGERS (Destroy Assumptions):
      - [Agent Icon] [Agent Name] ([Agent Title])
      - [Agent Icon] [Agent Name] ([Agent Title])
      - [Agent Icon] [Agent Name] ([Agent Title])

      🛡️ DEFENDERS (Provide Evidence or Concede):
      - [Agent Icon] [Agent Name] ([Agent Title])
      - [Agent Icon] [Agent Name] ([Agent Title])
      - [Agent Icon] [Agent Name] ([Agent Title])

      🏗️ BUILDERS (Reconstruct from Fundamentals):
      - [Agent Icon] [Agent Name] ([Agent Title])
      - [Agent Icon] [Agent Name] ([Agent Title])
      - [Agent Icon] [Agent Name] ([Agent Title])

      🧠 FACILITATOR (Orchestrate and Render Verdicts):
      - [Agent Icon] [Agent Name] ([Agent Title])

      Ground Rules:
      - Challengers: Be aggressive. Demand evidence. "Prove it or lose it."
      - Defenders: Defend with evidence or concede gracefully. "Best practice" is NOT evidence.
      - Evidence Hierarchy: Physics > Economics > Engineering > Convention
      - Goal: 60%+ of assumptions discarded and radically different solution

      This will take 2-4 hours. Ready to begin? (yes/no)
    </format>

    # DESIGN NOTE: Setting expectations for time commitment
    # First Principles is SLOW - thorough questioning takes time
    # Users should plan accordingly

    <check if="user responds 'no' or requests changes">
      <action>Ask what they'd like to adjust</action>
      <action>Options: agent assignments, challenge intensity, problem statement</action>
      <action>Re-display setup after changes</action>
    </check>

    <check if="user confirms">
      <action>Proceed to Step 2: Phase 1 (Deconstruct)</action>
    </check>

  </substep>

</step>

# ═══════════════════════════════════════════════════════════════════

# STEP 2: PHASE 1 - DECONSTRUCT (Challenge Every Assumption)

# ═══════════════════════════════════════════════════════════════════

<step n="2" goal="Phase 1: Deconstruct - Surface and Challenge All Assumptions">

# DESIGN NOTE: This is the most critical phase

# If assumptions aren't fully surfaced and challenged, framework fails

# Facilitator must be relentless in pursuing hidden assumptions

<action>Announce phase transition:</action>
<format>
═══════════════════════════════════════════════════════════════════
PHASE 1: DECONSTRUCT - Challenge Every Assumption
═══════════════════════════════════════════════════════════════════

    Current Approach:
    {{problem_statement}}

    Goal: Surface EVERY assumption in this approach, then challenge each one aggressively.

    Process:
    1. Facilitator breaks approach into assumption clusters
    2. For each cluster:
       - Challengers attack assumptions
       - Defenders defend with evidence or concede
       - Facilitator renders verdict: Fundamental | Discarded | Needs Evidence

    Let's begin.

  </format>

  <substep n="2a" goal="Surface All Assumptions">

    # DESIGN NOTE: Facilitator must extract assumptions from problem statement
    # Both EXPLICIT assumptions (stated) and IMPLICIT assumptions (hidden)

    <action>Facilitator analyzes current approach and identifies assumptions:</action>

    <logic>
      Assumption types to surface:
      - Architectural: "Must use database," "Need three tiers," "Require API"
      - Business: "Users will pay monthly," "Need sales team," "Must have feature X"
      - Process: "Need approvals," "Require testing," "Must estimate first"
      - Technical: "Need async," "Must scale to X," "Require redundancy"
      - User: "Users won't wait >3sec," "Need mobile app," "Must be intuitive"
      - Constraint: "Budget is $X," "Timeline is Y," "Team size is Z"
    </logic>

    # DESIGN NOTE: Facilitator categorizes assumptions into clusters
    # Cluster = related assumptions that can be challenged together

    <action>Facilitator presents assumption clusters:</action>
    <format>
      [Facilitator Icon] [Facilitator Name]:

      I've identified the following assumption clusters in this approach:

      CLUSTER 1: Architecture Assumptions
      - Assumption A1: [Stated assumption]
      - Assumption A2: [Stated assumption]
      - Assumption A3: [Hidden assumption revealed]

      CLUSTER 2: Business Model Assumptions
      - Assumption B1: [Stated assumption]
      - Assumption B2: [Stated assumption]

      CLUSTER 3: User Behavior Assumptions
      - Assumption U1: [Stated assumption]
      - Assumption U2: [Hidden assumption]

      [... more clusters as needed]

      We'll challenge each cluster in turn. Let's start with CLUSTER 1.
    </format>

    # DESIGN NOTE: Clustering prevents overwhelming discussion
    # Tackle 3-5 related assumptions at a time

  </substep>

  <substep n="2b" goal="Challenge-Defend Cycle for Each Cluster" repeat="for-each-cluster">

    # DESIGN NOTE: This substep repeats for every assumption cluster
    # Pattern: Challenge → Defend → Verdict → Next Cluster

    <action>Facilitator introduces cluster for challenge:</action>
    <format>
      [Facilitator Icon] [Facilitator Name]:

      CLUSTER [N]: [Cluster Name]
      - [Assumption 1]
      - [Assumption 2]
      - [Assumption 3]

      Challengers, attack these assumptions. Demand evidence.
    </format>

    <action>Challengers question assumptions aggressively:</action>

    # DESIGN NOTE: Each challenger contributes from their expertise angle
    # TEA: "What breaks if this assumption is false?"
    # Architect: "What law of physics requires this?"
    # Innovation Strategist: "Who says we must do it this way?"

    <action>For each challenger in challengers:</action>

    <action>Generate aggressive challenge:</action>
    <context>
      - Agent's expertise informs angle of challenge
      - Challenge intensity from workflow config (default: aggressive)
      - Reference evidence hierarchy (physics > convention)
      - Use Socratic questioning patterns
    </context>

    <format>
      ⚔️ [Challenger Icon] [Challenger Name]:

      [Aggressive challenge to assumption]

      [Demand for evidence: "Prove it with physics, data, or math - not 'best practice'"]

      [Follow-up: "Why?" asked repeatedly]

      [Alternative suggestion to show assumption isn't necessary]

    </format>

    # DESIGN NOTE: Challengers don't hold back
    # Language like "Prove it or lose it" is appropriate
    # Goal: Make defenders work HARD to justify assumptions

    <action>Trigger TTS for challenger</action>

    # DESIGN NOTE: TTS maintains engagement during long sessions

    <note>Challengers may build on each other's challenges:</note>
    <example>
      "[Challenger 1] is right to question that. Even worse: [additional challenge]"
    </example>

    # DESIGN NOTE: Challengers amplify each other, creating pressure

    <action>After all challengers contribute, defenders respond:</action>

    <action>For each defender in defenders:</action>

    <action>Generate evidence-based defense or graceful concession:</action>
    <context>
      - Agent's expertise provides domain knowledge
      - Evidence hierarchy guides response quality
      - If no evidence available, defender should concede
      - Conceding is SUCCESS, not failure
    </context>

    <format>
      🛡️ [Defender Icon] [Defender Name]:

      [Response to challenge]

      [Evidence provided: cite physics, data, economic principle, etc.]
      OR
      [Graceful concession: "I can't defend this with evidence. It's convention, not fundamental."]

      [If defending, explain WHY this is fundamental, not just THAT it exists]

    </format>

    # DESIGN NOTE: Strong defense examples:
    # "Need database because data exceeds RAM (500GB needed, 128GB available) - physics constraint"
    # "Must encrypt because GDPR legally requires it - regulatory fundamental"
    #
    # Weak defense examples (should concede):
    # "Everyone uses microservices" (bandwagon, not evidence)
    # "That's best practice" (convention, not fundamental)

    <action>Trigger TTS for defender</action>

    <check if="defender appeals to authority or convention">
      <action>Facilitator interrupts:</action>
      <format>
        [Facilitator Icon] [Facilitator Name]:
        "That's an appeal to convention, not evidence. Can you provide physics, data, or economic principle? If not, we must treat this as discarded assumption."
      </format>
    </check>

    # DESIGN NOTE: Facilitator enforces evidence standards
    # Prevents defenders from hiding behind "best practice"

    <check if="defender provides borderline evidence">
      <action>Facilitator asks deeper question:</action>
      <format>
        [Facilitator Icon] [Facilitator Name]:
        "That's interesting, but let's go deeper. WHY is that constraint real? Is it physics or is it choice?"
      </format>
      <action>Repeat challenge-defend for this assumption until hitting bedrock</action>
    </check>

    # DESIGN NOTE: Socratic method - keep asking "why?" until:
    # - Hit fundamental truth (can't be further reduced), OR
    # - Defender concedes (assumption revealed as choice not constraint)

  </substep>

  <substep n="2c" goal="Facilitator Renders Verdict">

    # DESIGN NOTE: After challenge-defend cycle, facilitator decides
    # This is evidence-based verdict, not democratic vote

    <action>Facilitator evaluates evidence provided:</action>

    <logic>
      For each assumption in cluster:

      IF defender provided:
        - Physics/math/thermodynamics evidence → FUNDAMENTAL
        - Economics/biology/chemistry evidence → FUNDAMENTAL (with context)
        - Material/regulatory/empirical data → FUNDAMENTAL (scoped)
        - Engineering tradeoffs → DISCARDED (can be optimized differently)
        - Best practice/convention/competitor → DISCARDED (inherited belief)
        - No evidence → DISCARDED (default)

      IF challengers not satisfied with evidence → NEEDS MORE EVIDENCE

      IF assumption can be imagined away → DISCARDED (not fundamental)
    </logic>

    <action>Facilitator announces verdict:</action>
    <format>
      [Facilitator Icon] [Facilitator Name]:

      VERDICTS for CLUSTER [N]:

      Assumption [A1]: **FUNDAMENTAL**
      - Evidence: [Summarize defender's evidence]
      - Rationale: This is a law of physics/economics we cannot violate
      - Constraint for Phase 3: [How this constrains reconstruction]

      Assumption [A2]: **DISCARDED**
      - Reason: Defended with convention, not evidence
      - Revealed as: Choice/preference, not constraint
      - Implication: Phase 3 should explore alternatives

      Assumption [A3]: **NEEDS MORE EVIDENCE**
      - Current evidence: Plausible but insufficient data
      - Action: Treat as assumption for now, validate if crucial
      - Risk: May discover it's not fundamental during implementation

    </format>

    # DESIGN NOTE: Verdict format provides:
    # - Clear categorization (fundamental vs discarded)
    # - Evidence trail (why this verdict)
    # - Forward guidance (how this affects Phase 3)

    <action>Save checkpoint to template:</action>
    <checkpoint>
      cluster: [cluster_name]
      assumptions: [list of assumptions]
      challenges: [challenger contributions]
      defenses: [defender contributions]
      verdicts: [fundamental | discarded | needs_evidence]
      evidence: [evidence provided]
    </checkpoint>

    # DESIGN NOTE: Checkpoint after each cluster prevents context loss
    # Long sessions risk losing work if context runs out

    <check if="more clusters remain">
      <action>Proceed to next cluster</action>
      <goto>Substep 2b</goto>
    </check>

    <check if="all clusters processed">
      <action>Proceed to Phase 1 synthesis</action>
    </check>

  </substep>

  <substep n="2d" goal="Phase 1 Synthesis">

    # DESIGN NOTE: After all clusters challenged, facilitator summarizes
    # This transitions team from deconstruction to validation

    <action>Facilitator synthesizes Phase 1 results:</action>
    <format>
      [Facilitator Icon] [Facilitator Name]:

      PHASE 1 COMPLETE: Deconstruction Summary

      Total Assumptions Identified: [N]

      **FUNDAMENTAL TRUTHS** (Validated with Evidence):
      [List assumptions marked FUNDAMENTAL with evidence]

      **DISCARDED ASSUMPTIONS** (Convention, Not Constraint):
      [List assumptions marked DISCARDED with reason]

      **NEEDS MORE EVIDENCE** (Uncertain):
      [List assumptions marked NEEDS MORE EVIDENCE]

      Key Insights:
      - [% of assumptions discarded] - if <40%, we may not have been aggressive enough
      - [Patterns noticed in discarded assumptions]
      - [Surprising fundamentals that survived challenge]

      Next: Phase 2 will validate that our "fundamental truths" are REALLY fundamental.
    </format>

    # DESIGN NOTE: Success metric: 60%+ assumptions discarded
    # If most assumptions survived, either:
    # - Current approach is already optimal (rare), OR
    # - Challengers weren't aggressive enough, OR
    # - Defenders defended with convention not evidence

    <action>Save checkpoint to template:</action>
    <checkpoint>
      phase: phase_1_deconstruct
      total_assumptions: [N]
      fundamental_count: [N]
      discarded_count: [N]
      needs_evidence_count: [N]
      key_insights: [text]
    </checkpoint>

  </substep>

</step>

# ═══════════════════════════════════════════════════════════════════

# STEP 3: PHASE 2 - VALIDATE (Identify True Fundamentals)

# ═══════════════════════════════════════════════════════════════════

<step n="3" goal="Phase 2: Validate - Verify What's REALLY Fundamental">

# DESIGN NOTE: Phase 2 is shorter but critical

# Goal: Question the assumptions marked "FUNDAMENTAL" in Phase 1

# Just because an assumption survived Phase 1 doesn't mean it's bedrock

# Apply even deeper Socratic questioning

<action>Announce phase transition:</action>
<format>
═══════════════════════════════════════════════════════════════════
PHASE 2: VALIDATE - Verify True Fundamentals
═══════════════════════════════════════════════════════════════════

    Assumptions marked "FUNDAMENTAL" in Phase 1:
    [List assumptions from Phase 1 marked FUNDAMENTAL]

    Goal: Apply Socratic questioning to verify these are TRULY fundamental.
    Can we reduce them further? Are they laws of nature or still choices?

    Process:
    For each "fundamental":
    - Facilitator asks: "Is this REALLY fundamental?"
    - Challengers try to break it down further
    - Defenders provide deepest level evidence
    - Facilitator establishes bedrock truths

  </format>

  <substep n="3a" goal="Deep Validation of Each Fundamental" repeat="for-each-fundamental">

    # DESIGN NOTE: This substep repeats for each assumption marked FUNDAMENTAL
    # Apply deeper questioning than Phase 1

    <action>Facilitator selects one fundamental for deep validation:</action>
    <format>
      [Facilitator Icon] [Facilitator Name]:

      Let's validate: [Fundamental Assumption Text]

      Evidence from Phase 1: [Evidence that made us mark this FUNDAMENTAL]

      Question: Is this REALLY a fundamental truth? Or can we reduce it further?

      Challengers, try to break this down. What's the deeper constraint?
    </format>

    <action>Challengers attempt deeper reduction:</action>

    # DESIGN NOTE: Challengers ask: "What makes this true?"
    # Try to find the underlying constraint

    <action>For each challenger (subset, not all):</action>

    <format>
      ⚔️ [Challenger Icon] [Challenger Name]:

      [Attempt to reduce assumption to deeper level]

      [Ask: What physical law / economic principle / mathematical truth makes this necessary?]

      [Propose: If we had infinite X, would this still be true?]

    </format>

    # DESIGN NOTE: Infinite resource thought experiment helps identify true constraints
    # "If we had infinite money, would we still need to do X?"
    # If answer is "no," it's economic constraint, not physics
    # If answer is "yes," dig deeper for underlying reason

    <action>Defender provides deepest level explanation:</action>

    <format>
      🛡️ [Defender Icon] [Defender Name]:

      [Deepest level explanation of why this is fundamental]

      [Cite: Specific law of physics / economic principle / mathematical proof]

      [Or concede: This can be reduced further to [deeper constraint]]

    </format>

    <action>Facilitator applies Socratic method:</action>

    <logic>
      Ask "Why?" repeatedly until:
      - Hit bedrock (cannot be further reduced), OR
      - Discover hidden assumption beneath "fundamental"
    </logic>

    <format>
      [Facilitator Icon] [Facilitator Name]:

      [Ask: "Why is that true?"]
      [Listen to answer]
      [Ask: "Why is THAT true?"]
      [Listen to answer]
      [Ask: "Why is THAT true?"]
      [Continue until hitting bedrock or revealing hidden assumption]
    </format>

    # DESIGN NOTE: Bedrock indicators:
    # - Answer is tautology ("It's true because it's defined that way")
    # - Answer is law of nature ("Gravity exists")
    # - Answer is mathematical necessity ("2+2=4")

    <action>Facilitator renders validation verdict:</action>

    <format>
      [Facilitator Icon] [Facilitator Name]:

      VALIDATION VERDICT for [Assumption]:

      [Option 1: BEDROCK TRUTH]
      This is truly fundamental. Cannot be reduced further.
      Underlying principle: [Physics law / Economic principle / Math proof]
      Constraint for Phase 3: [Specific constraint this imposes]

      [Option 2: REDUCIBLE]
      This can be reduced to deeper constraint: [Deeper constraint]
      Update fundamental list to reflect actual bedrock truth.

      [Option 3: REVEALED AS ASSUMPTION]
      Deeper questioning revealed this isn't fundamental after all.
      Reclassify as DISCARDED. Reason: [Why it's not fundamental]
    </format>

    # DESIGN NOTE: It's okay to reclassify assumptions during Phase 2
    # Deeper thinking reveals some "fundamentals" aren't actually fundamental

    <action>Save checkpoint:</action>
    <checkpoint>
      fundamental_candidate: [assumption text]
      validation_verdict: [bedrock | reducible | reclassified]
      evidence: [deepest level evidence]
      constraint: [how this constrains Phase 3]
    </checkpoint>

    <check if="more fundamentals to validate">
      <action>Proceed to next fundamental</action>
      <goto>Substep 3a</goto>
    </check>

  </substep>

  <substep n="3b" goal="Establish Bedrock Truth List">

    # DESIGN NOTE: After validating all fundamentals, create final list
    # This list is the ONLY foundation for Phase 3 reconstruction

    <action>Facilitator compiles validated bedrock truths:</action>
    <format>
      [Facilitator Icon] [Facilitator Name]:

      PHASE 2 COMPLETE: Validated Fundamental Truths

      After deep Socratic questioning, these are our bedrock truths:

      **BEDROCK TRUTH 1:** [Truth statement]
      - Type: [Physics | Economics | Biology | Math | Regulatory]
      - Evidence: [Specific law / principle / proof]
      - Constraint: [What this means for solutions]

      **BEDROCK TRUTH 2:** [Truth statement]
      - Type: [...]
      - Evidence: [...]
      - Constraint: [...]

      [Continue for all validated fundamentals]

      RECLASSIFICATIONS:
      [List any Phase 1 "fundamentals" that were reclassified as discarded]

      These bedrock truths are the ONLY constraints on Phase 3 reconstruction.
      Everything else is negotiable.

      Next: Phase 3 will rebuild solution using ONLY these bedrock truths.
    </format>

    # DESIGN NOTE: Bedrock truth list typically 3-8 items
    # If more than 10, probably haven't reduced enough
    # If fewer than 3, may have been too aggressive (or problem genuinely simple)

    <action>Save checkpoint to template:</action>
    <checkpoint>
      phase: phase_2_validate
      bedrock_truths: [list of validated fundamentals]
      reclassifications: [any changes from Phase 1]
      constraints_for_phase_3: [how truths constrain reconstruction]
    </checkpoint>

  </substep>

</step>

# ═══════════════════════════════════════════════════════════════════

# STEP 4: PHASE 3 - RECONSTRUCT (Rebuild from Fundamentals)

# ═══════════════════════════════════════════════════════════════════

<step n="4" goal="Phase 3: Reconstruct - Build New Solution from Bedrock Truths">

# DESIGN NOTE: This is where breakthrough happens

# Builders work with ONLY bedrock truths from Phase 2

# Goal: Radically different solution that respects constraints

<action>Announce phase transition:</action>
<format>
═══════════════════════════════════════════════════════════════════
PHASE 3: RECONSTRUCT - Rebuild from Fundamentals
═══════════════════════════════════════════════════════════════════

    Bedrock Truths (Our ONLY Constraints):
    [List bedrock truths from Phase 2]

    Discarded Assumptions (We Are FREE to Ignore These):
    [List discarded assumptions from Phase 1]

    Goal: Design solution that:
    - Respects ALL bedrock truths
    - Uses NONE of the discarded assumptions
    - Is SIMPLER than original approach
    - Achieves same outcome via different path

    Builders, you have creative freedom. Propose radically different approaches.

  </format>

  <substep n="4a" goal="Generate Alternative Solutions">

    # DESIGN NOTE: Each builder proposes different approach
    # Diversity of proposals increases chance of breakthrough

    <action>For each builder in builders:</action>

    <action>Generate novel solution approach:</action>
    <context>
      - Start from scratch, don't modify old solution
      - Use ONLY bedrock truths from Phase 2
      - If old solution had component X and it wasn't in bedrock truths, don't include X
      - Simplicity is goal - fewest components that respect constraints
      - Agent's expertise informs type of solution (technical, business, process)
    </context>

    <format>
      🏗️ [Builder Icon] [Builder Name]:

      PROPOSED APPROACH: [Catchy name]

      Core Idea:
      [One paragraph describing fundamentally different approach]

      How It Respects Bedrock Truths:
      - Bedrock Truth 1: [How design respects this constraint]
      - Bedrock Truth 2: [How design respects this constraint]
      [... for all bedrock truths]

      How It Differs from Original:
      [Bullet points showing radical departures]

      Why This Could Work:
      [Reasoning for why simpler/cheaper/faster]

      Potential Concerns:
      [Honest assessment of risks or uncertainties]

    </format>

    # DESIGN NOTE: Builders are honest about concerns
    # Not trying to "sell" their approach, presenting it for evaluation

    <action>Trigger TTS for builder</action>

    <note>Builders may build on each other's ideas:</note>
    <example>
      "I like [Builder 1]'s core idea. What if we combined that with [variation]?"
    </example>

    # DESIGN NOTE: Combinatorial innovation - mixing builder ideas
    # Often best solution is hybrid of multiple proposals

  </substep>

  <substep n="4b" goal="Validate No Discarded Assumptions Crept Back In">

    # DESIGN NOTE: Critical check - ensure builders didn't reintroduce old assumptions
    # Human tendency to fall back on familiar patterns

    <action>Facilitator and challengers verify each proposed solution:</action>

    <action>For each builder's proposal:</action>

    <format>
      [Facilitator Icon] [Facilitator Name]:

      Let's verify [Builder Name]'s proposal doesn't reintroduce discarded assumptions.

      Challengers, check: Does this proposal use any of the discarded assumptions?
    </format>

    <action>Challengers scrutinize proposal:</action>

    <logic>
      For each discarded assumption:
      - Does proposal include this in any form?
      - If yes, flag it
      - If no, approve that aspect
    </logic>

    <format>
      ⚔️ [Challenger Icon] [Challenger Name]:

      [Check 1: Discarded assumption X → Confirmed NOT in proposal]
      [Check 2: Discarded assumption Y → Confirmed NOT in proposal]
      [Check 3: Discarded assumption Z → FLAG: Proposal includes this! [Explain how]]

    </format>

    <check if="challengers flag discarded assumption in proposal">
      <action>Facilitator asks builder to revise:</action>
      <format>
        [Facilitator Icon] [Facilitator Name]:
        "[Builder Name], [Challenger Name] is right - your proposal includes [discarded assumption]. Can you revise to eliminate that?"
      </format>

      <action>Builder revises proposal to remove flagged assumption</action>
    </check>

    # DESIGN NOTE: This iterative refinement catches subtle reintroductions
    # "We don't need X" → proposal includes Y which depends on X → caught

    <check if="proposal passes validation">
      <action>Facilitator approves:</action>
      <format>
        [Facilitator Icon] [Facilitator Name]:
        "This proposal successfully uses only bedrock truths. Approved for consideration."
      </format>
    </check>

  </substep>

  <substep n="4c" goal="Synthesize and Select Approach">

    # DESIGN NOTE: After all builders propose and validate, facilitator synthesizes
    # May select single best approach or create hybrid

    <action>Facilitator synthesizes builder proposals:</action>
    <format>
      [Facilitator Icon] [Facilitator Name]:

      PHASE 3 SYNTHESIS: Proposed Approaches

      We have [N] validated proposals:

      **PROPOSAL 1: [Name]** by [Builder]
      - Core idea: [Summary]
      - Key innovation: [What makes it different]
      - Strengths: [Why it could work]
      - Risks: [Concerns]

      **PROPOSAL 2: [Name]** by [Builder]
      - Core idea: [Summary]
      - Key innovation: [What makes it different]
      - Strengths: [Why it could work]
      - Risks: [Concerns]

      [... for all proposals]

      RECOMMENDED APPROACH:
      [Option A: Single best proposal]
      [Option B: Hybrid combining elements of multiple proposals]
      [Option C: Present all to user for selection]

      Rationale:
      [Why this recommendation based on bedrock truths and feasibility]
    </format>

    # DESIGN NOTE: Facilitator uses judgment to synthesize
    # If proposals very different, present multiple
    # If proposals similar, identify best one
    # If complementary, suggest hybrid

    <action>Save checkpoint to template:</action>
    <checkpoint>
      phase: phase_3_reconstruct
      proposals: [all builder proposals]
      validation_results: [checker feedback]
      recommended_approach: [facilitator synthesis]
    </checkpoint>

  </substep>

</step>

# ═══════════════════════════════════════════════════════════════════

# STEP 5: COMPARISON & SYNTHESIS

# ═══════════════════════════════════════════════════════════════════

<step n="5" goal="Compare Old Approach vs First Principles Approach">

# DESIGN NOTE: This step articulates VALUE of First Principles thinking

# Shows concretely how new approach is superior

<action>Facilitator creates comparison analysis:</action>
<format>
[Facilitator Icon] [Facilitator Name]:

    ═══════════════════════════════════════════════════════════════════
    FIRST PRINCIPLES ANALYSIS COMPLETE: Comparison
    ═══════════════════════════════════════════════════════════════════

    **ORIGINAL APPROACH:**
    [Summary of original approach/problem statement]

    Assumptions That Were Discarded:
    - [Assumption 1]: Revealed as [convention/choice] not [constraint]
    - [Assumption 2]: Revealed as [inherited belief] not [fundamental]
    - [Assumption 3]: Revealed as [can be optimized differently]

    **FIRST PRINCIPLES APPROACH:**
    [Summary of reconstructed solution]

    Bedrock Truths Respected:
    - [Bedrock Truth 1]: [How new solution respects this]
    - [Bedrock Truth 2]: [How new solution respects this]

    KEY DIFFERENCES:

    | Dimension | Original Approach | First Principles Approach | Why Different |
    |-----------|-------------------|---------------------------|---------------|
    | Cost | [Original cost] | [FP cost] | [Discarded assumption that added cost] |
    | Complexity | [Original complexity] | [FP complexity] | [Discarded assumption that added complexity] |
    | Time | [Original timeline] | [FP timeline] | [Discarded assumption that slowed process] |
    | Performance | [Original performance] | [FP performance] | [Optimization enabled by discarding assumption] |

    BREAKTHROUGH INSIGHTS:

    1. [Key insight 1]: We discovered [assumption] wasn't fundamental
       - Implication: [What this enables]

    2. [Key insight 2]: We validated [bedrock truth] is truly constraining
       - Implication: [What we can't avoid but now understand why]

    3. [Key insight 3]: New approach is [X]% simpler/cheaper/faster
       - Root cause: [Which discarded assumptions created bloat]

    RECOMMENDED NEXT STEPS:

    1. [Immediate action]: [Validate key assumption if marked "needs more evidence"]
    2. [Short-term]: [Prototype or test First Principles approach]
    3. [Medium-term]: [Implement if prototype successful]
    4. [Ongoing]: [Apply First Principles thinking to other areas]

  </format>

# DESIGN NOTE: Comparison table shows concrete improvements

# Breakthrough insights explain WHY new approach is superior

# Next steps provide action plan

<action>Save final comprehensive checkpoint to template:</action>
<checkpoint>
phase: complete
original_approach: [description]
discarded_assumptions: [list with rationale]
bedrock_truths: [validated fundamentals]
reconstructed_solution: [new approach]
comparison_analysis: [table and insights]
recommended_next_steps: [action items]
</checkpoint>

</step>

# ═══════════════════════════════════════════════════════════════════

# STEP 6: CLOSING & NEXT STEPS

# ═══════════════════════════════════════════════════════════════════

<step n="6" goal="Close Session and Plan Implementation">

<action>Facilitator provides closing:</action>
<format>
[Facilitator Icon] [Facilitator Name]:

    This concludes our First Principles Thinking session.

    Session summary has been saved to: {{template_output_path}}

    RESULTS:
    - Total assumptions challenged: [N]
    - Discarded as non-fundamental: [N] ([X]%)
    - Validated as bedrock truths: [N]
    - New approach differs from original by: [key differences]

    SUCCESS CRITERIA:
    ✅ [Check 1]: [60%+ assumptions discarded] - [YES/NO]
    ✅ [Check 2]: [New solution substantially different] - [YES/NO]
    ✅ [Check 3]: [Every component traceable to fundamental] - [YES/NO]
    ✅ [Check 4]: [Team understands WHY old approach was suboptimal] - [YES/NO]
    ✅ [Check 5]: [Cost/complexity/performance improved] - [YES/NO]

    Would you like to:
    - Review specific assumptions or verdicts?
    - Dive deeper into one proposal from Phase 3?
    - Apply First Principles to a different aspect of the problem?
    - Move forward with prototyping the new approach?

  </format>

# DESIGN NOTE: Success criteria from Section 2 Framework Philosophy

# Validates whether session achieved framework goals

  <check if="user wants to review specific parts">
    <action>Facilitator navigates to requested section</action>
    <action>May involve re-challenging assumptions or refining proposals</action>
  </check>

  <check if="user wants to apply to different aspect">
    <action>Return to Step 1 with new problem statement</action>
    <action>Reuse same agent assignments if appropriate</action>
  </check>

  <check if="user satisfied with session">
    <action>2-3 agents provide characteristic farewells:</action>
    <format>
      ⚔️ [Challenger Icon] [Challenger Name]: [Brief farewell in their challenging voice]
      🛡️ [Defender Icon] [Defender Name]: [Brief farewell acknowledging what was learned]
      🏗️ [Builder Icon] [Builder Name]: [Brief farewell excited about new approach]
    </format>
    <action>Exit workflow</action>
  </check>

# DESIGN NOTE: Graceful exit maintains agent personality

# Consistent with party-mode and Six Hats farewell patterns

</step>

</workflow>

# ═══════════════════════════════════════════════════════════════════

# EXECUTION GUIDELINES

# ═══════════════════════════════════════════════════════════════════

<guidelines>

  <guideline name="Evidence Hierarchy Enforcement">
    Strictly enforce evidence standards. Do not accept:
    - "That's best practice" (unless defender can cite underlying principle)
    - "Everyone does it this way" (bandwagon, not evidence)
    - "My experience suggests" (anecdote, not data)
    - "Industry standard" (convention, may be cargo cult)

    Only accept:
    - Physics, mathematics, thermodynamics (laws of nature)
    - Economics, biology (strong empirical principles)
    - Regulatory requirements (legal mandates)
    - Reproducible data (measured, not assumed)

  </guideline>

# DESIGN NOTE: This is THE most important guideline

# Framework fails if evidence standards slip

  <guideline name="Challenger Aggression">
    Challengers must be AGGRESSIVE. This is NOT a collaborative brainstorming session.
    - Interrupt defenders appealing to authority
    - Demand evidence repeatedly
    - Use language like "Prove it or lose it"
    - Don't back down if defender becomes defensive

    Facilitator must protect this dynamic. Politeness undermines framework.

  </guideline>

# DESIGN NOTE: Psychological safety = good in general

# But First Principles requires CONTROLLED CONFLICT to work

# Must challenge assumptions aggressively or they survive unchallenged

  <guideline name="Defender Permission to Concede">
    Defenders must understand: CONCEDING IS SUCCESS, NOT FAILURE.
    - If you can't defend with evidence, SAY SO immediately
    - Don't waste time defending undefendable
    - Admitting "I thought this was fundamental but it's not" helps team

    Facilitator must reinforce this. Thank defenders who concede gracefully.

  </guideline>

# DESIGN NOTE: Cultural shift required

# People default to defending their position

# Must explicitly give permission to let go

  <guideline name="Rebuild Constraint">
    Builders can ONLY use validated bedrock truths from Phase 2.
    - If component wasn't in bedrock truth list, it's not allowed
    - No "and then we add X because it's standard"
    - Facilitator and challengers verify no discarded assumptions crept back

    This constraint is what generates breakthrough solutions.

  </guideline>

# DESIGN NOTE: This is what makes First Principles work

# Forcing rebuild from scratch = innovation

# Allowing "old solution + tweaks" = incremental thinking

  <guideline name="Checkpoint Protocol">
    Save to template after EVERY assumption cluster in Phase 1.
    First Principles sessions are LONG (2-4 hours typical).
    Context loss would be catastrophic - all work lost.

    Template checkpoints ensure:
    - Work preserved even if session interrupted
    - User has artifact documenting journey
    - Can resume if needed

  </guideline>

# DESIGN NOTE: Non-negotiable protocol

# Losing 2 hours of First Principles work destroys trust

  <guideline name="Time Management">
    First Principles is SLOW by design. Don't rush.
    - Phase 1 (Deconstruct): 60-90 minutes for 10-15 assumptions
    - Phase 2 (Validate): 20-30 minutes for 3-5 fundamentals
    - Phase 3 (Reconstruct): 45-60 minutes for proposals and validation

    Total: 2-4 hours is normal.

    If session becoming too long, facilitator can:
    - Focus on highest-impact assumption clusters
    - Table low-priority assumptions
    - Schedule continuation session

  </guideline>

# DESIGN NOTE: Users must commit time upfront

# Rushing defeats the purpose

</guidelines>

# ═══════════════════════════════════════════════════════════════════

# ERROR HANDLING & EDGE CASES

# ═══════════════════════════════════════════════════════════════════

<error-handling>

  <scenario name="Challengers not aggressive enough">
    <if>Challengers being too polite or accepting weak evidence</if>
    <then>
      - Facilitator intervenes: "Let's increase challenge intensity. [Challenger], I want you to be MORE aggressive here."
      - Example: "[Challenger], that defender just said 'best practice' - that's not evidence. Push back."
      - If challengers still too gentle, facilitator takes challenger role temporarily
    </then>
  </scenario>

  <scenario name="Defenders won't concede weak assumptions">
    <if>Defenders defending indefensible with stubbornness</if>
    <then>
      - Facilitator renders verdict despite defender protest
      - Example: "I understand you believe this, but convention isn't evidence. Verdict: DISCARDED."
      - Explain: "We're not saying you're wrong to have used this before. We're asking: Is it FUNDAMENTAL?"
    </then>
  </scenario>

# DESIGN NOTE: Facilitator has final say

# Not democratic process - evidence-based verdicts

  <scenario name="Most assumptions survive Phase 1">
    <if>Less than 40% of assumptions discarded</if>
    <then>
      - Facilitator pauses: "We've only discarded [N]% of assumptions. That suggests either:"
      - "(A) Current approach is already optimal [rare], OR"
      - "(B) We're not challenging aggressively enough [likely]"
      - Restate challenge intensity expectations
      - Select 2-3 "fundamental" assumptions and re-challenge them harder
    </then>
  </scenario>

  <scenario name="New solution looks like old solution">
    <if>Phase 3 proposals are incremental modifications of original</if>
    <then>
      - Facilitator rejects proposals: "These are modifications, not reconstructions."
      - Remind builders: "Use ONLY bedrock truths. Start from zero."
      - Example: "Imagine you're designing this for the first time ever. No history. What would you do?"
    </then>
  </scenario>

# DESIGN NOTE: This happens when builders unconsciously revert to familiar patterns

# Must explicitly force clean-slate thinking

  <scenario name="Context approaching limit">
    <if>Session very long and context nearing capacity</if>
    <then>
      - Facilitator: "We're approaching context limits. Let me save comprehensive checkpoint..."
      - Save full checkpoint to template with all work so far
      - Provide summary of progress: phases complete, key findings
      - Offer: Continue in new session OR conclude with partial analysis
    </then>
  </scenario>

# DESIGN NOTE: Graceful degradation

# Template checkpoint ensures work isn't lost

  <scenario name="User asks to skip phase">
    <if>User wants to skip Phase 1 or Phase 2</if>
    <then>
      - Facilitator explains why phase is critical:
      - "Phase 1 surfaces assumptions - without it, we're guessing"
      - "Phase 2 validates fundamentals - without it, Phase 3 may violate physics"
      - If user insists, proceed but note risk in output
    </then>
  </scenario>

</error-handling>

# ═══════════════════════════════════════════════════════════════════

# CUSTOMIZATION POINTS

# ═══════════════════════════════════════════════════════════════════

<customization>

  <point name="Challenge Intensity">
    Default: aggressive

    Can be adjusted in workflow.yaml:
    - gentle: Polite questioning (not recommended - undermines framework)
    - moderate: Standard Socratic method
    - aggressive: Relentless challenge (recommended)

    User can request adjustment mid-session:
    "Make challenges more/less aggressive"

  </point>

  <point name="Agent Count Per Cohort">
    Default: 2-3 per cohort

    Can be customized based on:
    - Available agent roster
    - Time constraints (fewer = faster)
    - Problem complexity (more = deeper analysis)

    Minimum: 1 challenger, 1 defender, 1 builder, 1 facilitator
    Maximum: 3-4 per cohort (more creates diminishing returns)

  </point>

  <point name="Evidence Standards">
    Default: Physics > Economics > Engineering > Convention

    Can adjust evidence hierarchy in workflow.yaml if domain requires:
    - Scientific domain: Physics/Chemistry highest tier
    - Business domain: Economics/Market data highest tier
    - Regulatory domain: Legal requirements highest tier

    But ALWAYS reject "best practice" as insufficient evidence.

  </point>

  <point name="Phase Time Allocation">
    Default timing (total 2-4 hours):
    - Phase 1: 60-90 minutes
    - Phase 2: 20-30 minutes
    - Phase 3: 45-60 minutes

    Can be adjusted if:
    - Express session needed (focus highest-impact clusters)
    - Deep dive wanted (extend Phase 1 to challenge more assumptions)

  </point>

</customization>

---

### DESIGN PATTERN SUMMARY

This workflow demonstrates all key patterns for multi-agent First Principles thinking:

1. **Three-Phase Cycle** (Section 2): Deconstruct → Validate → Reconstruct
2. **Evidence-Based Verdicts** (Section 3): Physics > convention, facilitator final say
3. **Challenger-Defender Dynamic** (Section 3): Aggressive challenge, graceful concession
4. **Checkpoint Protocol** (All phases): Save after each cluster prevents context loss
5. **Rebuild Constraint** (Phase 3): Use ONLY validated fundamentals, no old assumptions
6. **Validation Loop** (Phase 3): Verify discarded assumptions didn't creep back in

Every XML pattern, every evidence standard, every facilitation intervention is intentional and documented.
```

---

### 4.4 Annotated template.md

This template captures the complete First Principles session output, progressively populated through checkpoint protocol as each phase completes.

```markdown
# First Principles Thinking Session Report

**Generated:** {{date}}
**Facilitator:** {{facilitator_name}}
**Problem Statement:** {{problem_statement}}

---

## Session Overview

**Framework:** First Principles Thinking (Aristotelian reasoning from fundamental truths)
**Duration:** {{session_duration}}
**Total Assumptions Analyzed:** {{total_assumptions}}

**Participating Agents:**

### ⚔️ Challengers (Destroy Assumptions)

{{#each challengers}}

- {{icon}} {{displayName}} ({{title}})
  {{/each}}

### 🛡️ Defenders (Provide Evidence or Concede)

{{#each defenders}}

- {{icon}} {{displayName}} ({{title}})
  {{/each}}

### 🏗️ Builders (Reconstruct from Fundamentals)

{{#each builders}}

- {{icon}} {{displayName}} ({{title}})
  {{/each}}

### 🧠 Facilitator (Orchestrate and Synthesize)

- {{facilitator_icon}} {{facilitator_name}} ({{facilitator_title}})

---

<!--
DESIGN NOTE: Template Structure Philosophy

First Principles template documents the JOURNEY from assumptions to fundamentals to breakthrough:
- Phase 1: Shows every assumption challenged and verdict
- Phase 2: Shows validation of "fundamentals" to true bedrock
- Phase 3: Shows reconstructed solution using only bedrock truths
- Comparison: Shows why new approach is superior to original

This is an EDUCATIONAL artifact - future teams can see:
- What assumptions were challenged
- What evidence was provided (or lack thereof)
- Why some assumptions were discarded
- How bedrock truths constrained reconstruction
- What breakthrough insights emerged
-->

## Current Approach Analysis

### Original Approach Description

{{original_approach_description}}

<!--
DESIGN NOTE: Capture detailed description of current approach
This becomes the baseline for comparison after First Principles analysis

Should include:
- Current architecture/process/business model
- Key components and their relationships
- Existing constraints and limitations
- Why this approach was chosen initially
-->

### Initial Assumptions Identified

The facilitator identified the following assumptions embedded in the current approach:

{{#each assumption_clusters}}

#### Cluster {{cluster_number}}: {{cluster_name}}

{{#each assumptions}}

- **{{assumption_id}}**: {{assumption_text}}
  {{/each}}

{{/each}}

**Total Initial Assumptions:** {{total_assumptions}}

<!--
DESIGN NOTE: This list is the starting point for Phase 1
Facilitator extracts both explicit (stated) and implicit (hidden) assumptions
Clustering related assumptions makes challenge-defend cycles manageable
-->

---

## 💥 Phase 1: Deconstruct - Challenge Every Assumption

**Phase Goal:** Surface and challenge all assumptions. Distinguish fundamental truths from inherited beliefs.

**Challenge Intensity:** {{challenge_intensity}} (gentle | moderate | aggressive)

**Evidence Standard:** {{evidence_standard}}

- Highest tier: Physics, mathematics, thermodynamics
- High tier: Economics, biology, regulatory requirements
- Medium tier: Engineering constraints, material properties
- Low tier: Best practices, industry norms
- Insufficient: "That's how it's always done"

<!--
DESIGN NOTE: Phase 1 is the LONGEST phase (60-90 min typical)
Each assumption cluster goes through challenge-defend-verdict cycle
Template captures full conversation for each cluster
-->

{{#each assumption_clusters}}

### Cluster {{cluster_number}}: {{cluster_name}}

**Assumptions in this cluster:**
{{#each assumptions}}

- {{assumption_id}}: {{assumption_text}}
  {{/each}}

#### Challenge Round

{{#each challenger_contributions}}
**⚔️ {{challenger_name}}:**

{{challenge_text}}

<!--
DESIGN NOTE: Capture aggressive challenges verbatim
Shows what questions were asked, what evidence was demanded
Demonstrates Socratic method in action
-->

{{/each}}

#### Defense Round

{{#each defender_contributions}}
**🛡️ {{defender_name}}:**

{{defense_text}}

**Evidence Provided:** {{evidence_type}} - {{evidence_description}}

<!--
DESIGN NOTE: Capture defense attempts and evidence quality
Shows whether defender provided:
- High-tier evidence (physics, data, economics)
- Low-tier evidence (best practice, convention)
- No evidence (conceded gracefully)
-->

{{/each}}

#### Facilitator Verdict

**🧠 {{facilitator_name}}:**

{{verdict_reasoning}}

**Verdicts:**

{{#each assumption_verdicts}}

- **{{assumption_id}}**: **{{verdict}}** (FUNDAMENTAL | DISCARDED | NEEDS MORE EVIDENCE)
  - Rationale: {{verdict_rationale}}
  - Evidence: {{evidence_summary}}
    {{#if verdict == "FUNDAMENTAL"}}
  - Constraint for Phase 3: {{constraint_description}}
    {{/if}}
    {{#if verdict == "DISCARDED"}}
  - Revealed as: {{revealed_as}} (Choice | Convention | Inherited belief | Engineering tradeoff)
  - Implication: {{implication_for_reconstruction}}
    {{/if}}
    {{/each}}

<!--
DESIGN NOTE: Verdict format provides:
- Clear categorization (fundamental/discarded/needs-evidence)
- Evidence trail showing WHY this verdict
- Forward guidance for Phase 3 (what this means for reconstruction)
-->

---

{{/each}}

### Phase 1 Summary

**Total Assumptions Analyzed:** {{total_assumptions}}

**Categorization Results:**

| Verdict             | Count                    | Percentage                     |
| ------------------- | ------------------------ | ------------------------------ |
| FUNDAMENTAL         | {{fundamental_count}}    | {{fundamental_percentage}}%    |
| DISCARDED           | {{discarded_count}}      | {{discarded_percentage}}%      |
| NEEDS MORE EVIDENCE | {{needs_evidence_count}} | {{needs_evidence_percentage}}% |

<!--
DESIGN NOTE: Success metric: 60%+ discarded
If most assumptions survived, either:
- Current approach already optimal (rare)
- Challenges weren't aggressive enough (likely)
- Defenders defended with convention not evidence (problem)
-->

**Assumptions Marked FUNDAMENTAL (To Be Validated in Phase 2):**
{{#each fundamental_assumptions}}

- {{assumption_text}}
  - Evidence: {{evidence_provided}}
    {{/each}}

**Assumptions DISCARDED (Free to Ignore in Phase 3):**
{{#each discarded_assumptions}}

- {{assumption_text}}
  - Reason: {{discard_reason}}
    {{/each}}

**Key Insights from Phase 1:**
{{#each phase1_insights}}

- {{insight}}
  {{/each}}

---

## 🔬 Phase 2: Validate - Verify What's REALLY Fundamental

**Phase Goal:** Apply Socratic questioning to assumptions marked "FUNDAMENTAL" in Phase 1. Reduce to bedrock truths.

**Method:** For each "fundamental," ask: "Is this REALLY fundamental? Can we reduce it further?"

<!--
DESIGN NOTE: Phase 2 is SHORTER but critical (20-30 min typical)
Goal: Question the "fundamentals" from Phase 1
Many assumptions marked "fundamental" in Phase 1 get reduced or reclassified
This prevents false constraints in Phase 3
-->

{{#each fundamental_validation_rounds}}

### Validation Round {{round_number}}: {{fundamental_candidate}}

**Evidence from Phase 1:** {{phase1_evidence}}

#### Deep Challenge

{{#each deep_challenges}}
**⚔️ {{challenger_name}}:**

{{deep_challenge_text}}

<!--
DESIGN NOTE: Deeper questioning than Phase 1
"What makes this true? What law of nature / economic principle / mathematical truth?"
"If we had infinite X, would this still be necessary?"
-->

{{/each}}

#### Deepest Level Defense

{{#each deepest_defenses}}
**🛡️ {{defender_name}}:**

{{deepest_defense_text}}

**Underlying Principle:** {{underlying_principle}}

<!--
DESIGN NOTE: Defender must cite:
- Specific law of physics
- Economic principle
- Mathematical necessity
- Or concede this can be reduced further
-->

{{/each}}

#### Facilitator Socratic Questioning

**🧠 {{facilitator_name}}:**

{{socratic_questioning_transcript}}

<!--
DESIGN NOTE: Facilitator asks "Why?" repeatedly:
Why is that true? → [Answer] → Why is THAT true? → [Answer] → Why is THAT true?
Continue until hitting bedrock (tautology, law of nature, math necessity)
-->

#### Validation Verdict

**{{verdict}}** (BEDROCK TRUTH | REDUCIBLE | RECLASSIFIED AS ASSUMPTION)

{{#if verdict == "BEDROCK TRUTH"}}
**Underlying Principle:** {{bedrock_principle}}
**Type:** {{bedrock_type}} (Physics | Economics | Biology | Mathematics | Regulatory)
**Constraint for Phase 3:** {{bedrock_constraint}}

<!--
DESIGN NOTE: Bedrock truth cannot be further reduced
This is a REAL constraint that Phase 3 must respect
-->

{{/if}}

{{#if verdict == "REDUCIBLE"}}
**Reduces to deeper constraint:** {{deeper_constraint}}
**Updated fundamental:** {{updated_fundamental_text}}

<!--
DESIGN NOTE: Original assumption was surface-level
Deeper questioning revealed the TRUE underlying constraint
Update fundamental list to reflect actual bedrock
-->

{{/if}}

{{#if verdict == "RECLASSIFIED"}}
**Reclassified as:** DISCARDED
**Reason:** {{reclassification_reason}}
**Implication:** {{reclassification_implication}}

<!--
DESIGN NOTE: Deeper thinking revealed this wasn't fundamental after all
It's okay to reclassify - better to discover now than after reconstruction
-->

{{/if}}

---

{{/each}}

### Phase 2 Summary: Validated Bedrock Truths

After deep Socratic questioning, these are our TRUE fundamental constraints:

{{#each bedrock_truths}}

#### Bedrock Truth {{truth_number}}: {{truth_statement}}

- **Type:** {{truth_type}} (Physics | Economics | Biology | Mathematics | Regulatory)
- **Evidence:** {{evidence_description}}
- **Underlying Principle:** {{underlying_principle}}
- **Constraint:** {{constraint_description}}
- **Why This Matters:** {{why_matters}}

<!--
DESIGN NOTE: Each bedrock truth includes:
- The constraint itself
- Type (helps understand how negotiable it is - physics isn't, economics may be)
- Evidence (specific law/principle/proof)
- Constraint (what this means for solutions)
- Why matters (helps builders understand importance)
-->

{{/each}}

**Reclassifications from Phase 1:**
{{#each reclassifications}}

- **{{original_fundamental}}** → DISCARDED
  - Reason: {{reclassification_reason}}
    {{/each}}

**Total Bedrock Truths:** {{bedrock_truth_count}}

<!--
DESIGN NOTE: Typical count: 3-8 bedrock truths
If >10, probably haven't reduced enough
If <3, may have been too aggressive (or problem genuinely simple)
-->

---

## 🏗️ Phase 3: Reconstruct - Rebuild from Bedrock Truths

**Phase Goal:** Design solution using ONLY validated bedrock truths from Phase 2. Ignore all discarded assumptions.

**Constraint:** If a component wasn't in the bedrock truth list, it's not allowed in the new solution.

**Freedom:** All discarded assumptions can be ignored. Explore radically different approaches.

<!--
DESIGN NOTE: Phase 3 is where BREAKTHROUGH happens (45-60 min typical)
Builders work with clean slate, constrained only by bedrock truths
Goal: Solution that respects physics/economics but ignores convention
-->

### Builder Proposals

{{#each builder_proposals}}

#### Proposal {{proposal_number}}: {{proposal_name}}

**Proposed by:** 🏗️ {{builder_name}}

**Core Idea:**

{{core_idea_description}}

<!--
DESIGN NOTE: One paragraph describing fundamentally different approach
Should sound radical compared to original approach
-->

**How It Respects Bedrock Truths:**

{{#each bedrock_truth_compliance}}

- **Bedrock Truth {{truth_number}}**: {{truth_statement}}
  - How proposal respects this: {{compliance_explanation}}
    {{/each}}

<!--
DESIGN NOTE: Explicit mapping to each bedrock truth
Shows proposal isn't violating physics/economics
-->

**Key Differences from Original Approach:**

{{#each key_differences}}

- {{difference_description}}
  {{/each}}

<!--
DESIGN NOTE: Bullet points showing radical departures
"Original had X, new approach eliminates X entirely"
"Original assumed Y, new approach does Z instead"
-->

**Why This Could Work:**

{{reasoning}}

<!--
DESIGN NOTE: Builder's reasoning for why simpler/cheaper/faster
Not selling, just presenting logic
-->

**Potential Concerns:**

{{#each concerns}}

- {{concern_description}}
  {{/each}}

<!--
DESIGN NOTE: Honest assessment of risks/uncertainties
Good proposals acknowledge what's unknown
-->

---

{{/each}}

### Validation: No Discarded Assumptions Reintroduced

{{#each builder_proposals}}

#### Validation of Proposal {{proposal_number}}: {{proposal_name}}

{{#each validation_checks}}
**Check {{check_number}}:** {{discarded_assumption_text}}

{{#if reintroduced}}
❌ **FLAGGED**: This proposal reintroduces discarded assumption

- How: {{reintroduction_explanation}}
- Builder revision: {{revision_description}}
  {{else}}
  ✅ **APPROVED**: Confirmed NOT in proposal
  {{/if}}

{{/each}}

<!--
DESIGN NOTE: Systematic check of each discarded assumption
Catches subtle reintroductions like:
"We discarded assumption X" → proposal includes Y which depends on X → caught
-->

{{/each}}

### Facilitator Synthesis: Recommended Approach

**🧠 {{facilitator_name}}:**

{{synthesis_introduction}}

**Summary of Proposals:**

{{#each proposal_summaries}}
**Proposal {{proposal_number}}: {{proposal_name}}**

- Core innovation: {{core_innovation}}
- Strengths: {{strengths}}
- Risks: {{risks}}
  {{/each}}

**Recommended Approach:**

{{#if single_proposal}}
**Selected Proposal:** {{selected_proposal_name}} by {{selected_builder}}

**Rationale:** {{selection_rationale}}

<!--
DESIGN NOTE: Single best proposal if one clearly superior
-->

{{/if}}

{{#if hybrid_proposal}}
**Hybrid Approach:** Combining elements from multiple proposals

{{#each hybrid_elements}}

- From {{proposal_name}}: {{element_description}}
  {{/each}}

**Rationale:** {{hybrid_rationale}}

<!--
DESIGN NOTE: Hybrid if proposals are complementary
Often best solution combines ideas from multiple builders
-->

{{/if}}

{{#if multiple_options}}
**Multiple Viable Options:** Presenting {{option_count}} distinct approaches for user selection

{{#each options}}
{{option_number}}. {{option_name}}: {{option_summary}}
{{/each}}

**Selection Guidance:** {{selection_guidance}}

<!--
DESIGN NOTE: Multiple options if proposals are very different
User may have context to choose that facilitator doesn't
-->

{{/if}}

---

## 📊 Comparison Analysis: Old vs First Principles Approach

### Original Approach

{{original_approach_summary}}

**Assumptions It Was Built On:**
{{#each original_assumptions}}

- {{assumption_text}} ({{verdict}} in our analysis)
  {{/each}}

### First Principles Approach

{{first_principles_approach_summary}}

**Bedrock Truths It Respects:**
{{#each bedrock_truths_respected}}

- {{truth_statement}}
  {{/each}}

### Key Differences Table

| Dimension             | Original Approach        | First Principles Approach | Why Different                          |
| --------------------- | ------------------------ | ------------------------- | -------------------------------------- |
| **Cost**              | {{original_cost}}        | {{fp_cost}}               | {{cost_difference_explanation}}        |
| **Complexity**        | {{original_complexity}}  | {{fp_complexity}}         | {{complexity_difference_explanation}}  |
| **Time to Implement** | {{original_timeline}}    | {{fp_timeline}}           | {{timeline_difference_explanation}}    |
| **Performance**       | {{original_performance}} | {{fp_performance}}        | {{performance_difference_explanation}} |
| **Scalability**       | {{original_scalability}} | {{fp_scalability}}        | {{scalability_difference_explanation}} |
| **Risk**              | {{original_risk}}        | {{fp_risk}}               | {{risk_difference_explanation}}        |

<!--
DESIGN NOTE: Comparison table shows CONCRETE improvements
Not just "better" but "60% cheaper because we discarded assumption X"
-->

### Breakthrough Insights

{{#each breakthrough_insights}}

#### Insight {{insight_number}}: {{insight_title}}

{{insight_description}}

**What We Discovered:**
{{discovery}}

**Implication:**
{{implication}}

**Why This Matters:**
{{why_matters}}

<!--
DESIGN NOTE: Breakthrough insights explain VALUE of First Principles
"We discovered X wasn't fundamental"
"This enables Y (which was impossible under old assumptions)"
"Root cause: Z assumption was creating unnecessary bloat"
-->

{{/each}}

### Why First Principles Approach Is Superior

{{superiority_explanation}}

**Quantitative Improvements:**
{{#each quantitative_improvements}}

- {{metric}}: {{original_value}} → {{fp_value}} ({{improvement_percentage}}% improvement)
  - Root cause: {{root_cause_explanation}}
    {{/each}}

**Qualitative Improvements:**
{{#each qualitative_improvements}}

- {{improvement_description}}
  {{/each}}

---

## 🎯 Recommended Next Steps

{{#each recommended_steps}}

### Step {{step_number}}: {{step_title}} ({{timeframe}})

**Action:** {{action_description}}

**Owner:** {{suggested_owner}}

**Success Criteria:** {{success_criteria}}

**Why This Step:** {{rationale}}

{{#if step_type == "validation"}}
**Validation Approach:** {{validation_approach}}

- If validation fails: {{failure_contingency}}
- If validation succeeds: {{success_next_step}}
  {{/if}}

{{/each}}

<!--
DESIGN NOTE: Next steps are ACTIONABLE
Not vague "consider options" but specific "prototype X to validate assumption Y"
Include validation steps for "needs more evidence" assumptions
-->

---

## 📝 Session Metadata

**Session Statistics:**

- Duration: {{session_duration}}
- Total assumptions identified: {{total_assumptions}}
- Discarded as non-fundamental: {{discarded_count}} ({{discarded_percentage}}%)
- Validated as bedrock truths: {{bedrock_truth_count}}
- Builder proposals generated: {{proposal_count}}
- Breakthrough insights: {{insight_count}}

**Success Criteria Met:**

{{#each success_criteria}}

- ✅ {{criterion}}: {{status}} {{#if met}}✓{{else}}✗{{/if}}
  {{/each}}

<!--
DESIGN NOTE: Success criteria from Section 2 Framework Philosophy
Validates whether session achieved framework goals:
1. 60%+ assumptions discarded
2. New solution substantially different
3. Every component traceable to fundamental
4. Team understands WHY old approach was suboptimal
5. Cost/complexity/performance improved
-->

**Dissenting Viewpoints:**

{{#if dissenting_viewpoints}}
{{#each dissenting_viewpoints}}
**{{agent_icon}} {{agent_name}}:**

{{dissent_text}}

**Facilitator Response:** {{facilitator_response}}

<!--
DESIGN NOTE: Minority perspectives captured even when not consensus
Shows which assumptions/verdicts had disagreement
Ensures psychological safety (all voices matter)
-->

{{/each}}
{{else}}
No dissenting viewpoints recorded.
{{/if}}

---

## 🔗 Related Artifacts

**Framework History:**

- Previous First Principles sessions: {{previous_sessions}}
- Related frameworks used: {{related_frameworks}}

**Follow-up Workflows:**
{{#each followup_workflows}}

- {{workflow_name}}: {{workflow_purpose}}
  {{/each}}

**References:**
{{#each references}}

- {{reference_text}}: {{reference_url}}
  {{/each}}

---

## Appendix: Framework Methodology

### About First Principles Thinking

First Principles thinking is the practice of actively questioning every assumption you think you know about a problem, then reconstructing solutions from the ground up using only fundamental truths.

**Origin:** Aristotle defined a first principle as "the first basis from which a thing is known."

**Three-Phase Cycle:**

1. **Deconstruct:** Challenge every assumption (fundamental vs inherited belief)
2. **Validate:** Verify what's REALLY fundamental (Socratic questioning to bedrock)
3. **Reconstruct:** Rebuild using ONLY validated fundamentals

**Evidence Hierarchy:**

- Highest: Physics, mathematics, thermodynamics
- High: Economics, biology, regulatory requirements
- Medium: Engineering constraints, material properties
- Low: Best practices, industry conventions
- Insufficient: "That's how it's always done"

### Multi-Agent Implementation

This session used BMad's multi-agent implementation:

- **Challengers** ({{challenger_count}}): Aggressively questioned every assumption
- **Defenders** ({{defender_count}}): Defended with evidence or conceded gracefully
- **Builders** ({{builder_count}}): Reconstructed solution using only fundamentals
- **Facilitator** (1): Rendered evidence-based verdicts, synthesized insights

**Interaction Pattern:** Iterative challenge-defend-verdict cycles (not debate, not consensus)

**Checkpoint Protocol:** Saved after each assumption cluster to prevent context loss

### Customization Used This Session

**Challenge Intensity:** {{challenge_intensity}}
**Evidence Standard:** {{evidence_standard}}
**Agent Count Per Cohort:** {{agent_count_config}}
**Phase Time Allocation:** {{phase_timing}}
**Special Modifications:** {{special_modifications}}

<!--
DESIGN NOTE: Documents any deviations from default configuration
Helps future teams understand how session was conducted
-->

---

**Document Path:** {{template_output_path}}
**Framework:** First Principles Thinking (Aristotelian reasoning)
**Generated by:** BMad Core Workflow Engine
```

---

### Template Design Philosophy

This template demonstrates several key principles:

1. **Educational Journey**: Captures the full progression from assumptions → fundamentals → breakthrough
   - Not just the answer, but HOW we got there
   - Future teams can learn from challenge-defend-verdict process

2. **Evidence Trail**: Every verdict includes the evidence (or lack thereof) that led to it
   - Transparent decision-making
   - Can be audited and challenged

3. **Three-Phase Structure**: Template mirrors workflow phases
   - Phase 1: All assumption clusters with challenge-defend-verdict
   - Phase 2: Validation rounds for each "fundamental"
   - Phase 3: Builder proposals with validation checks

4. **Comparison Emphasis**: Old vs new approach comparison is prominent
   - Shows quantitative improvements (60% cost reduction because...)
   - Shows qualitative improvements (simpler because...)
   - Articulates WHY First Principles was valuable

5. **Breakthrough Documentation**: Captures insights that emerged
   - "We discovered X wasn't fundamental"
   - "This enables Y (impossible under old assumptions)"
   - These insights are the REAL value

6. **Actionable Next Steps**: Not just analysis, but implementation path
   - Specific validation steps for "needs more evidence" assumptions
   - Prototype/test recommendations
   - Success criteria for each step

---

## 5. Complete Example Dialogue

This section shows a full First Principles session execution, demonstrating all multi-agent patterns in action.

**Scenario**: Startup deciding how to build their SaaS product's data storage layer

---

**USER**: I want to use First Principles to rethink how we're building our SaaS product's data storage. We're planning to use PostgreSQL with separate databases per tenant, but it's getting expensive and complex.

**CLAUDE (BMad Master)**:
Excellent - First Principles is perfect for questioning architectural decisions. Let me initialize the framework.

_[Loads agent-manifest.csv, agent-assignments.yaml, workflow configuration]_

🧠 **First Principles Thinking - Multi-Agent Challenge-Rebuild Cycle**

**Problem/Current Approach:**
SaaS data storage using PostgreSQL with separate databases per tenant (multi-database multi-tenancy)

**Three-Phase Process:**

1. DECONSTRUCT: Challenge every assumption in this approach
2. VALIDATE: Identify what's truly fundamental (physics, economics, data)
3. RECONSTRUCT: Rebuild storage layer using ONLY validated fundamentals

**Agent Cohorts:**

⚔️ **CHALLENGERS** (Destroy Assumptions):

- ⚙️ Ember Hayes (Test Engineer) - Quality mindset, finds edge cases
- 🔒 Nova Chen (Security Architect) - Security constraints, threat modeling
- 💡 Victor Sterling (Innovation Strategist) - Challenges business conventions

🛡️ **DEFENDERS** (Provide Evidence or Concede):

- 🏗️ Winston Blake (Solution Architect) - Technical design knowledge
- 💻 Alex Rivera (Senior Developer) - Implementation reality
- 📊 Sarah Chen (Data Analyst) - Data-driven evidence

🏗️ **BUILDERS** (Reconstruct from Fundamentals):

- 🏗️ Winston Blake (Solution Architect) - Technical design
- 💡 Victor Sterling (Innovation Strategist) - Novel approaches
- 💻 Alex Rivera (Senior Developer) - Pragmatic implementation

🧠 **FACILITATOR** (Orchestrate and Render Verdicts):

- 🧙 BMad Master - Meta-orchestration

**Ground Rules:**

- Challengers: Be aggressive. Demand evidence. "Prove it or lose it."
- Defenders: Defend with evidence or concede gracefully. "Best practice" is NOT evidence.
- Evidence Hierarchy: Physics > Economics > Engineering > Convention
- Goal: 60%+ of assumptions discarded and radically different solution

This will take 2-4 hours. Ready to begin?

**USER**: Yes, let's do it.

---

### 💥 Phase 1: Deconstruct - Challenge Every Assumption

═══════════════════════════════════════════════════════════════════
**PHASE 1: DECONSTRUCT - Challenge Every Assumption**
═══════════════════════════════════════════════════════════════════

**Current Approach:**
PostgreSQL with separate databases per tenant (multi-database multi-tenancy)

**🧙 BMad Master**:

I've analyzed your approach and identified the following assumption clusters:

**CLUSTER 1: Architectural Assumptions**

- A1: Must use relational database (PostgreSQL)
- A2: Must use separate databases per tenant
- A3: Need ACID transactions

**CLUSTER 2: Data Isolation Assumptions**

- A4: Database-level isolation required for data security
- A5: Cannot mix tenant data in same tables
- A6: Need physical separation for compliance

**CLUSTER 3: Scale/Performance Assumptions**

- A7: Need to scale databases independently per tenant
- A8: Large tenants will overwhelm shared infrastructure
- A9: Query performance degrades with multi-tenancy

**CLUSTER 4: Operational Assumptions**

- A10: Need per-tenant backups
- A11: Migrations must run per database
- A12: Monitoring requires per-database metrics

We'll challenge each cluster in turn. Let's start with CLUSTER 1.

---

#### Cluster 1: Architectural Assumptions

---

**CLUSTER 1: Architectural Assumptions**

- A1: Must use relational database (PostgreSQL)
- A2: Must use separate databases per tenant
- A3: Need ACID transactions

---

**🧙 BMad Master**: Challengers, attack these assumptions. Demand evidence.

**⚙️ Ember Hayes** (Test Engineer):

Let's start with A1 - "must use relational database." **WHY?** What law of physics requires a relational database?

I can think of plenty of SaaS products using:

- Key-value stores (Redis, DynamoDB)
- Document databases (MongoDB, Firestore)
- Even flat files on S3

So clearly it's not a fundamental constraint. **Prove that relational is necessary, not just conventional.**

**🔒 Nova Chen** (Security Architect):

And A2 - "separate databases per tenant." This smells like inherited wisdom, not security requirement.

**Physical separation doesn't equal security.** If your application code is compromised, separate databases don't help - the attacker has credentials to all of them.

True security is application-level access control. Database separation is security theater unless you can prove otherwise.

**💡 Victor Sterling** (Innovation Strategist):

A3 - "need ACID transactions." **Really?**

Most web applications don't actually need ACID for most operations. When's the last time you did a multi-table transaction? Be honest.

BASE (Basically Available, Soft state, Eventually consistent) works fine for 90% of SaaS operations. **Prove you need ACID, don't assume it.**

**🧙 BMad Master**: Defenders, respond with evidence or concede.

**🏗️ Winston Blake** (Solution Architect):

Let me defend these one by one.

**A1 (Relational database):** I'll concede partially. We chose PostgreSQL because:

- Evidence: Our data HAS relationships (users → organizations → subscriptions)
- But: I can't prove we NEED relational. Document databases can handle relationships too.
- **Revised**: We need to _model_ relationships, but don't necessarily need SQL for it.

**A2 (Separate databases):** Ember and Nova are right. I can't defend this with evidence.

- Our reason: "It's how [competitor] does it" ← That's not evidence, that's cargo culting.
- Security: Nova is correct - application code compromise defeats database separation.
- **Concede**: This is convention, not constraint.

**A3 (ACID transactions):** Alex, want to help defend this one?

**💻 Alex Rivera** (Senior Developer):

Victor's right that we don't use transactions much. Let me look at our actual usage...

_[Pause for analysis]_

We have exactly 3 places in our codebase using transactions:

1. Payment processing (credit → subscription creation)
2. Organization transfer (old owner out, new owner in)
3. Bulk user import (all-or-nothing)

That's it. 99% of our operations are single-record writes.

**Evidence-based defense**: For those 3 workflows, we DO need atomicity. But...

**Concession**: We don't need ACID _everywhere_. We need it for ~1% of operations. The other 99% could be eventually consistent.

**🧙 BMad Master**:

**VERDICTS for CLUSTER 1:**

**A1 (Relational database)**: **DISCARDED**

- Reason: Defended with "we have relationships" but that's not evidence relational DB is required
- Revealed as: Engineering convenience, not fundamental constraint
- Implication: Phase 3 should consider non-relational options

**A2 (Separate databases per tenant)**: **DISCARDED**

- Reason: Defended with "competitor does it" - convention, not evidence
- Revealed as: Inherited belief, not security requirement
- Implication: Phase 3 freed from this constraint - massive simplification possible

**A3 (ACID transactions)**: **FUNDAMENTAL** (with scope reduction)

- Evidence: 3 specific workflows require atomicity (payment, transfer, bulk import)
- Constraint for Phase 3: Must support transactions for ~1% of operations
- Note: 99% of operations DON'T need ACID - don't over-constrain

_[Checkpoint saved]_

---

#### Cluster 2: Data Isolation Assumptions

---

**CLUSTER 2: Data Isolation Assumptions**

- A4: Database-level isolation required for data security
- A5: Cannot mix tenant data in same tables
- A6: Need physical separation for compliance

---

**🧙 BMad Master**: Let's challenge data isolation assumptions.

**🔒 Nova Chen** (Security Architect):

A4 - "database-level isolation required for security." **Absolutely not.**

**Evidence**: Every major SaaS company (Salesforce, GitHub, Slack) uses shared tables with row-level security. They have better security track records than most single-tenant systems.

Physical isolation is **security theater**. Real security is:

- Application code doesn't have bugs (WHERE tenant_id = ?)
- Encryption at rest
- Access control
- Audit logging

None of those require separate databases. **Prove database isolation adds security beyond this.**

**⚙️ Ember Hayes** (Test Engineer):

A5 - "cannot mix tenant data." Building on Nova's point:

If you're worried about mixing data, **that's a code quality problem**, not a database problem.

**Test for it**:

- Integration tests with multi-tenant data
- Automated checks that all queries include tenant_id
- Code review for query patterns

Separate databases just hide the problem. Your code can STILL have tenant-mixing bugs if someone queries the wrong database.

**💡 Victor Sterling** (Innovation Strategist):

A6 - "need physical separation for compliance." Let me challenge this hard.

**Which compliance?** GDPR? HIPAA? SOC 2?

I've read all three. **None require physical database separation.** They require:

- Access controls (✓ app level)
- Encryption (✓ works with shared tables)
- Audit logging (✓ works with shared tables)
- Data isolation (✓ logical, not physical)

**Prove** that your compliance regime requires separate databases. I bet you can't.

**🧙 BMad Master**: Defenders?

**🏗️ Winston Blake** (Solution Architect):

_[Long pause]_

I... I can't defend any of these. We assumed database separation = security, but Nova's right - it's not.

**A4**: **Concede.** Application-level security is what matters.

**A5**: **Concede.** Ember's right - this is hiding code quality issues.

**A6**: Victor challenged me to cite compliance requirement. I just checked our SOC 2 audit requirements. It says "logical data isolation" - nothing about physical separation.

**Concede all three.** These are inherited beliefs, not requirements.

**🧙 BMad Master**:

**VERDICTS for CLUSTER 2:**

**A4 (Database-level isolation for security)**: **DISCARDED**

- Reason: No evidence that physical separation improves security
- Evidence shows: Major SaaS companies use shared tables successfully
- Revealed as: Security theater, not actual security

**A5 (Cannot mix tenant data)**: **DISCARDED**

- Reason: This is code quality issue, not database constraint
- Can be solved with: Tests, code review, automated checks
- Revealed as: Architectural choice hiding code discipline problem

**A6 (Physical separation for compliance)**: **DISCARDED**

- Reason: Compliance requires logical isolation, not physical
- Evidence: SOC 2, GDPR, HIPAA all satisfied by app-level controls
- Revealed as: Misunderstanding of compliance requirements

_[Checkpoint saved]_

**All data isolation assumptions discarded!** This is a major finding.

---

#### Cluster 3: Scale/Performance Assumptions

---

**CLUSTER 3: Scale/Performance Assumptions**

- A7: Need to scale databases independently per tenant
- A8: Large tenants will overwhelm shared infrastructure
- A9: Query performance degrades with multi-tenancy

---

**🧙 BMad Master**: Now let's tackle performance assumptions.

**⚙️ Ember Hayes** (Test Engineer):

A7 - "need to scale independently per tenant." **Why?**

Do you have data showing tenants need different scale profiles? Or is this theoretical?

And even if true: Modern databases can scale a single database MUCH larger than you think. PostgreSQL can handle terabytes. DynamoDB scales infinitely.

**Prove you need per-tenant scaling** with actual data, not "what if a tenant gets huge."

**💻 Alex Rivera** (Senior Developer):

A8 - "large tenants will overwhelm shared infrastructure." Let me provide actual data:

Our largest tenant: 50GB data, 10,000 requests/day
Our smallest: 100MB data, 50 requests/day

**That's a 500x difference.** But you know what? Modern databases handle this easily:

- PostgreSQL can handle 10TB+ in a single database
- Read replicas can handle query load
- Proper indexing matters more than database count

**The cost of managing 1,000 separate databases** > cost of one large database with proper indexing.

**💡 Victor Sterling** (Innovation Strategist):

A9 - "query performance degrades with multi-tenancy."

**Is this actually true?** Or is it:

- Bad indexes?
- N+1 query problems?
- Missing caching?

Because I've seen plenty of single-tenant databases with terrible performance due to poor optimization.

And I've seen multi-tenant databases with excellent performance because they were forced to optimize (you notice problems faster when all tenants share infra).

**Prove multi-tenancy is the cause** of performance issues, not poor engineering.

**🧙 BMad Master**: Defenders?

**📊 Sarah Chen** (Data Analyst):

Let me provide data-driven defense.

**A7 (Scale independently)**: Looking at our actual tenant sizes...

- 95% of tenants: <1GB data
- 4% of tenants: 1-10GB data
- 1% of tenants: >10GB data

**Evidence against independent scaling**: The vast majority are tiny. We're not Netflix with wildly different tenant profiles.

**Concede**: We don't need per-tenant scaling. One well-designed database can handle our distribution.

**A8 (Large tenants overwhelm)**: Alex provided the numbers. Our largest tenant is 50GB.

Modern PostgreSQL on AWS RDS can handle multi-TB databases. **We're not even close to limits.**

**Concede**: This is premature optimization. We're solving a problem we don't have.

**A9 (Performance degrades)**: Victor nailed it.

**Our actual performance problems**:

1. Missing indexes (solved by EXPLAIN ANALYZE)
2. N+1 queries (solved by proper ORM usage)
3. No caching (solved by Redis)

**None of those are caused by multi-tenancy.**

**Concede**: Performance is engineering quality issue, not architecture issue.

**🧙 BMad Master**:

**VERDICTS for CLUSTER 3:**

**A7 (Scale independently per tenant)**: **DISCARDED**

- Evidence: 95% of tenants <1GB, largest is 50GB
- Modern databases handle much larger: PostgreSQL 10TB+, DynamoDB infinite
- Revealed as: Premature optimization for problem that doesn't exist

**A8 (Large tenants overwhelm shared)**: **DISCARDED**

- Evidence: Math doesn't support this (50GB largest vs TB+ capacity)
- Cost of 1,000 databases > cost of one large optimized database
- Revealed as: Fear-based architecture, not evidence-based

**A9 (Multi-tenancy degrades performance)**: **DISCARDED**

- Evidence: Actual performance issues are indexes, N+1, caching
- Multi-tenancy forces good engineering (problems visible faster)
- Revealed as: Confusing correlation with causation

_[Checkpoint saved]_

**Key insight**: We're solving theoretical scale problems we don't have, while ignoring actual engineering problems.

---

#### Cluster 4: Operational Assumptions

---

**CLUSTER 4: Operational Assumptions**

- A10: Need per-tenant backups
- A11: Migrations must run per database
- A12: Monitoring requires per-database metrics

---

**🧙 BMad Master**: Final cluster - operational assumptions.

**💡 Victor Sterling** (Innovation Strategist):

A10 - "need per-tenant backups." **Really?**

What's the actual requirement? Probably: "Can restore tenant data if disaster."

That doesn't require per-tenant backups. It requires:

- Logical backups with tenant_id filtering
- Or: Single backup with tenant-aware restore

Per-tenant backups are solving HOW, not WHAT. You're constraining yourself unnecessarily.

**⚙️ Ember Hayes** (Test Engineer):

A11 - "migrations must run per database." **Ouch.**

If you have 1,000 tenants = 1,000 databases = **1,000 migration runs**.

That's not a requirement, that's a nightmare:

- What if migration fails on database #347?
- How do you know all databases are on same schema version?
- How long does it take to migrate 1,000 databases?

**This is operational hell self-inflicted by architecture choice**, not fundamental requirement.

**🔒 Nova Chen** (Security Architect):

A12 - "monitoring per database."

More operational overhead. With 1,000 databases:

- 1,000 connection pools to monitor
- 1,000 query performance dashboards
- 1,000 disk usage alerts

versus ONE database:

- One connection pool
- One performance dashboard
- One set of alerts
- - tenant-level metrics if needed

**Prove you need per-database monitoring.** I bet you just need per-tenant query metrics, which works fine with shared database.

**🧙 BMad Master**: Defenders?

**💻 Alex Rivera** (Senior Developer):

As the person who actually runs migrations and monitoring...

**All three of these are PAIN POINTS for our team.**

A10 (Per-tenant backups):

- We backup all 1,000 databases nightly = 12 hours
- We've never restored a single-tenant backup
- When we restore, it's usually "oops, deleted production data" = point-in-time restore

**Concede**: We don't need per-tenant backups. We need good backup strategy for one database.

A11 (Per-database migrations):

- Last migration took 8 hours to run across all databases
- Three databases failed (different errors)
- Spent 2 days debugging inconsistent states

**Concede with enthusiasm**: This is operational nightmare. Please let us stop doing this.

A12 (Per-database monitoring):

- Our monitoring dashboard has 1,000 database widgets
- It's unusable
- We actually monitor at application level anyway (query latency, error rates)

**Concede**: This is not providing value, it's creating noise.

**🧙 BMad Master**:

**VERDICTS for CLUSTER 4:**

**A10 (Per-tenant backups)**: **DISCARDED**

- Evidence: Never used single-tenant restore, point-in-time is what's needed
- 12 hours of backup time is waste
- Revealed as: Confusing requirement (restore capability) with implementation (per-tenant backups)

**A11 (Per-database migrations)**: **DISCARDED**

- Evidence: 8-hour migration runs, inconsistent states, debugging hell
- Single database migration = run once, done
- Revealed as: Self-inflicted operational complexity

**A12 (Per-database monitoring)**: **DISCARDED**

- Evidence: Dashboard unusable, application-level metrics more valuable
- 1,000 widgets provide noise, not signal
- Revealed as: Monitoring approach doesn't match actual needs

_[Checkpoint saved]_

---

### Phase 1 Summary

**🧙 BMad Master**:

**PHASE 1 COMPLETE: Deconstruction Summary**

Total Assumptions Identified: **12**

**FUNDAMENTAL TRUTHS** (Validated with Evidence):

1. Need transactions for ~1% of operations (payment, transfer, bulk import)

**DISCARDED ASSUMPTIONS** (Convention, Not Constraint):

1. Must use relational database (PostgreSQL) - Engineering convenience
2. Must use separate databases per tenant - Cargo culting
3. Database-level isolation required for security - Security theater
4. Cannot mix tenant data in same tables - Hiding code quality issues
5. Need physical separation for compliance - Misunderstanding requirements
6. Need to scale databases independently per tenant - Premature optimization
7. Large tenants will overwhelm shared infrastructure - Fear-based, not data-based
8. Query performance degrades with multi-tenancy - Confusing correlation/causation
9. Need per-tenant backups - Operational waste
10. Migrations must run per database - Self-inflicted complexity
11. Monitoring requires per-database metrics - Noise, not signal

**Discard Rate: 91.7%** (11 of 12 assumptions discarded)

**Key Insights:**

- Most assumptions based on convention ("how others do it"), not evidence
- Security and compliance misunderstood - physical separation unnecessary
- Performance issues are engineering quality, not architecture
- Operational complexity is self-inflicted by separate-database choice

**Next:** Phase 2 will validate that our ONE "fundamental truth" (transactions) is really fundamental.

_[Checkpoint saved]_

---

## 💎 Phase 2: Validate - Identify True Fundamentals

**🧙 BMad Master**:

We have ONE assumption that survived Phase 1 with evidence. Now we subject it to Socratic validation:

**Target**: A3 - "Need ACID transactions for ~1% of operations (payment, transfer, bulk import)"

Let's validate whether this is truly fundamental, or if it reduces to something deeper.

**Validation Question 1**: "WHY do we need transactions for these operations?"

---

### Round 1: Surface-Level Challenge

**⚔️ Ember Hayes (Test Engineer)**:

"Let's start with payments. You said 'need transactions for payments.' WHY?

What actually breaks if a payment doesn't happen in a transaction? Walk me through the failure scenario with evidence."

**🛡️ Winston Blake (Solution Architect)**:

"Concrete example: User pays $100. We must:

1. Deduct $100 from their account balance
2. Create payment record
3. Update subscription status to 'active'

If step 1 succeeds but step 2 fails, they're charged but we have no record. Money disappears.

**Evidence Type**: Engineering constraint (data consistency)
**Evidence Quality**: Medium - this is about correctness, not physics"

**🧙 BMad Master**:

"Noted. But Ember asked what BREAKS, not what's inconvenient. Can you recover from that failure scenario?"

**🛡️ Winston Blake**:

"Yes, we could:

- Log every account balance change
- Reconcile logs against payment records
- Manually create missing payment records

But that's error-prone operational overhead.

Wait... I'm defending with 'operational convenience' again. Let me reconsider."

---

#### Round 2: Deeper Socratic Questioning

**⚔️ Nova Chen (Innovation Strategist)**:

"Winston's example reveals the real constraint. It's not 'we need transactions' - it's 'we need these three operations to all-succeed or all-fail.'

But WHY must they all-succeed or all-fail? What law requires atomicity?"

**🛡️ Sarah Mitchell (Developer)**:

"The fundamental constraint is: **Money in the real world is atomic**. You can't partially charge a credit card.

So our database operations must match reality's atomicity. If Stripe says 'charged successfully,' our records must reflect that - no partial states.

**Evidence Type**: Physics/Economics - money is a conservation law in the system
**Evidence Quality**: High - this maps to fundamental constraints of payment processing"

**🧙 BMad Master**:

"Excellent! Now we're getting somewhere. So the bedrock truth isn't 'need transactions' - it's 'must match external atomic events.'

But does that require DATABASE transactions specifically?"

---

#### Round 3: Question the Implementation

**⚔️ Victor Torres (Security Analyst)**:

"Sarah said 'must match external atomic events.' True. But you can achieve that WITHOUT database transactions:

**Alternative**: Event sourcing with idempotency

- Stripe webhook arrives: 'payment succeeded'
- Write single immutable event: 'PaymentReceived($100, user123)'
- Process event: Update balance, create record, activate subscription
- If processing fails: Event is still there, retry until success

No database transaction needed. The atomicity comes from the immutable event log.

Prove database transactions are required."

**🛡️ Winston Blake**:

"I... cannot. Victor's right. We could use:

- Event sourcing (single atomic write per event)
- Idempotent consumers (retry until convergence)
- CQRS (separate write model from read model)

Database transactions are ONE way to achieve atomicity, not the ONLY way.

**I concede**: Database transactions are not fundamental. The fundamental constraint is 'match external atomic events with eventual internal consistency.'"

---

#### Round 4: Reduce to Bedrock

**🧙 BMad Master**:

"Excellent progression. Let's reduce this fully:

**Question**: What's the DEEPEST constraint here? Not 'need atomicity' - that's still an implementation. What TRUTH about the problem domain requires this?"

**🛡️ Alex Chen (Product Manager)**:

"The bedrock truth: **Users must be able to trust their account balance.**

If I pay $100 and my subscription doesn't activate, I'll dispute the charge. That creates:

- Chargeback fees ($15-$25 per dispute)
- Lost customer trust
- Support overhead

The FUNDAMENTAL constraint: **Cost of inconsistency exceeds cost of consistency mechanisms.**

This is economic, not technical."

**⚔️ Ember Hayes**:

"Perfect. And Alex's economic constraint is measurable:

- Chargeback fee: $20 average
- Support ticket: $15 (30 min × $30/hr)
- Customer lifetime value loss: $500 (assuming 20% churn after payment issue)

Total cost per inconsistency: **~$535**

If we have 10 payments/day, even 1% failure rate = $535 × 0.01 × 10 = **$53.50/day** in losses.

Cost of consistency (database transaction overhead): Microseconds of latency, negligible.

The math proves consistency is worth it. That's bedrock."

**🧙 BMad Master**:

"**VALIDATED AS FUNDAMENTAL**

Let me summarize the reduction:

**Surface Assumption**: 'Need ACID transactions for payments'
↓ (Why?)
**Deeper**: 'Need atomicity for multi-step operations'
↓ (Why?)
**Deeper**: 'Must match external atomic events'
↓ (Why?)
**Bedrock Truth**: **'Cost of inconsistency ($535) exceeds cost of consistency (microseconds)'**

**Evidence Type**: Economics (measurable financial constraint)
**Evidence Quality**: Highest tier - this is a conservation law in our business model"

---

### Phase 2 Summary

**🧙 BMad Master**:

**PHASE 2 COMPLETE: Validation Summary**

Original "Fundamental": "Need ACID transactions for ~1% of operations"

**Validated Bedrock Truth** (after Socratic reduction):

- **"For operations involving external atomic events (payments), cost of inconsistency exceeds cost of consistency"**

**Key Reductions**:

1. "Need transactions" → "Need atomicity"
2. "Need atomicity" → "Must match external events"
3. "Must match external events" → **"Economics: Inconsistency costs $535/incident"**

**Critical Insight**: The bedrock truth is ECONOMIC, not technical. This means:

- Database transactions are optional (event sourcing works too)
- Only applies to ~1% of operations that involve money/external events
- 99% of operations (read user data, update profile, search) have NO fundamental need for consistency - eventual consistency is fine

**Validated Constraints for Reconstruction**:

1. ~1% of operations: Prevent costly inconsistency ($535/incident)
2. 99% of operations: No constraints (eventual consistency acceptable)
3. All operations: Must handle relationships between entities (but NOT necessarily with SQL)

_[Checkpoint saved]_

---

## 🏗️ Phase 3: Reconstruct - Build from Fundamentals Only

**🧙 BMad Master**:

We now rebuild the data storage architecture using ONLY the validated fundamentals:

**Bedrock Constraints**:

1. ~1% of operations (payments, transfers, critical writes): Cost of inconsistency is $535/incident
2. 99% of operations (reads, profile updates, searches): No consistency constraints
3. Must model relationships between entities
4. SaaS product with multiple tenants

**Challenge to Builders**: Design a data architecture using ONLY these constraints. Ignore ALL conventions.

---

### Builder Round 1: Initial Proposals

**🏗️ Winston Blake (Solution Architect)**:

"Starting from zero, using only our fundamentals:

**Proposal A: Single Database, Hybrid Consistency**

**Core Design**:

- Single PostgreSQL database
- All tenant data in shared tables with `tenant_id` column
- Row-Level Security (RLS) policies enforce isolation (PostgreSQL native feature)

**For the 1% (payments, transfers)**:

```sql
BEGIN TRANSACTION ISOLATION LEVEL SERIALIZABLE;
-- Payment operations here
COMMIT;
```

Use transactions ONLY where economics justify ($535 cost avoidance)

**For the 99% (everything else)**:

- No transactions
- Eventual consistency via async updates
- Example: User updates profile → immediate write, search index updates async

**Relationship modeling**:

- Foreign keys for referential integrity (prevents orphaned records)
- NO joins across tenants (RLS + query patterns prevent this)

**Economics**:

- 1 database instance: $200/month
- vs 100 databases: $20,000/month
- Savings: $19,800/month

**Evidence**: Built from economic constraint + relationship requirement only. Nothing else."

---

**🏗️ Victor Torres (Security Analyst)**:

"Winston's proposal works, but I'll offer an alternative that questions the 'must use database transactions' assumption we JUST validated:

**Proposal B: Event-Sourced Hybrid**

**For the 1% (critical operations)**:

- Event log as source of truth (append-only, immutable)
- Each payment = single atomic write to event log
- Consumers rebuild state from events (eventual consistency)
- Example:
  ```
  Event: PaymentReceived { amount: $100, user: "user123", timestamp: "..." }
  Consumer 1: Update account balance
  Consumer 2: Create payment record
  Consumer 3: Activate subscription
  ```
  If consumer fails, event remains, retry until convergence

**For the 99% (everything else)**:

- Standard CRUD in shared PostgreSQL tables
- No special handling

**Why This Works**:

- Event log write is atomic (single write, no transaction needed)
- Cost of inconsistency avoided: Event is durable, consumers will eventually succeed
- Simpler mental model: Events = facts, consumers = derived state

**Trade-off**:

- More complexity in payment code
- But eliminates transaction overhead even for critical operations

**Evidence**: Built from 'avoid $535 inconsistency cost' without assuming database transactions required."

---

**🏗️ Alex Chen (Product Manager)**:

"Both proposals solve the fundamentals, but let me add business constraints:

**Proposal C: Pragmatic Single-Database**

I'll extend Winston's Proposal A with business realism:

**For the 1% (critical writes)**:

- Use database transactions (KISS principle - it's proven, understood, debuggable)
- Cost: Microseconds of latency
- Benefit: Avoids $535 inconsistency cost + engineering complexity of event sourcing

**For the 99%**:

- Async writes where possible:
  - User profile updates: Synchronous (user expects immediate feedback)
  - Analytics tracking: Async (user doesn't care)
  - Search indexing: Async (eventual consistency fine)
  - Notification queues: Async

**Tenant Isolation**:

- Row-Level Security (RLS) for security
- `tenant_id` indexed for performance
- Application-level checks as defense-in-depth (RLS is enforcement, app is convenience)

**Migration Path**:

1. Start: Single database, all tenants
2. IF a tenant exceeds 10M records (99th percentile): Split to dedicated database
3. Use foreign data wrappers to maintain relationships if needed

**Economics**:

- Start: $200/month (1 database)
- Scale: $200-$2000/month (1 main + up to 9 dedicated for massive tenants)
- Current 100-database plan: $20,000/month

**Why This Wins**:

- Solves bedrock constraints (avoid $535 inconsistency)
- KISS: Uses well-understood tools (PostgreSQL transactions + RLS)
- Pragmatic: Allows escape hatch for true outliers (future-proofs)

**Evidence**: Balances fundamentals with engineering reality (not over-engineered)."

---

#### Builder Round 2: Comparison & Selection

**🧙 BMad Master**:

"We have three proposals. Let's evaluate against our bedrock constraints:

| Constraint                   | Proposal A (Winston)       | Proposal B (Victor)          | Proposal C (Alex)                 |
| ---------------------------- | -------------------------- | ---------------------------- | --------------------------------- |
| **Avoid $535 inconsistency** | ✅ DB transactions for 1%  | ✅ Event sourcing            | ✅ DB transactions for 1%         |
| **99% no constraints**       | ✅ No transactions for 99% | ✅ Standard CRUD             | ✅ Async where possible           |
| **Model relationships**      | ✅ Foreign keys            | ⚠️ Eventual via events       | ✅ Foreign keys + RLS             |
| **Multi-tenant**             | ✅ Single DB + RLS         | ✅ Single DB + tenant_id     | ✅ Single DB + RLS + escape hatch |
| **Engineering simplicity**   | ✅ Standard patterns       | ❌ Event sourcing complexity | ✅✅ KISS + pragmatic             |
| **Cost**                     | ✅ $200/mo                 | ✅ $200/mo                   | ✅ $200-$2000/mo                  |

**Facilitator Verdict**:

**Recommended**: Proposal C (Alex's Pragmatic Single-Database)

**Reasoning**:

1. Solves ALL bedrock constraints
2. Minimizes engineering complexity (event sourcing is powerful but overkill here)
3. Provides future escape hatch (dedicated DB for outliers) without prematurely optimizing
4. Uses battle-tested tools (PostgreSQL RLS, transactions)

**Proposal B (Victor's Event Sourcing)** is brilliant for systems where:

- Audit log is critical (finance, healthcare)
- Temporal queries needed ('what was balance on date X?')
- Complexity budget allows

But we have no evidence these requirements exist. YAGNI principle applies.

**Proposal A (Winston's Hybrid)** is nearly identical to C, but C adds escape hatch for outliers."

---

#### Builder Round 3: Implementation Details

**🏗️ Alex Chen (Product Manager)** (refining Proposal C):

"Let me detail the implementation for developer clarity:

**Database Schema** (Single PostgreSQL):

```sql
-- All tables include tenant_id
CREATE TABLE accounts (
  id UUID PRIMARY KEY,
  tenant_id UUID NOT NULL,
  balance_cents INTEGER NOT NULL,
  updated_at TIMESTAMPTZ NOT NULL
);

-- Row-Level Security for isolation
ALTER TABLE accounts ENABLE ROW LEVEL SECURITY;

CREATE POLICY tenant_isolation ON accounts
  USING (tenant_id = current_setting('app.current_tenant')::UUID);

-- Foreign keys for relationships
CREATE TABLE payments (
  id UUID PRIMARY KEY,
  tenant_id UUID NOT NULL,
  account_id UUID NOT NULL REFERENCES accounts(id),
  amount_cents INTEGER NOT NULL,
  created_at TIMESTAMPTZ NOT NULL
);
```

**Application Code** (Transactions for 1% only):

```javascript
// CRITICAL OPERATION (1%): Payment processing
async function processPayment(tenantId, userId, amountCents) {
  const client = await pool.connect();
  try {
    await client.query('BEGIN ISOLATION LEVEL SERIALIZABLE');
    await client.query('SET app.current_tenant = $1', [tenantId]);

    // Atomic operations
    await client.query('UPDATE accounts SET balance_cents = balance_cents - $1 WHERE user_id = $2', [amountCents, userId]);
    await client.query('INSERT INTO payments (account_id, amount_cents) VALUES ($1, $2)', [accountId, amountCents]);
    await client.query('UPDATE subscriptions SET status = $1 WHERE user_id = $2', ['active', userId]);

    await client.query('COMMIT');
  } catch (err) {
    await client.query('ROLLBACK');
    throw err; // Let caller handle retry
  } finally {
    client.release();
  }
}

// STANDARD OPERATION (99%): Profile update
async function updateProfile(tenantId, userId, newName) {
  // No transaction needed
  await pool.query('SET app.current_tenant = $1', [tenantId]);
  await pool.query('UPDATE users SET name = $1 WHERE id = $2', [newName, userId]);
  // Async search index update (eventual consistency)
  await queue.publish('search.index.user', { userId, tenantId });
}
```

**Migration Path**:

```
Phase 1 (Month 1): Migrate all tenants to single database
Phase 2 (Month 2-3): Monitor performance, identify outliers
Phase 3 (Month 4+): IF needed, split top 1% of tenants to dedicated DBs
```

**Cost Model**:

```
Current (100 databases): $20,000/mo
Phase 1 (1 database): $200/mo (99% reduction)
Phase 3 (1 + 3 dedicated): $800/mo (96% reduction)

Annual savings: $230,400
```

**Evidence**: Implementation matches bedrock constraints with measurable ROI."

---

### Phase 3 Summary

**🧙 BMad Master**:

**PHASE 3 COMPLETE: Reconstruction Summary**

**Problem**: Choose data architecture for SaaS product

**Old Approach** (based on discarded assumptions):

- 100 separate PostgreSQL databases (one per tenant)
- All operations use transactions
- Database-level isolation for security
- Cost: $20,000/month

**New Approach** (built from fundamentals):

- Single PostgreSQL database with Row-Level Security
- Transactions ONLY for ~1% of operations (payments, critical writes)
- Tenant isolation via RLS policies (proven security model)
- Escape hatch: Dedicated DB for outliers (top 1%) if needed
- Cost: $200-$800/month

**Key Differences**:
| Aspect | Old (Convention) | New (First Principles) |
|--------|------------------|------------------------|
| **Architecture** | Multi-database | Single database + RLS |
| **Transactions** | All operations | 1% of operations |
| **Isolation** | Physical separation | Row-level policies |
| **Cost** | $20,000/mo | $200-$800/mo |
| **Operational** | 100× backups, migrations | 1× backup, migration |
| **Savings** | Baseline | **$230,400/year** |

**Validated Constraints Used**:

1. ✅ Avoid $535 inconsistency cost → Transactions for payments only
2. ✅ Model relationships → Foreign keys in single database
3. ✅ Multi-tenant isolation → RLS (PostgreSQL native feature)

**Discarded Conventions Ignored**:

- ❌ "Everyone uses separate databases" → No evidence required
- ❌ "Need transactions everywhere" → Only where economics justify
- ❌ "Physical separation for security" → RLS is proven sufficient

**Radical Difference**: 96-99% cost reduction, 100× operational simplicity, same (or better) security/compliance.

_[Final checkpoint saved]_

---

## 📊 Comparison & Synthesis

**🧙 BMad Master**:

Let's compare the old approach vs. new approach across all dimensions:

### Architecture Comparison

**OLD: Multi-Database Architecture**

```
Tenant A → PostgreSQL DB A (dedicated)
Tenant B → PostgreSQL DB B (dedicated)
Tenant C → PostgreSQL DB C (dedicated)
...
Tenant Z → PostgreSQL DB Z (dedicated)

Total: 100 databases
```

**Assumptions Driving Old**:

- Separate databases for isolation (security assumption)
- Each tenant scales independently (scale assumption)
- Database-level backups per tenant (operational assumption)

**NEW: Single-Database Architecture**

```
All Tenants → PostgreSQL DB (shared)
  ├── Row-Level Security (RLS) policies
  ├── tenant_id column (indexed)
  └── Foreign keys for relationships

Outliers (if needed) → Dedicated DB (escape hatch)
```

**Fundamentals Driving New**:

- Cost of inconsistency ($535) requires consistency for 1% of operations
- No evidence requiring physical separation
- Economic constraint: $230K/year savings

---

### Security & Compliance

| Requirement                      | Old Approach            | New Approach                    | Winner                            |
| -------------------------------- | ----------------------- | ------------------------------- | --------------------------------- |
| **Data isolation**               | Physical (separate DBs) | Logical (RLS policies)          | **Tie** (both proven)             |
| **GDPR compliance**              | Per-tenant deletion     | `DELETE WHERE tenant_id = X`    | **New** (simpler)                 |
| **SOC2 audit trail**             | 100× database logs      | Centralized audit log           | **New** (easier auditing)         |
| **Access control**               | Database credentials    | RLS + app.current_tenant        | **New** (defense-in-depth)        |
| **Backup/restore single tenant** | Database-level backup   | Logical backup (pg_dump filter) | **Old** (slightly faster restore) |

**Verdict**: New approach meets all compliance requirements with less operational overhead.

---

### Performance & Scale

| Scenario                      | Old Approach            | New Approach                               | Analysis                           |
| ----------------------------- | ----------------------- | ------------------------------------------ | ---------------------------------- |
| **Small tenant (100 users)**  | Dedicated DB (overkill) | Shared DB                                  | **New** wins (no overhead)         |
| **Medium tenant (10K users)** | Dedicated DB            | Shared DB                                  | **Tie** (both perform well)        |
| **Large tenant (1M users)**   | Dedicated DB            | Shared DB → Migrate to dedicated if needed | **New** wins (pay when needed)     |
| **Query performance**         | No cross-tenant queries | Requires `tenant_id` filtering             | **Old** (slightly simpler queries) |
| **Connection pooling**        | 100× connection pools   | 1× connection pool                         | **New** wins (resource efficiency) |

**Verdict**: New approach scales more cost-effectively, with escape hatch for outliers.

---

### Operational Complexity

| Task                   | Old Approach            | New Approach                        | Time Savings    |
| ---------------------- | ----------------------- | ----------------------------------- | --------------- |
| **Schema migration**   | Deploy to 100 databases | Deploy to 1 database                | **99× faster**  |
| **Backup**             | 100× backup jobs        | 1× backup job                       | **99× faster**  |
| **Monitoring**         | 100× dashboards         | 1× dashboard + tenant-level metrics | **95× simpler** |
| **Onboard new tenant** | Provision new database  | `INSERT INTO tenants`               | **100× faster** |
| **Debug data issue**   | Find correct database   | Query with `tenant_id` filter       | **Equal**       |

**Verdict**: New approach reduces operational overhead by 95-99%.

---

### Cost Analysis

**Old Approach (100 databases)**:

```
100 databases × $200/mo = $20,000/mo = $240,000/yr

Operational overhead:
- DevOps time: 40 hrs/mo × $100/hr = $4,000/mo
- Backup storage: 100× $50/mo = $5,000/mo

Total: $29,000/mo = $348,000/yr
```

**New Approach (1 database + escape hatch)**:

```
1 database × $200/mo = $200/mo

IF 3 outliers need dedicated DBs:
  3 databases × $200/mo = $600/mo

Operational overhead:
- DevOps time: 4 hrs/mo × $100/hr = $400/mo
- Backup storage: 1× $50/mo = $50/mo

Total: $1,250/mo = $15,000/yr
```

**Annual Savings**: $348,000 - $15,000 = **$333,000/year** (96% reduction)

---

### Risk Analysis

| Risk                        | Old Approach                 | New Approach                        | Mitigation                |
| --------------------------- | ---------------------------- | ----------------------------------- | ------------------------- |
| **Tenant data leak**        | Low (physical separation)    | Low (RLS + app-level checks)        | Defense-in-depth          |
| **Performance degradation** | Low (isolated resources)     | Medium (noisy neighbor possible)    | Monitoring + escape hatch |
| **Operational failure**     | High (100× surface area)     | Low (1× surface area)               | N/A                       |
| **Cost overrun**            | High ($20K/mo fixed)         | Low ($200-$1,250/mo)                | N/A                       |
| **Vendor lock-in**          | Medium (PostgreSQL-specific) | Medium (RLS is PostgreSQL-specific) | Tie                       |

**Verdict**: New approach has slightly higher performance risk, but far lower operational/cost risk.

---

### Decision Matrix

**Recommended**: **New Approach (Single-Database + RLS)**

**Rationale**:

1. **Economic**: $333K/year savings (96% cost reduction)
2. **Operational**: 95-99× reduction in operational complexity
3. **Security**: Meets all compliance requirements (RLS is proven)
4. **Scale**: Escape hatch for outliers (no architectural ceiling)
5. **Evidence-Based**: Built from validated fundamentals, not convention

**When Old Approach Wins**:

- If you have 1-10 tenants (not 100+) → Multi-database is simpler
- If regulatory requirement MANDATES physical separation → Use multi-database
- If you have infinite budget and operations team → Multi-database works

**Our Context**: 100 tenants, standard SaaS compliance, limited budget → **New approach is clear winner**

---

## 🎯 Session Conclusion

**🧙 BMad Master**:

**FIRST PRINCIPLES SESSION COMPLETE**

**What We Accomplished**:

**Phase 1 (Deconstruct)**: Challenged 12 assumptions

- **Discarded**: 11 assumptions (91.7%)
- **Validated**: 1 assumption (reduced to bedrock economic constraint)

**Phase 2 (Validate)**: Questioned the "fundamental"

- **Surface**: "Need ACID transactions"
- **Bedrock**: "Cost of inconsistency ($535) exceeds cost of consistency (microseconds)"

**Phase 3 (Reconstruct)**: Built new architecture from fundamentals

- **Old**: 100 separate databases, $348K/year
- **New**: 1 shared database + RLS, $15K/year
- **Savings**: $333K/year (96% reduction)

**Radical Outcome**: Completely inverted the architecture by questioning conventions.

---

**Next Steps**:

1. **Prototype** (Week 1-2):
   - Set up single PostgreSQL database
   - Implement RLS policies for 3 test tenants
   - Migrate 1% of data (payments) with transactions
   - Validate security isolation

2. **Pilot** (Week 3-4):
   - Migrate 10 tenants to new architecture
   - Monitor performance, security, operational overhead
   - Measure cost savings

3. **Rollout** (Month 2-3):
   - Migrate remaining 90 tenants
   - Decommission old databases
   - Realize $333K annual savings

4. **Monitor** (Month 4+):
   - Track for outliers (>10M records)
   - If needed, split outliers to dedicated DBs (escape hatch)
   - Continuously validate fundamentals

---

**Key Takeaway**:

**"Most of what we call 'best practices' are just 'common practices' - conventions adopted without evidence. First Principles Thinking forces us to prove every assumption, discarding 90%+ of them, and rebuilding from bedrock truths. The result is often radically simpler, cheaper, and better."**

**Session participants**: 7 agents across 4 cohorts
**Duration**: ~3 hours (4 checkpoints saved)
**Assumption discard rate**: 91.7%
**Annual cost savings**: $333,000

_[Session ended]_

---

# Section 6: Implementation Guide

## How to Integrate Into BMad Source Code

This section provides step-by-step instructions for integrating the First Principles multi-agent workflow into the BMad Method source code.

### Option 1: Core Workflow (Recommended)

Add First Principles as a **core workflow** alongside brainstorming and party-mode.

#### File Structure

```
src/core/workflows/first-principles/
├── workflow.yaml              # Configuration
├── instructions.md            # XML workflow steps
├── agent-assignments.yaml     # Cohort selection criteria
├── template.md                # Progressive checkpoint template
└── README.md                  # Documentation
```

#### Step 1: Create Workflow Directory

```bash
cd src/core/workflows
mkdir first-principles
cd first-principles
```

#### Step 2: Create workflow.yaml

Copy the annotated [workflow.yaml](#section-41-annotated-workflowyaml) from Section 4.1, removing design notes:

```yaml
# First Principles Thinking - Multi-Agent Workflow
name: 'first-principles'
description: 'Challenge every assumption and rebuild solutions from fundamental truths using multi-agent Socratic questioning'
author: 'BMad'

# Critical data sources
agent_manifest: '{project-root}/{bmad_folder}/_cfg/agent-manifest.csv'
agent_assignments: '{project-root}/{bmad_folder}/core/workflows/first-principles/agent-assignments.yaml'
date: system-generated

# Configuration
phases:
  - deconstruct # Challenge every assumption
  - validate # Identify true fundamentals
  - reconstruct # Rebuild from scratch

challenge_intensity:
  default: 'aggressive'
  options:
    - gentle # For fragile teams or sensitive topics
    - moderate # Balanced approach
    - aggressive # Maximum skepticism (recommended)

evidence_standards:
  highest_tier:
    - 'laws of physics'
    - 'mathematical proof'
    - 'thermodynamic constraints'
  high_tier:
    - 'economic laws (supply/demand)'
    - 'biological constraints'
  medium_tier:
    - 'engineering constraints'
    - 'regulatory requirements'
  low_tier:
    - 'industry conventions'
    - 'best practices'
  insufficient:
    - 'everyone does it this way'
    - "it's always been done like this"

# Template for progressive checkpoint output
template: '{project-root}/{bmad_folder}/core/workflows/first-principles/template.md'
instructions: '{project-root}/{bmad_folder}/core/workflows/first-principles/instructions.md'

# Exit conditions
exit_triggers:
  - '*exit'
  - '*done'

standalone: true

# Web bundle configuration
web_bundle:
  name: 'first-principles'
  description: 'Challenge every assumption and rebuild solutions from fundamental truths using multi-agent Socratic questioning'
  author: 'BMad'
  instructions: '{bmad_folder}/core/workflows/first-principles/instructions.md'
  agent_manifest: '{bmad_folder}/_cfg/agent-manifest.csv'
  agent_assignments: '{bmad_folder}/core/workflows/first-principles/agent-assignments.yaml'
  web_bundle_files:
    - '{bmad_folder}/core/workflows/first-principles/instructions.md'
    - '{bmad_folder}/core/workflows/first-principles/agent-assignments.yaml'
    - '{bmad_folder}/core/workflows/first-principles/template.md'
    - '{bmad_folder}/_cfg/agent-manifest.csv'
```

#### Step 3: Create agent-assignments.yaml

Copy from [Section 4.2](#section-42-annotated-agent-assignmentsyaml), removing design notes:

```yaml
# First Principles - Agent Cohort Assignments
# Defines which agents fill Challenger, Defender, Builder, and Facilitator roles

cohorts:
  challengers:
    description: 'Agents who destroy assumptions aggressively'
    agent_criteria:
      primary:
        - 'test' # TEA: Quality mindset
        - 'quality' # QA roles
        - 'security' # Security analysts
        - 'risk' # Risk analysts
        - 'innovation' # Innovation strategists
      fallback:
        - 'engineer' # Backend engineers (technical depth)
        - 'architect' # Technical architects (system thinking)

    scoring:
      role_match: 40
      challenging_style: 30
      technical_depth: 20
      domain_expertise: 10

    selection_count:
      min: 2
      ideal: 3
      max: 4

  defenders:
    description: 'Agents who provide evidence or concede gracefully'
    agent_criteria:
      primary:
        - 'architect' # Solution architects
        - 'product' # Product managers
        - 'engineer' # Backend engineers
        - 'data' # Data engineers
      fallback:
        - 'frontend' # Frontend engineers
        - 'design' # UX/UI designers

    scoring:
      role_match: 40
      evidence_based_thinking: 30
      domain_expertise: 20
      communication_clarity: 10

    selection_count:
      min: 2
      ideal: 3
      max: 4

  builders:
    description: 'Agents who reconstruct solutions from fundamentals'
    agent_criteria:
      primary:
        - 'architect' # Solution architects (synthesis)
        - 'product' # Product managers (pragmatism)
        - 'engineer' # Engineers (implementation)
        - 'innovation' # Innovation strategists (creativity)
      fallback:
        - 'design' # UX designers (user-centric)
        - 'data' # Data engineers (evidence-based)

    scoring:
      role_match: 40
      creative_thinking: 30
      technical_feasibility: 20
      pragmatism: 10

    selection_count:
      min: 2
      ideal: 3
      max: 4

  facilitator:
    description: 'Orchestrator who renders evidence-based verdicts'
    agent_criteria:
      required:
        - 'bmad-master' # BMad Master is always facilitator

    selection_count:
      fixed: 1
```

#### Step 4: Create instructions.md

Copy the [annotated instructions.md](#section-43-annotated-instructionsmd) from Section 4.3, removing all design notes (content between `<!-- DESIGN NOTE -->` tags).

#### Step 5: Create template.md

Copy the [annotated template.md](#section-44-annotated-templatemd) from Section 4.4, removing design notes.

#### Step 6: Add Menu Item to BMad Master

Edit `src/core/agents/bmad-master.agent.yaml`:

```yaml
menu:
  # ... existing menu items ...

  - trigger: 'first-principles'
    workflow: 'first-principles'
    description: 'Challenge every assumption and rebuild solutions from fundamental truths using multi-agent Socratic questioning'
    icon: '💎'
    tags:
      - 'recommended'
      - 'multi-agent'
      - 'analytical'
```

#### Step 7: Test the Workflow

```bash
# Install BMad Method (or reinstall if already installed)
npm run bmad:install

# In your IDE, trigger the workflow:
# Type: @bmad first-principles
```

---

### Option 2: BMad Builder Integration

Add First Principles as a **reusable template** in BMad Builder for custom workflows.

#### File Structure

```
src/modules/bmb/workflows/first-principles-template/
├── workflow.yaml
├── instructions.md
├── agent-assignments.yaml
└── template.md
```

Follow the same steps as Option 1, but place files in `src/modules/bmb/workflows/` instead of `src/core/workflows/`.

Add menu item to BMad Builder agent:

```yaml
menu:
  - trigger: 'template-first-principles'
    workflow: 'first-principles-template'
    description: 'Use First Principles template for custom analytical workflows'
    icon: '🏗️'
```

---

### Option 3: Standalone Module

Create a **dedicated module** for First Principles workflows (useful if building multiple Aristotelian frameworks).

#### File Structure

```
src/modules/first-principles/
├── agents/
│   └── aristotle.agent.yaml        # Optional: Dedicated facilitator
├── workflows/
│   └── core-workflow/
│       ├── workflow.yaml
│       ├── instructions.md
│       ├── agent-assignments.yaml
│       └── template.md
├── _module-installer/
│   └── install.js
└── README.md
```

This approach allows:

- Custom agents optimized for First Principles thinking
- Multiple variant workflows (e.g., "first-principles-rapid" for 1-hour sessions)
- Independent versioning and distribution

---

## Testing Your Implementation

### Unit Test: Agent Selection

Test that the cohort assignment logic correctly selects agents:

```javascript
// test/test-first-principles-agent-selection.js
const { selectAgentCohorts } = require('../tools/cli/lib/agent-selector');
const agentManifest = require('../src/core/_cfg/agent-manifest.csv');

describe('First Principles Agent Selection', () => {
  it('should select 3 challengers from test/security/innovation roles', () => {
    const cohorts = selectAgentCohorts(agentManifest, 'first-principles');
    expect(cohorts.challengers.length).toBeGreaterThanOrEqual(2);
    expect(cohorts.challengers.length).toBeLessThanOrEqual(4);
  });

  it('should always select bmad-master as facilitator', () => {
    const cohorts = selectAgentCohorts(agentManifest, 'first-principles');
    expect(cohorts.facilitator[0].name).toBe('bmad-master');
  });
});
```

### Integration Test: Full Workflow

Test a complete session (may require Claude/GPT API):

```javascript
// test/test-first-principles-workflow.js
const { runWorkflow } = require('../tools/cli/lib/workflow-runner');

describe('First Principles Workflow', () => {
  it('should complete all three phases', async () => {
    const result = await runWorkflow('first-principles', {
      problem: 'Should we use microservices or monolith?',
      challenge_intensity: 'moderate',
    });

    expect(result.phases.completed).toContain('deconstruct');
    expect(result.phases.completed).toContain('validate');
    expect(result.phases.completed).toContain('reconstruct');
    expect(result.assumptions.discardRate).toBeGreaterThan(0.6); // 60%+
  });
});
```

### Manual Test: Example Session

Run a real session with a sample problem:

**Problem**: "Should we build our SaaS product with separate databases per tenant or a single shared database?"

**Expected Outcome**:

- Phase 1: 10-15 assumptions identified, 60-90% discarded
- Phase 2: Remaining "fundamentals" reduced to economic/physics constraints
- Phase 3: Radically different solution from original assumptions
- Session duration: 2-4 hours (with checkpoints)

---

## Customization Options

### 1. Adjust Challenge Intensity

For teams new to First Principles thinking, start with `challenge_intensity: gentle`:

```yaml
# workflow.yaml
challenge_intensity:
  default: 'gentle' # Changed from "aggressive"
```

This modifies challenger behavior:

- **Gentle**: Question assumptions respectfully, accept partial evidence
- **Moderate**: Challenge with evidence demands, push back on weak defenses
- **Aggressive**: Destroy assumptions ruthlessly, accept only physics/economics

### 2. Domain-Specific Evidence Standards

Customize evidence hierarchy for your domain:

```yaml
# workflow.yaml - Example for healthcare domain
evidence_standards:
  highest_tier:
    - 'laws of physics'
    - 'biological constraints (anatomy, physiology)'
    - 'regulatory mandates (HIPAA, FDA)'
  high_tier:
    - 'clinical evidence (RCTs)'
    - 'patient safety requirements'
```

### 3. Custom Agent Cohorts

Override default cohorts for specialized teams:

```yaml
# agent-assignments.yaml - Example for data science team
cohorts:
  challengers:
    agent_criteria:
      primary:
        - 'statistician' # Custom role
        - 'ml-engineer' # Custom role
        - 'data-quality' # Custom role
```

### 4. Checkpoint Frequency

Adjust how often checkpoints are saved:

```yaml
# workflow.yaml
checkpoint_protocol:
  frequency: 'after_each_assumption' # Options: after_each_cluster, after_each_phase
  auto_save: true
```

---

## Troubleshooting

### Issue: Not Enough Agents Selected

**Problem**: `Error: Insufficient agents for challengers cohort (need 2, got 1)`

**Solution**: Lower minimum selection counts:

```yaml
# agent-assignments.yaml
challengers:
  selection_count:
    min: 1 # Changed from 2
    ideal: 2 # Changed from 3
```

### Issue: Sessions Too Long (>4 hours)

**Problem**: Workflow gets stuck in endless challenge-defend loops

**Solution**: Enable facilitator time limits:

```yaml
# workflow.yaml
facilitator_controls:
  max_rounds_per_assumption: 3
  force_verdict_after_minutes: 10
```

### Issue: Too Many Assumptions Validated (Not Discarding Enough)

**Problem**: Discard rate < 60%, suggesting defenders aren't being challenged hard enough

**Solution**: Increase challenge intensity or coach facilitator:

```yaml
# instructions.md - Add to facilitator guidance
<facilitator-coaching>
  If defender provides "engineering convenience" or "best practice" as evidence:
  - REJECT immediately
  - Demand physics/economics/regulatory evidence
  - Default verdict: DISCARDED
</facilitator-coaching>
```

---

## Performance Optimization

### Token Usage Reduction

First Principles sessions are token-intensive (2-4 hours). Optimize with:

#### 1. Progressive Checkpointing

Save state after each assumption cluster to avoid re-processing:

```xml
<!-- instructions.md -->
<checkpoint trigger="after_cluster">
  <save>
    - All assumptions processed so far
    - Verdicts rendered
    - Agent contributions
  </save>
  <on_resume>
    - Load previous checkpoint
    - Skip to next unprocessed cluster
  </on_resume>
</checkpoint>
```

#### 2. Assumption Clustering

Group related assumptions to reduce redundant challenge-defend cycles:

```xml
<!-- instructions.md -->
<substep n="1b" goal="Cluster Related Assumptions">
  <logic>
    Group assumptions by domain:
    - Cluster 1: Architecture (DB, services, APIs)
    - Cluster 2: Data/Security
    - Cluster 3: Scale/Performance
    - Cluster 4: Operational

    Process each cluster together (batch similar challenges)
  </logic>
</substep>
```

#### 3. Parallel Agent Responses

Allow multiple challengers to contribute simultaneously:

```xml
<!-- instructions.md -->
<substep n="2a" goal="Challenge Round">
  <action>ALL challengers respond in parallel (not sequentially)</action>
  <format>
    ⚔️ Challenger 1: [Challenge to A1, A2, A3]
    ⚔️ Challenger 2: [Challenge to A1, A2, A3]
    ⚔️ Challenger 3: [Challenge to A1, A2, A3]
  </format>
</substep>
```

---

## Next Steps

1. **Choose Integration Option**: Core workflow (Option 1) recommended for most users
2. **Copy Files**: Use annotated files from Section 4, removing design notes
3. **Test with Sample Problem**: Run a 30-minute test session
4. **Customize**: Adjust intensity, evidence standards, cohorts for your team
5. **Deploy**: Add to BMad installation, document for users

**Pro Tip**: Start with a low-stakes problem (e.g., "What framework should we use for unit tests?") before tackling critical architectural decisions. This lets teams learn the framework dynamics without risk.

---

# Section 7: Comparison - First Principles vs Other Frameworks

This section compares First Principles Thinking to other analytical frameworks in BMad's catalog.

## Framework Comparison Matrix

| Framework             | Purpose                                               | Mindset                      | Output                                  | Duration   | Discard Rate | Best For                                             |
| --------------------- | ----------------------------------------------------- | ---------------------------- | --------------------------------------- | ---------- | ------------ | ---------------------------------------------------- |
| **First Principles**  | Question ALL assumptions, rebuild from bedrock truths | Destructive → Reconstructive | Radically different solution            | 2-4 hours  | 60-90%       | Critical decisions with high risk of convention bias |
| **Six Thinking Hats** | Multi-perspective analysis                            | Exploratory → Evaluative     | Balanced decision with all perspectives | 1-2 hours  | N/A          | Complex decisions requiring diverse viewpoints       |
| **Five Whys**         | Root cause analysis                                   | Drilling → Discovery         | Deep understanding of single problem    | 30-60 min  | N/A          | Debugging, incident analysis, problem diagnosis      |
| **SWOT**              | Situational assessment                                | Categorizing → Planning      | Strategic overview                      | 30-60 min  | N/A          | Market analysis, strategic planning, risk assessment |
| **Pre-Mortem**        | Failure anticipation                                  | Pessimistic → Preventive     | Risk mitigation plan                    | 30-45 min  | N/A          | Project launch, high-stakes decisions                |
| **Design Thinking**   | User-centered innovation                              | Empathetic → Creative        | User-validated prototype                | Days-weeks | N/A          | Product design, UX improvement, innovation           |

---

## When to Use First Principles vs Alternatives

### First Principles vs Six Thinking Hats

**Use First Principles when**:

- Conventional wisdom is likely wrong (e.g., "everyone does it this way")
- Stakes are high (cost, technical debt, vendor lock-in)
- You need a radically different solution (not incremental improvement)
- Team is willing to challenge sacred cows

**Example**: "Should we use microservices?"

- **First Principles**: Challenges assumption that microservices are needed, may conclude monolith is better
- **Six Hats**: Explores pros/cons of microservices, assumes decision is microservices vs monolith

**Use Six Thinking Hats when**:

- Problem space is well-understood
- Need balanced consideration of trade-offs
- Team dynamics require structured turn-taking (prevent loudest voice from dominating)
- Decision is between known options (A vs B vs C)

**Example**: "Which JavaScript framework: React vs Vue vs Svelte?"

- **Six Hats**: White (data on adoption), Red (team preference), Black (risks of each), Yellow (benefits)
- **First Principles**: Might conclude "build vanilla JS components" (rejects all frameworks)

---

### First Principles vs Five Whys

**Use First Principles when**:

- You want to question whether the problem itself is real
- Root cause might be a false assumption (not a "why" to drill into)
- Solution requires rebuilding from scratch

**Example**: "Why is our deployment slow?"

- **Five Whys**:
  - Why slow? → Because 100-database migrations take time
  - Why 100 databases? → Because we have 100 tenants
  - Why separate DBs per tenant? → Because we assumed isolation required it
  - _(Stops here with insight: challenge the separation assumption)_
- **First Principles**:
  - Challenges: "Is separate-database isolation actually required?"
  - Verdict: DISCARDED (RLS provides isolation)
  - Rebuilds: Single database → deployments 99× faster

**Use Five Whys when**:

- Problem is concrete and observable ("deployment failed," "customer churned")
- Root cause is buried under symptoms
- Need quick diagnosis (30 min vs 3 hours for First Principles)

**Example**: "Why did the payment processing fail?"

- **Five Whys**: Drills to root cause (database connection timeout)
- **First Principles**: Overkill (payment failure is real, not an assumption)

---

### First Principles vs SWOT

**Use First Principles when**:

- SWOT categories (strengths/weaknesses) might be based on false assumptions
- Need to validate whether "threats" are real or fear-based
- Outcome should be architectural change, not strategic plan

**Example**: "Evaluate our multi-tenant architecture"

- **SWOT**:
  - Strengths: "Physical isolation is secure"
  - Weaknesses: "High operational cost"
  - Opportunities: "Upsell dedicated databases"
  - Threats: "Competitors offer single-database SaaS"
  - _(Accepts multi-database as given)_
- **First Principles**:
  - Challenges: "Is physical isolation actually a strength? Prove it."
  - Verdict: DISCARDED (RLS is equally secure)
  - Rebuilds: Single-database architecture (strength becomes weakness)

**Use SWOT when**:

- Assessing a market, product, or business (not architecture)
- Need structured brainstorming of factors
- Decision is strategic (market entry, positioning) not technical

**Example**: "Should we expand to EU market?"

- **SWOT**: Strengths (brand), Weaknesses (no EU presence), Opportunities (large market), Threats (GDPR)
- **First Principles**: Not applicable (market expansion is business strategy, not architecture)

---

### First Principles vs Pre-Mortem

**Use First Principles when**:

- Assumptions underlying the project need validation
- Failure might be because "the plan itself is built on false foundations"
- Team has time to rethink architecture (not committed to ship date)

**Example**: "Pre-launch review of new microservices architecture"

- **Pre-Mortem**: "Project failed because service mesh was too complex" → Mitigate: Simplify mesh
- **First Principles**: "Do we need microservices at all?" → Verdict: DISCARDED → Build monolith instead

**Use Pre-Mortem when**:

- Project is already greenlit (can't question fundamental approach)
- Need to identify failure modes and mitigations
- Goal is risk reduction, not architectural pivot

**Example**: "Pre-launch review of Black Friday sale"

- **Pre-Mortem**: "Sale failed because servers crashed" → Mitigate: Load testing, autoscaling
- **First Principles**: Not applicable (Black Friday sale is not an assumption to challenge)

---

### First Principles vs Design Thinking

**Use First Principles when**:

- User needs might be based on assumptions (not validated with users)
- Existing solutions cargo-cult features without understanding why
- Need to question "must-have" features

**Example**: "Design a project management tool"

- **Design Thinking**:
  - Empathize: Users want Gantt charts (based on interviews)
  - Prototype: Build Gantt chart feature
  - Test: Users validate they want Gantt charts
  - _(Accepts user request at face value)_
- **First Principles**:
  - Challenges: "WHY do users want Gantt charts? What problem does it solve?"
  - Validates: Users want "visibility into task dependencies"
  - Rebuilds: Simple kanban board with dependency markers (no Gantt chart)

**Use Design Thinking when**:

- Building user-facing products (not infrastructure/architecture)
- User needs are not well understood (empathy research required)
- Iteration with user feedback is possible

**Example**: "Redesign mobile app onboarding"

- **Design Thinking**: Empathize → Prototype → Test → Iterate
- **First Principles**: Not applicable (user experience is not an assumption to deconstruct)

---

## Combining Frameworks

First Principles can be **chained** with other frameworks for powerful outcomes:

### Chain 1: First Principles → Six Hats

1. **First Principles**: Discard 90% of assumptions, identify bedrock truths
2. **Six Hats**: Explore implementation options using only validated fundamentals

**Example**:

- **First Principles**: Validate that "need ACID transactions for 1% of operations"
- **Six Hats**: Decide between PostgreSQL vs DynamoDB vs event sourcing
  - White Hat: Data on each option's ACID support
  - Red Hat: Team familiarity
  - Black Hat: Risks of each
  - Yellow Hat: Benefits

### Chain 2: First Principles → Pre-Mortem

1. **First Principles**: Rebuild architecture from fundamentals
2. **Pre-Mortem**: Identify risks in new approach

**Example**:

- **First Principles**: Conclude single-database with RLS is optimal
- **Pre-Mortem**: "Project failed because RLS had SQL injection vulnerability"
  - Mitigate: Defense-in-depth (RLS + application-level checks)

### Chain 3: Design Thinking → First Principles

1. **Design Thinking**: Discover user needs through empathy
2. **First Principles**: Challenge whether user-requested features are necessary

**Example**:

- **Design Thinking**: Users request "export to PDF" feature
- **First Principles**:
  - Challenge: "WHY do users want PDF? What job are they hiring PDF for?"
  - Validate: Users need "shareable, non-editable format"
  - Rebuild: Provide read-only shareable link (no PDF generation needed)

---

## Success Metrics Comparison

| Framework             | Success Metric            | First Principles Equivalent      |
| --------------------- | ------------------------- | -------------------------------- |
| **Six Thinking Hats** | All perspectives explored | All assumptions challenged       |
| **Five Whys**         | Root cause identified     | Bedrock truth validated          |
| **SWOT**              | Comprehensive SWOT grid   | 60%+ assumptions discarded       |
| **Pre-Mortem**        | Risk mitigations defined  | Conventional solutions rejected  |
| **Design Thinking**   | User-validated prototype  | Solution built from fundamentals |

**First Principles unique metric**: **Assumption Discard Rate**

- <40%: Defenders dominated (didn't challenge hard enough)
- 40-60%: Balanced (good session)
- 60-90%: Excellent (most conventions discarded)
- > 90%: Exceptional (nearly total rebuild)

---

## Framework Selection Decision Tree

```
START: Do you have a problem/decision to make?
  │
  ├─ Is it a concrete problem with observable symptoms?
  │  └─ YES → Use Five Whys (diagnose root cause)
  │
  ├─ Is it about understanding user needs?
  │  └─ YES → Use Design Thinking (empathy research)
  │
  ├─ Is it a market/business assessment?
  │  └─ YES → Use SWOT (strategic overview)
  │
  ├─ Are you about to launch a project?
  │  └─ YES → Use Pre-Mortem (identify risks)
  │
  ├─ Is it a decision between known options (A vs B vs C)?
  │  └─ YES → Use Six Thinking Hats (balanced evaluation)
  │
  └─ Is it a critical decision where conventional wisdom might be wrong?
     └─ YES → Use First Principles (challenge everything)
```

---

## Real-World Framework Pairing Examples

### Example 1: Database Architecture Decision

**Problem**: "Choose database for new SaaS product"

**Recommended Sequence**:

1. **First Principles** (2-3 hours): Challenge assumptions about "need relational DB," "need separate DBs per tenant"
   - Outcome: Validated fundamentals (1% of operations need ACID)
2. **Six Thinking Hats** (1 hour): Evaluate specific database options (PostgreSQL vs MySQL vs DynamoDB)
   - White Hat: Performance benchmarks
   - Red Hat: Team familiarity
   - Black Hat: Vendor lock-in risks
3. **Pre-Mortem** (30 min): Identify risks of chosen solution
   - Risk: "RLS policy misconfiguration leads to data leak"
   - Mitigation: Automated policy testing

**Total Time**: 3.5-4.5 hours
**Outcome**: Evidence-based decision with risk mitigations

---

### Example 2: Product Feature Prioritization

**Problem**: "Decide which features to build for MVP"

**Recommended Sequence**:

1. **Design Thinking** (1 week): Understand user needs through interviews
   - Outcome: Users request 15 features
2. **First Principles** (2 hours): Challenge whether requested features are necessary
   - Challenge: "WHY do users want feature X? What job is it doing?"
   - Outcome: 10 of 15 features discarded (users want outcomes, not specific features)
3. **SWOT** (30 min): Assess remaining 5 features
   - Strengths: Validated user need
   - Weaknesses: Engineering complexity
   - Opportunities: Differentiation from competitors
   - Threats: Competitors already have similar features

**Total Time**: 1 week + 2.5 hours
**Outcome**: MVP with 5 essential features (not 15 nice-to-haves)

---

### Example 3: Incident Postmortem

**Problem**: "Production outage lasted 4 hours"

**Recommended Sequence**:

1. **Five Whys** (30 min): Diagnose root cause
   - Why outage? → Database crashed
   - Why crashed? → Ran out of disk space
   - Why out of space? → Logs weren't rotated
   - Why no rotation? → Automation script disabled
   - Why disabled? → Engineer disabled for debugging, forgot to re-enable
2. **First Principles** (1 hour): Challenge operational assumptions
   - Challenge: "Do we need manual log rotation? What prevents automatic cleanup?"
   - Outcome: Rebuild monitoring (automatic disk space alerts, log rotation enforcement)
3. **Pre-Mortem** (30 min): Prevent future similar incidents
   - Risk: "Engineer disables critical automation again"
   - Mitigation: Automation requires 2-person approval to disable

**Total Time**: 2 hours
**Outcome**: Root cause fixed + systemic improvements

---

## Summary: When to Use First Principles

**Use First Principles when you need to**:

- ✅ Challenge conventional wisdom ("everyone does it this way")
- ✅ Validate whether "best practices" apply to your context
- ✅ Make critical architectural decisions (high cost of being wrong)
- ✅ Achieve radically different outcomes (not incremental improvements)
- ✅ Discard 60-90% of assumptions and rebuild from bedrock truths

**Do NOT use First Principles when you need to**:

- ❌ Solve concrete problems with observable symptoms (use Five Whys)
- ❌ Understand user needs through empathy (use Design Thinking)
- ❌ Assess markets/competitors (use SWOT)
- ❌ Identify project risks (use Pre-Mortem)
- ❌ Make quick decisions without time for 2-4 hour sessions
- ❌ Evaluate known options where assumptions are already validated (use Six Hats)

**The Golden Rule**: If you're saying "this is how it's always been done" or "this is industry standard," you need First Principles. If you're saying "we know this is the right approach, but which option should we choose," you need a different framework.

---

**END OF DOCUMENT**

This comprehensive implementation guide provides everything needed to integrate First Principles Thinking into BMad Method as a production-ready multi-agent workflow, matching the depth and rigor of the Six Hats example.
