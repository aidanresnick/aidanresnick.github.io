---
# Leave the homepage title empty to use the site title
title: ''
summary: ''
date: 2026-08-26
type: landing

sections:
  - block: resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: me
      text: ''
      headings:
        about: 'Biography'
        education: ''
        interests: ''
    design:
      background:
        gradient_mesh:
          enable: true
      name:
        size: md
      avatar:
        size: medium
        shape: circle
  - block: markdown
    content:
      title: '⚾ My Research'
      subtitle: ''
      text: |-
        I build models of pitch quality — how much of run prevention is
        attributable to a pitch's physical characteristics alone. My current
        work treats stuff as a continuous index per pitch type and borrows the
        language of options pricing: each pitch gets "greeks," the local
        sensitivities of expected run value to velocity, induced movement, and
        approach angles, evaluated on the manifold of pitches that actually
        get thrown.

        Please reach out if you'd like to talk pitching models 😃
    design:
      columns: '1'
  - block: collection
    id: papers
    content:
      title: Publications
      text: ''
      filters:
        folders:
          - publications
        exclude_featured: false
    design:
      view: citation
  - block: collection
    id: talks
    content:
      title: Talks
      filters:
        folders:
          - events
    design:
      view: card
---
