---
name: strategic-tech-writing
description: Write strategic technology analysis for senior technical audiences. Use when writing blog posts, articles, or thought leadership pieces for publications like O'Reilly Radar, company engineering blogs, or industry outlets. Blends forward-looking industry analysis with technical depth, using historical parallels and scenario-based framing. Produces 2,000-4,000 word pieces targeting senior technical leaders and decision-makers.
allowed-tools: "Read,Write,Edit,Bash,Glob,Grep,WebSearch,WebFetch"
---

# O'Reilly Radar Writer

Write strategic technology analysis that blends O'Reilly Radar's forward-looking editorial voice with deep technical insight.

## Core Philosophy

O'Reilly Radar pieces are **strategic analysis, not tutorials**. The goal is to help readers understand *why* something matters for the industry, not *how* to implement it. Think "alpha geek insights for decision makers."

Key principle: **"The future is here, it's just not evenly distributed yet."** Surface patterns that practitioners see but haven't yet been articulated for a broader audience.

## Voice and Tone

### The Radar Voice
- **Authoritative but humble**: Make strong claims, but acknowledge uncertainty
- **Pattern-seeking**: Connect current developments to historical parallels
- **Forward-looking**: Focus on implications and trajectories, not just current state
- **Collaborative**: Use "we" to include the reader in exploration
- **Accessible expertise**: Technical depth without jargon gatekeeping

### Blending with Technical Depth
Maintain technical precision while elevating to strategic framing:

❌ "Skills use isMeta: true to hide prompts from the UI"
✅ "Skills solve a fundamental transparency problem: users need to know what's happening, but Claude needs detailed instructions they shouldn't see. The solution—dual-channel messaging—reveals something important about how we'll design AI interfaces going forward."

## Article Structure

### 1. Opening Hook (100-200 words)
State a provocative thesis that challenges conventional thinking or surfaces a non-obvious insight.

**Pattern**: "[Conventional wisdom] suggests X. But [surprising observation] points to Y."

**Examples from Radar:**
- "The market is betting that AI is an unprecedented technology breakthrough... The slow progress of enterprise AI adoption, however, still suggests at least the possibility of a less earthshaking future."
- "The debate about open source AI has largely featured open weight models. But that's a bit like arguing that in the PC era, the most important goal would have been to have Intel open source its chip designs."

### 2. Context and Stakes (200-400 words)
Explain why this matters now. Connect to broader industry dynamics, economic forces, or historical patterns.

**Techniques:**
- Historical parallel: "This reminds me of [Unix/web/mobile]..."
- Economic framing: "The question is not [obvious thing] but [deeper thing]"
- Scenario setup: "Two fundamentally different futures are competing..."

### 3. Core Analysis (1,000-2,000 words)
Develop the argument with evidence, examples, and technical grounding.

**Structure options:**
- **Comparison**: Contrast two approaches (GPTs vs Skills, AGI vs Normal Technology)
- **Scenario**: Explore multiple possible futures with evidence for each
- **Architecture**: Explain a system or pattern and its implications
- **Evolution**: Trace a trajectory from past → present → future

**Include:**
- Concrete examples from real systems
- Technical details that support strategic claims
- Quotes or references to practitioners and experts
- "What to watch for" signals that indicate which future is emerging

### 4. Implications and Actions (400-600 words)
What should readers do with this insight?

**Patterns:**
- "Robust strategies" that work regardless of which scenario unfolds
- "What to watch for" specific signals
- Call to action: "Don't wait for [X] to happen to you"

### 5. Conclusion (100-200 words)
Restate the core insight. End with a forward-looking statement or call to action.

**Pattern**: Return to opening thesis with new depth. Often ends with a quote or aphorism.

## Formatting Guidelines

### Headers
- Use `##` for major sections (3-5 per article)
- Use `###` for subsections sparingly
- Headers should be descriptive, not clever

### Emphasis
- **Bold** for key concepts being introduced
- *Italics* for emphasis within sentences and important phrases
- Use both sparingly—if everything is emphasized, nothing is

### Lists
- Prefer prose over bullet points
- Use bullets only for genuinely parallel items (3-7 items)
- Never use bullets for the main argument flow

### Code and Technical Details
- Include only when essential to the argument
- Frame technical details strategically: "The implementation reveals..."
- Keep code blocks short (<20 lines)

### Footnotes
- Use for supplementary points that would interrupt flow
- Good for: attributions, caveats, additional context
- Not for: core arguments

## Diction and Language

### Prefer
- "suggests" over "proves"
- "points to" over "demonstrates"
- "we see" over "it is clear"
- "the question is" over "the answer is"
- Active voice
- Concrete nouns

### Avoid
- Jargon without explanation
- Hedge words that add no meaning ("somewhat," "fairly")
- Marketing language ("revolutionary," "game-changing")
- Academic passive voice
- Bullet-point thinking in prose

### Signature Phrases (use sparingly)
- "The future is here, it's just not evenly distributed yet"
- "What to watch for:"
- "The real question is not [X] but [Y]"
- "This is the same quality that made [historical example] work"
- "Robust strategies"
- "News from the future"

## Length and Pacing

- **Target**: 2,000-4,000 words (15-25 minute read)
- **Pacing**: Front-load the insight, develop in middle, action at end
- **Paragraph length**: Mix short (1-2 sentences) with medium (3-5 sentences)
- **Section length**: 300-600 words per major section

## Pre-Writing Checklist

Before drafting, answer:

1. **Thesis**: What's the one provocative claim this piece makes?
2. **Stakes**: Why does this matter now? What decision does it inform?
3. **Evidence**: What concrete examples support the thesis?
4. **Historical parallel**: What past technology transition does this echo?
5. **Counterargument**: What's the strongest objection? How do you address it?
6. **Action**: What should readers do differently after reading?

## Post-Writing Checklist

After drafting, verify:

- [ ] Opening paragraph contains a clear, provocative thesis
- [ ] Historical parallel or pattern recognition appears early
- [ ] Technical details serve strategic arguments (not vice versa)
- [ ] "What to watch for" signals are specific and observable
- [ ] Formatting uses bold/italics purposefully, not habitually
- [ ] Bullet lists appear <3 times total
- [ ] Conclusion returns to opening thesis with added depth
- [ ] Word count is 2,000-4,000

## Example Transformations

### Topic: Claude Skills Architecture

**Tutorial approach** (wrong for Radar):
"Claude Skills are defined in SKILL.md files with YAML frontmatter. Here's how to create one..."

**Radar approach** (correct):
"We've figured out how to share code, data, and models. Skills represent something new: sharing *expertise* as a composable, versioned artifact. The implications for how organizations scale knowledge are profound."

### Topic: MCP Adoption

**News summary** (wrong for Radar):
"MCP has been adopted by OpenAI, Google, and Microsoft. Here's what each company announced..."

**Radar approach** (correct):
"MCP's cross-platform adoption proves something important: when a protocol solves real problems and remains truly open, companies embrace it even when it comes from a competitor. The challenge now is to maintain that openness as the protocol matures."

## Writing Process

1. **Outline first**: Map the argument structure before writing prose
2. **Draft the opening last**: The thesis often clarifies during writing
3. **Read aloud**: Radar pieces should sound like informed conversation
4. **Cut 20%**: First drafts are always too long
5. **Check emphasis**: If >5% of text is bold/italic, reduce

## Reference Materials

For deeper guidance on specific aspects:
- See `references/radar-examples.md` for annotated article examples
- See `references/historical-parallels.md` for technology history patterns
- See `references/scenario-planning.md` for scenario-based framing techniques
