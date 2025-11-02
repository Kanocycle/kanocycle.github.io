# Solutions — Exercise Sheet 3 (Cosmology) — Clear, first-principles derivation  
*Source: exercise sheet `es_03.pdf`. See the original sheet for wording and hints. :contentReference[oaicite:0]{index=0}*

---

## Notation & conventions (first principles)
- Spacetime metric \(g_{\mu\nu}\) (signature \((-,+,+,+)\)). Determinant \(g=\det g_{\mu\nu}\). We set \(c=1\).
- Covariant derivative \(\nabla_\mu\) is metric-compatible: \(\nabla_\rho g_{\mu\nu}=0\). Torsion-free: \([\nabla_\mu,\nabla_\nu]\) acting on scalars vanishes.
- Repeated indices summed (Einstein convention).
- Partial derivative: \(\partial_\mu\).
- Variation: when we vary the metric we hold matter fields fixed unless otherwise stated.

---

# **Exercise 1 — The real Klein–Gordon (KG) field in curved spacetime**

Lagrangian density (minimal coupling):
\[
\mathcal{L} = -\tfrac{1}{2}(\nabla_\mu\varphi)(\nabla^\mu\varphi) - \tfrac{1}{2} m^2\varphi^2,
\qquad S_M[\varphi,g]=\int d^4x\;\sqrt{-g}\,\mathcal{L}.
\]

### 1) **Equations of motion (Euler–Lagrange)**

**Goal:** Derive the curved-space Klein–Gordon equation from the Euler–Lagrange formula
\[
\frac{\delta\mathcal L}{\delta\varphi} - \nabla_\mu\!\left(\frac{\delta\mathcal L}{\delta(\nabla_\mu\varphi)}\right)=0.
\]

**Step-by-step:**

1. The Lagrangian depends on \(\varphi\) only via \(\varphi\) and \(\nabla_\mu\varphi\). Compute the partial functional derivatives.

2. Compute \(\dfrac{\delta\mathcal L}{\delta\varphi}\):
   - Only the mass term depends explicitly on \(\varphi\): \(\partial(\tfrac12 m^2\varphi^2)/\partial\varphi = m^2\varphi\).
   - With the overall minus sign in \(\mathcal L\), we get
     \[
     \frac{\delta\mathcal L}{\delta\varphi} = - m^2 \varphi.
     \]

3. Compute \(\dfrac{\delta\mathcal L}{\delta(\nabla_\mu\varphi)}\):
   - Kinetic term is \(-\tfrac12 g^{\alpha\beta}\nabla_\alpha\varphi\nabla_\beta\varphi\).
   - Differentiate w.r.t. \(\nabla_\mu\varphi\): factor 2 from the symmetric pair cancels the 1/2, giving
     \[
     \frac{\delta\mathcal L}{\delta(\nabla_\mu\varphi)} = - g^{\mu\nu}\nabla_\nu\varphi = -\nabla^\mu\varphi.
     \]

4. Insert into Euler–Lagrange:
   \[
   -m^2\varphi - \nabla_\mu(-\nabla^\mu\varphi) = 0
   \quad\Longrightarrow\quad
   \nabla_\mu\nabla^\mu\varphi - m^2\varphi = 0.
   \]

5. Define the covariant d’Alembertian \(\Box \equiv \nabla_\mu\nabla^\mu\). Final equation:
   \[
   \boxed{(\Box - m^2)\varphi = 0.}
   \]

**Why each step is valid (first principles):**  
- Variation principle: stationary action -> Euler–Lagrange.  
- Covariant derivative acting on scalar equals ordinary partial derivative, but index raising uses metric \(g^{\mu\nu}\).  
- No extra Christoffel terms appear in \(\nabla_\mu\nabla^\mu\varphi\) because \(\nabla_\mu\varphi = \partial_\mu\varphi\) and commuting two covariant derivatives on scalar is trivial.

---

### 2) **Energy–momentum tensor \(T_{\mu\nu}\) from metric variation**

**Goal:** Use the definition
\[
T_{\mu\nu} \equiv -\frac{2}{\sqrt{-g}}\,\frac{\delta S_M}{\delta g^{\mu\nu}},
\]
and compute \(T_{\mu\nu}\) for the KG field.

**Key identities (proveable from linear algebra / determinant properties):**
1. \(\delta\sqrt{-g} = -\tfrac12\sqrt{-g}\,g_{\alpha\beta}\,\delta g^{\alpha\beta}.\)
2. \(\delta g^{\alpha\beta} = - g^{\alpha\mu} g^{\beta\nu} \delta g_{\mu\nu}.\)

