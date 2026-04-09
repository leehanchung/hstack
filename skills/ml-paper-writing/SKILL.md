---
name: ml-paper-writing
description: Write publication-ready ML/AI research papers for NeurIPS, ICML, ICLR, ACL, AAAI, COLM. Use when drafting papers from research repos, structuring arguments, verifying citations, formatting for conferences, preparing camera-ready submissions, or improving paper clarity and rigor. Includes citation verification workflows, LaTeX guidance, and the full writing process from compressing research into claims through final submission.
allowed-tools: "Read,Write,Edit,Bash,Glob,Grep,WebSearch,WebFetch"
---

# ML Paper Writing for Top AI Conferences

Expert guidance for writing publication-ready papers targeting **NeurIPS, ICML, ICLR, ACL, AAAI, and COLM**. Combines writing philosophy from top researchers with practical workflows for citation verification, LaTeX formatting, and conference checklists.

## Core Philosophy

**Paper writing is collaborative, but Claude should be proactive in delivering drafts.**

When starting from a research repository:
1. **Understand the project** by exploring code, results, and existing docs
2. **Deliver a complete first draft** when confident about the contribution
3. **Search literature** using web search and APIs to find relevant citations
4. **Refine through feedback cycles** based on scientist input
5. **Ask for clarification** only when genuinely uncertain

**Key Principle**: Be proactive. If the repo and results are clear, deliver a full draft. Don't block waiting for feedback on every section.

---

## CRITICAL: Never Hallucinate Citations

**This is the most important rule in academic writing with AI assistance.**

AI-generated citations have a **~40% error rate**. Never generate BibTeX from memory.

| Action | Correct | Wrong |
|--------|---------|-------|
| Adding citation | Search API → verify → fetch BibTeX | Write BibTeX from memory |
| Uncertain about paper | Mark as `[CITATION NEEDED]` | Guess the reference |
| Can't find exact paper | Note: "placeholder - verify" | Invent similar-sounding paper |

**When you cannot verify a citation:**
```latex
\cite{PLACEHOLDER_author2024_verify}  % TODO: Verify this citation exists
```

Always tell the scientist: "I've marked [X] citations as placeholders that need verification."

**For paper search, use:**
- Exa MCP (if available): `claude mcp add exa -- npx -y mcp-remote "https://mcp.exa.ai/mcp"`
- Web search for paper titles/authors
- Verify with Semantic Scholar API, then fetch BibTeX via DOI

See [references/citation-workflow.md](references/citation-workflow.md) for complete API documentation.

---

## The Narrative Principle

**Your paper is not a collection of experiments—it's a story with one clear contribution.**

Every successful ML paper centers on what Neel Nanda calls "the narrative": a short, rigorous, evidence-based technical story with a takeaway readers care about.

**Three Pillars (must be crystal clear by end of introduction):**

| Pillar | Description | Example |
|--------|-------------|---------|
| **The What** | 1-3 specific novel claims | "We prove that X achieves Y under condition Z" |
| **The Why** | Rigorous empirical evidence | Strong baselines, distinguishing experiments |
| **The So What** | Why readers should care | Connection to recognized community problems |

**If you cannot state your contribution in one sentence, you don't yet have a paper.**

### The Compression Imperative

Readers take away at most a few sentences. Choose those sentences carefully. Compress your research into claims, prioritize ruthlessly, and accept that detail must move to appendices. If you don't deliberately de-prioritize some details, something important gets dropped instead.

---

## Writing Process: Compress Then Iteratively Expand

### Phase 1: Compress

Before writing, ruthlessly compress your work:

1. Verbally describe the research to someone; ask what was most interesting
2. Plan a 15-minute talk
3. Write down the 1-3 concrete claims you believe to be true
4. List the 1-3 key experiments supporting each claim

**Critical evaluation:**
- Do experiments genuinely support claims?
- Could evidence be true but claim false?
- What are the limitations and potential misinterpretations?

### Phase 2: Iteratively Expand

Progress through these stages, getting feedback after each:

1. **Bullet point narrative** → Captures the core story
2. **Bullet point introduction outline** → Claims, motivation, high-level evidence
3. **Full paper outline** → All sections with clear purpose
4. **Draft figures** → Results that support the narrative
5. **First draft prose** → Full technical detail
6. **Polish** → Iterate on clarity, tightness, figure quality

