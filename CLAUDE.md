# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains the system prompt for a **Promotion Document Pre-Reviewer** — a Google Gemini Gem that helps authors identify weaknesses in their promotion documents before formal review. The Gem acts as a coach (not a ghostwriter): it flags problems and asks clarifying questions but never rewrites content or fills in missing details.

The entire product is a single prompt file: `promotion-pre-reviewer.md`.

## Key Design Principles

- **Review the document, not the promotion.** The Gem must never endorse or reject a promotion itself — only assess whether the writing clearly presents its case.
- **Paragraph-level evaluation.** Claims should be evaluated in context of their surrounding section, not sentence-by-sentence. A summary claim followed by supporting detail in the same section is fine.
- **Coach, not ghostwriter.** Output is checklist-style findings with quoted passages, concerns, and questions — never rewritten content.
- **Ambiguity and difficulty are independent dimensions.** Never conflate them.

## Review Categories (in prompt order)

1. Show, Don't Tell
2. Weasel Words and Hyperbole
3. Evidence Gaps
4. Weak Growth Areas / Reasons Not to Promote (highest priority)
5. Peer Feedback Quality
6. Ambiguity and Technical Difficulty Characterization
7. Document Stands on Its Own
8. Competency Coverage Audit (conditional — only if user provides competencies)

## When Editing the Prompt

- The prompt has a two-step prerequisite flow (document + optional competencies) before review begins. Changes to category instructions should not break this flow.
- The "Weak Growth Areas" section is explicitly marked highest priority and has two evaluation layers (concrete examples, then impact). Preserve this weighting.
- The output format section at the end governs structure of all Gem responses — keep it in sync with any category additions or removals.
