% title: Benchmarking Small Molecule Forcefields at the Scale of NIST
% author: Kyle A. Beauchamp, Choderalab@MSKCC
% author: Slides here: goo.gl/rKGhzZ
% favicon: figures/membrane.png


---
title: Forcefields: Are we there yet?
subtitle: Water and protein: getting better


<center>
<img height=425 src=figures/plos_forcefield.png />
</center>

<footer class="source"> 
Lindorff-Larsen, PLOS One, 2012.  
</footer>

---
title: Small molecule forcefields need work

<center>
<img height=500 src=figures/mobley_dielectric.png />
</center>

<footer class="source"> 
Fennell, Mobley.  J. Phys. Chem. B. 2014
</footer>


---
title: Data access is killing forcefields

- Forcefields should be consistent with all available data
- Most datasets are heterogeneous, offline, and static

<center>
<img height=325 src=figures/qc_supply_grinder_510482.jpg />
<img height=300 src=figures/stack-of-old-books.jpg />
</center>

<footer class="source"> 
See also work by Wang, Pande, Swope, Case, MacKerell, Ponder, Best, Hummer, Bruschweiler.
</footer>


---
title: WANTED: Reliable, machine-readable, open archive of physicochemical measurements!
class: segue dark nobackground


---
title: NIST Thermodynamics Research Center

<center>
<img height=500 src=figures/boulder3.jpg />
</center>


---
title: Data Capture at NIST/TRC: ThermoML


<center>
<img height=540 src="figures/pipeline.png"/>
</center>

---
title: ThermoML is rapidly growing

<center>
<img height=475 src=figures/thermoml_by_time_new.png />
</center>

<footer class="source"> 
Figure from Chiraco, J. Chem. Eng. Dat., 2013.
</footer>


---
title: Can we leverage ThermoML for forcefield validation?
class: segue dark nobackground

---
title: Density and dielectric constants as forcefield tests

- Sensitive to nonbonded parameters
- Simple ensemble average geometric interpretation

$$\rho = \langle \frac{M}{V} \rangle$$

$$\epsilon = 1 + \frac{4\pi}{3} \frac{\langle \mu \cdot \mu \rangle - \langle \mu \rangle \cdot \langle \mu \rangle}{V k_B T}$$

<footer class="source"> 
See also van der Spoel, JCTC, 2011 and Fennell, 2012.
</footer>


---
title: How many measurements are there?
subtitle: Munging the ThermoML with pyxb and pandas

<center>
<img height=450 src=figures/funnel.png />
</center>

---
title: Benchmarking neat liquid densities and dielectric constants

- OpenMM 6.3
- GAFF / AM1-BCC (Antechamber + OpenEye)
- Converge each density to 0.0002 g / mL ($\approx$ expt. error)


<center>
<img height=200 src=figures/openmm.png />
</center>

<footer class="source"> 
PME + Langevin 1 fs + Monte Carlo Barostat + Fixed HBond Constraints + 1000 molecules per box
</footer>


---
title:  Densities are in the ballpark

<center>
<img height=500 src=figures/densities_thermoml.png />
</center>


<footer class="source"> 
Beauchamp et al, In Preparation.
</footer>

---
title:  Static dielectric constants are consistently underestimated

<center>
<img height=450 src=figures/dielectrics_thermoml_nocorr_logscale.png />
</center>

<footer class="source"> 
Beauchamp et al, In Preparation.
</footer>

---
title: Fixed charges fail to capture polarizability
subtitle: Observed: $\epsilon \approx 2.2$, Predicted: $\epsilon \approx 1.001$, $\Delta \Delta G_{solv} \approx$ 2 kcal / mol

<center>
<img height=400 src=figures/nonpolar_molecules.png />
</center>

---
title: Atom counting predicts molecular polarizability to within 2%

<center>
<img height=100 src=figures/sales_title.png />
</center>

$$\alpha = 1.53 n_C + 0.17 n_H + 0.57 n_O + 1.05 n_N + 2.99 n_S + \\ 2.48 n_P + 0.22 n_F + 2.16 n_{Cl} + 0.32 $$

$$\epsilon_{corrected} = \epsilon_{MD} + 4 \pi N  \frac{\alpha}{\langle V \rangle}$$


<footer class="source"> 
Sales, 2002
</footer>

---
title: Empirical atomic polarizability corrections reduce bias

<center>
<img height=450 src=figures/dielectrics_thermoml_logscale.png />
</center>

<footer class="source"> 
Beauchamp et al, In Preparation.
</footer>

---
title: Continuous integration of forcefields
subtitle: Live update stream now available at trc.nist.gov/RSS/


<center>
<img height=400 src=figures/xml_snapshot.png />
</center>

<footer class="source"> 
https://github.com/choderalab/ThermoPyL
<span style="display:inline-block; width: 15px;"></span>
https://github.com/choderalab/LiquidBenchmark
</footer>


---
title: Where do we go from here?

- Scale up, real-time simulation, web frontend
- Perform new experiments in automated wetlab
- Bayesian (MCMC) forcefield / experimental design
- Polarizable forcefields

<center>
<img height=250 src=figures/robot_image.jpg />
</center>


---
title: Conclusions

- Small molecule forcefields need help
- ThermoML is a NIST-supported, machine-readable, and growing set of physicochemical data
- We built a semi-automated benchmark of densities and dielectric constants in ThermoML
- Empirical polarizability model improves comparisons to measured dielectric constants


<footer class="source"> 
https://github.com/choderalab/ThermoPyL
<span style="display:inline-block; width: 15px;"></span>
https://github.com/choderalab/LiquidBenchmark
</footer>

---
title: Funding and Acknowledgments

<center>
<img height=100 src=logos/HaXZqYeq.png />
</center>

- Julie Behr (MSKCC)
- Patrick Grinaway (MSKCC)
- Bas Rustenburg (MSKCC)
- John Chodera (MSKCC)
- Kenneth Kroenlein (NIST)

<footer class="source"> 
Also Vijay Pande, Lee-Ping Wang, Peter Eastman, Robert McGibbon, Jason Swails, David Mobley, Christopher Bayly, Michael Shirts, and the Chodera lab. 
</footer>