**Step-by-step variation:**

Write
\[
\delta S_M = \int d^4x\ \left( \delta\sqrt{-g}\,\mathcal L + \sqrt{-g}\,\delta\mathcal L \right).
\]

**Term A — \(\delta\sqrt{-g}\,\mathcal L\):**
\[
\delta\sqrt{-g}\,\mathcal L = -\tfrac12\sqrt{-g}\,g_{\mu\nu}\mathcal L\;\delta g^{\mu\nu}.
\]
(This produces the \(g_{\mu\nu}\mathcal L\) term in \(T_{\mu\nu}\).)

**Term B — \(\sqrt{-g}\,\delta\mathcal L\):**  
The matter Lagrangian depends on the metric only through \(g^{\alpha\beta}\) in the kinetic term (mass term has no explicit metric dependence). Thus,
\[
\delta\mathcal L = -\tfrac12 \, \delta g^{\alpha\beta}\,\nabla_\alpha\varphi\,\nabla_\beta\varphi.
\]
So
\[
\sqrt{-g}\,\delta\mathcal L = -\tfrac12\sqrt{-g}\,\nabla_\alpha\varphi\,\nabla_\beta\varphi\;\delta g^{\alpha\beta}.
\]

**Combine A and B:**
\[
\delta S_M
= -\tfrac12\int d^4x\ \sqrt{-g}\;\Big[ \nabla_\mu\varphi\,\nabla_\nu\varphi + g_{\mu\nu}\,\mathcal L \Big]\ \delta g^{\mu\nu}.
\]

**Compare to definition:** \(\delta S_M = -\tfrac12\int \sqrt{-g}\,T_{\mu\nu}\,\delta g^{\mu\nu}\). Therefore read off
\[
\boxed{T_{\mu\nu} = \nabla_\mu\varphi\,\nabla_\nu\varphi + g_{\mu\nu}\,\mathcal L.}
\]

**Substitute \(\mathcal L\) explicitly:**
\[
\begin{aligned}
T_{\mu\nu}
&= \nabla_\mu\varphi\,\nabla_\nu\varphi
    + g_{\mu\nu}\Big( -\tfrac12 \nabla_\alpha\varphi\nabla^\alpha\varphi - \tfrac12 m^2\varphi^2\Big)\\[6pt]
&= \nabla_\mu\varphi\,\nabla_\nu\varphi - \tfrac12 g_{\mu\nu}\big(\nabla_\alpha\varphi\nabla^\alpha\varphi + m^2\varphi^2\big).
\end{aligned}
\]

**Interpretation:** This is the symmetric, covariantly conserved stress–energy tensor for the minimally-coupled scalar field.

---

### 3) **Conserved current for Killing field \(v^\mu\)**

**Given:** \(v^\mu\) is a Killing vector: \(\nabla_{(\mu} v_{\nu)} = 0\). Define current
\[
j^\mu \equiv - T^{\mu}{}_{\nu} v^\nu.
\]

**Show:** \(\nabla_\mu j^\mu = 0.\)

**Proof (first principles):**

1. Compute divergence:
   \[
   \nabla_\mu j^\mu = - \nabla_\mu\big(T^{\mu}{}_{\nu} v^\nu\big)
   = -(\nabla_\mu T^{\mu}{}_{\nu}) v^\nu - T^{\mu}{}_{\nu} \,\nabla_\mu v^\nu.
   \]

2. In GR, when matter obeys its field equations derived from the diffeomorphism-invariant action, the stress tensor is covariantly conserved: \(\nabla_\mu T^{\mu}{}_{\nu}=0\). (First-principles reason: diffeomorphism invariance of the matter action gives \(\nabla_\mu T^{\mu}{}_{\nu}=0\) on-shell.)

3. Therefore \(\nabla_\mu j^\mu = - T^{\mu}{}_{\nu} \nabla_\mu v^\nu\).

4. Use symmetry of \(T^{\mu\nu}\) and Killing property:
   \[
   T^{\mu}{}_{\nu}\nabla_\mu v^\nu = T^{\mu\nu}\nabla_\mu v_\nu
   = \tfrac12 T^{\mu\nu}\big(\nabla_\mu v_\nu + \nabla_\nu v_\mu\big) = T^{\mu\nu}\nabla_{(\mu}v_{\nu)} = 0.
   \]

Hence \(\nabla_\mu j^\mu = 0\). QED.

