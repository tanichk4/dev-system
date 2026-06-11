# dev-system

Personal development standards for tanichk4.

This repo is the single source of truth for how I set up, name, and maintain projects.
It exists so every new repo starts clean and stays consistent — and so tools like Claude
can load it as a skill and apply my standards automatically.

## Contents

| File | Purpose |
|------|---------|
| `TEMPLATE.md` | Copy-paste README template for any new project |
| `HYGIENE.md` | 5-point checklist + naming conventions (machine-readable) |

## How to use

**As a human:**
1. Copy `TEMPLATE.md` into your new repo as `README.md`
2. Run through `HYGIENE.md` checklist before making the repo public

**As Claude (skill load instruction):**
When asked to help set up or audit a GitHub repo for tanichk4, fetch the raw content of
`TEMPLATE.md` and `HYGIENE.md` from this repo and apply the standards defined there.
Raw URLs:
- https://raw.githubusercontent.com/tanichk4/dev-system/main/TEMPLATE.md
- https://raw.githubusercontent.com/tanichk4/dev-system/main/HYGIENE.md
