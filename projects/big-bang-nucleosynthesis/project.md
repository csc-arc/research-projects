---
title: "Big Bang Nucleosynthesis and Light-Element Abundances"
pi: "cfastrophysica"
goals:
  - "Identify the nuclear reactions that matter for light-element synthesis in the early universe"
  - "Specify physically motivated initial abundances at the start of nucleosynthesis"
  - "Write Python code that integrates the time evolution of isotope mass fractions"
  - "Produce a plot of log(mass fraction) versus log(time) for each relevant isotope"
  - "Explain in writing how nuclear reaction rates and the expanding universe set the abundances we observe today"
---

# Research Project: Big Bang Nucleosynthesis and Light-Element Abundances

## Project overview

In the first few minutes after the Big Bang, the universe was hot and dense
enough for protons and neutrons to undergo nuclear reactions and build the
lightest elements — primarily deuterium (\(^2\)H), helium-3 and helium-4
(\(^3\)He, \(^4\)He), and traces of lithium-7 (\(^7\)Li). This process is
called **Big Bang nucleosynthesis (BBN)**. The abundances it predicts are among
the earliest quantitative tests of cosmology and remain a benchmark for our
understanding of the early universe.

In this project, you will build a small **reaction network** in Python: you
will identify which reactions and isotopes matter, choose sensible initial
conditions, integrate how each species' **mass fraction** changes with time,
and plot the result. The goal is not to match every observational detail at
research precision, but to understand **how nuclear reactions couple to time
evolution** and to see, in a single figure, how the light elements appear,
grow, and freeze out.

This project is designed for students who have seen introductory nuclear or
particle physics and basic differential equations. You do not need prior
experience with astrophysical nucleosynthesis. By the end, you should be able
to explain which reactions dominate at each stage, why initial abundances
matter, and how a network of rate equations produces the familiar BBN picture.

---

## Core idea

Each isotope \(i\) in your network carries a **mass fraction** \(X_i\): the
fraction of the total baryonic mass in that species, with \(\sum_i X_i = 1\).
The abundances change because nuclei are created and destroyed by nuclear
reactions. Schematically, for each species you write a rate equation of the
form

\[
\frac{dX_i}{dt} = \sum_j (\text{production from } j) - \sum_k (\text{loss to } k),
\]

where each term is proportional to a **reaction rate** (which depends on
temperature and density in the early universe) and on the abundances of the
reactants.

For BBN, the relevant network is small compared to stellar nucleosynthesis,
but you must still choose it deliberately. A minimal network often includes
neutron (\(n\)), proton (\(p\)), deuterium (\(^2\)H), tritium (\(^3\)H),
helium-3 (\(^3\)He), helium-4 (\(^4\)He), and optionally lithium-7 (\(^7\)Li).
Key processes include \(n + p \rightleftharpoons {}^2\mathrm{H} + \gamma\),
deuterium burning into helium, and the chains that build \(^4\)He. You will
look up or adopt standard rate expressions (see `resources.md`) and study how
sensitive your evolution is to the rates and to your **initial** \(n/p\) ratio.

Your main deliverable is a **log–log plot**: \(\log X_i\) versus \(\log t\)
for each isotope you include, over the minutes when nucleosynthesis is active.
That plot should make the sequence visible: when deuterium forms, when it is
destroyed to make helium, and when the network effectively **freezes out** as
the universe expands and cools.

---

## What you will do

### 1. Choose the reaction network

From the references in `resources.md`, list the reactions you will include and
draw a simple diagram showing which isotopes connect to which. For each
reaction, note the reactants, products, and whether it is important at early
times (high temperature) or late times (cooler). Drop reactions that are
negligible for your temperature range, but document why you omitted them.

### 2. Set initial abundances

Before nucleosynthesis begins in earnest, the universe is mostly free protons
and neutrons (with photons and electrons in equilibrium). Specify **initial
mass fractions** at the start of your integration — for example, after
neutron–proton freeze-out, when the \(n/p\) ratio is set by weak interactions
and no longer tracks equilibrium. State your choice clearly (e.g. all mass in
\(n\) and \(p\) with a given \(n/p\), or a standard textbook value) and why it
is reasonable.

### 3. Implement the evolution in Python

Write a script or notebook that:

- Defines the mass fractions \(X_i(t)\) for your network
- Evaluates reaction rates (using simplified temperature and density histories
  from the literature, or fixed parameters over a short integration window if
  you are not yet coupling to cosmological expansion)
- Integrates the coupled ordinary differential equations forward in time (e.g.
  with `scipy.integrate.solve_ivp`)
- Checks that \(\sum_i X_i\) stays near unity (or enforces normalization)

Keep the code readable: separate rate functions, network definitions, and
plotting.

### 4. Plot log(mass fractions) versus log(time)

Produce one figure with \(\log X_i\) on the vertical axis and \(\log t\) on the
horizontal axis (with \(t\) in seconds or minutes — label the units). Include
a curve for each isotope in your network. Use distinct colors or line styles
and a legend. The plot should show, at a glance, when each species rises or
falls and which species dominate at late times (typically \(^4\)He and
remaining \(p\)).

---

## Required products

At the end of the project, you should submit:

- **A reaction-network diagram** (hand-drawn or digital) listing the reactions
  you implemented
- **A log–log abundance plot** — \(\log X_i\) versus \(\log t\) for all
  species in your network
- **A clean Python notebook or script** that reproduces the integration and the
  plot
- **A short written explanation** (roughly one to two pages) that answers:
  - Which reactions drove the rise of \(^4\)He?
  - Why is deuterium often called a "bottleneck"?
  - How did your choice of initial \(n/p\) affect the helium abundance?
  - What does "freeze-out" mean in this context?

---

## Suggested workflow

1. Read the BBN overview in `resources.md` and skim a standard reaction-rate
   table or lecture notes.
2. Fix your isotope list and write down the rate equations on paper before
   coding.
3. Implement rates and a test integration with only \(n\), \(p\), and \(^2\)H
   if that helps debug.
4. Add helium and lithium channels, then run the full network to several
   minutes after the start of nucleosynthesis.
5. Generate the log–log plot and iterate until the curves tell a coherent
   story (deuterium peak, helium growth, late-time freeze-out).
6. Write the explanation connecting your plot to the physics.

---

## Stretch goals

- **Couple to cosmological expansion:** use a simple scaling \(T(t)\) and
  \(\rho(t)\) from the radiation-dominated era instead of fixed temperature.
- **Compare to observations:** quote predicted primordial mass fractions for
  \(^4\)He and D/H and compare order-of-magnitude to published values.
- **Sensitivity study:** vary the initial \(n/p\) ratio or a single reaction
  rate by 10% and show how the final helium fraction changes.

---

## What a successful project should demonstrate

A successful project is clear, physically motivated, and computationally sound.
You should be able to say:

- I can list the main BBN reactions and explain why each matters.
- I chose initial abundances consistent with the physics before
  nucleosynthesis.
- I integrated a coupled network of rate equations in Python.
- My log–log plot shows how light-element mass fractions evolve with time.
- I can explain nuclear reaction rates and abundance evolution in my own
  words, without relying only on the plot legend.

The purpose is to **learn nuclear reactions and time evolution of abundances**
through a concrete, visual calculation — not to publish a new BBN code.
