This is a collection of lattice projects that I have made and will continue to make over time.

So far, I have the following: 

- U(1) Gauge theory without any matter fields
  - Plots with MatPlotLib the thermalization of the lattice over several iterations
  - Functions with a relatively small lattice size (L = 16)
  - Uses Numpy (effectively a proof of concept)
  - Able to calculate observables such as average action per plaquette


- phi^4 theory without any gauge fields used to extract the true renormalized mass of the particle
  - This one's formalism works for any (scalar) matter fields without caring much about what the actual lagrangian since metropolis step almost entirely disregards how complicated the action is 
  - Demonstrates how lattice QFT can be used to calculate observables (in this case, the mass)
  - Uses Numpy (effectively a proof of concept)


- QED3 (compact U(1) in 2+1 dimensions) with a massive Dirac fermion, used to extract the fermion mass
  - Fermions use the **staggered** discretization, so the Dirac operator is small enough (4N x 4N) to solve with **exact dense linear algebra** rather than stochastic estimators
  - The mass is extracted **spectrally**, as the smallest |lambda| of the lattice Dirac operator
  - Extends the two projects above by actually putting matter fields on the same lattice as the gauge field
  - Validated against exact free-theory results before being trusted:
    - the free-theory mass is recovered to ~1e-15, and the entire spectrum matches E^2 = m^2 + sum_mu sin^2(p_mu)
    - the extracted mass is gauge invariant (catches a missing complex conjugation on the backward hopping term, which is invisible in the free theory)
    - the local Metropolis action change matches a full recomputation of the action to ~1e-13
  - Results: the mass is renormalized *multiplicatively* with no additive offset, as the remnant chiral symmetry of staggered fermions requires; Z_m rises above 1 as m_0 shrinks
  - Uses Numpy + SciPy (effectively a proof of concept, N_t = L = 6)
  - **Caveats stated in the notebook**: the fermions are *quenched* (not in the Metropolis weight), taste doublers are present at finite lattice spacing, and there is no continuum extrapolation


