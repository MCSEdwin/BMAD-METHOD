# Six Thinking Hats - Multi-Agent Workflow

## Overview

The Six Thinking Hats workflow implements Edward de Bono's parallel thinking method using multi-agent orchestration. Different agents wear different "hats" (thinking perspectives), enabling comprehensive analysis without conflict.

## What It Does

This workflow enables teams to analyze decisions, problems, or opportunities from six distinct perspectives:

- ⚪ **White Hat** (Facts & Data): Objective information, data points, gaps in knowledge
- 🔴 **Red Hat** (Emotions & Intuition): Gut reactions, feelings, hunches (no justification needed)
- ⚫ **Black Hat** (Risks & Problems): Critical judgment, what could go wrong, risks
- 🟡 **Yellow Hat** (Benefits & Optimism): Positive thinking, opportunities, value creation
- 🟢 **Green Hat** (Creativity & Alternatives): New ideas, creative solutions, lateral thinking
- 🔵 **Blue Hat** (Process & Synthesis): Meta-thinking, facilitation, integration

## When to Use

- **Complex decisions** requiring multiple perspectives
- **Strategic planning** where balanced analysis is critical
- **Risk assessment** combined with opportunity identification
- **Team alignment** when diverse viewpoints need structured exploration
- **Conflict resolution** by separating emotional and logical thinking

## How It Works

### Agent Selection

Agents are automatically assigned to hats based on their roles and expertise:

- **White Hat**: Analysts, Data Engineers, Researchers (objective, data-driven)
- **Red Hat**: UX Designers, Product Managers, Creative roles (emotional intelligence)
- **Black Hat**: TEA, Security, Quality Assurance (critical thinking, risk-aware)
- **Yellow Hat**: Product Managers, Innovation Strategists (optimistic, benefit-focused)
- **Green Hat**: Innovation Strategists, Creative Problem Solvers (creative, lateral thinking)
- **Blue Hat**: BMad Master (facilitator, orchestrator, synthesizer)

### Rotation Modes

1. **Sequential**: All agents wear the same hat, rotate through all 6 colors (comprehensive)
2. **Parallel**: Different agents wear different hats simultaneously (faster)
3. **Focus**: User selects specific hats to explore (targeted)

### Session Flow

1. **Initialization**: Agents assigned to hats, topic presented
2. **Hat Rounds**: Each hat perspective explored systematically
3. **Synthesis**: Blue Hat integrates all perspectives
4. **Recommendation**: Evidence-based decision or action items

## Usage

```
Load BMad Master
*six-hats

Provide your topic/decision/problem when prompted
```

## Output

Structured analysis document including:

- Facts gathered
- Emotional landscape
- Risks identified
- Benefits identified
- Creative alternatives
- Integrated synthesis
- Consensus points and tensions
- Recommendation with action items

## Example Topics

- "Should we migrate to microservices architecture?"
- "Evaluate the proposed product feature roadmap"
- "Decide on database technology for new project"
- "Assess acquisition of competitor company"
- "Review post-incident architecture changes"

## Duration

Typically 1-2 hours depending on complexity and rotation mode selected.

## File Structure

```
six-hats/
├── workflow.yaml              # Configuration and hat definitions
├── hat-assignments.yaml       # Agent-to-hat mapping criteria
├── instructions.md            # Workflow execution steps
├── template.md                # Output document template
└── README.md                  # This file
```

## Integration

This workflow integrates with:

- **Party Mode**: Can switch from freeform discussion to structured Six Hats
- **Research Workflow**: White Hat can trigger research for fact-gathering
- **Innovation Strategy**: Green Hat outputs can feed into strategic planning
- **Problem-Solving**: Black Hat analysis can trigger root cause investigation

## Tips for Success

1. **Stay in Hat**: Agents must strictly maintain their hat's perspective
2. **No Hat Hopping**: Don't mix perspectives (e.g., risks in Yellow Hat round)
3. **Red Hat Brevity**: Emotional responses should be quick, not lengthy explanations
4. **Black Hat Balance**: Critical but not destructive; identify real risks, not nitpicking
5. **Green Hat Freedom**: No criticism during creativity rounds
6. **Blue Hat Control**: Facilitator keeps process on track, prevents repetition

## Comparison to Other Frameworks

| Framework            | Best For                            | Output                       | Duration  |
| -------------------- | ----------------------------------- | ---------------------------- | --------- |
| **Six Hats**         | Balanced multi-perspective analysis | Comprehensive synthesis      | 1-2 hours |
| **First Principles** | Challenging assumptions             | Radically different solution | 2-4 hours |
| **Five Whys**        | Root cause diagnosis                | Deep problem understanding   | 30-60 min |
| **SWOT**             | Strategic assessment                | Market/competitive analysis  | 30-60 min |

## Success Metrics

- All six perspectives explored comprehensively
- Consensus points identified across hats
- Tensions/trade-offs clearly articulated
- Evidence-based recommendation produced
- Participant satisfaction with balanced analysis

## References

- Edward de Bono. "Six Thinking Hats" (1985)
- BMad Multi-Agent Implementation Guide: [docs/multi-agent-workflow-implementation-guide.md](../../../../docs/multi-agent-workflow-implementation-guide.md)
