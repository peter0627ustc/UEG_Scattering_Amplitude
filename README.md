# UEG Scattering Amplitude

This repository contains scattering-amplitude data for the three-dimensional
uniform electron gas (UEG).

The CSV files in `data/` provide the same angular grid and last-order VDMC
amplitudes reorganized from `spec_2_para.jl`.

## Data Layout

Each file has four columns:

```text
theta_over_pi,phi_over_pi,data,error
```

- `theta_over_pi`: scattering angle `theta / pi`
- `phi_over_pi`: azimuthal angle `phi / pi`
- `data`: last-order amplitude value
- `error`: uncertainty estimated as

```math
\sigma = \sqrt{\sigma_{\mathrm{MC}}^2 + (A_{o=4} - A_{o=3})^2}.
```

For each density parameter `rs = 1, 2, 3, 4, 5`, the files are:

```text
spec_2_para_Auu_rs*.csv
spec_2_para_Aud_rs*.csv
```

Here `Auu` and `Aud` correspond to the same-spin and opposite-spin scattering
amplitudes used as `Wuu` and `Wud` in `spec_2_para.jl`.

## Lifetime Formula

Following `spec_2_para.jl`, the spin-summed squared scattering amplitude is

```math
W(\theta,\phi)
= \frac{1}{4} A_{uu}(\theta,\phi)^2
+ \frac{1}{2} A_{ud}(\theta,\phi)^2 .
```

The angular integral used for the quasiparticle lifetime is

```math
I_\tau
= \frac{1}{2\pi}
\int_0^\pi d\theta
\int_0^\pi d\phi\,
\frac{W(\theta,\phi)}{\cos(\theta/2)}\sin\theta .
```

On the tabulated grid, `spec_2_para.jl` evaluates this integral with the
trapezoidal-cell average over neighboring grid points.

The Fermi-liquid lifetime coefficient is then

```math
\frac{\tau^{-1}}{T^2}
= I_\tau\,
\frac{m_e \pi^3}{8\hbar p_F^2}
k_B^2\, m^\ast ,
```

where `m*` is the dimensionless effective mass used in the Julia script, and
`p_F = k_F \hbar / a_0`.
