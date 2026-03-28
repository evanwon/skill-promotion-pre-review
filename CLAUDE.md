# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository is a **cross-platform skill plugin** for the **Promotion Document Pre-Reviewer** — a tool that helps authors identify weaknesses in their promotion documents before formal review. It acts as a coach (not a ghostwriter): it flags problems and asks clarifying questions but never rewrites content or fills in missing details.

The skill works on **Claude Code** (plugin) and **Codex** (symlink). The core prompt is also usable as a **Google Gemini Gem** by pasting it into AI Studio.

## Repository Structure

- `skills/promotion-pre-review/core-prompt.md` — The review instructions. This is the **single source of truth** for review logic. Also serves as the Gemini Gem prompt (paste directly into AI Studio).
- `skills/promotion-pre-review/SKILL.md` — Thin skill wrapper that handles file input and delegates to `core-prompt.md`. Do not duplicate review logic here.
- `.claude-plugin/plugin.json` — Claude Code plugin manifest.
- `.codex/INSTALL.md` — Codex installation instructions.

## Key Design Principles

- **Review the document, not the promotion.** Never endorse or reject a promotion itself — only assess whether the writing clearly presents its case.
- **Paragraph-level evaluation.** Claims should be evaluated in context of their surrounding section, not sentence-by-sentence. A summary claim followed by supporting detail in the same section is fine.
- **Coach, not ghostwriter.** Output is checklist-style findings with quoted passages, concerns, and questions — never rewritten content.
- **Ambiguity and difficulty are independent dimensions.** Never conflate them.
- **Thorough with tiered output.** Find all issues per category but present up to 5 in detail; additional findings appear as compact one-liners. Every category ends with an explicit completeness signal.

## Review Categories (in prompt order)

1. Show, Don't Tell
2. Weasel Words and Hyperbole
3. Evidence Gaps
4. Weak Growth Areas / Reasons Not to Promote (highest priority)
5. Peer Feedback Quality
6. Ambiguity and Technical Difficulty Characterization
7. Document Stands on Its Own

## When Editing the Review Instructions

Edit `skills/promotion-pre-review/core-prompt.md` for any changes to review logic. Key constraints:

- The PREREQUISITES section must stay intact for Gemini Gem compatibility (the skill wrapper skips it).
- The "Weak Growth Areas" section is explicitly marked highest priority and has two evaluation layers (concrete examples, then impact). Preserve this weighting.
- The output format section at the end governs structure of all responses — keep it in sync with any category additions or removals.
- Each category must end with a completeness signal. Preserve this pattern when adding or modifying categories.
- The VERSION line at the top is referenced in the output format. Update it when making changes.

## When Editing the Skill Wrapper

Edit `skills/promotion-pre-review/SKILL.md` only for changes to input handling or invocation behavior. The wrapper must:

- Read the document from disk (or accept pasted content as fallback).
- Read `core-prompt.md` at runtime — never duplicate review logic inline.
- Instruct the agent to skip the PREREQUISITES section (input is already loaded).
- Fail visibly if `core-prompt.md` cannot be read (do not review from memory).