**Meaning:** A spacetime symmetry (Killing vector) gives a conserved current by contracting the stress tensor with the symmetry generator.

---

### 4) **Derive KG equation from \(\nabla_\mu T^{\mu\nu}=0\)**

**Idea:** Insert \(T^{\mu\nu}\) for the scalar into \(\nabla_\mu T^{\mu\nu}=0\) and show it implies \((\Box-m^2)\varphi=0\) (except possibly when \(\nabla^\nu\varphi\equiv0\), which is trivial).

**Detailed steps:**

1. Start with
   \[
   T^{\mu\nu} = \nabla^\mu\varphi\nabla^\nu\varphi - \tfrac12 g^{\mu\nu}\big(\nabla_\alpha\varphi\nabla^\alpha\varphi + m^2\varphi^2\big).
   \]

2. Compute divergence:
   \[
   \nabla_\mu T^{\mu\nu}
   = \nabla_\mu(\nabla^\mu\varphi\nabla^\nu\varphi) - \tfrac12 \nabla^\nu(\nabla_\alpha\varphi\nabla^\alpha\varphi) - \tfrac12 m^2 \nabla^\nu(\varphi^2).
   \]

   Expand the first term using product rule:
   \[
   \nabla_\mu(\nabla^\mu\varphi\nabla^\nu\varphi)
   = (\nabla_\mu\nabla^\mu\varphi)\nabla^\nu\varphi + \nabla^\mu\varphi \,\nabla_\mu\nabla^\nu\varphi.
   \]

3. Observe identity (product derivative on scalar gradients):
   \[
   \nabla^\mu\varphi \,\nabla_\mu\nabla^\nu\varphi - \tfrac12 \nabla^\nu(\nabla_\alpha\varphi\nabla^\alpha\varphi)
   = 0,
   \]
   because \(\nabla^\nu(\nabla_\alpha\varphi\nabla^\alpha\varphi) = 2\,\nabla^\mu\varphi\,\nabla^\nu\nabla_\mu\varphi\) (use torsion-free property to exchange \(\nabla_\mu\nabla^\nu\varphi=\nabla^\nu\nabla_\mu\varphi\) when needed).

4. Thus the divergence reduces to
   \[
   \nabla_\mu T^{\mu\nu} = (\Box\varphi)\nabla^\nu\varphi - m^2\varphi\,\nabla^\nu\varphi
   = (\Box\varphi - m^2\varphi)\,\nabla^\nu\varphi.
   \]

5. Therefore \(\nabla_\mu T^{\mu\nu}=0\) implies
   \[
   (\Box\varphi - m^2\varphi)\,\nabla^\nu\varphi = 0.
   \]
   If \(\nabla^\nu\varphi\) is not identically zero globally, we must have \(\Box\varphi - m^2\varphi = 0\). If \(\nabla^\nu\varphi\equiv0\), \(\varphi\) is constant and the field equation reduces to \(m^2\varphi=0\), consistent.

**Conclusion:** Conservation of stress tensor encodes the KG equation (on-shell equivalence).

---

### 5) **Projections of perfect-fluid \(T_{\mu\nu}\)**

Perfect fluid stress tensor:
\[
T_{\mu\nu} = (\rho + p) u_\mu u_\nu + p g_{\mu\nu},\qquad u_\mu u^\mu = -1.
\]
Projector orthogonal to \(u^\mu\):
\[
h_{\mu\nu} \equiv g_{\mu\nu} + u_\mu u_\nu,\qquad h_{\mu\nu}u^\nu=0.
\]

**(a) Completely longitudinal part** (project both indices along \(u\)):
\[
u^\mu u^\nu T_{\mu\nu}
= u^\mu u^\nu [(\rho+p)u_\mu u_\nu + p g_{\mu\nu}]
= (\rho+p)(u^\mu u_\mu)(u^\nu u_\nu) + p (u^\mu u_\mu).
\]
But \(u^\mu u_\mu = -1\), so
\[
u^\mu u^\nu T_{\mu\nu} = (\rho+p)(-1)(-1) + p(-1) = \rho.
\]
So the completely longitudinal projection yields the energy density:
\[
\boxed{u^\mu u^\nu T_{\mu\nu} = \rho.}
\]

