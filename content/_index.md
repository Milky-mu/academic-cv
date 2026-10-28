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
  # "About Me", CV button and the Education cards on the right.
  # All of it comes from `data/authors/me.yaml`. Swap the photo by replacing
  # `assets/media/authors/me.png` with your own (square, 640x640 or larger).
  - block: resume-biography-3
    content:
      username: me
      text: ''
      # ── CV button: temporarily off ──────────────────────────────────────
      # The PDF was taken down while the CV is being trimmed. To put it
      # back: drop the new file at `static/uploads/Ouyang-Muzi-CV.pdf` and
      # uncomment the three lines below. The button only renders when both
      # `text` and `url` are non-empty, so leaving it commented hides it
      # cleanly — no placeholder, no dead link.
      # button:
      #   text: Download CV
      #   url: uploads/Ouyang-Muzi-CV.pdf
      # Leave blank for the defaults ("Professional Summary", "Education").
      headings:
        about: 'About Me'
        education: ''
        interests: ''
    design:
      # padding: [top, right, bottom, left]. Top is 0 to close the white band
      # between the navbar and this section — .hbb-section defaults to 6rem
      # top padding, and the section's tinted background sits on an inner
      # div, so that 6rem showed the plain white page background.
      spacing:
        padding: ['0', '0', '6rem', '0']
      banner:
        filename: kalen-emsley-Bkci_8qcdvQ-unsplash.jpg
      name:
        size: md # xs, sm, md, lg, xl
      avatar:
        size: medium # small, medium, large, xl, xxl
        shape: circle # circle, square, rounded

  # ── 2. Research ──────────────────────────────────────────────────────────
  # A local block (layouts/_partials/hbx/blocks/research-labs): a lead
  # line, then one card per area, side by side. Add, remove or reorder areas
  # freely; `icon` takes any Hero icon name.
  - block: research-labs
    id: research
    content:
      title: '📚 Research'
      text: >-
        My work moves constantly between the bench and the computer, usually
        because one keeps raising questions the other has to answer.
      areas:
        - label: Wet Lab
          title: Targeted Protein Degradation & Drug Resistance
          icon: beaker
          text: |-
            I design and test protein degraders, mostly **bioPROTACs** built
            on E3 ligase scaffolds like TRIM21, and use cancer drug resistance
            as a lens for understanding when and why they fail. My central
            finding came from comparing a tamoxifen-resistant breast cancer
            line (LCC2) to its drug-sensitive parent (MCF7): whole-genome
            sequencing turned up **a mutation in the KRAS hypervariable
            region**, a region with no previously known function, that nearly
            abolished the activity of a TRIM21-based KRAS degrader
            specifically in the resistant line. Beyond mechanism, I also build
            degraders as therapeutic candidates directly, including a
            tumor-specific bioPROTAC that **co-degrades ERα and PI3K p85α** to
            resensitize resistant breast cancer cells to tamoxifen, and, in an
            ongoing collaboration, a TRIM21-based bioPROTAC achieving
            **dual-target degradation of oncogenic KRAS assemblies** in
            pancreatic cancer.
        - label: Dry Lab
          title: Molecular Dynamics & Computational Protein Design
          icon: cpu-chip
          text: |-
            The wet-lab puzzles above are usually what send me back to the
            computer. To explain why the KRAS mutation broke degrader
            activity, I ran **182-ns all-atom molecular dynamics simulations**
            (AMBER, with explicit GppNHp and Mg^2+^) and showed that the
            mutation changes how KRAS clusters at the membrane, which the
            degrader's activity turns out to depend on; swapping in a degrader
            architecture that doesn't rely on clustering restored activity,
            confirming the mechanism computationally and experimentally at
            once. Separately, I taught myself a full **de novo protein design
            pipeline**, Rosetta Match for scaffold matching, ProteinMPNN for
            sequence design, and AlphaFold2 for structural validation, and
            used it to design new binders for small-molecule targets from
            scratch, open-sourcing the pipeline on GitHub. I see this
            computational side less as a separate skill set and more as the
            other half of the same question: once you know why a degrader
            fails, you can start predicting it.

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
  # Commented out: with no items in `content/events/`, this renders as a bare
  # heading with nothing under it. Add a folder there, then uncomment this
  # block AND the "Talks" entry in `config/_default/menus.yaml`.
  # - block: collection
  #   id: talks
  #   content:
  #     title: Talks & Presentations
  #     filters:
  #       folders:
  #         - events
  #   design:
  #     view: card

  # ── 6. News ──────────────────────────────────────────────────────────────
  # Commented out for the same reason — see the note above. Add a folder in
  # `content/news/`, then uncomment this and the "News" menu entry.
  # - block: collection
  #   id: news
  #   content:
  #     title: News
  #     subtitle: ''
  #     text: ''
  #     count: 5
  #     filters:
  #       folders:
  #         - news
  #     order: desc
  #   design:
  #     view: card
  #     spacing:
  #       padding: [0, 0, 0, 0]

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
          positions starting in late 2027, in computational protein design,
          targeted protein degradation, and chemical biology. Happy to
          share my research statement and references on request.
---
