# hydrogendimers
Repository for hydrogen collision-induced absorption spectra.

This github repository contains calculated hydrogen dimer absorption coefficients based on the paper:
Fletcher, Gustaffson and Orton (2017), Hydrogen dimers in giant-planet infrared spectra, submitted to ApJ.

**Abstract:

Despite being one of the weakest dimers in nature, the (H2)2 dimer had been identified in low-spectral-resolution 
Voyager/IRIS observations of Jupiter and Saturn.  However, collision-induced H2-H2 opacity databases have only included 
free-to-free transitions and have not previously incorporated dimer contributions, which have both fine-scale structure 
near the S(0) and S(1) quadrupole lines (354 and 587 cm-1, respectively), and broad continuum contributions 
up to ±50 cm-1 from the line centres.  We develop a new ab initio model for the free-to-bound, bound-to-free and 
bound-to-bound transitions of the hydrogen dimer for a range of temperatures (40-400 K) and para-hydrogen fractions 
(0.2-1.0).  The model is validated against low-temperature laboratory experiments, and used to simulate the spectra of 
the giant planets.  The model reproduces the dimer signatures observed in Voyager/IRIS data near S(0), and generally lowers 
the amount of para-H2 (and the extent of disequilibrium) required to reproduce IRIS observations.  The new dimer database 
permits the first high-resolution (0.5-1.0 cm-1) spectral modelling of dimer spectra near S(0) and S(1) in both Cassini 
Composite Infrared Spectrometer (CIRS) observations of Jupiter and Saturn, and in Spitzer Infrared Spectrometer (IRS) 
observations of Uranus and Neptune for the first time. 

**Contents of this repository:

The CIA database must be assembled from a series of seperately calculated components:  the free-free transitions (replacing those previously provided by Borysow et al. 1985 and Orton et al. 2007), the free-bound and bound-free transitions, and the bound-bound transitions.  For ease of calculation, the dimeric transitions are subdivided into the rotational Q spectrum, those transitions near S(0) and those near S(1).  An adaptive frequency grid is used to capture any high-resolution structure.

Calculations were performed on the following temperature grid:
temp = [40.00000  ,51.66200  ,66.72400  ,86.17700  ,111.3020   ,143.7530   ,185.6640   ,239.7940   ,309.7050   ,400.0000]
   
...and the following para-hydrogen fraction grid:
fpmagnus=[0.25,0.30,0.35,0.41,0.47,0.54,0.62,0.70,0.80,0.90,1.0]

These are then interpolated onto the temperature, para-hydrogen and wavenumber grid required by our radiative transfer model.  

**Step 1:  Free-Free (ff)

The free-free transitions were calculated over the full range from 0.1-2400 cm-1.  Each para-H2 fraction has a seperate file, containing NTEMP=10 arrays of 3xNWAVE (where NWAVE=223), where column 1 is the temperature, column 2 is the wavenumber, and column 3 is the absorption coefficient (cm-1 amagat-2).

**Step 2:  Free-bound and bound-free (fbbf)

The files have the same format as in step one, but are calculated on a different frequency grid and over a different spectral range to capture high-resolution structure.  The three regions are:

- Qband:  1.0-100 cm-1 in NWAVE=34 steps
- S0:  254.39-454.39 cm-1 in NWAVE=68 steps
- S1:  487.04-687.04 cm-1 in NWAVE=68 steps

Depending on the intended use, these additional files should be interpolated onto the same grid as the smoother free-free transitions.

**Step 3:  Bound-bound (bb)

The final files have the same format as in step 1, and span 0.0-594.0 cm-1 in NWAVE=2503 steps (note that the grid is not uniform).  Note that the bb transitions could not be validated against the measured giant planet spectra, but do reproduce laboratory measurements.

**Summary

The three types of transitions have the same temperature and para-hydrogen grids, but different wavenumber grids to make the quantum mechanical calculations more efficient.  For the paper, these were combined into uniformly-sampled wavenumber grids with different step sizes depending on the instrument spectral resolution.  The non-interpolated absorption coefficients are provided here so that they can be adapted as appropriate to new instrument characteristics.

Please address queries to leigh.fletcher@le.ac.uk.
L.N. Fletcher (2017)