**(b) Completely transverse part** (project both indices with \(h\)):
\[
h^\alpha{}_\mu h^\beta{}_\nu T_{\alpha\beta}
= h^\alpha{}_\mu h^\beta{}_\nu [(\rho+p)u_\alpha u_\beta + p g_{\alpha\beta}] .
\]
The \(u_\alpha\) terms vanish because \(h^\alpha{}_\mu u_\alpha = 0\). The remaining term gives
\[
h^\alpha{}_\mu h^\beta{}_\nu p g_{\alpha\beta} = p\, h_{\mu\nu}.
\]
So the completely transverse (spatial) part is
\[
\boxed{h^\alpha{}_\mu h^\beta{}_\nu T_{\alpha\beta} = p\, h_{\mu\nu}.}
\]

**Interpretation:** Longitudinal = energy measured by fluid comoving observer; transverse = isotropic pressure in spatial directions.

---

### 6) **Split \(\nabla_\mu T^{\mu\nu}=0\) into parallel and orthogonal parts**

**Parallel (contract with \(u_\nu\)):** \(u_\nu \nabla_\mu T^{\mu\nu} = 0\).

Compute using product rule and perfect-fluid form (derivation from first principles):

1. Evaluate \(u_\nu \nabla_\mu T^{\mu\nu}\):
   \[
   u_\nu \nabla_\mu T^{\mu\nu}
   = \nabla_\mu(u_\nu T^{\mu\nu}) - (\nabla_\mu u_\nu)T^{\mu\nu}.
   \]
   But a more direct route uses substitution of \(T^{\mu\nu}\) and contraction:

2. Using \(T^{\mu\nu}=(\rho+p)u^\mu u^\nu + p g^{\mu\nu}\), compute
   \[
   u_\nu \nabla_\mu T^{\mu\nu}
   = \nabla_\mu\big[(\rho+p)u^\mu (u_\nu u^\nu)\big] + u_\nu\nabla_\mu(p g^{\mu\nu}).
   \]
   Simplifying and using \(u_\nu u^\nu=-1\) and \(\nabla_\mu g^{\mu\nu}=0\) yields the energy equation:
   \[
   \boxed{u^\mu\nabla_\mu \rho + (\rho+p)\nabla_\mu u^\mu = 0.}
   \]
   This is the relativistic continuity equation: rate of change of energy density along flow + expansion work term \( (\rho+p)\theta\) (with \(\theta=\nabla_\mu u^\mu\)) equals zero.

**Orthogonal (project with \(h^\sigma{}_\nu\)):** \(h^\sigma{}_\nu\nabla_\mu T^{\mu\nu}=0\).

1. Project the conservation equation:
   \[
   h^\sigma{}_\nu \nabla_\mu T^{\mu\nu} = 0.
   \]
2. Substitute \(T^{\mu\nu}\) and use \(h^\sigma{}_\nu u^\nu =0\). After algebra one obtains the relativistic Euler equation:
   \[
   \boxed{(\rho+p)u^\mu\nabla_\mu u^\sigma + h^{\sigma\nu}\nabla_\nu p = 0.}
   \]
   Interpretation: inertia density \((\rho+p)\) times acceleration = spatial pressure gradient.

**Physical interpretation of the longitudinal equation:** It encodes local energy conservation: the change of energy density measured by comoving observers equals negative of work done by pressure during expansion/compression.

---

### 7) **Weak energy condition (WEC) for perfect fluids**

**Definition:** For all timelike vectors \(t^\mu\), \(T_{\mu\nu} t^\mu t^\nu \ge 0\).

**Apply to perfect fluid:**
\[
T_{\mu\nu}t^\mu t^\nu = (\rho+p)(u_\mu t^\mu)^2 + p (t_\mu t^\mu).
\]
- If we choose \(t^\mu = u^\mu\) (comoving observer), then \(T_{\mu\nu}u^\mu u^\nu = \rho\), so WEC gives \(\rho \ge 0\).
- For all timelike \(t^\mu\) the stronger condition that ensures non-negativity is
  \[
  \boxed{\rho \ge 0\quad\text{and}\quad \rho + p \ge 0.}
  \]
**Interpretation:** energy density measured by any physical observer is non-negative; the second condition prevents negative-energy densities for observers boosted relative to the fluid.

---

### 8) **Energy density of the KG field for an observer with 4-velocity \(u^\mu\)**

Definition: energy density measured by observer \(u^\mu\) is \(\rho_\varphi \equiv T_{\mu\nu}u^\mu u^\nu\).

