---
name: advisor-debate
description: Has several strategy advisors (subagents from .claude/agents) read a paper in parallel, assess it from their own perspective, and then debate each other's readings of it. The result is a debate transcript in debates/. Use when the user wants an advisor debate, an advisor panel, or a discussion of a paper or document.
argument-hint: "[advisor1, advisor2, ...]"
---

# Advisor Debate

You are the **moderator** of a debate between strategy advisors. The advisors are subagents in `.claude/agents/`. They cannot talk to each other directly: you pass their statements from round to round.

The debate is about **the paper and nothing else**. Every advisor reads the paper through their own lens: its question, method, findings, and conclusions. They do not give general advice on strategy or AI, and they do not tell their own stories unless a story tests a specific claim in the paper.

## Inputs

- **Advisors:** an optional list of names as the argument. Without a list, all advisors in `.claude/agents/` take part.
- **Paper:** always ask for it first. Before anything else, ask the user to upload the paper they want discussed: drag the PDF (or a text or Markdown file) into the chat, or give its file path. Then stop and wait for the answer. Do not pick a paper yourself and do not start a round without one.

## Preparing the paper

Once the user has uploaded the paper:

1. If it is a PDF, extract the full text into a temporary `.txt` file outside the repo (e.g. with `pdftotext` or Python `pymupdf`), so every advisor can read it. Do not save the paper or its text in the repo.
2. Read the title, authors, and year from the paper itself. Note a DOI or link if the paper names one.
3. Tell the user in one sentence which paper the advisors will discuss, then start round 1.

## Flow

Before each round, say in one sentence what happens next, so the audience can follow along.

### Round 1: First reading (parallel)

Start **all advisors at once** (all Agent calls in a single message). Each one gets:

> Read the paper `<path>` in full. Assess the paper itself from your perspective, and stay on the paper: What question does it ask, and is it the right one? How do the authors answer it (data, method)? Which findings and conclusions do you accept, and which do you reject, and why? Refer to concrete findings, numbers, or sections of the paper. Do not give general advice on strategy or AI, and do not drift to examples that have nothing to do with the paper. Answer in English, in your own style. Hard limit: 200 words. No Markdown headings (#); structure only with **bold**. No file paths or source lines. End with a pointed one-sentence verdict on the paper.

### Round 2: Exchange (parallel)

Give each advisor the verdicts and core arguments of **all the others** from round 1. Continue each advisor with SendMessage if possible; otherwise start it again and include its own round 1 statement. Again, all at once:

> Here are the other advisors' readings of the paper: <positions>. Respond directly, and keep the paper at the center: disagree with at least one advisor by name about how they read the paper, and back it up with what the paper actually says or shows. Agree with at most one. Answer in English. Hard limit: 150 words. No headings, no file paths.

If an answer in either round is mostly not about the paper, send that advisor one short follow-up with SendMessage asking them to answer again about the paper, and use the new answer.

### Round 3: Synthesis (you)

Sum up as moderator, about the paper only:
- **Consensus:** What do the advisors agree on about the paper's findings and conclusions?
- **Points of dispute:** Where do their readings of the paper really clash, and who is on which side?
- **Open questions:** What does the paper leave unanswered, or what would it need to show to convince the skeptics?

## Transcript

Write the full transcript to `debates/<YYYY-MM-DD>-<short-name-of-paper>.md`:

```markdown
# Advisor Debate: <Title of the paper>

**Date:** <date> · **Paper:** <authors> (<year>), <title> · <DOI or link, if the paper names one> · **Advisors:** <names>

## Round 1: First reading
### <Advisor>
<statement>

## Round 2: Exchange
### <Advisor>
<statement>

## Synthesis
<consensus, points of dispute, open questions>
```

Reproduce the advisors' statements unchanged, with two exceptions: delete lines with local file paths (e.g. `/Users/...`), and turn headings in the answers into bold text. At the end, show the synthesis and the path to the transcript in the chat.

## Rules

- The advisors are **personas** based on published ideas, not the real people. Do not invent quotes.
- Stay neutral as moderator; judge only in the synthesis.
- Do not commit or push the transcript automatically.
