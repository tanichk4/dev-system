# HYGIENE.md
# Repo Hygiene Standards — tanichk4
# Machine-readable: Claude and other tools should parse this file to audit or set up repos.

## NAMING_CONVENTIONS

format: kebab-case
examples_valid:
  - petal-budget-tracker
  - movie-tracker
  - english-exam-trainer
  - dev-system
examples_invalid:
  - PetalBudgetTracker
  - petal_budget_tracker
  - petalBudgetTracker

categories:
  portfolio:
    description: Showcase-worthy projects. Built with intention. Deployed or demo-ready.
    naming_hint: use descriptive noun phrase (what it does), e.g. "swim-pulse", "petal-budget-tracker"
  learning-archive:
    description: Coursework, homework, workshop outputs. Honest label, low-maintenance.
    naming_hint: can include course context, e.g. "react-practical", "figures-of-speech"
  experimental:
    description: Side projects, fun builds, no further dev planned.
    naming_hint: keep it short and honest, e.g. "boba-shop", "fos-test"
  tooling:
    description: Personal dev infrastructure. This repo is an example.
    naming_hint: use system-like names, e.g. "dev-system", "templates"

## HYGIENE_CHECKLIST

# Run this checklist before making any repo public.
# Status values: required | optional | skip-if-not-applicable

checklist:
  - id: description
    label: Repository description filled in
    status: required
    guidance: One sentence. What it is. No jargon. Max 80 chars.
    bad_example: "my project"
    good_example: "Budget tracker with category tagging and monthly summaries — TypeScript + React"

  - id: gitignore
    label: .gitignore present and appropriate
    status: required
    guidance: Use standard Node/React gitignore. Never commit node_modules, .env, or dist.
    template_hint: https://github.com/github/gitignore/blob/main/Node.gitignore

  - id: readme
    label: Custom README.md (not auto-generated)
    status: required
    guidance: Use TEMPLATE.md as base. Fill in all sections. Remove placeholder text.
    template_url: https://raw.githubusercontent.com/tanichk4/dev-system/main/TEMPLATE.md

  - id: topics
    label: At least 1 topic tag added
    status: required
    guidance: >
      Use lowercase kebab-case tags. Minimum 1, ideal 3-5.
      Portfolio repos: use tech stack + domain (e.g. typescript react budget-tracker)
      Learning repos: always include "coursework" tag.
      Fun/experimental: include "side-project" tag.

  - id: commit_messages
    label: Meaningful commit messages
    status: required
    guidance: >
      No "fix", "update", "asdf", "wip" as standalone messages.
      Format: imperative verb + subject. e.g. "Add budget summary chart", "Fix date parsing edge case"
      For initial commit: "Init project with [stack]" or "Add [feature] scaffold"

  - id: live_demo
    label: Live demo link in README or description
    status: optional
    guidance: Add if deployed. Use Vercel, Netlify, or GitHub Pages. Skip if local-only project.

  - id: env_example
    label: .env.example file present if project uses env vars
    status: skip-if-not-applicable
    guidance: Never commit real secrets. Always provide .env.example with dummy values.

## AUDIT_RULES
# Claude uses these rules when auditing an existing repo for tanichk4.

rules:
  - if: description is empty or generic
    flag: missing-description
    action: add description following HYGIENE_CHECKLIST.description.guidance

  - if: no topic tags
    flag: missing-topics
    action: suggest 3-5 tags based on tech stack and repo content

  - if: README is auto-generated (only contains repo name and description line)
    flag: stub-readme
    action: offer to rewrite using TEMPLATE.md

  - if: repo name contains uppercase or underscores
    flag: naming-violation
    action: suggest kebab-case rename, ask user permission before renaming

  - if: repo appears to be coursework (e.g. "hw", "homework", "lesson", "practice" in name or commits)
    flag: learning-archive
    action: ensure "coursework" tag is present, description is honest

  - if: repo is empty (no files beyond auto-init)
    flag: empty-repo
    action: skip silently — do not add description or topics to empty repos

## VERSION
last_updated: 2026-06-11
owner: tanichk4
