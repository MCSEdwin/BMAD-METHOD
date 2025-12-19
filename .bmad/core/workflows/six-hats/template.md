# Six Thinking Hats Analysis

**Date:** {{date}}
**Topic:** {{topic}}
**Facilitator:** {{facilitator}}
**Participants:** {{agent_count}} agents

---

## Session Overview

**Analysis Goal:** {{goal}}

**Rotation Mode:** {{rotation_mode}}

**Hats Explored:** {{hats_explored}}

---

## ⚪ White Hat: Facts & Data

{{#each white_hat_insights}}
**{{agent_name}}:**
{{contribution}}

{{/each}}

**Key Facts:**
{{#each key_facts}}

- {{this}}
  {{/each}}

**Information Gaps:**
{{#each info_gaps}}

- {{this}}
  {{/each}}

---

## 🔴 Red Hat: Emotions & Intuition

{{#each red_hat_insights}}
**{{agent_name}}:**
{{contribution}}

{{/each}}

**Emotional Landscape:**
{{#each emotional_themes}}

- {{this}}
  {{/each}}

**Gut Reactions:**
{{#each gut_reactions}}

- {{this}}
  {{/each}}

---

## ⚫ Black Hat: Risks & Problems

{{#each black_hat_insights}}
**{{agent_name}}:**
{{contribution}}

{{/each}}

**Critical Risks:**
{{#each critical_risks}}

- **{{risk}}**: {{description}}
  {{/each}}

**Potential Failures:**
{{#each potential_failures}}

- {{this}}
  {{/each}}

---

## 🟡 Yellow Hat: Benefits & Optimism

{{#each yellow_hat_insights}}
**{{agent_name}}:**
{{contribution}}

{{/each}}

**Key Benefits:**
{{#each key_benefits}}

- **{{benefit}}**: {{description}}
  {{/each}}

**Opportunities:**
{{#each opportunities}}

- {{this}}
  {{/each}}

---

## 🟢 Green Hat: Creativity & Alternatives

{{#each green_hat_insights}}
**{{agent_name}}:**
{{contribution}}

{{/each}}

**Creative Alternatives:**
{{#each alternatives}}

- **{{alternative}}**: {{description}}
  {{/each}}

**Novel Ideas:**
{{#each novel_ideas}}

- {{this}}
  {{/each}}

---

## 🔵 Blue Hat: Synthesis & Integration

### Integrated Analysis

{{synthesis}}

### Consensus Points

{{#each consensus_points}}

- {{this}}
  {{/each}}

### Tensions & Trade-offs

{{#each tensions}}

- **{{tension}}**: {{description}}
  {{/each}}

### Recommendation

{{recommendation}}

---

## Decision Matrix

| Perspective     | Key Insight            | Weight            |
| --------------- | ---------------------- | ----------------- |
| ⚪ Facts        | {{white_key_insight}}  | {{white_weight}}  |
| 🔴 Emotions     | {{red_key_insight}}    | {{red_weight}}    |
| ⚫ Risks        | {{black_key_insight}}  | {{black_weight}}  |
| 🟡 Benefits     | {{yellow_key_insight}} | {{yellow_weight}} |
| 🟢 Alternatives | {{green_key_insight}}  | {{green_weight}}  |

---

## Next Steps

{{#each action_items}}
{{number}}. **{{action}}** (Owner: {{owner}}, Due: {{due_date}})
{{description}}
{{/each}}

---

## Session Metadata

**Participants by Hat:**

- ⚪ White Hat: {{white_hat_agents}}
- 🔴 Red Hat: {{red_hat_agents}}
- ⚫ Black Hat: {{black_hat_agents}}
- 🟡 Yellow Hat: {{yellow_hat_agents}}
- 🟢 Green Hat: {{green_hat_agents}}
- 🔵 Blue Hat: {{blue_hat_agent}}

**Total Duration:** {{duration}}

**Session Quality:** {{quality_rating}}/10

---

_Generated with Six Thinking Hats multi-agent workflow_
