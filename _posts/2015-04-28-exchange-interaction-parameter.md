---
layout: default
title: Exchange Interaction Parameters 
---

#Calculation of Exchange Interaction Parameter from Multiple Scattering Theory (MST)

In this snippet I am going to summarize the calculation of one-site rotation and pair-site rotation parameters $$$J_0$$$ and $$$J_{ij}$$$, presuming the knowledge of physical meaning related with scattering matrixes.


##First variation of total energy 

In the limit of small perturbations from ground state, the variation of total energy is 
$$
\delta E = - \int^{\varepsilon_F} d\varepsilon~ \delta N(\varepsilon),
$$
where the integration is over complex energy domain for the reasion described below, and $$$\delta N(\varepsilon)$$$ stands for the change of number of states degenerated with energy $$$\varepsilon$$$. This can be evaluated by implementing Lloyd's formula:
$$
N(\varepsilon) = N_0(\varepsilon) +\frac{1}{\pi} \text{Im}~\text{Tr}_L \ln{\hat{T}(\varepsilon)}, 
$$
where $$$ \hat{T}(\varepsilon)$$$ is **Scattering Path Operator**. 


For a perturbed state, the new Scattering Path Matrix is defined as 
$$
\hat{T}' = \hat{T} (1+\delta\hat{t}^{-1}\cdot\hat{T})^{-1},
$$
where $$$\hat{t}$$$ is **Single Site Scattering Operator** and 
$$$
\delta\hat{t}_i^{-1}=\hat{t}'^{-1}-\hat{t}^{-1}
$$$
for each site. $$$\hat{t}$$$ and $$$\hat{T}$$$ are evaluated at ground state energy in these formulae.

Since 
$$
\ln{\hat{T}'}-\ln{\hat{T}}=-\ln(1+\delta\hat{t}^{-1}\cdot\hat{T}),
$$
The first variation of total energy is 
$$
\delta E = \frac{1}{\pi} \int^{\varepsilon_F} d\varepsilon \text{Im}~ \text{Tr}\ln(1+\delta\hat{t}^{-1}\cdot\hat{T})
$$


The $$$t$$$-operator can be expressed explicitly in spin representation as 
$$
\hat{t}_i=\frac{1}{2}(\hat{t}\_{i\uparrow}+\hat{t}\_{i\downarrow})+\frac{1}{2}\Delta_i(\delta\mathbf{e}\_i\cdot \mathbf{\hat{\sigma}})
$$
where $$$\hat{\sigma}$$$ is the Pauli matrix vector and $$$\Delta_i = \hat{t}\_{i\uparrow}-\hat{t}\_{i\downarrow}$$$.


## One-Site Rotation
First we consider the rotation of a spin along $$$y$$$ axis at site 0:
$$
\delta \mathbf{e}_0 = (\sin\theta, 0, \cos\theta-1)
$$

In ground ferromagnetic state we have 
$$
\hat{T}^{00} = diag (\hat{T}\_{\uparrow}^{00}, \hat{T}\_{\downarrow}^{00})
$$


The result is 
$$
J_0 = \frac{1}{\pi} \int^{\varepsilon_F} d\varepsilon \text{Im} \text{Tr}[\Delta_0 T_{00} + \Delta\_0 T\_{00} ^\uparrow \Delta\_0 T\_{00} ^\downarrow]
$$

## Two-Site Rotation
Next we consider the rotation of two spins along $$$y$$$ axis on opposite directions:
$$
\delta \mathbf{e}\_{i(j)}= (\pm\sin\theta/2, 0, \cos\theta/2-1)
$$

The final result is 
$$
J_{ij} = \frac{1}{\pi} \int^{\varepsilon} d\varepsilon \text{Im}~\text{Tr}[\Delta\_i\hat{T}^{ij}\_{\uparrow} \Delta\_j \hat{T}^{ji}\_{\downarrow}]
$$