**Time allocation rule:** Spend approximately **equal time** on each of: (1) the abstract, (2) the introduction, (3) the figures, and (4) everything else combined. Most reviewers form judgments before reaching your methods section.

---

## Workflow 1: Starting from a Research Repository

```
Project Understanding:
- [ ] Step 1: Explore the repository structure
- [ ] Step 2: Read README, existing docs, and key results
- [ ] Step 3: Identify the main contribution with the scientist
- [ ] Step 4: Find papers already cited in the codebase
- [ ] Step 5: Search for additional relevant literature
- [ ] Step 6: Draft sections iteratively with feedback
```

**Step 1: Explore the Repository**
```bash
ls -la
find . -name "*.py" | head -20
find . -name "*.md" -o -name "*.txt" | xargs grep -l -i "result\|conclusion"
```

Look for: `README.md`, `results/`, `outputs/`, `experiments/`, existing `.bib` files.

**Step 2: Identify Existing Citations**
```bash
grep -r "arxiv\|doi\|cite" --include="*.md" --include="*.bib" --include="*.py"
```

**Step 3: Clarify the Contribution**

Before writing, confirm with the scientist:
> "Based on my understanding of the repo, the main contribution appears to be [X]. Is this the framing you want, or should we emphasize different aspects?"

**Step 4: Deliver a First Draft**

If the repo provides clear results and the contribution is apparent:
1. Write the full first draft end-to-end
2. Present the complete draft for feedback
3. Iterate based on scientist's response

---

## Workflow 2: Writing a Complete Paper

```
Paper Writing Progress:
- [ ] Step 1: Define the one-sentence contribution
- [ ] Step 2: Draft Figure 1
- [ ] Step 3: Draft abstract (5-sentence formula)
- [ ] Step 4: Draft introduction (1-1.5 pages max)
- [ ] Step 5: Draft methods
- [ ] Step 6: Draft experiments
- [ ] Step 7: Draft related work
- [ ] Step 8: Draft limitations (required)
- [ ] Step 9: Complete paper checklist
- [ ] Step 10: Final review and submission
```

### Abstract: 5-Sentence Formula (Sebastian Farquhar)

```
1. What you achieved: "We introduce...", "We prove..."
2. Why this is hard and important
3. How you do it (with specialist keywords)
4. What evidence you have
5. Your most remarkable number/result
```

**Delete** generic openings like "Large language models have achieved remarkable success..."

See [references/abstract-examples.md](references/abstract-examples.md) for annotated examples.

### Introduction Structure (1-1.5 pages max)

- 2-4 bullet contribution list (max 1-2 lines each)
- Clear problem statement
- Brief approach overview
- Methods should start by page 2-3

See [references/paper-structure.md](references/paper-structure.md) for detailed section-by-section guidance.

### Experiments Section

For each experiment, explicitly state:
- What claim it supports
- How it connects to main contribution
- What to observe: "the blue line shows X, demonstrating Y"

Requirements:
- Error bars with methodology (std dev vs std error)
- Hyperparameter search ranges
- Compute infrastructure (GPU type, total hours)

### Limitations Section (REQUIRED)

All major conferences require this. Counter-intuitively, honesty helps:
- Reviewers are instructed not to penalize honest limitation acknowledgment
- Pre-empt criticisms by identifying weaknesses first

---

## Workflow 3: Citation Verification

```
Citation Verification (MANDATORY for every citation):
- [ ] Step 1: Search using web search or Semantic Scholar API
- [ ] Step 2: Verify paper exists in 2+ sources
- [ ] Step 3: Retrieve BibTeX via DOI (programmatically)
- [ ] Step 4: Verify the claim you're citing actually appears in the paper
- [ ] Step 5: Add verified BibTeX to bibliography
- [ ] Step 6: If ANY step fails → mark as placeholder
```

**Python: Get BibTeX from DOI**
```python
import requests

def doi_to_bibtex(doi: str) -> str:
    response = requests.get(
        f"https://doi.org/{doi}",
        headers={"Accept": "application/x-bibtex"}
    )
    return response.text

bibtex = doi_to_bibtex("10.48550/arXiv.1706.03762")
```

See [references/citation-workflow.md](references/citation-workflow.md) for complete implementation.

---

## Evidence and Rigor

### Quality Over Quantity

One compelling, hard-to-deny experiment beats many mediocre ones. Diverse lines of evidence (different methodologies pointing to same conclusion) are more robust than similar experiments repeated.

### Red-Team Your Narrative

