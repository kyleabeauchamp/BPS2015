% title: Benchmarking Small Molecule Forcefields at the Scale of NIST
% author: Kyle A. Beauchamp, Choderalab@MSKCC
% author: Slides here: goo.gl/rKGhzZ
% favicon: figures/membrane.png

---
title: Goal: Predictive atomistic models
subtitle: Proteins, drugs, ions, solvents, membranes

<center>
<img height=460 src=figures/dhfr.png />
</center>


---
title: Molecular dynamics is (finally) fast
subtitle: A \$999 GPU buys 128 ns / day on solvated proteins

<center>
<img height=420 src=figures/TitanNew.jpg />
</center>

<footer class="source"> 
GTX Titan, DHFR, OpenMM 6.1 (openmm.org) See also: Gromacs, AMBER, Charmm, NAMD, DESMOND, ACEMD
</footer>


---
title: Forcefields: Are we there yet?
subtitle: Water and protein: getting better


<center>
<img height=425 src=figures/plos_forcefield.png />
</center>

<footer class="source"> 
Lindorff-Larsen, PLOS One, 2012.  See also Beauchamp, JCTC, 2012.
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
<img height=350 src=figures/qc_supply_grinder_510482.jpg />
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
<img height=540 src="https://docs.google.com/drawings/d/1At1SJcpKbbe28izMj3S4bodHuXtNe4dXiJpBX7Y_QkE/pub?w=1440&h=1080"/>
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

<center>
<img height=450 src=figures/funnel.png />
</center>

---
title: Benchmarking neat liquid densities and dielectric constants

- OpenMM 6.2
- GAFF + AM1-BCC (Antechamber + OpenEye)
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

---
title: Inverse dielectric constant is proportional to interaction strength

$$U(r) = \frac{1}{4 \pi \epsilon} \frac{q_1 q_2}{r} \propto \frac{1}{\epsilon}$$

---
title:  Static dielectric constants are consistently underestimated

<center>
<img height=450 src=figures/dielectrics_thermoml_nocorr.png />
</center>


---
title: Atom counting predicts molecular polarizability to within 2%

<center>
<img height=100 src=figures/sales_title.png />
</center>


<center>
<img height=230 src=figures/polarizability_eqn.png />
</center>

---
title: Empirical atomic polarizability corrections reduce bias

<center>
<img height=450 src=figures/dielectrics_thermoml.png />
</center>

---
title: Where do we go from here?

- Small molecule forcefields need help
- ThermoML is a NIST-supported, machine-readable, and growing set of physicochemical data
- We built a semi-automated benchmark of densities and dielectric constants in ThermoML
- Empirical polarizability model improves comparisons to measured dielectric constants
- Can we validate forcefields in real-time on all publication quality measurements?

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


---
title:  Results do not depend on forcefield and benchmark set

<center>
<img height=330 src=figures/dielectrics_virtual_chemistry_gaff_nocoff.png />
<img height=330 src=figures/dielectrics_virtual_chemistry_opls_nocoff.png />
</center>

<footer class="source"> 
Using data from virtualchemistry.org <br>
van der Spoel, JCTC, 2011 and van der Spoel, Bioinformatics, 2012
</footer>
