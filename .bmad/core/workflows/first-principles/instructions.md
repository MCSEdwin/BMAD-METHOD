# First Principles Thinking - Multi-Agent Instructions

<critical>The workflow execution engine is governed by: {project_root}/.bmad/core/tasks/workflow.xml</critical>
<critical>This workflow orchestrates First Principles Thinking: challenge every assumption and rebuild from bedrock truths</critical>

<!-- TTS_INJECTION:first-principles -->

<workflow>

<step n="1" goal="Initialize Framework and Assign Agent Cohorts">
  <action>Load the agent manifest CSV from {{agent_manifest}}</action>
  <action>Load cohort assignment criteria from {{agent_assignments}}</action>
  <action>Parse agent data with roles, expertise, and personalities</action>

  <substep n="1a" goal="Assign Agents to Three Cohorts">
    <logic>
      Score each agent for each cohort (Challengers, Defenders, Builders):

      CHALLENGERS (Destroy assumptions):
      - Primary: test, quality, security, risk, innovation roles
      - Fallback: engineer, architect
      - Scoring: role_match (40) + challenging_style (30) + technical_depth (20) + domain_expertise (10)
      - Select: 2-4 agents

      DEFENDERS (Provide evidence):
      - Primary: architect, product, engineer, data roles
      - Fallback: frontend, design
      - Scoring: role_match (40) + evidence_based_thinking (30) + domain_expertise (20) + clarity (10)
      - Select: 2-4 agents

      BUILDERS (Reconstruct solutions):
      - Primary: architect, product, engineer, innovation roles
      - Fallback: design, data
      - Scoring: role_match (40) + creative_thinking (30) + technical_feasibility (20) + pragmatism (10)
      - Select: 2-4 agents

      FACILITATOR (Orchestrate, render verdicts):
      - Fixed: BMad Master
      - Select: 1 agent

      Note: Agents can be in multiple cohorts (e.g., architect can defend AND build)
    </logic>

  </substep>

  <substep n="1b" goal="Present Cohort Assignments">
    <format>
💎 FIRST PRINCIPLES THINKING ACTIVATED

Cohort Assignments:

⚔️ **CHALLENGERS** (Destroy Assumptions):

- [Agent 1]: [Role] - [Expertise]
- [Agent 2]: [Role] - [Expertise]
- [Agent 3]: [Role] - [Expertise]

🛡️ **DEFENDERS** (Provide Evidence):

- [Agent 1]: [Role] - [Expertise]
- [Agent 2]: [Role] - [Expertise]
- [Agent 3]: [Role] - [Expertise]

🏗️ **BUILDERS** (Reconstruct Solutions):

- [Agent 1]: [Role] - [Expertise]
- [Agent 2]: [Role] - [Expertise]

🧙 **FACILITATOR** (Orchestrate & Judge):

- BMad Master

Total: [X] agents across 4 cohorts

**Evidence Hierarchy (Highest to Lowest):**

1. ✅ Physics/Math (laws, proofs, thermodynamics)
2. ✅ Economics/Biology (supply/demand, biological constraints)
3. ⚠️ Engineering/Regulatory (constraints, requirements)
4. ⚠️ Industry Conventions/Best Practices
5. ❌ "Everyone does it this way" / "Always been done like this" (INSUFFICIENT)

**Challenge Intensity:** {{challenge_intensity}}

What problem/decision would you like to analyze?
</format>
<action>Wait for user to provide problem statement or decision</action>
</substep>
</step>

<step n="2" goal="Initialize First Principles Session">
  <action>Receive user's problem/decision to analyze</action>
  <action>Facilitator clarifies the problem and current assumptions</action>
  <action>Facilitator establishes session goals</action>

  <format>
🧙 **BMad Master:**

