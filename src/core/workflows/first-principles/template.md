# First Principles Analysis

**Date:** {{date}}
**Problem:** {{problem}}
**Facilitator:** {{facilitator}}
**Participants:** {{agent_count}} agents

---

## Session Overview

**Problem Statement:** {{problem_statement}}

**Current Approach:** {{current_approach}}

**Challenge Intensity:** {{challenge_intensity}}

**Total Duration:** {{duration}}

---

## 💥 Phase 1: Deconstruct - Challenge Every Assumption

### Assumptions Identified

**Total:** {{total_assumptions}}

{{#each assumption_clusters}}

### Cluster {{cluster_number}}: {{cluster_name}}

{{#each assumptions}}
**A{{assumption_id}}:** {{assumption_text}}
{{/each}}

#### Challenge Round

{{#each challenger_contributions}}
**⚔️ {{challenger_name}}:**
{{challenge_text}}
{{/each}}

#### Defense Round

{{#each defender_contributions}}
**🛡️ {{defender_name}}:**
{{defense_text}}
**Evidence Provided:** {{evidence_type}}
{{/each}}

#### Facilitator Verdict

**Verdicts:**

{{#each assumption_verdicts}}

- **A{{assumption_id}}**: **{{verdict}}** (FUNDAMENTAL | DISCARDED | NEEDS MORE EVIDENCE)
  - Reason: {{reason}}
  - Revealed as: {{revelation}}
    {{/each}}

_[Checkpoint: Cluster {{cluster_number}} complete]_

---

{{/each}}

### Phase 1 Summary

**Total Assumptions:** {{total_assumptions}}

**FUNDAMENTAL** (Validated with Evidence): {{fundamental_count}}
{{#each fundamentals}}

- {{assumption_id}}: {{assumption_text}} (Evidence: {{evidence_type}})
  {{/each}}

**DISCARDED** (Convention, Not Constraint): {{discarded_count}}
{{#each discarded}}

- {{assumption_id}}: {{assumption_text}} (Reason: {{discard_reason}})
  {{/each}}

**Discard Rate:** {{discard_rate}}%

**Key Insights:**
{{#each phase1_insights}}

- {{this}}
  {{/each}}

---

## 💎 Phase 2: Validate - Identify True Fundamentals

{{#each validation_rounds}}

### Validation Round {{round_number}}: {{assumption_target}}

**Target:** {{assumption_text}}

**Socratic Reduction:**

{{#each reduction_steps}}
**WHY #{{step_number}}:** {{question}}

{{#each responses}}
**{{agent_name}}:** {{response}}
{{/each}}

**Deeper Truth:** {{deeper_truth}}
{{/each}}

**Bedrock Truth Identified:**
{{bedrock_truth}}

**Evidence Type:** {{evidence_type}}
**Evidence Quality:** {{evidence_quality}}

**Verdict:** {{verdict}}

---

{{/each}}

### Phase 2 Summary

**Original "Fundamentals":** {{original_fundamentals_count}}

**VALIDATED BEDROCK TRUTHS:**
{{#each bedrock_truths}}
{{number}}. {{truth_text}}

- Evidence: {{evidence_type}}
- Scope: {{scope}}
  {{/each}}

**RECLASSIFIED AS DISCARDED:**
{{#each reclassified}}

- {{assumption_text}} (Reason: {{reason}})
  {{/each}}

**Total Discard Rate:** {{total_discard_rate}}% (Phase 1 + Phase 2 combined)

**Validated Constraints for Reconstruction:**
{{#each final_constraints}}
{{number}}. {{constraint}}
{{/each}}

---

## 🏗️ Phase 3: Reconstruct - Build from Fundamentals Only

### Builder Proposals

{{#each builder_proposals}}

#### Proposal {{proposal_letter}}: {{proposal_name}}

**Builder:** {{builder_name}}

**Core Design:**
{{core_design}}

**How It Solves Constraints:**
{{#each constraint_solutions}}

- **{{constraint}}:** {{solution}}
  {{/each}}

**Economics:**
{{economics}}

**Trade-offs:**
{{#each tradeoffs}}

- {{this}}
  {{/each}}

**Evidence:**
{{evidence}}

---

{{/each}}

### Proposal Comparison

| Constraint | {{#each proposals}}Proposal {{letter}}{{#unless @last}} | {{/unless}}{{/each}} |
|------------|{{#each proposals}}-----------|{{/each}}
{{#each constraints}}
| {{constraint_name}} | {{#each proposal_scores}}{{score}}{{#unless @last}} | {{/unless}}{{/each}} |
{{/each}}
| **Simplicity** | {{#each simplicity_scores}}{{score}}{{#unless @last}} | {{/unless}}{{/each}} |
| **Cost** | {{#each cost_scores}}{{score}}{{#unless @last}} | {{/unless}}{{/each}} |
| **Risk** | {{#each risk_scores}}{{score}}{{#unless @last}} | {{/unless}}{{/each}} |

### Facilitator Recommendation

**Recommended:** {{recommended_proposal}}

**Reasoning:**
{{recommendation_reasoning}}

**Alternatives Rejected:**
{{#each rejected_proposals}}

- **{{proposal_name}}:** {{rejection_reason}}
  {{/each}}

---

### Implementation Details

{{implementation_details}}

**Migration Path:**
{{#each migration_steps}}
{{number}}. {{step}}
{{/each}}

**Cost Model:**
{{cost_model}}

---

### Phase 3 Summary

**Problem:** {{problem}}

**Old Approach** (based on discarded assumptions):
{{old_approach_summary}}

**New Approach** (built from fundamentals):
{{new_approach_summary}}

**Key Differences:**

| Aspect | Old (Convention) | New (First Principles) |
| ------ | ---------------- | ---------------------- |

{{#each differences}}
| {{aspect}} | {{old_way}} | {{new_way}} |
{{/each}}

**Radical Difference:** {{quantified_improvement}}

---

## 📊 Comparison & Synthesis

### Architecture Comparison

**OLD:**
{{old_architecture}}

**NEW:**
{{new_architecture}}

### Impact Analysis

| Dimension | Old Approach | New Approach | Winner |
| --------- | ------------ | ------------ | ------ |

{{#each impact_dimensions}}
| {{dimension}} | {{old_value}} | {{new_value}} | {{winner}} |
{{/each}}

### Cost Analysis

**Old Approach:**
{{old_cost_breakdown}}

**New Approach:**
{{new_cost_breakdown}}

**Savings:** {{annual_savings}}

---

## 🎯 Session Conclusion

### What We Accomplished

**Phase 1 (Deconstruct):**

- Challenged {{total_assumptions}} assumptions
- Discarded {{discarded_phase1}} ({{discard_rate_phase1}}%)
- Validated {{validated_phase1}}

**Phase 2 (Validate):**

- Questioned {{fundamentals_questioned}} "fundamentals"
- Bedrock truths: {{bedrock_count}}
- Reclassified: {{reclassified_count}}

**Phase 3 (Reconstruct):**

- Built {{proposal_count}} proposals from {{bedrock_count}} fundamentals
- Selected: {{winning_proposal}}
- Impact: {{quantified_impact}}

### Metrics

- **Total Discard Rate:** {{total_discard_rate}}%
- **Session Duration:** {{duration}}
- **Participants:** {{agent_count}} agents
- **Outcome:** {{outcome_type}}

### Next Steps

{{#each action_items}}
{{number}}. **{{action}}** (Owner: {{owner}}, Due: {{due}})
{{description}}
{{/each}}

### Key Takeaway

{{key_takeaway}}

---

## Session Metadata

**Participants by Cohort:**

- ⚔️ **Challengers:** {{challenger_agents}}
- 🛡️ **Defenders:** {{defender_agents}}
- 🏗️ **Builders:** {{builder_agents}}
- 🧙 **Facilitator:** {{facilitator_agent}}

**Checkpoints Saved:** {{checkpoint_count}}

**Quality Rating:** {{quality_rating}}/10

---

_Generated with First Principles multi-agent workflow_
