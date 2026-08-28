---
# ═══════════════════════════════════════════════════════════════════════════
#  EXAMPLE PUBLICATION — copy this folder for each paper, then delete this one.
#
#  FASTER OPTION: put a `publications.bib` file in the repo root and push.
#  A GitHub Action converts every BibTeX entry into a page like this one
#  automatically. See the README.
# ═══════════════════════════════════════════════════════════════════════════
title: "The Title of Your Paper"

# Use `me` for yourself so it links to your profile; plain text for co-authors.
authors:
  - me
  - Co Author
# Optional footnotes lining up with `authors` above. Delete if unused.
author_notes:
  - "Equal contribution"
  - "Equal contribution"

# The publication date.
date: "2026-01-15T00:00:00Z"

# CSL publication type. Common values:
#   article-journal | paper-conference | chapter | thesis | report | manuscript
publication_types: ["article-journal"]

publication:
  name: "Name of the Journal or Conference"
  volume: 12
  issue: 3

peer_reviewed: true
open_access: true

abstract: Paste your abstract here as a single paragraph.

# Optional shorter version used in listings. Delete to fall back to `abstract`.
summary: A one- or two-sentence version of the abstract for listing pages.

tags:
  - Your Topic

# `true` puts this paper in the "Selected Publications" grid on the homepage.
featured: true

# Optional identifiers — these enable the Cite button and metadata lookup.
hugoblox:
  ids:
    doi: ""
    arxiv: ""

# Buttons on the publication page. Delete any you don't have.
links:
  - type: pdf
    url: ""
  - type: code
    url: ""
  - type: dataset
    url: ""
  - type: poster
    url: ""
  - type: slides
    url: ""
  - type: video
    url: ""

# Optional thumbnail: add `featured.jpg` or `featured.png` to this folder.
image:
  caption: ''
  focal_point: ""
  preview_only: false

# Link to entries in `content/projects/` by folder name, e.g. ["example-project"]
projects: []
---

Optional full text, supplementary notes, or a plain-language summary of the
paper goes here. Delete this if you only want the abstract to show.