Compute with scalar \(T_{\mu\nu}\):
\[
\begin{aligned}
\rho_\varphi
&= u^\mu u^\nu \left[\nabla_\mu\varphi\,\nabla_\nu\varphi - \tfrac12 g_{\mu\nu}(\nabla_\alpha\varphi\nabla^\alpha\varphi + m^2\varphi^2)\right] \\
&= (u^\mu\nabla_\mu\varphi)^2 + \tfrac12\big(\nabla_\alpha\varphi\nabla^\alpha\varphi + m^2\varphi^2\big),
\end{aligned}
\]
because \(u^\mu u^\nu g_{\mu\nu} = u_\mu u^\mu = -1\).

**Interpretation:** energy density measured by an observer equals kinetic energy along observer's worldline squared plus half the Lagrangian-density-like combination.

---

# **Exercise 2 — FLRW metric (flat slices)**

Metric:
\[
ds^2 = -dt^2 + a^2(t)\big(dx^2+dy^2+dz^2\big).
\]

---

### 1) **Conformal flatness — find coordinates and conformal factor**

**Goal:** show there exist coordinates \(y^\mu\) with
\[
ds^2 = \Omega^2(\eta,\mathbf x)\,\eta_{\mu\nu}dy^\mu dy^\nu.
\]

**Standard construction:**

1. Define conformal time \(\eta\) by
   \[
   d\eta \equiv \frac{dt}{a(t)} \quad\Longrightarrow\quad dt = a(\eta) d\eta.
   \]
   (This is a coordinate transformation \(t\mapsto\eta\).)

2. Substitute \(dt=a(\eta)\,d\eta\) into the metric:
   \[
   ds^2 = -a^2(\eta)d\eta^2 + a^2(\eta)\,(dx^2+dy^2+dz^2)
        = a^2(\eta)\Big(-d\eta^2 + d\mathbf x^2\Big).
   \]

3. Hence the metric is conformally flat with conformal factor
   \[
   \boxed{\Omega(\eta,\mathbf x)=a(\eta),\quad y^0=\eta,\ y^i = x^i.}
   \]

**First-principles reason:** Multiplying Minkowski metric by a scalar conformal factor preserves the causal light cone structure; writing the FLRW metric as a scale factor times Minkowski shows that FLRW is conformally flat.

---

### 2) **Compute Christoffel component \(\Gamma^0_{ij} = a\dot a\,\delta_{ij}\)**

**Use definition (first principle):**
\[
\Gamma^\sigma_{\mu\nu} = \tfrac12 g^{\sigma\rho}\big(\partial_\mu g_{\nu\rho} + \partial_\nu g_{\mu\rho} - \partial_\rho g_{\mu\nu}\big).
\]

**Steps:**

1. Nonzero metric components: \(g_{00}=-1,\; g_{ij}=a^2(t)\delta_{ij}\). Inverse: \(g^{00}=-1,\; g^{ij} = a^{-2}(t)\delta^{ij}\).

2. For spatial indices \(i,j\), the only time-dependent part is \(g_{ij}\) so \(\partial_0 g_{ij} = \dot g_{ij} = 2 a \dot a\, \delta_{ij}\). Partial derivatives with respect to spatial coordinates vanish because \(a(t)\) depends only on \(t\).

3. Compute \(\Gamma^0_{ij}\):
   \[
   \Gamma^0_{ij} = \tfrac12 g^{00}\big(\partial_i g_{j0} + \partial_j g_{i0} - \partial_0 g_{ij}\big).
   \]
   But \(g_{i0}=0\), so the first two terms vanish. Thus
   \[
   \Gamma^0_{ij} = -\tfrac12 g^{00}\partial_0 g_{ij} = -\tfrac12(-1)\cdot 2a\dot a\,\delta_{ij} = a\dot a\,\delta_{ij}.
   \]

4. So
   \[
   \boxed{\Gamma^0_{ij} = a\dot a\,\delta_{ij}.}
   \]

**Check index positions and symmetry:** \(\Gamma^\sigma_{\mu\nu}=\Gamma^\sigma_{\nu\mu}\) — consistent.

---

### 3) **Photon geodesic: show \(\dfrac{dt}{d\lambda} = \dfrac{\omega_0}{a(t)}\)**

**Given:** null (photon) path \(x^\mu(\lambda)=(t(\lambda),x(\lambda),0,0)\). Also previously derived (from null condition)
\[
\frac{dx}{dt} = \frac{1}{a(t)}.
\]

**Goal:** use geodesic equation's 0th component with affine parameter \(\lambda\).

**Steps:**

