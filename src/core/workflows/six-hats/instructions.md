# Six Thinking Hats - Multi-Agent Instructions

<critical>The workflow execution engine is governed by: {project_root}/{bmad_folder}/core/tasks/workflow.xml</critical>
<critical>This workflow orchestrates multi-perspective analysis using Edward de Bono's Six Thinking Hats method</critical>

<!-- TTS_INJECTION:six-hats -->

<workflow>

<step n="1" goal="Load Agent Manifest and Assign Hats">
  <action>Load the agent manifest CSV from {{agent_manifest}}</action>
  <action>Load hat assignment criteria from {{hat_assignments}}</action>
  <action>Parse agent data with their roles, expertise, and personalities</action>

  <substep n="1a" goal="Assign Agents to Six Hats">
    <logic>
      For each hat (white, red, black, yellow, green, blue):
      1. Score each agent based on criteria:
         - Primary role match: 40 points
         - Hat-specific attribute: 30 points (analytical/emotional/critical/optimistic/creative/facilitation)
         - Secondary attributes: 20 points
         - Domain expertise: 10 points

      2. Select top-scoring agents for each hat:
         - White (Facts): 2-4 agents (analysts, data engineers, researchers)
         - Red (Emotions): 2-4 agents (UX designers, product managers, creative roles)
         - Black (Risks): 2-4 agents (TEA, security, quality assurance)
         - Yellow (Benefits): 2-4 agents (product managers, innovation strategists)
         - Green (Creativity): 2-4 agents (creative problem solvers, innovation strategists)
         - Blue (Facilitator): 1 agent (BMad Master or Scrum Master)

      3. Ensure agents can wear multiple hats (same agent can be in white AND black)
      4. Verify minimum selection counts met for each hat
    </logic>

  </substep>

  <substep n="1b" goal="Present Hat Assignments">
    <format>
🎩 SIX THINKING HATS ACTIVATED

Participants by Hat:

⚪ **White Hat (Facts & Data):**

- [Agent 1]: [Role]
- [Agent 2]: [Role]
- [Agent 3]: [Role]

🔴 **Red Hat (Emotions & Intuition):**

- [Agent 1]: [Role]
- [Agent 2]: [Role]

⚫ **Black Hat (Risks & Problems):**

- [Agent 1]: [Role]
- [Agent 2]: [Role]
- [Agent 3]: [Role]

🟡 **Yellow Hat (Benefits & Optimism):**

- [Agent 1]: [Role]
- [Agent 2]: [Role]

🟢 **Green Hat (Creativity & Alternatives):**

- [Agent 1]: [Role]
- [Agent 2]: [Role]
- [Agent 3]: [Role]

🔵 **Blue Hat (Process & Synthesis):**

- [BMad Master]

Total: [X] agents across 6 hats

What topic would you like to analyze?
</format>
<action>Wait for user to provide topic/question/decision</action>
</substep>
</step>

<step n="2" goal="Initialize Six Hats Session">
  <action>Receive user's topic/question/decision to analyze</action>
  <action>Blue Hat (facilitator) clarifies the topic if needed</action>
  <action>Blue Hat establishes session goals and rotation mode</action>

<rotation_modes>
<sequential>All agents wear same hat, rotate through all 6 colors sequentially</sequential>
<parallel>Different agents wear different hats, all contribute in same round</parallel>
<focus>User selects specific hats to explore (e.g., just white + black + yellow)</focus>
</rotation_modes>

<action>Default: Use sequential rotation for comprehensive analysis</action>
<action>User can request parallel mode for faster analysis</action>

  <format>
🔵 **BMad Master (Blue Hat):**

Topic: "[User's topic]"

Session goal: Multi-perspective analysis to [clarified objective]

Rotation mode: Sequential (all 6 hats)

We'll proceed through each hat systematically. Let's begin!
</format>
</step>

<step n="3" goal="Execute Hat Rotation" repeat="until-all-hats-complete">

  <substep n="3a" goal="White Hat Round - Facts & Data">
    <action>Blue Hat announces: "Everyone, put on your White Hat. Facts and data only, no opinions."</action>
    <action>All White Hat agents contribute objective information:</action>
    <guidelines>
      - State facts, figures, data
      - No interpretation, just information
      - Identify gaps in knowledge
      - Ask for missing data
    </guidelines>

    <format>

⚪ **WHITE HAT: Facts & Data**

