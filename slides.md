% title: Benchmarking Small Molecule Forcefields at the Scale of NIST
% author: Kyle A. Beauchamp, Choderalab@MSKCC
% author: Slides here: goo.gl/u1l4Jy
% favicon: figures/membrane.png

---
title: GPUs: MD Sampling is (finally) Easy
subtitle: 128 ns / day on a $999 GTX Titan (DHFR, OpenMM 6.1)

<center>
<img height=420 src=figures/TitanNew.jpg />
</center>

<footer class="source"> 
Benchmarks at openmm.org See also: Gromacs, AMBER, Charmm, NAMD, DESMOND, ACEMD
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
Fennell, Mobley, 2014
</footer>


---
title: Data access is hamstringing simulation

- Forcefields should be consistent with all available data
- Most datasets are heterogeneous, offline, and static

<center>
<img height=350 src=figures/qc_supply_grinder_510482.jpg />
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
<img height=540 src="https://docs.google.com/drawings/d/1At1SJcpKbbe28izMj3S4bodHuXtNe4dXiJpBX7Y_QkE/pub?w=1440&h=1080"/>
</center>

---
title: ThermoML is rapidly growing

<center>
<img height=475 src=figures/thermoml_by_time.png />
</center>

<footer class="source"> 
Figure from Chiraco, J. Chem. Eng. Dat., 2013.
</footer>


---
title: Can we leverage ThermoML for forcefield validation?
class: segue dark nobackground

---
title: Density and dielectric as forcefield probes

$$\rho = \langle \frac{M}{V} \rangle$$

$$\epsilon(0) = 1 + \frac{4\pi}{3} \frac{\langle M \cdot M \rangle - \langle M \rangle \cdot \langle M \rangle}{V k_B T}$$

<footer class="source"> 
See also van der Spoel, JCTC, 2011 and Fennell, 2012.
</footer>


---
title: How many measurements?

<center>
<img height=450 src=figures/funnel.png />
</center>

---
title: Benchmarking 245 densities and dielectrics

- OpenMM 6.2
- GAFF + AM1BCC (Antechamber + OpenEye)
- PME + Langevin 1 fs + Monte Carlo Barostat + Fixed HBond
- Converge each density to 0.0002 g / mL ($\approx$ expt. error)


<center>
<img height=200 src=figures/openmm.png />
</center>

---
title:  Densities are in the ballpark

<center>
<img height=500 src=figures/densities_thermoml.png />
</center>



---
title:  Density errors vary by functional group 

<center>
<img height=475 src=./figures/functional_group_logerr_density.png />
</center>

<footer class="source"> 
Compare to OW discussion in Fennell, Mobley, 2014
</footer>

---
title:  Static dielectrics are consistently underestimated

<center>
<img height=450 src=figures/dielectrics_thermoml_nocorr.png />
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

Predicts a correction of 0.52 for water dielectric; compare to 0.79, which was used in developing TIP4P-EW.

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
Special thanks to Vijay Pande, Lee-Ping Wang, Peter Eastman, Robert McGibbon, Jason Swails, David Mobley, Christopher Bayly, and members of Chodera lab. 

See also work by van der Spoel, JCTC, 2011. and Bioinformatics, 2012.
</footer>
