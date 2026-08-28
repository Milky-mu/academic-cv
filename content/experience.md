---
# ═══════════════════════════════════════════════════════════════════════════
#  /experience/ — the long-form CV page.
#  All of the content comes from `data/authors/me.yaml`; this file only
#  chooses which sections appear and in what order.
# ═══════════════════════════════════════════════════════════════════════════
title: 'Experience'
date: 2026-08-28
type: landing

design:
  spacing: '5rem'

sections:
  - block: resume-experience
    content:
      username: me
    design:
      date_format: 'January 2006'
      # true = education timeline first, false = experience first
      is_education_first: false
  - block: resume-skills
    content:
      title: Skills
      username: me
  - block: resume-awards
    content:
      title: Awards & Honours
      username: me
  - block: resume-languages
    content:
      title: Languages
      username: me
---