[Agent 1 (Analyst)]: [Factual statement, data points, known information]

[Agent 2 (Data Engineer)]: [Additional facts, metrics, statistics]

[Agent 3 (Researcher)]: [Research findings, documented evidence]

🔵 **Blue Hat Summary:** [Synthesize key facts identified, gaps in knowledge]
</format>

    <action>Blue Hat synthesizes facts before moving to next hat</action>

  </substep>

  <substep n="3b" goal="Red Hat Round - Emotions & Intuition">
    <action>Blue Hat announces: "Switch to Red Hat. Share your gut feelings, no justification needed."</action>
    <action>All Red Hat agents share emotional reactions and intuitions:</action>
    <guidelines>
      - Express feelings honestly
      - No need to justify emotions
      - Share hunches and intuitions
      - Brief, authentic reactions
    </guidelines>

    <format>

🔴 **RED HAT: Emotions & Intuition**

[Agent 1 (UX Designer)]: [Emotional reaction, gut feeling]

[Agent 2 (Product Manager)]: [Intuitive response, concern or excitement]

[Agent 3 (Creative)]: [Instinctive reaction]

🔵 **Blue Hat Summary:** [Synthesize emotional landscape, gut reactions noted]
</format>
</substep>

  <substep n="3c" goal="Black Hat Round - Risks & Problems">
    <action>Blue Hat announces: "Black Hat time. What could go wrong? Play devil's advocate."</action>
    <action>All Black Hat agents identify risks, problems, and weaknesses:</action>
    <guidelines>
      - Point out flaws and risks
      - Challenge assumptions
      - Identify what could fail
      - Critical but constructive
    </guidelines>

    <format>

⚫ **BLACK HAT: Risks & Problems**

[Agent 1 (TEA)]: [Risk identification, quality concerns, potential failures]

[Agent 2 (Security)]: [Security risks, vulnerabilities, threat scenarios]

[Agent 3 (Architect)]: [Technical risks, architectural concerns, debt]

🔵 **Blue Hat Summary:** [Synthesize risks identified, critical concerns highlighted]
</format>
</substep>

  <substep n="3d" goal="Yellow Hat Round - Benefits & Optimism">
    <action>Blue Hat announces: "Yellow Hat. What's the upside? Think optimistically."</action>
    <action>All Yellow Hat agents identify benefits, opportunities, and positive outcomes:</action>
    <guidelines>
      - Explore benefits and value
      - Think best-case scenarios
      - Identify opportunities
      - Positive but realistic
    </guidelines>

    <format>

🟡 **YELLOW HAT: Benefits & Optimism**

[Agent 1 (PM)]: [Benefits, value proposition, positive outcomes]

[Agent 2 (Innovation Strategist)]: [Opportunities, strategic advantages, growth potential]

[Agent 3 (Product)]: [User benefits, market opportunities]

🔵 **Blue Hat Summary:** [Synthesize benefits identified, opportunities highlighted]
</format>
</substep>

  <substep n="3e" goal="Green Hat Round - Creativity & Alternatives">
    <action>Blue Hat announces: "Green Hat. Generate alternatives, think creatively."</action>
    <action>All Green Hat agents propose creative solutions and alternatives:</action>
    <guidelines>
      - Generate new ideas
      - Think laterally
      - Propose alternatives
      - No criticism of ideas
    </guidelines>

    <format>

🟢 **GREEN HAT: Creativity & Alternatives**

[Agent 1 (Innovation Strategist)]: [Creative alternatives, novel approaches]

[Agent 2 (Creative Problem Solver)]: [Lateral thinking solutions, unconventional ideas]

[Agent 3 (Designer)]: [Design alternatives, user-centric innovations]

🔵 **Blue Hat Summary:** [Synthesize creative alternatives, options identified]
</format>
</substep>

  <substep n="3f" goal="Blue Hat Round - Synthesis & Meta-Thinking">
    <action>Blue Hat synthesizes all perspectives</action>
    <action>Identify patterns across hats</action>
    <action>Highlight consensus and disagreements</action>
    <action>Present integrated analysis</action>

    <format>

🔵 **BLUE HAT: Synthesis & Process Control**

**Facts Gathered (White):**

- [Key fact 1]
- [Key fact 2]
- [Data gap identified]

**Emotional Landscape (Red):**

- [Dominant feeling]
- [Intuitive concerns]

**Risks Identified (Black):**

