# First Principles Thinking - Multi-Agent Workflow

## Overview

The First Principles Thinking workflow implements Aristotelian reasoning from fundamental truths. This multi-agent system challenges every assumption, validates bedrock constraints, and rebuilds solutions from scratch.

## What It Does

This workflow deconstructs conventional solutions, questions every assumption, and reconstructs from fundamental truths only. The result is often radically simpler, cheaper, and better than conventional approaches.

### Three-Phase Cycle

1. **💥 Deconstruct**: Challenge every assumption aggressively
2. **💎 Validate**: Identify true fundamentals via Socratic questioning
3. **🏗️ Reconstruct**: Build new solution using ONLY validated fundamentals

## When to Use

- **Critical architectural decisions** with high cost of being wrong
- **Conventional wisdom questioning** ("everyone does it this way")
- **Cost reduction** opportunities (often find 60-90% savings)
- **Innovation** requiring radically different approaches
- **Suspected cargo-culting** (adopting patterns without understanding why)

## When NOT to Use

- Concrete problems with observable symptoms (use Five Whys instead)
- User needs discovery (use Design Thinking instead)
- Quick decisions without time for 2-4 hour sessions
- Evaluating known options where assumptions are validated (use Six Hats instead)

## How It Works

### Agent Cohorts

Agents are assigned to four distinct cohorts:

1. **⚔️ Challengers** (Destroy assumptions):
   - TEA, Security, Quality Assurance, Risk Analysts
   - Demand evidence, question necessity, challenge source
   - Aggressive, no politeness needed

2. **🛡️ Defenders** (Provide evidence):
   - Architects, Product Managers, Engineers, Data Engineers
   - Provide highest-tier evidence or concede gracefully
   - No "best practices" defenses allowed

3. **🏗️ Builders** (Reconstruct solutions):
   - Architects, Product Managers, Engineers, Innovation Strategists
   - Design from fundamentals only
   - Ignore ALL conventions

4. **🧙 Facilitator** (Orchestrate & judge):
   - BMad Master
   - Renders evidence-based verdicts
   - Breaks ties based on evidence quality

### Evidence Hierarchy (Highest to Lowest)

1. ✅ **Physics/Math**: Laws, proofs, thermodynamics
2. ✅ **Economics/Biology**: Supply/demand, biological constraints
3. ⚠️ **Engineering/Regulatory**: Measurable constraints, requirements
4. ⚠️ **Industry Conventions**: "Best practices"
5. ❌ **"Everyone does it this way"**: INSUFFICIENT (discarded immediately)

### Challenge Intensity

- **Gentle**: Question respectfully, accept partial evidence (for new teams)
- **Moderate**: Challenge with evidence demands (most decisions)
- **Aggressive**: Destroy ruthlessly, accept ONLY physics/economics (recommended for critical decisions)

## Session Flow

### Phase 1: Deconstruct

1. Identify all assumptions in current approach
2. Cluster related assumptions (Architecture, Data, Scale, etc.)
3. For each cluster:
   - **Challenge Round**: Challengers attack assumptions
   - **Defense Round**: Defenders provide evidence or concede
   - **Verdict Round**: Facilitator renders verdict (FUNDAMENTAL vs DISCARDED)
4. Summary: Typically 60-90% of assumptions discarded

### Phase 2: Validate

1. For each "fundamental" that survived Phase 1:
   - Apply Socratic questioning: WHY? (repeatedly)
   - Reduce to deepest possible truth
   - Validate it's truly bedrock (not still convention)
2. Summary: Many "fundamentals" reclassified as discarded

### Phase 3: Reconstruct

1. Builders propose solutions using ONLY validated bedrock truths
2. Multiple proposals presented
3. Facilitator evaluates against fundamentals
4. Winning proposal selected with implementation details
5. Comparison: Old (convention) vs New (first principles)

## Usage

```
Load BMad Master
*first-principles

Provide your problem/decision when prompted
```

## Output

Comprehensive analysis document including:

