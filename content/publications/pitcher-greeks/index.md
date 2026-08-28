---
title: 'Pitcher Greeks: First Principles, Stuff Models, and Derivatives'
authors:
  - me
date: '2026-08-01T00:00:00Z'

publication_types: ['manuscript']

# TODO: when the paper has a venue or public link, fill these in
# publication:
#   name: ''
# url_pdf: ''

abstract: |
  FILLER ABSTRACT — replace with the paper's real abstract. Stuff models grade
  a pitch from its physical characteristics alone. This paper builds a
  continuous, differentiable stuff index per pitch type and borrows the
  language of options pricing: each pitch gets greeks, the local sensitivities
  of expected run value to its physical inputs, evaluated on the manifold of
  pitches that actually get thrown.

summary: |
  A continuous, differentiable stuff model whose sensitivities — "pitcher
  greeks" — show how run value responds to velocity, movement, and approach
  angle.

featured: true
---

> [!NOTE]
> **Filler draft.** Everything below is placeholder text to preview the paper
> layout — the prose and equations are illustrative, not results.

## 1. Introduction

An option's price is a number; its greeks are an explanation. A trader who
knows only the price of a call can neither hedge it nor say why it moved. The
same distinction applies to a pitch. A stuff grade is a mark on one pitch; its
derivatives with respect to the pitch's physical inputs say what the grade is
made of and what would change it. This paper develops that second object.

Placeholder paragraph: we motivate a continuous index $\eta$ per pitch type,
fit on flight characteristics alone, and define the greeks as the gradient of
$\eta$ at each pitcher's operating point. Lorem-adjacent filler continues here
to give the section realistic length and rhythm for judging the layout.

## 2. A differentiable stuff index

Write the grade of a pitch with feature vector $x = (v, z, x_h)$ — velocity,
vertical movement, horizontal movement — as a smooth map

$$
\eta(x) \;=\; f_\theta(x), \qquad f_\theta \in C^1,
$$

so that the object of interest exists everywhere:

$$
\Delta \;=\; \frac{\partial \eta}{\partial v},
\qquad
\nu_z \;=\; \frac{\partial \eta}{\partial z},
\qquad
\nu_x \;=\; \frac{\partial \eta}{\partial x_h}.
$$

Filler sentence: trees and forests price the surface but their derivatives are
a staircase; a smooth parametric family gives greeks by construction, the way
Black–Scholes gives $\partial C/\partial S$ in closed form rather than by
finite difference.

$$
C(S, t) = S\,N(d_1) - K e^{-r(T-t)}\,N(d_2)
\quad\Longrightarrow\quad
\Delta_{\text{BS}} = N(d_1).
$$

## 3. Greeks on the manifold

Physical features co-move: a pitcher who adds a tick of velocity does not hold
movement fixed. The partial derivative answers a counterfactual no one can
throw. Define instead the manifold-adjusted greek as the total derivative
along the empirical coupling,

$$
\tilde{\Delta}
\;=\;
\frac{\partial \eta}{\partial v}
\;+\;
\frac{\partial \eta}{\partial z}\frac{dz}{dv}
\;+\;
\frac{\partial \eta}{\partial x_h}\frac{dx_h}{dv},
$$

which prices the move a pitcher can actually make. Placeholder discussion of
identification and the operating point goes here — two or three sentences of
filler so the section reads at true length.

## 4. What the leaderboard says

Filler section. A table or figure would sit here — e.g. the distribution of
$\tilde{\Delta}$ by pitch type, or the top of the four-seam board — with a
caption in sentence case beneath it.

## References

1. Hull, J. — *Options, Futures, and Other Derivatives*. (Filler citation.)
2. Placeholder, A. — A second reference to show list styling.