1. Null condition in terms of affine parameter:
   \[
   0 = g_{\mu\nu}\frac{dx^\mu}{d\lambda}\frac{dx^\nu}{d\lambda}
     = -\Big(\frac{dt}{d\lambda}\Big)^2 + a^2\Big(\frac{dx}{d\lambda}\Big)^2.
   \]
   So
   \[
   \frac{dx}{d\lambda} = \frac{1}{a}\frac{dt}{d\lambda}.
   \]

2. 0th component of geodesic equation:
   \[
   \frac{d^2 t}{d\lambda^2} + \Gamma^0_{\alpha\beta}\frac{dx^\alpha}{d\lambda}\frac{dx^\beta}{d\lambda} = 0.
   \]
   Only spatial components \(\alpha,\beta=i,j\) contribute since \(\Gamma^0_{00}=0\). Use \(\Gamma^0_{ij}=a\dot a\,\delta_{ij}\):
   \[
   \frac{d^2 t}{d\lambda^2} + a\dot a\,\delta_{ij}\frac{dx^i}{d\lambda}\frac{dx^j}{d\lambda} = 0.
   \]

3. For our path only \(x^1=x\) varies, so
   \[
   \frac{d^2 t}{d\lambda^2} + a\dot a \Big(\frac{dx}{d\lambda}\Big)^2 = 0.
   \]

4. Substitute \(\frac{dx}{d\lambda} = \frac{1}{a}\frac{dt}{d\lambda}\):
   \[
   \frac{d^2 t}{d\lambda^2} + a\dot a \cdot \frac{1}{a^2}\Big(\frac{dt}{d\lambda}\Big)^2
   = \frac{d^2 t}{d\lambda^2} + \frac{\dot a}{a}\Big(\frac{dt}{d\lambda}\Big)^2 = 0.
   \]

5. Let \(y(\lambda)=dt/d\lambda\). ODE:
   \[
   \frac{dy}{d\lambda} + \frac{\dot a}{a} y^2 = 0.
   \]
   Change variable to \(t\): \(\dfrac{dy}{d\lambda} = \dfrac{dy}{dt}\dfrac{dt}{d\lambda} = y \dfrac{dy}{dt}\). Hence
   \[
   y\frac{dy}{dt} + \frac{\dot a}{a} y^2 = 0 \quad\Rightarrow\quad \frac{1}{y}\frac{dy}{dt} + \frac{\dot a}{a} = 0.
   \]
   Integrate in \(t\):
   \[
   \frac{d}{dt}\big(\ln y\big) + \frac{d}{dt}\big(\ln a\big) = 0
   \quad\Rightarrow\quad \frac{d}{dt}\ln(ay)=0.
   \]
   So \(a(t)y(\lambda)=\) constant along geodesic. Denote constant \(\omega_0\):
   \[
   \boxed{\frac{dt}{d\lambda} = \frac{\omega_0}{a(t)}.}
   \]

**Interpretation:** photon's coordinate-time component of 4-momentum redshifts like \(1/a\).

---

### 4) **Photon energy measured by comoving observer**

Photon 4-momentum: \(p^\mu \equiv \dfrac{dx^\mu}{d\lambda}\). Comoving observer 4-velocity \(u^\mu=(1,0,0,0)\) (properly normalized). Energy measured by that observer:
\[
E \equiv - p_\mu u^\mu = -g_{\mu\nu}p^\mu u^\nu.
\]

**Compute:**
- \(u^\nu=(1,0,0,0)\), \(u_\nu = g_{\nu\alpha}u^\alpha = g_{00}u^0 = -1\).
- Thus \(E = - p^0 u_0 = -\frac{dt}{d\lambda}\,(-1) = \frac{dt}{d\lambda}\).

Using result from previous part,
\[
\boxed{E(t) = \frac{\omega_0}{a(t)}.}
\]

**Meaning:** energy (frequency) redshifts as \(1/a(t)\): cosmological redshift.

---

### 5) **Why energy is not conserved**

**First-principles reason:** Global energy conservation requires a global timelike Killing vector (time-translation symmetry). In a general expanding FLRW spacetime, there is no global timelike Killing vector because the metric explicitly depends on time through \(a(t)\). Therefore there is no conserved global energy associated to time translations. Locally, stress-energy is covariantly conserved (\(\nabla_\mu T^{\mu\nu}=0\)), but that does not imply a globally conserved scalar "total energy" in an expanding universe. Physically, photon's energy changes because spacetime geometry evolves (wavelength stretched).

---

### 6) **Energy–momentum tensor matrix for perfect fluid in comoving frame**