- All assumptions identified and clustered
- Challenge-defend-verdict transcripts for each
- Bedrock truths validated with evidence type
- Builder proposals with comparison matrix
- Old vs new approach comparison
- Quantified impact (cost savings, simplicity gains, etc.)
- Implementation details and next steps

## Example Applications

### Architecture Decision

**Problem**: "Should we use separate databases per tenant or single shared database?"
**Result**: 91.7% discard rate (11 of 12 assumptions), $333K/year savings by switching to single-database with RLS

### Technology Selection

**Problem**: "Which JavaScript framework for new project?"
**Result**: Discarded need for framework entirely, built vanilla JS components (10× smaller bundle)

### Process Optimization

**Problem**: "Why are deployments slow?"
**Result**: Questioned need for 100-database migrations, consolidated to 1 database, 99× faster deployments

## Duration

Typically 2-4 hours with progressive checkpoints:

- Phase 1 (Deconstruct): 1-2 hours
- Phase 2 (Validate): 30-60 min
- Phase 3 (Reconstruct): 1-1.5 hours

Checkpoints saved after each assumption cluster to prevent context loss.

## Success Metrics

- **Assumption Discard Rate**:
  - <40%: Defenders dominated (didn't challenge hard enough)
  - 40-60%: Balanced (good session)
  - 60-90%: Excellent (most conventions discarded) ✅
  - > 90%: Exceptional (nearly total rebuild)

- **Outcome**: Radically different solution (not incremental improvement)
- **Quantified Impact**: Measurable savings (cost, time, complexity)

## File Structure

```
first-principles/
├── workflow.yaml              # Configuration and evidence standards
├── agent-assignments.yaml     # Cohort selection criteria
├── instructions.md            # Workflow execution steps
├── template.md                # Progressive checkpoint template
└── README.md                  # This file
```

## Integration

This workflow integrates with:

- **Six Thinking Hats**: Chain First Principles → Six Hats to evaluate options using validated fundamentals
- **Pre-Mortem**: Chain First Principles → Pre-Mortem to identify risks in new approach
- **Five Whys**: Five Whys may reveal assumption to challenge, triggering First Principles
- **Innovation Strategy**: First Principles output feeds strategic planning

## Tips for Success

1. **Start Low-Stakes**: Practice with non-critical decisions before tackling architecture
2. **Embrace Discomfort**: High discard rates are SUCCESS, not failure
3. **Concede Gracefully**: Defenders should admit when evidence is weak
4. **Challenge Aggressively**: Challengers attack ideas, not people
5. **Evidence Over Seniority**: Facilitator judges based on evidence, not agent rank
6. **Use Checkpoints**: Save after each cluster (sessions are 2-4 hours)

## Comparison to Other Frameworks

| Framework            | Purpose                    | Output                       | Discard Rate | Duration  |
| -------------------- | -------------------------- | ---------------------------- | ------------ | --------- |
| **First Principles** | Question ALL assumptions   | Radically different solution | 60-90%       | 2-4 hours |
| **Six Hats**         | Multi-perspective analysis | Balanced synthesis           | N/A          | 1-2 hours |
| **Five Whys**        | Root cause diagnosis       | Deep problem understanding   | N/A          | 30-60 min |
| **SWOT**             | Strategic assessment       | Market/competitive analysis  | N/A          | 30-60 min |

## The Golden Rule

**If you're saying "this is how it's always been done" or "this is industry standard," you need First Principles.**

**If you're saying "we know this is the right approach, but which option should we choose," you need a different framework (Six Hats).**

## Key Takeaway

> "Most of what we call 'best practices' are just 'common practices' - conventions adopted without evidence. First Principles Thinking forces us to prove every assumption, discarding 90%+ of them, and rebuilding from bedrock truths. The result is often radically simpler, cheaper, and better."

## References

- Aristotle. "Metaphysics" (350 BCE) - Foundation of first principles reasoning
- Elon Musk on First Principles: "Boil things down to fundamental truths and reason up from there"
- BMad First Principles Implementation Guide: [docs/first-principles-workflow-implementation.md](../../../../docs/first-principles-workflow-implementation.md)