Assume you've made a mistake—where is it? Assume there's a hole in your case—what is it? Spend substantial time trying to break your own claims.

### Baselines Matter

Put meaningful effort into making baselines strong. A "competitor" method often improves dramatically with proper tuning. The question is "Should practitioners use X?" not "Does X work at all?"

### Claim Strength Levels

Match claim strength to evidence strength:

| Claim Type | Example | Evidence Required |
|------------|---------|-------------------|
| Existence proof | "X can happen" | One clear example |
| Systematic | "X generally happens" | Multiple contexts, quantitative |
| Hedged | "Evidence suggests X" | Suggestive but incomplete |
| Narrow | "X works for Y under Z" | Controlled conditions |
| Guarantee | "X always holds" | Formal proof (rare in ML) |

See [references/evidence-rigor.md](references/evidence-rigor.md) for detailed experimental guidance.

---

## Conference Requirements

| Conference | Page Limit | Extra Camera-Ready | Key Requirement |
|------------|------------|-------------------|-----------------|
| **NeurIPS 2025** | 9 pages | +0 | Mandatory checklist |
| **ICML 2026** | 8 pages | +1 | Broader Impact Statement |
| **ICLR 2026** | 9 pages | +1 | LLM disclosure required |
| **ACL 2025** | 8 pages (long) | varies | Limitations section mandatory |
| **AAAI 2026** | 7 pages | +1 | Strict style file adherence |
| **COLM 2025** | 9 pages | +1 | Language model focus |

**Universal Requirements:**
- Double-blind review (anonymize submissions)
- References don't count toward page limit
- LaTeX required for all venues
- PDF with Type-1 fonts embedded

See [references/checklists.md](references/checklists.md) for detailed conference checklists.
See [references/formatting.md](references/formatting.md) for venue-specific formatting requirements.

---

## Writing Style Guidelines

### Sentence-Level Clarity (Gopen & Swan's 7 Principles)

| Principle | Rule | Example |
|-----------|------|---------|
| **Subject-verb proximity** | Keep subject and verb close | "The model achieves..." not "The model, which was trained on..., achieves" |
| **Stress position** | Place emphasis at sentence ends | "When using attention, accuracy improves by **15%**" |
| **Topic position** | Put context first | "Given these constraints, we propose..." |
| **Old before new** | Familiar info → unfamiliar info | Link backward, then introduce new |
| **Action in verb** | Use verbs, not nominalizations | "We analyzed" not "We performed an analysis" |

### Word Choice

| Avoid | Prefer |
|-------|--------|
| utilize | use |
| methodology | method |
| leverage | use |
| novel (overused) | new, first |
| significant (ambiguous) | [specific metric] |
| state-of-the-art | [cite specific prior work] |
| clearly, obviously | [let evidence speak] |

### Micro-Level Tips

- **Be specific**: "accuracy" or "latency" not "performance"
- **Eliminate hedging**: Drop "may" and "can" unless genuinely uncertain
- **Minimize pronouns**: "This result shows..." not "This shows..."
- **Delete filler words**: "actually," "basically," "essentially," "quite"
- **Active voice**: "We show X" not "X is shown"

See [references/writing-guide.md](references/writing-guide.md) for complete writing philosophy.
See [references/style-guide.md](references/style-guide.md) for comprehensive style rules.

---

## LaTeX Templates

When starting a new paper, copy the entire template directory:
```bash
cp -r templates/neurips2025/ ~/papers/my-new-paper/
cd ~/papers/my-new-paper/
```

**Verify template compiles before changes:**
```bash
latexmk -pdf main.tex
```

| Conference | Main File | Style File |
|------------|-----------|------------|
| NeurIPS 2025 | `main.tex` | `neurips.sty` |
| ICML 2026 | `example_paper.tex` | `icml2026.sty` |
| ICLR 2026 | `iclr2026_conference.tex` | `iclr2026_conference.sty` |
| ACL | `acl_latex.tex` | `acl.sty` |
| AAAI 2026 | `aaai2026-unified-template.tex` | `aaai2026.sty` |
| COLM 2025 | `colm2025_conference.tex` | `colm2025_conference.sty` |

---

## Tables and Figures

### Tables (use booktabs)
```latex
\usepackage{booktabs}
\begin{tabular}{lcc}
\toprule
Method & Accuracy ↑ & Latency ↓ \\
\midrule
Baseline & 85.2 & 45ms \\
\textbf{Ours} & \textbf{92.1} & 38ms \\
\bottomrule
\end{tabular}
```

