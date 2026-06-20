---
# ============================================================
# Member Frontmatter Configuration Guide
# ============================================================

# _hidden [Internal]: Hide this file from the members list
_hidden: true

# name [Required]: Full name of the member
name: Demo Member

# role [Optional]: Display role (shown on card)
role: Research Position

# title [Optional]: Academic title (e.g., PhD, MSc, BSc)
title: PhD Candidate

# email [Optional]: Contact email
email: demo@example.com

# scholar [Optional]: Google Scholar profile URL
scholar: https://scholar.google.com/citations?user=xxxxx

# orcid [Optional]: Bare ORCID iD (e.g. 0000-0001-2345-5678). Matching a
# publication's `authors_orcid` entry cross-links this member with that paper.
orcid: 0000-0000-0000-0000

# image [Optional]: Profile photo path
# Recommended size: 400x400px (square)
# Supported formats: WebP (recommended), JPG, PNG
# Image location: alongside the markdown file in content/ (synced to public/_content/ at build time)
image: /images/logo.png

# category [Required]: Member category. This template declares four in
# nuxt.config.ts (members.categories) — there are no built-in defaults:
#   - staff              : Faculty and staff members
#   - research-students  : PhD and research students
#   - research-assistants: Research assistants
#   - alumni             : Former members
# Customize or replace them freely; the `key` here must match a configured
# category's `key` (see README → Member categories).
category: research-students

# order [Optional]: Sort order within category (lower = earlier)
order: 999

# interests [Optional]: Research interests
interests:
  - Research Interest One
  - Research Interest Two
---

## Biography

Write a brief biography here. Markdown format is fully supported.

### Research Interests

Describe your research interests and current projects.

### Education

- PhD in Your Field, Your University, 2024
- MSc in Your Field, Your University, 2020
- BSc in Your Field, Your University, 2018

### Publications

List your key publications here or link to your Google Scholar profile.