Perfect fluid:
\[
T_{\mu\nu} = (\rho+p)u_\mu u_\nu + p g_{\mu\nu}.
\]
Comoving observer \(u^\mu=(1,0,0,0)\Rightarrow u_\mu = (-1,0,0,0)\). Substitute with FLRW metric:

Compute components:
- \(T_{00} = (\rho+p)u_0u_0 + p g_{00} = (\rho+p)(-1)(-1) + p(-1) = \rho.\)
- \(T_{0i} = (\rho+p)u_0u_i + p g_{0i} = 0.\)
- \(T_{ij} = (\rho+p)u_i u_j + p g_{ij} = p\, g_{ij} = p\,a^2(t)\delta_{ij}.\)

Matrix form (\(\mu,\nu\) rows/columns \(=0,1,2,3\)):
\[
\boxed{T_{\mu\nu} =
\begin{pmatrix}
\rho & 0 & 0 & 0 \\
0 & p\,a^2(t) & 0 & 0 \\
0 & 0 & p\,a^2(t) & 0 \\
0 & 0 & 0 & p\,a^2(t)
\end{pmatrix}.}
\]

(If you raise an index: \(T^\mu{}_\nu = \mathrm{diag}(-\rho, p, p, p)\).)

---

### 7) **Evolution of energy density from \(\nabla_\mu T^{\mu\nu}=0\); solve for \(p=w\rho\)**

**Goal:** derive \(\dot\rho + 3\frac{\dot a}{a}(\rho+p) = 0\) and solve for \(p=w\rho\).

**Steps:**

1. Use conservation law in coordinate basis: \(\nabla_\mu T^{\mu 0} = 0\) (take \(\nu=0\)). Because universe is homogeneous and isotropic, \(\rho=\rho(t)\), \(p=p(t)\), and spatial derivatives vanish.

2. Using Christoffel symbols (nonzero relevant ones: \(\Gamma^0_{ij}=a\dot a \delta_{ij}\), \(\Gamma^i_{j0}=(\dot a/a)\delta^i_j\)), perform component calculation (straightforward but mechanical). Alternatively use the fluid projection derived earlier: contract \(\nabla_\mu T^{\mu\nu}=0\) with \(u_\nu\) to get energy equation:
   \[
   u_\nu \nabla_\mu T^{\mu\nu} = 0 \quad\Longrightarrow\quad u^\mu\nabla_\mu \rho + (\rho+p)\nabla_\mu u^\mu = 0.
   \]
   For comoving flow \(u^\mu=(1,0,0,0)\), \(\nabla_\mu u^\mu = 3 \frac{\dot a}{a}\) (expansion scalar in FLRW). Therefore:
   \[
   \boxed{\dot\rho + 3 \frac{\dot a}{a}(\rho + p) = 0.}
   \]

**Solve for equation of state \(p = w \rho\) with constant \(w\):**

1. Substitute \(p=w\rho\):
   \[
   \dot\rho + 3\frac{\dot a}{a}\rho(1+w) = 0.
   \]

2. Separate variables:
   \[
   \frac{d\rho}{\rho} = -3(1+w)\frac{da}{a}.
   \]

3. Integrate:
   \[
   \ln\rho = -3(1+w)\ln a + \mathrm{const} \quad\Longrightarrow\quad
   \boxed{\rho(a) = \rho_0\, a^{-3(1+w)},}
   \]
   where \(\rho_0\) is the integration constant (value at \(a=1\)).

**Examples:** dust \(w=0\Rightarrow \rho\propto a^{-3}\); radiation \(w=\tfrac13\Rightarrow \rho\propto a^{-4}\); cosmological constant \(w=-1\Rightarrow \rho=\text{const}\).

---

### 8) **Why assume \(\varphi(t,\mathbf x)=\varphi(t)\) (homogeneous ansatz)?**

**Reasoning from first principles:**

1. Cosmological principle: on large scales the universe is homogeneous and isotropic; background fields are taken spatially homogeneous. Taking \(\varphi=\varphi(t)\) respects these symmetries.

2. From dynamical viewpoint: expand the scalar field into Fourier modes \(\varphi(t,\mathbf x)=\sum_{\mathbf k}\varphi_{\mathbf k}(t)e^{i\mathbf k\cdot\mathbf x}\). The \(k=0\) (spatially constant) mode evolves independently of the others in a homogeneous background; it represents the background field. For studying background cosmology (energy density driving expansion) we keep the \(k=0\) mode only.

3. Mathematically: if initial data are homogeneous (\(\partial_i\varphi=0\) at some time) and equations and geometry are homogeneous, the solution remains homogeneous.

