% title: Benchmarking Small Molecule Forcefields at the Scale of NIST
% author: Kyle A. Beauchamp, Choderalab@MSKCC
% author: Slides here: TODO
% favicon: figures/membrane.png

---
title: GPUs: MD Sampling is (finally) Easy

<center>
<img height=475 src=figures/TitanNew.jpg />
</center>

<footer class="source"> 
E.g. OpenMM, Gromacs, AMBER, Charmm, NAMD, DESMOND, ACEMD
</footer>


---
title: Forcefields: Are we there yet?
subtitle: Water and protein: getting better


<center>
<img height=425 src=figures/plos_forcefield.png />
</center>

<footer class="source"> 
Lindorff-Larsen, 2012
</footer>

---
title: Forcefields: Are we there yet?
subtitle: Small molecules: needs work


<center>
<img height=450 src=figures/mobley_dielectric.png />
</center>

<footer class="source"> 
Fennell, Mobley, 2014
</footer>


---
title: What's holding us back?  Data access

- Forcefields should be consistent with available data
- Datasets (and forcefields) should improve over time
- Many datasets are heterogeneous and offline

<center>
<img height=300 src=figures/meat-grinder-gun.jpg />
</center>

<footer class="source"> 
See also work by Wang, Pande, Swope, Case, MacKerell, Ponder, Best, Hummer, Bruschweiler.
</footer>


---
title: WANTED: Curated, Machine-Readible, Open archive of physicochemical measurements!
class: segue dark nobackground


---
title: NIST Thermodynamics Research Center

<center>
<img height=500 src=figures/boulder3.jpg />
</center>


---
title: Data Capture at NIST TRC: ThermoML


<center>
<img height=525 src="https://docs.google.com/drawings/d/1At1SJcpKbbe28izMj3S4bodHuXtNe4dXiJpBX7Y_QkE/pub?w=1440&h=1080"/>
</center>

<footer class="source"> 
J. Chem. Eng. Dat., J. Chem. Therm., Fluid Phase Eq., Therm. Acta, Int. J. Therm.
</footer>

---
title: ThermoML: Rapid Growth

<center>
<img height=475 src=figures/thermoml_by_time.png />
</center>

<footer class="source"> 
Chiraco, 2013
</footer>


---
title: Can we leverage ThermoML for forcefield validation?
class: segue dark nobackground

---
title: How many measurements?
subtitle: Neat Liquids?

- 130074 Densities
- 1649 Dielectrics


---
title: How many measurements?
subtitle: Druglike elements?

- 120410 Densities
- 1649 Dielectrics


---
title: How many measurements?
subtitle: Ten or fewer heavy atoms?

- 67897 Densities
- 1567 Dielectrics

---
title: How many measurements?
subtitle: Ambient temperature and pressure?

- 13598 Densities
- 461 Dielectrics

---
title: How many measurements?
subtitle: After averaging over duplicated measurements

- 3591 Densities
- 432 Dielectrics

---
title: How many measurements?
subtitle: Having both density and dielectric measurements

- 245


---
title: Benchmarking 245 densities and dielectrics

- OpenMM 6.2
- GAFF
- Converge each density to 0.0002 g / mL


<center>
<img height=300 src=figures/openmm.png />
</center>


---
title:  Static Dielectrics: Underestimated

<center>
<img height=500 src=figures/./dielectrics_thermoml_nocorr.png />
</center>

---
title: GAFF fails for nonpolar dielectrics
subtitle: Missing atomic polarizibilities

Expt: 2.2
GAFF: 1.0

<center>
<img height=400 src=figures/Carbon-tetrachloride-3D-balls.png />
</center>

<footer class="source"> 
Fennell, 2012
</footer>


---
title: Polarizability Corrections

Counting atoms explains molecular polarizability to within 2%

<center>
<img height=225 src=figures/polarizability_eqn.png />
</center>

<footer class="source"> 
Sales, 2012.  J. Chem. Inf. Comp. Sci.
</footer>

Predicts a correction of 0.52 for water; compare to 0.79, which was used in developing TIP4P-EW.

---
title: Static Dielectrics with Polarizibility

<center>
<img height=525 src=figures/dielectrics_thermoml.png />
</center>

---
title: Conclusions

- Small molecule forcefields need help
- ThermoML is a NIST-funded, curated, and growing set of physicochem data
- We built a semi-automated benchmark of densities and dielectrics in ThermoML
- Elemental polarizability models improves comparisons to measured dielectric constants
- Can we validate forcefields in real-time on all publication quality measurements?

---
title: People

- Julie Behr (MSKCC)
- Patrick Grinaway (MSKCC)
- Bas Rustenburg (MSKCC)
- John Chodera (MSKCC)
- Michael Shirts (UVA)
- Kenneth Kroenlein (NIST)


<footer class="source"> 
Special thanks to Vijay Pande, Lee-Ping Wang, Peter Eastman, Robert McGibbon, Jason Swails, David Mobley, Christopher Bayly, and members of Chodera lab. \n 
See also work by van der Spoel, JCTC, 2011. and Bioinformatics, 2012.
</footer>