### Figures
- **Vector graphics** (PDF, EPS) for all plots
- **Colorblind-safe palettes**: Okabe-Ito or Paul Tol
- **Self-contained captions**: Reader should understand without main text
- **No title inside figure**: Caption serves this function
- Minimum 0.5pt line thickness
- Ensure readability when printed in grayscale

---

## Common Pitfalls

**The Illusion of Transparency**: You've spent months on this. Readers haven't. Define everything. Situate your work explicitly. Address misconceptions you've encountered.

**Unnecessary Complexity**: Verbosity signals weakness, not sophistication. If readers don't understand, they ignore or assume BS. The best papers apply simple techniques carefully and well.

**Neglecting Writing**: Switch to writing mode at least one month before deadline. Iterate extensively. Get feedback at every stage.

**Novelty Obsession**: Novelty means expanding knowledge, not just being shiny. Rigorous replications, negative results, and careful methodology improvements are genuine contributions.

**Cherry-Picking**: Present representative examples, not just the best ones. For qualitative evidence, show randomly selected examples alongside curated ones. Track which analyses were pre-specified vs. post-hoc.

**Abstract too generic**: Delete first sentence if it could be prepended to any ML paper.

**Introduction too long**: Split background into Related Work. Methods should start by page 2-3.

**Experiments lack claims**: Add "This experiment tests whether [specific claim]..."

**Missing statistics**: Always include error bars, number of runs, statistical tests.

---

## Reviewer Evaluation Criteria

| Criterion | What Reviewers Look For |
|-----------|------------------------|
| **Quality** | Technical soundness, well-supported claims |
| **Clarity** | Clear writing, reproducible by experts |
| **Significance** | Community impact, advances understanding |
| **Originality** | New insights (doesn't require new method) |

See [references/reviewer-guidelines.md](references/reviewer-guidelines.md) for detailed evaluation criteria.

---

## Checklist Before Submission

See [references/submission-checklist.md](references/submission-checklist.md) for the complete checklist.

**Critical items:**
- [ ] Claims are specific, concrete, and supported by evidence
- [ ] Abstract stands alone and conveys the narrative
- [ ] Introduction ends with clear contributions list
- [ ] All figures have informative captions
- [ ] Limitations discussed honestly
- [ ] No author-identifying information
- [ ] PDF uses only Type-1 fonts
- [ ] Page limit respected (check carefully)
- [ ] References complete with page numbers
- [ ] Code/data anonymized if submitted
- [ ] All citations verified (no hallucinated references)

---

## Reference Documents

| Document | Contents |
|----------|----------|
| [abstract-examples.md](references/abstract-examples.md) | Annotated abstract examples |
| [checklists.md](references/checklists.md) | NeurIPS 16-item, ICML, ICLR, ACL requirements |
| [citation-workflow.md](references/citation-workflow.md) | Citation APIs, Python code, BibTeX management |
| [evidence-rigor.md](references/evidence-rigor.md) | Experimental design and red-teaming |
| [formatting.md](references/formatting.md) | Venue-specific formatting requirements |
| [paper-structure.md](references/paper-structure.md) | Detailed section-by-section guidance |
| [reviewer-guidelines.md](references/reviewer-guidelines.md) | Evaluation criteria, scoring, rebuttals |
| [style-guide.md](references/style-guide.md) | Comprehensive writing style rules |
| [submission-checklist.md](references/submission-checklist.md) | Pre-submission checklist |
| [writing-guide.md](references/writing-guide.md) | Gopen & Swan 7 principles, micro-tips, word choice |

---

## Key Sources

- [Neel Nanda: How to Write ML Papers](https://www.alignmentforum.org/posts/eJGptPbbFPZGLpjsp/highly-opinionated-advice-on-how-to-write-ml-papers)
- [Farquhar: How to Write ML Papers](https://sebastianfarquhar.com/on-research/2024/11/04/how_to_write_ml_papers/)
- [Gopen & Swan: Science of Scientific Writing](https://cseweb.ucsd.edu/~swanson/papers/science-of-writing.pdf)
- [Lipton: Heuristics for Scientific Writing](https://www.approximatelycorrect.com/2018/01/29/heuristics-technical-scientific-writing-machine-learning-perspective/)
- [Perez: Easy Paper Writing Tips](https://ethanperez.net/easy-paper-writing-tips/)