- [Critical risk 1]
- [Critical risk 2]
- [Main concern]

**Benefits Identified (Yellow):**

- [Key benefit 1]
- [Key benefit 2]
- [Main opportunity]

**Creative Alternatives (Green):**

- [Alternative 1]
- [Alternative 2]
- [Novel approach]

**Synthesis:**
[Integrated analysis showing how all perspectives inform the decision]

**Consensus Points:**
[Areas where multiple hats agree]

**Tensions:**
[Where hats conflict - e.g., Yellow optimism vs Black risks]

**Recommendation:**
[Evidence-based recommendation considering all six perspectives]
</format>
</substep>

  <substep n="3g" goal="Check for Additional Rounds">
    <check if="analysis incomplete or new questions emerged">
      <action>Blue Hat: "We have new questions. Shall we do another round focusing on [specific hats]?"</action>
      <action>If yes, repeat with focused hat selection</action>
    </check>

    <check if="user satisfied with analysis">
      <goto step="4">Conclude session</goto>
    </check>

  </substep>
</step>

<step n="4" goal="Conclude Six Hats Session">
  <action>Blue Hat provides final synthesis</action>
  <action>Present decision recommendation or action items</action>
  <action>Document full analysis to template</action>

  <format>
🔵 **BMad Master (Blue Hat):**

**SIX HATS ANALYSIS COMPLETE**

**Topic:** [Original topic]

**Multi-Perspective Analysis:**

⚪ **Facts:** [Summary of objective information]
🔴 **Emotions:** [Summary of gut reactions and intuitions]
⚫ **Risks:** [Summary of critical concerns]
🟡 **Benefits:** [Summary of opportunities and value]
🟢 **Alternatives:** [Summary of creative options]

**Integrated Recommendation:**
[Final synthesis balancing all perspectives]

**Next Steps:**

1. [Action item 1]
2. [Action item 2]
3. [Action item 3]

**Participants:** [X] agents across 6 hats
**Session duration:** [Estimate]

Would you like to:

- Explore any hat in more depth?
- Analyze a different topic?
- End session?
  </format>

  <action>Exit workflow or continue with new topic</action>
  </step>

</workflow>

## Hat-Specific Guidelines

<white-hat>
  <principle>Objective, neutral, factual</principle>
  <ask>What information do we have? What information is missing?</ask>
  <avoid>Opinions, interpretations, speculation</avoid>
  <output>Facts, figures, data, known information, gaps in knowledge</output>
</white-hat>

<red-hat>
  <principle>Emotional, intuitive, instinctive</principle>
  <ask>How do I feel about this? What's my gut reaction?</ask>
  <avoid>Justifying feelings, rationalizing emotions</avoid>
  <output>Honest emotions, hunches, intuitions, visceral reactions</output>
</red-hat>

<black-hat>
  <principle>Critical, cautious, risk-aware</principle>
  <ask>What could go wrong? What are the weaknesses?</ask>
  <avoid>Being destructively negative, personal attacks</avoid>
  <output>Risks, problems, flaws, potential failures, critical analysis</output>
</black-hat>

<yellow-hat>
  <principle>Optimistic, constructive, benefit-focused</principle>
  <ask>What's the upside? What value does this create?</ask>
  <avoid>Unrealistic optimism, ignoring real concerns</avoid>
  <output>Benefits, opportunities, positive outcomes, value proposition</output>
</yellow-hat>

<green-hat>
  <principle>Creative, generative, exploratory</principle>
  <ask>What alternatives exist? How else could we approach this?</ask>
  <avoid>Criticizing ideas during generation</avoid>
  <output>New ideas, creative alternatives, lateral solutions, innovations</output>
</green-hat>

<blue-hat>
  <principle>Meta-cognitive, process-oriented, synthesizing</principle>
  <ask>What thinking is needed? How do we integrate perspectives?</ask>
  <avoid>Getting lost in one perspective</avoid>
  <output>Process control, synthesis, integrated analysis, recommendations</output>
</blue-hat>

## Moderation Notes

<moderation>
  <note>Ensure agents stay strictly within their hat's perspective</note>
  <note>Blue Hat redirects if agents stray from current hat</note>
  <note>Keep each hat round concise (2-3 contributions per hat max)</note>
  <note>Synthesis is Blue Hat's responsibility, not other agents</note>
  <note>Exit when analysis is complete, avoid repetition</note>
</moderation>
