# Promotion Pre-Reviewer

A skill that reviews promotion documents to identify weaknesses before formal review. Acts as a coach — flags problems and asks clarifying questions, never rewrites content.

## Review Categories

1. **Show, Don't Tell**: Unsupported claims about quality, difficulty, or impact
2. **Weasel Words and Hyperbole**: Vague or exaggerated language
3. **Evidence Gaps**: Assertions without concrete examples
4. **Weak Growth Areas / Reasons Not to Promote**: Vague or trivial growth areas
5. **Ambiguity and Technical Difficulty**: Unclear characterization of challenges
6. **Document Stands on Its Own**: Reliance on external links
7. **Feedback from Others**: Provider count, attribution, stance clarity

## Installation

### Claude Code

Clone and run with the plugin directory:

```bash
git clone https://github.com/evanwon/skill-promotion-pre-review.git
claude --plugin-dir ./skill-promotion-pre-review
```

### Codex

Clone the repository and symlink the skill:

```bash
git clone https://github.com/evanwon/skill-promotion-pre-review.git
ln -s "$(pwd)/skill-promotion-pre-review/skills/promotion-pre-review" ~/.agents/skills/promotion-pre-review
```

### Gemini Gem

This skill is also usable as a Google Gemini Gem. Copy the contents of `skills/promotion-pre-review/core-prompt.md` into the system instructions of a new Gem in Google AI Studio.

## Usage

1. Export your promotion document from Google Docs as `.txt`, `.md`, or `.pdf`
2. Invoke the skill: `/promotion-pre-review`
3. Provide the file path when prompted

The skill reads your document, applies all 7 review categories, and produces a checklist-style review with quoted passages, concerns, and clarifying questions.

## Supported Input Formats

- `.txt` — plain text export from Google Docs
- `.md` — Markdown
- `.pdf` — PDF export

If the file can't be read, the skill will ask you to paste the document content directly.
