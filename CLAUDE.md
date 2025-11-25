# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

This repository contains CLAUDE.md templates and supporting files for configuring Claude Code in other projects. It is not an application codebase.

## Repository Contents

- `base-claude.md` - Base template for creating project-specific CLAUDE.md files
- `owasp-asvs-l1.md` - OWASP ASVS Level 1 security checklist for security reviews
- `setup-prompt.md` - Workflow guide and prompt for setting up CLAUDE.md in new projects
- `.claude/commands/security-review.md` - Custom slash command for security code reviews

## Usage

When setting up a new project:

1. Copy `base-claude.md` content to the target project as `CLAUDE.md`
2. Follow the workflow in `setup-prompt.md` to customize for the specific codebase
3. Optionally copy `.claude/commands/security-review.md` for security review capability

## Editing Templates

- Keep templates generic and adaptable to different tech stacks
- Maintain placeholder sections (marked with `[brackets]`) for project-specific values
- Security checklist in `owasp-asvs-l1.md` follows OWASP ASVS L1 categories