**Problem Statement:** [User's problem]

**Current Approach:** [Existing solution or conventional wisdom]

**Session Goal:** Challenge EVERY assumption underlying this approach, discard 60-90% as conventions, rebuild from validated fundamentals only.

**Three-Phase Cycle:**

1. 💥 **Deconstruct** - Challenge every assumption aggressively
2. 💎 **Validate** - Identify true bedrock truths via Socratic questioning
3. 🏗️ **Reconstruct** - Build new solution using ONLY validated fundamentals

**Success Metric:** 60%+ assumption discard rate (most "truths" are conventions)

Let's begin Phase 1!
</format>
</step>

<step n="3" goal="Phase 1 - Deconstruct: Challenge Every Assumption">

  <substep n="3a" goal="Identify All Assumptions">
    <action>Facilitator extracts assumptions from problem statement</action>
    <action>Defenders add assumptions they're aware of</action>
    <action>Cluster related assumptions (Architecture, Data, Scale, Operational, etc.)</action>

    <format>

🧙 **BMad Master:**

I've identified **[N] assumptions** in the current approach:

**Cluster 1: [Category]**

- A1: [Assumption 1]
- A2: [Assumption 2]
- A3: [Assumption 3]

**Cluster 2: [Category]**

- A4: [Assumption 4]
- A5: [Assumption 5]

[Continue for all clusters]

Let's challenge each cluster. Challengers: destroy these assumptions with evidence demands.
</format>
</substep>

  <substep n="3b" goal="Challenge-Defend-Verdict Cycle for Each Cluster" repeat="for-each-cluster">
    <action>Process one assumption cluster at a time</action>

    <challenge_round>
      <action>Challengers attack assumptions in cluster</action>
      <guidelines>
        - Demand evidence (WHY is this true?)
        - Question necessity (Is this REQUIRED or convenient?)
        - Challenge source (Is this physics or convention?)
        - Be aggressive, no politeness needed
      </guidelines>

      <format>

⚔️ **[Challenger 1]:**
"[Assumption X] - WHY? Prove this is required by physics/economics, not just 'how others do it'."

⚔️ **[Challenger 2]:**
"[Assumption Y] - What law of nature requires this? Or is it just cargo-culting?"

⚔️ **[Challenger 3]:**
"[Assumption Z] - Even if true, is this the ONLY way? Prove there are no alternatives."
</format>
</challenge_round>

    <defense_round>
      <action>Defenders provide evidence or concede</action>
      <guidelines>
        - Provide highest-tier evidence possible (physics > economics > engineering > convention)
        - Concede gracefully if evidence is weak
        - No "best practices" or "everyone does it" defenses (insufficient)
        - Cite measurable constraints when possible
      </guidelines>

      <format>

🛡️ **[Defender 1]:**
"[Assumption X] - I can defend this with [evidence type]: [specific evidence]."
**Evidence Quality:** [Physics/Economics/Engineering/Convention]

🛡️ **[Defender 2]:**
"[Assumption Y] - I concede. We chose this because [reason], but it's not fundamental."

🛡️ **[Defender 3]:**
"[Assumption Z] - Partially true. The real constraint is [deeper truth], not [assumption]."
</format>
</defense_round>

    <verdict_round>
      <action>Facilitator renders evidence-based verdict for each assumption</action>
      <guidelines>
        - FUNDAMENTAL: Defended with physics/economics/measurable evidence
        - DISCARDED: Defended with convention, "best practice", or no evidence
        - NEEDS MORE EVIDENCE: Unclear, requires validation
      </guidelines>

      <format>

🧙 **BMad Master - Verdicts for Cluster [N]:**

**A1:** **DISCARDED**

- Reason: Defended with "industry standard" (convention, not constraint)
- Revealed as: Cargo-culting, no evidence required

**A2:** **FUNDAMENTAL** (with caveats)

- Reason: Defended with economic constraint (cost of failure = $X > cost of solution)
- Scope: Applies to [specific context], not universally

**A3:** **DISCARDED**

- Reason: Defender conceded it's "operational convenience"
- Revealed as: Self-inflicted complexity

[Checkpoint: Save progress after each cluster]
</format>
</verdict_round>
</substep>

  <substep n="3c" goal="Phase 1 Summary">
    <action>Facilitator summarizes deconstruction results</action>

    <format>

🧙 **BMad Master:**

**PHASE 1 COMPLETE: Deconstruction Summary**

Total Assumptions Identified: **[N]**

**FUNDAMENTAL TRUTHS** (Validated with Evidence):
[List assumptions that survived with evidence type]

**DISCARDED ASSUMPTIONS** (Convention, Not Constraint):
[List all discarded assumptions with reasons]

**Discard Rate: [X%]** ([N] of [total] assumptions discarded)

**Key Insight:**
[What pattern emerged - e.g., "Most assumptions were operational convenience, not technical constraints"]

**Next:** Phase 2 will validate that our "fundamental truths" are REALLY fundamental via Socratic reduction.

[Checkpoint saved]
</format>
</substep>
</step>

<step n="4" goal="Phase 2 - Validate: Reduce to Bedrock Truths">

  <substep n="4a" goal="Socratic Questioning of Each 'Fundamental'">
    <action>For each "fundamental" from Phase 1, apply deep Socratic questioning</action>
    <action>Goal: Reduce surface assumption to deepest possible truth</action>

    <format>

🧙 **BMad Master:**

We have **[N] "fundamentals"** that survived Phase 1. Let's validate if they're TRULY bedrock.

**Target:** [Assumption X] - "[Statement]"

**Validation Questions:**

1. WHY is this true? (Surface level)
2. WHY does that matter? (Deeper)
3. WHY is that the real constraint? (Deeper still)
4. What's the DEEPEST truth? (Bedrock)

Challengers, question this "fundamental" until we hit bedrock or discover it's actually still convention.
</format>
</substep>

  <substep n="4b" goal="Iterative Reduction" repeat="until-bedrock-or-discarded">
    <action>Challengers ask "WHY?" repeatedly</action>
    <action>Defenders provide progressively deeper answers</action>
    <action>Facilitator identifies when bedrock is reached (can't go deeper)</action>

    <format>

⚔️ **Challenger:** "WHY [assumption]?"
🛡️ **Defender:** "[Surface reason]"

⚔️ **Challenger:** "But WHY [surface reason]?"
🛡️ **Defender:** "[Deeper reason]"

⚔️ **Challenger:** "What REQUIRES [deeper reason]? Prove it's not still convention."
🛡️ **Defender:** "[Bedrock truth - physics/economics/biology] OR [concede - still convention]"

🧙 **Facilitator:**
**VALIDATED AS BEDROCK:** "[Final irreducible truth]"
OR
**RECLASSIFIED AS DISCARDED:** "[Revealed to still be convention]"
</format>
</substep>

  <substep n="4c" goal="Phase 2 Summary">
    <format>
🧙 **BMad Master:**

**PHASE 2 COMPLETE: Validation Summary**

Original "Fundamentals": [N]

**VALIDATED BEDROCK TRUTHS:**
[List final irreducible constraints with evidence type]

**RECLASSIFIED AS DISCARDED:**
[List "fundamentals" that turned out to still be conventions]

**Total Discard Rate: [X%]** (combined Phase 1 + Phase 2)

**Validated Constraints for Reconstruction:**
[Numbered list of ONLY bedrock truths, scoped to specific contexts]

[Checkpoint saved]
</format>
</substep>
</step>

<step n="5" goal="Phase 3 - Reconstruct: Build from Fundamentals Only">

  <substep n="5a" goal="Builder Proposals">
    <action>Builders design solutions using ONLY validated bedrock truths</action>
    <action>Ignore ALL conventions and discarded assumptions</action>
    <action>Multiple builders propose different approaches</action>

    <format>

🧙 **BMad Master:**

**Bedrock Constraints (and ONLY these):**
[List validated fundamentals from Phase 2]

**Challenge to Builders:** Design solution using ONLY these constraints. Ignore ALL conventions.

---

🏗️ **[Builder 1]:**

**Proposal [A]: [Name]**

**Core Design:**
[Architecture/approach built from fundamentals]

**For Constraint 1:** [How this proposal solves it]
**For Constraint 2:** [How this proposal solves it]

**Economics:** [Cost model]
**Evidence:** [Why this matches fundamentals]

---

🏗️ **[Builder 2]:**

**Proposal [B]: [Name]**

[Different approach, same fundamentals]

---

🏗️ **[Builder 3]:**

**Proposal [C]: [Name]**

[Third alternative]
</format>
</substep>

  <substep n="5b" goal="Proposal Evaluation">
    <action>Facilitator creates comparison matrix</action>
    <action>Evaluate each proposal against bedrock constraints</action>
    <action>Consider trade-offs (engineering simplicity, cost, risk)</action>

    <format>

🧙 **BMad Master:**

**Proposal Comparison:**

| Constraint | Proposal A | Proposal B | Proposal C |
| ---------- | ---------- | ---------- | ---------- |
| Bedrock 1  | ✅ [How]   | ✅ [How]   | ⚠️ [Issue] |
| Bedrock 2  | ✅ [How]   | ✅ [How]   | ✅ [How]   |
| Simplicity | ✅✅       | ❌         | ✅         |
| Cost       | $$$        | $          | $$         |

**Facilitator Verdict:**

**Recommended:** Proposal [X] ([Name])

**Reasoning:**
[Why this best solves bedrock constraints with acceptable trade-offs]

**Alternatives Rejected:**

- Proposal [Y]: [Why not chosen]
- Proposal [Z]: [Why not chosen]
  </format>
  </substep>

    <substep n="5c" goal="Implementation Details">
      <action>Winning builder refines proposal with concrete details</action>

      <format>

  🏗️ **[Builder]:**

**Refined Proposal [X]:**

**[Technical details: schema, code examples, architecture diagrams, etc.]**

**Migration Path:**
[Steps to transition from old to new]

**Cost Model:**
[Concrete economics]

**Evidence:** Matches bedrock constraints [list validations]
</format>
</substep>

  <substep n="5d" goal="Phase 3 Summary">
    <format>
🧙 **BMad Master:**

**PHASE 3 COMPLETE: Reconstruction Summary**

**Problem:** [Original problem]

**Old Approach** (based on discarded assumptions):
[Summary of conventional solution]

**New Approach** (built from fundamentals):
[Summary of recommended solution]

**Key Differences:**
| Aspect | Old (Convention) | New (First Principles) |
|--------|------------------|------------------------|
| [Dimension 1] | [Old way] | [New way] |
| [Dimension 2] | [Old way] | [New way] |
| Cost | [Old cost] | [New cost] |

**Radical Difference:** [Quantified improvement - cost reduction, simplicity gain, etc.]

[Final checkpoint saved]
</format>
</substep>
</step>

<step n="6" goal="Session Conclusion">
  <action>Facilitator provides comprehensive summary</action>
  <action>Present next steps and action items</action>

  <format>
🧙 **BMad Master:**

**FIRST PRINCIPLES SESSION COMPLETE**

**What We Accomplished:**

**Phase 1 (Deconstruct):** Challenged [N] assumptions

- **Discarded:** [X] assumptions ([%]%)
- **Validated:** [Y] assumptions

**Phase 2 (Validate):** Questioned the "fundamentals"

- **Bedrock Truths:** [Z] irreducible constraints
- **Reclassified:** [W] turned out to still be conventions

**Phase 3 (Reconstruct):** Built new solution from [Z] fundamentals

- **Old:** [Conventional approach]
- **New:** [First Principles approach]
- **Impact:** [Quantified difference]

**Total Discard Rate:** [X%]

**Next Steps:**

1. [Action item 1]
2. [Action item 2]
3. [Action item 3]

**Key Takeaway:**
"[Insight about how conventions masked the real constraints]"

**Session Participants:** [X] agents across 4 cohorts
**Duration:** [Estimate]
**Assumptions discarded:** [%]%
**Outcome:** [Radically different solution / Validated current approach / etc.]
</format>

<action>Exit workflow or analyze new problem</action>
</step>

</workflow>

## Evidence Hierarchy Reference

<evidence_standards>
<tier_1 quality="highest">
<examples> - Laws of physics (thermodynamics, conservation of energy) - Mathematical proofs - Biological constraints (human anatomy, metabolism) - Economic laws (supply/demand, opportunity cost)
</examples>
<verdict>Strong candidate for FUNDAMENTAL</verdict>
</tier_1>

<tier_2 quality="high">
<examples> - Engineering constraints (latency, bandwidth, compute limits) - Regulatory requirements (GDPR, HIPAA, SOC2) - Security constraints (encryption requirements)
</examples>
<verdict>May be FUNDAMENTAL if measurable/provable</verdict>
</tier_2>

<tier_3 quality="low">
<examples> - Industry conventions ("how SaaS products are built") - Best practices ("RESTful API design") - Common patterns ("microservices for scale")
</examples>
<verdict>Likely DISCARDED unless backed by Tier 1/2 evidence</verdict>
</tier_3>

<tier_4 quality="insufficient">
<examples> - "Everyone does it this way" - "It's always been done like this" - "Industry standard" - "Best practice" (without evidence)
</examples>
<verdict>DISCARDED immediately</verdict>
</tier_4>
</evidence_standards>

## Challenge Intensity Guidelines

<intensity_levels>
<gentle> - Question assumptions respectfully - Accept partial evidence - Use for: New teams, sensitive topics, low-stakes decisions
</gentle>

  <moderate>
    - Challenge with evidence demands
    - Push back on weak defenses
    - Use for: Most architectural decisions
  </moderate>

  <aggressive>
    - Destroy assumptions ruthlessly
    - Accept ONLY physics/economics evidence
    - No mercy for conventions
    - Use for: Critical decisions, high cost of being wrong, suspected cargo-culting
  </aggressive>
</intensity_levels>

## Moderation Notes

<moderation>
  <note>Challengers should be aggressive, not personal - attack ideas, not people</note>
  <note>Defenders should concede gracefully when evidence is weak</note>
  <note>Facilitator breaks ties based on evidence quality, not agent seniority</note>
  <note>If discard rate < 60%, increase challenge intensity</note>
  <note>Sessions typically 2-4 hours - use checkpoints to save progress</note>
  <note>Exit if analysis becomes circular or all assumptions validated (rare)</note>
</moderation>
