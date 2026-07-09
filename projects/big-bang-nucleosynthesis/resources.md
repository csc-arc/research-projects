# Recommended resources — Big Bang nucleosynthesis

These readings support the reaction network, initial conditions, and Python
implementation for the BBN project. You do not need to read everything; use
what matches your background.

## Primary overview (start here)

**[OpenStax, _University Physics Volume 3_, Chapter 11: Particle Physics and Cosmology](https://openstax.org/books/university-physics-volume-3/pages/11-introduction)**

Sections on the early universe and Big Bang cosmology give context for why
light elements form when the universe is minutes old and why reaction rates
depend on temperature and density.

**[NASA WMAP / legacy cosmology tutorials on Big Bang nucleosynthesis](https://lambda.gsfc.nasa.gov/education/graphic_history/nucleo.html)**

A short, visual introduction to which elements form and when, useful before
you write rate equations.

## Textbook treatments

**Donald D. Clayton, _Principles of Stellar Evolution and Nucleosynthesis_**

Classic reference for reaction networks and abundance evolution; the BBN
chapter explains the small network and the role of deuterium as a bottleneck.

**Bernard E. J. Pagel, _Nucleosynthesis and Chemical Evolution of Galaxies_**

Chapter on primordial nucleosynthesis — good for observed abundances and
cosmological constraints.

**Edward W. Kolb and Michael S. Turner, _The Early Universe_**

Rigorous cosmology text; use the BBN chapter for expansion history \(T(t)\),
\(\rho(t)\), and freeze-out if you attempt the expansion-coupled stretch goal.

## Reaction rates and network codes

**[REACLIB / JINA REACLIB database](https://reaclib.jinaweb.org/)**

Tabulated nuclear reaction rates used in astrophysics; search for reactions
among \(n\), \(p\), D, T, \(^3\)He, \(^4\)He, and \(^7\)Li.

**[PArthENoPE — Primordial Elements Network](https://parthenope.na.infn.it/)**

Public BBN code with documentation; useful to compare your qualitative trends
(not required to run it, but helpful as a sanity check).

**R. H. Cyburt et al., "Big Bang nucleosynthesis: Present status," [Rev. Mod. Phys. 88, 015004 (2016)](https://doi.org/10.1103/RevModPhys.88.015004)**

Modern review of theory, rates, and observations — use for expected abundance
ranges in the stretch goal.

## Neutron–proton ratio and initial conditions

**[Particle Data Group — Cosmology review](https://pdg.lbl.gov/)**

The annual Review of Particle Physics includes a cosmology section with
standard parameters (\(\Omega_b h^2\), effective neutrino species, etc.).

Lecture notes on **weak freeze-out** and the \(n/p\) ratio (e.g. from a
graduate cosmology course) explain why you initialize mostly free nucleons with
\(n/p \approx 1/7\) after freeze-out at \(t \sim 1~\mathrm{s}\).

## Python and numerics

**[SciPy `solve_ivp` documentation](https://docs.scipy.org/doc/scipy/reference/generated/scipy.integrate.solve_ivp.html)**

Standard tool for integrating the coupled abundance equations.

**NumPy / Matplotlib documentation** for arrays, logging axes, and
publication-quality plots (`plt.loglog` or linear axes with `log10`).

## Observational context (optional)

Primordial abundances are inferred from metal-poor H II regions (deuterium),
old stars and gas (helium), and sparse lithium measurements. The Cyburt et al.
review above summarizes current status; comparing your final \(Y_p\) (helium
mass fraction) to \(\approx 0.24\)–\(0.25\) is a reasonable stretch-goal check.