---

### 9) **Compute \(\rho_\varphi = T_{00}\) and \(p_\varphi = T_{ii}\) (KG field in FLRW, homogeneous)**

Assume \(\varphi=\varphi(t)\) only. Use previously derived
\[
T_{\mu\nu} = \nabla_\mu\varphi\,\nabla_\nu\varphi - \tfrac12 g_{\mu\nu}(\nabla_\alpha\varphi\nabla^\alpha\varphi + m^2\varphi^2).
\]

**Compute kinetic scalar:**
\[
\nabla_\alpha\varphi\nabla^\alpha\varphi = g^{00}\dot\varphi^2 = -\dot\varphi^2.
\]

**Energy density \(T_{00}\):**
\[
\begin{aligned}
T_{00} &= \dot\varphi\dot\varphi - \tfrac12 g_{00}(-\dot\varphi^2 + m^2\varphi^2) \\
       &= \dot\varphi^2 - \tfrac12(-1)(-\dot\varphi^2 + m^2\varphi^2) \\
       &= \dot\varphi^2 + \tfrac12(-\dot\varphi^2 + m^2\varphi^2) \\
       &= \tfrac12\dot\varphi^2 + \tfrac12 m^2\varphi^2.
\end{aligned}
\]
So
\[
\boxed{\rho_\varphi = \tfrac12\dot\varphi^2 + \tfrac12 m^2\varphi^2.}
\]

**Pressure \(p_\varphi\):** compute spatial diagonal components \(T_{ii}\) (no sum):
\[
\begin{aligned}
T_{ii} &= 0 - \tfrac12 g_{ii}(-\dot\varphi^2 + m^2\varphi^2)
= \tfrac12 a^2(t)\delta_{ii}\,(\dot\varphi^2 - m^2\varphi^2).
\end{aligned}
\]
To get pressure, divide by \(g_{ii}=a^2\):
\[
\boxed{p_\varphi = \tfrac12\dot\varphi^2 - \tfrac12 m^2\varphi^2.}
\]

**Equation of state parameter:**
\[
w_\varphi \equiv \frac{p_\varphi}{\rho_\varphi} = \frac{\dot\varphi^2 - m^2\varphi^2}{\dot\varphi^2 + m^2\varphi^2}.
\]

---

### 10) **Why \(\dot\varphi^2 \ll m^2\varphi^2\) gives an effective cosmological constant**

**Assume:** kinetic energy negligible compared to potential energy:
\[
\dot\varphi^2 \ll m^2\varphi^2.
\]

Then approximate:
\[
\rho_\varphi \approx \tfrac12 m^2\varphi^2,\qquad p_\varphi \approx -\tfrac12 m^2\varphi^2.
\]

Thus
\[
p_\varphi \approx - \rho_\varphi \quad\Longrightarrow\quad w_\varphi \approx -1.
\]

**Interpretation (first principles):** A perfect fluid with \(w=-1\) has equation of state identical to a cosmological constant \(\Lambda\) (energy–momentum tensor \(T_{\mu\nu}\propto g_{\mu\nu}\)). Therefore when potential energy dominates, the scalar field behaves like a time-dependent cosmological constant — it produces negative pressure and drives accelerated expansion.

---

## Short recap / final remarks

- The KG equation in curved space follows from the Euler–Lagrange equations applied to the minimally-coupled Lagrangian.  
- The stress tensor is obtained as the functional derivative of the matter action w.r.t. the metric; the determinant variation identity is crucial.  
- Conservation of \(T^{\mu\nu}\) encodes field equations and provides conserved currents when combined with spacetime symmetries (Killing vectors).  
- In FLRW geometry, photon energy redshifts as \(1/a(t)\). Fluid energy evolves as \(\rho\propto a^{-3(1+w)}\).  
- A homogeneous scalar field has \(\rho_\varphi=\tfrac12\dot\varphi^2+\tfrac12 m^2\varphi^2\) and \(p_\varphi=\tfrac12\dot\varphi^2-\tfrac12 m^2\varphi^2\); potential-domination gives \(w\approx-1\).

---

If you want, I can:
- produce a compact single-file LaTeX (PDF) of this solution ready for submission, or
- expand any step even further (e.g. show line-by-line variation of determinant, or explicit componentwise expansion of \(\nabla_\mu T^{\mu 0}=0\) giving the continuity equation),
- or include small worked examples (e.g. solve KG in de Sitter background).

Which would you like next?
