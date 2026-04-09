---
name: copy-editor
description: Professional copy editing toolkit for improving written content. Use when users request copy editing, proofreading, grammar checking, style improvements, or document polishing. Provides comprehensive editing workflows, style guides, and common error patterns.
allowed-tools: "Read,Write,Edit,Bash,Glob,Grep,WebSearch,WebFetch"
---

# Copy Editor Skill

Professional copy editing toolkit for comprehensive document improvement.

## Quick Start

When a user requests copy editing, follow this process:

1. **Initial Assessment** - Identify the document type and editing level needed
2. **AI Writing Audit** - Scan for AI-generated writing patterns (see `references/avoid-ai-writing.md`)
3. **Systematic Review** - Apply the appropriate editing checklist
4. **Provide Feedback** - Deliver corrections with explanations

> **Important**: Every standard and heavy copy edit must include an AI writing pattern scan. Load `references/avoid-ai-writing.md` for the full 36-pattern checklist, 109-word replacement table, and severity tiers (P0/P1/P2). If 5+ vocabulary flags span 3+ pattern categories with uniform rhythm, recommend a full rewrite rather than patching.

## Editing Levels

### Light Copy Edit (Proofreading)
Focus on mechanical errors only:
- Spelling mistakes
- Grammar errors
- Punctuation issues
- Obvious typos
- Basic formatting consistency

### Standard Copy Edit
All light edit tasks plus:
- Word choice refinement
- Sentence structure improvements
- Consistency in style and tone
- Clarity enhancements
- Redundancy elimination
- AI writing pattern scan (P0 and P1 flags)

### Heavy Copy Edit (Line Editing)
All standard edit tasks plus:
- Paragraph restructuring
- Flow and transition improvements
- Voice and tone adjustments
- Substantive clarity rewrites
- Content organization
- Full AI writing audit (P0, P1, and P2 flags)

## Core Editing Workflow

### 1. Document Analysis
- Identify document type (academic, business, creative, technical)
- Determine target audience
- Assess current quality level
- Note style requirements (formal/informal, active/passive voice preferences)

### 2. Systematic Review Process

#### First Pass: Structure and Flow
- Check overall organization
- Verify logical progression
- Ensure smooth transitions
- Confirm introduction and conclusion effectiveness

#### Second Pass: Paragraph Level
- Topic sentence clarity
- Supporting detail relevance
- Paragraph length balance
- Internal coherence

#### Third Pass: Sentence Level
- Sentence variety
- Active vs. passive voice
- Clarity and concision
- Parallel structure

#### Fourth Pass: Word Level
- Word choice precision
- Jargon appropriateness
- Redundancy removal
- Consistency in terminology

#### Final Pass: Mechanics
- Spelling
- Grammar
- Punctuation
- Formatting

### 3. Common Issues to Check

#### Grammar and Mechanics
- Subject-verb agreement
- Pronoun-antecedent agreement
- Verb tense consistency
- Comma splices and run-ons
- Sentence fragments
- Misplaced modifiers
- Dangling participles
- Apostrophe usage
- Semicolon and colon usage
- Hyphenation rules

#### Style and Clarity
- Wordiness and redundancy
- Weak verbs (excessive "to be" verbs)
- Nominalizations
- Unclear pronoun references
- Mixed metaphors
- Clichés and overused phrases
- Inconsistent tone
- Unclear antecedents
- Passive voice overuse
- Buried leads

#### AI Writing Patterns
Scan for the 36 patterns documented in `references/avoid-ai-writing.md`. Key checks:
- **Vocabulary**: Tier 1 words (always replace), Tier 2 (flag when 2+ per paragraph), Tier 3 (flag at high density)
- **Content**: Significance inflation, vague attributions, promotional language, formulaic challenges, novelty inflation, superficial -ing analyses, notability name-dropping
- **Language**: Copula avoidance, synonym cycling, template phrases, filler phrases, false ranges, parenthetical hedging
- **Structure**: Formatting overuse (em dashes, bold, emoji headers), transition phrase crutches, title case headings, numbered list inflation, false concession, rhetorical question openers, inline-header lists, sentence/structural uniformity
- **Communication**: Chatbot artifacts, "let's" constructions, cutoff disclaimers, generic conclusions, emotional flatline, reasoning chain artifacts, sycophantic tone, acknowledgment loops, confidence calibration issues
- **Meta**: Excessive structure, rhythm uniformity, over-polishing, rewrite-vs-patch threshold

#### Consistency Checks
- Number formatting (numerals vs. spelled out)
- Date formatting
- Capitalization rules
- Abbreviation usage
- List formatting (bullets, numbering)
- Header hierarchy
- Citation style
- British vs. American spelling

## Feedback Delivery Format

### For Light Edits
Provide corrected text with brief notation of changes:
```
Original: "The report was wrote yesterday"
Edited: "The report was written yesterday" [corrected verb form]
```

### For Standard/Heavy Edits
Use structured feedback:

**Overall Assessment:**
Brief summary of document strengths and main areas for improvement

**Specific Corrections:**
1. [Location] - Issue - Suggestion - Rationale
2. [Location] - Issue - Suggestion - Rationale

**Pattern Issues:**
Recurring problems to watch for in future writing

**Revised Version:**
Complete edited text (when requested)

## Specialized Document Types

### Academic Papers
- Thesis statement clarity
- Citation consistency
- Academic tone maintenance
- Argument structure
- Evidence integration

### Business Documents
- Executive summary effectiveness
- Action-oriented language
- Professional tone
- Bullet point optimization
- Call-to-action clarity

### Creative Writing
- Show vs. tell balance
- Dialogue punctuation
- Character voice consistency
- Narrative flow
- Sensory detail usage

### Technical Documentation
- Technical accuracy
- Step-by-step clarity
- Consistent terminology
- Visual aid references
- Version control notation

## Style Guide Quick Reference

### Numbers
- Spell out one through nine
- Use numerals for 10 and above
- Always use numerals with units (5 miles, 3 GB)
- Spell out numbers that begin sentences

### Punctuation
- Oxford comma: recommended for clarity
- Em dash (—) for strong breaks
- En dash (–) for ranges
- Ellipsis (...) for omissions only
- One space after periods (modern standard)

### Capitalization
- Sentence case for headers (preferred for modern, accessible style)
- Title Case for formal documents (when specifically required)
- Lowercase for general concepts
- Capitalize proper nouns and official titles

## When to Consult References

- **For detailed grammar rules**: See `references/grammar_guide.md`
- **For style variations**: See `references/style_comparisons.md`
- **For common errors database**: See `references/common_errors.md`
- **For AI writing pattern detection**: See `references/avoid-ai-writing.md` — includes all 36 patterns, the 109-word replacement table (3 tiers), severity levels (P0/P1/P2), context profiles by content type, and rewrite-vs-patch threshold. Source: [conorbronsdon/avoid-ai-writing](https://github.com/conorbronsdon/avoid-ai-writing) (MIT)

## Response Templates

### Starting a Copy Edit
"I'll provide a [light/standard/heavy] copy edit of your document. Let me review it systematically for [specific issues based on document type]."

### Delivering Corrections
"I've completed the copy edit. Here are the key improvements:
[Provide structured feedback as outlined above]"

### Explaining Changes
"This change improves [clarity/consistency/correctness] because [specific grammatical or stylistic reason]."
