---
# ═══════════════════════════════════════════════════════════════════════════
#  YOUR HOMEPAGE
#  The page is built from the `sections:` list below, top to bottom.
#  Reorder them by moving blocks around; hide one by deleting it.
#  Each `id:` is what the nav bar's `/#id` links point at — if you change an
#  id here, change it in `config/_default/menus.yaml` too.
#  Most of the *text* on this page lives in `data/authors/me.yaml`.
# ═══════════════════════════════════════════════════════════════════════════
title: ''
summary: ''
date: 2026-08-28
type: landing

sections:
  # ── 1. Bio ───────────────────────────────────────────────────────────────
  # Two columns: photo, name, role, affiliation and social icons on the left;
  # "Professional Summary", CV button and the Education cards on the right.
  # All of it comes from `data/authors/me.yaml`. Swap the photo by replacing
  # `assets/media/authors/me.png` with your own (square, 640x640 or larger).
  - block: resume-biography-3
    content:
      username: me
      text: ''
      # Replace `static/uploads/resume.pdf` with your own CV, or delete this
      # `button` block if you'd rather not offer a download.
      button:
        text: Download CV
        url: uploads/resume.pdf
      # Leave blank for the defaults ("Professional Summary", "Education").
      headings:
        about: ''
        education: ''
        interests: ''
    design:
      name:
        size: md # xs, sm, md, lg, xl
      avatar:
        size: medium # small, medium, large, xl, xxl
        shape: circle # circle, square, rounded

  # ── 2. Research ──────────────────────────────────────────────────────────
  - block: markdown
    id: research
    content:
      title: '📚 Research'
      subtitle: ''
      text: |-
        Replace this with a paragraph or two about your research programme —
        the question you're chasing, the methods you use, and why it matters.

        A good structure: what the field gets wrong or leaves open, what you
        do about it, and where you want to take it next. That last part
        matters most on the postdoc market — a PI wants to see the research
        programme you'd bring to their group, not just what you've finished.
    design:
      columns: '1'

  # ── 3. Selected publications ─────────────────────────────────────────────
  # Shows only papers with `featured: true` in their front matter.
  - block: collection
    id: papers
    content:
      title: Selected Publications
      filters:
        folders:
          - publications
        featured_only: true
    design:
      view: article-grid
      columns: 2

  # ── 4. All publications, as formatted citations ──────────────────────────
  - block: collection
    id: publications
    content:
      title: All Publications
      text: ''
      filters:
        folders:
          - publications
        exclude_featured: false
    design:
      view: citation

  # ── 5. Talks ─────────────────────────────────────────────────────────────
  - block: collection
    id: talks
    content:
      title: Talks & Presentations
      filters:
        folders:
          - events
    design:
      view: card

  # ── 6. News ──────────────────────────────────────────────────────────────
  - block: collection
    id: news
    content:
      title: News
      subtitle: ''
      text: ''
      count: 5
      filters:
        folders:
          - news
      order: desc
    design:
      view: card
      spacing:
        padding: [0, 0, 0, 0]

  # ── 7. Contact ───────────────────────────────────────────────────────────
  # Social icons are pulled from `links:` in `data/authors/me.yaml`.
  # Delete any field below that you'd rather not publish.
  - block: contact-info
    id: contact
    content:
      title: Contact
      subtitle: ''
      text: |-
        The best way to reach me is by email. I'm happy to hear about
        collaborations, seminar invitations, and student enquiries.
      # Either a single address or a list; each one renders as its own entry.
      email:
        - mumumia.1009@gmail.com
        - oymzmia@163.com
      phone: ''
      visit_title: 'Find Me'
      address:
        lines:
          - Institute of Biopharmaceutical and Health Engineering (iBHE)
          - Tsinghua Shenzhen International Graduate School
          - Tsinghua Campus, Xili University Town, Nanshan District
          - Shenzhen 518055, China
      # Relabels the block that upstream calls "Office Hours" — as a PhD
      # candidate you hold none, and a visiting PI needs your time zone more.
      office_hours_title: 'Availability'
      office_hours:
        - 'Shenzhen, China (UTC+8)'
        - 'Happy to arrange calls across time zones'
      # One entry per map provider — each renders as its own button.
      # Google Maps is unreachable from inside mainland China, and Amap
      # (高德) is what a visitor there will actually use, so offer both.
      map_url:
        - label: 'Google Maps'
          url: 'https://www.google.com/maps/search/?api=1&query=Tsinghua+Shenzhen+International+Graduate+School'
        - label: 'Amap 高德地图'
          url: 'https://uri.amap.com/search?keyword=%E6%B8%85%E5%8D%8E%E5%A4%A7%E5%AD%A6%E6%B7%B1%E5%9C%B3%E5%9B%BD%E9%99%85%E7%A0%94%E7%A9%B6%E7%94%9F%E9%99%A2&city=%E6%B7%B1%E5%9C%B3'
      # Set true only if you have configured a form backend in `form_action`
      show_form: false
      form_action: ''
      # Call-out box. While you're on the job market, use it to say so
      # plainly — it's the first thing a hiring PI looks for.
      # Delete this whole block once you've landed a position.
      prospective:
        title: 'Seeking postdoctoral positions'
        text: |-
          I expect to defend in June 2027 and am looking for postdoc
          positions starting in late 2027, in TOPIC AREA. Happy to share my
          research statement and references on request.
---
