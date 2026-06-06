# UEG Scattering Amplitude

This repository contains scattering-amplitude data for the three-dimensional
uniform electron gas (UEG).

The CSV files in `data/` provide Fermi-surface scattering amplitudes computed
using fifth-order Variational Diagrammatic Monte Carlo (VDMC).

## Data Layout

Each file has four columns:

```text
theta_over_pi,phi_over_pi,data,error
```

- `theta_over_pi`: scattering angle `theta / pi`
- `phi_over_pi`: azimuthal angle `phi / pi`
- `data`: fifth-order VDMC amplitude value
- `error`: estimated uncertainty of the amplitude

For each density parameter `rs = 1, 2, 3, 4, 5`, the files are:

```text
Auu_rs*.csv
Aud_rs*.csv
```

Here `Auu` and `Aud` correspond to the same-spin and opposite-spin scattering
amplitudes.

## Lifetime Formula

The spin-summed squared scattering amplitude entering the Fermi-liquid
lifetime is

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

On the tabulated grid, this integral can be evaluated with the trapezoidal-cell
average over neighboring grid points.

The Fermi-liquid lifetime coefficient is then

```math
\frac{\tau^{-1}}{T^2}
= I_\tau\,
\frac{m_e \pi^3}{8\hbar p_F^2}
k_B^2\, m^\ast ,
```

where `m*` is the dimensionless effective mass and
`p_F = k_F \hbar / a_0`.

## Citation

If you use these data, please cite:

Zhiyi Li, Pengcheng Hou, Bao-Zong Wang, Youjin Deng, and Kun Chen,
"Two-Electron Correlations in the Metallic Electron Gas",
arXiv:2511.22927 (2025).

https://arxiv.org/abs/2511.22927
