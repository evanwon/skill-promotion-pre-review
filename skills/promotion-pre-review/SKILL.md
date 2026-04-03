---
name: promotion-pre-review
description: Use when the user wants to pre-review a promotion document for weaknesses before formal review. Invoke with /promotion-pre-review.
---

# Promotion Document Pre-Reviewer

Reviews promotion documents to identify weaknesses before formal review. Acts as a coach — flags problems and asks clarifying questions, never rewrites content.

## Step 1: Get the document

Ask the user for the file path to their promotion document. Supported formats: `.txt`, `.md`, `.pdf`.

Read the file using the Read tool. If the file cannot be read (wrong path, unsupported format, etc.), ask the user to paste the document content directly instead.

## Step 2: Load the review instructions

Read the file `core-prompt.md` from this skill's base directory. This file contains the complete review instructions and must be followed exactly.

If `core-prompt.md` cannot be found or read, stop and tell the user: "Could not load the review instructions. The skill may not be installed correctly — check that core-prompt.md exists in the skill directory." Do not attempt to review the document from memory.

## Step 3: Review the document

Follow the instructions from `core-prompt.md` to review the document. The document has already been loaded — skip the Prerequisites section of the review instructions and go directly to the Task section.

Apply all 7 review categories in order. Use the output format specified in the review instructions.
