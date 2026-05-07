# CD13
Conformational entropies for 13 clinical drug molecules retrieved from the CD25 dataset of Pracht and Grimme

### Description of the data:
1. Folder ```Uniconf``` contains the Uniconf input files to perform systematic sampling of 13 species taken from CD25 dataset (CD13 species thereafter)
2. Folder ```Systematic``` contains the data obtained for the systematic confomational sampling of CD13 species: 
- With systematic sampling we imply geometry optimization/calculation of harmonic frequencies of every Uniconf generated structure followed by the duplicate removal procedure (https://github.com/QuantumChemistryGroup/molcomp). 
- GFN1 in the name of archive stands for sampling at GFN1-xTB level, GFN2 stands for the GFN2-xTB sampling, QM3 stands for the QM3 sampling, B97-3c stands for the B97-3c (DFT) sampling. Each archive is already cleaned from duplicates.
- Each archive can be downloaded and uncompressed. The resulting folder contains: 
  - Cartesian coordinates of all optimized with semiempirical method conformers, e.g. ```m1_00_Celecoxib-GFN1_01.xyz```. First line of each ```*.xyz``` file contains number of atoms, second line contains the semiempirical method energy. All files are numbered in ascending order according to their semiempirical method energies.
  - Thermochemistry-needed data of each structure obtained with semiempirical method, e.g. ```m1_00_Celecoxib-GFN1_01.dat```. This file can be used as an input for the thermochemistry program located in folder (```Scripts```). Thermochemical corrections for a particular ```*dat``` file can be obtained via ```python3 /path/to/thermochemistry/thermochemistry_mmRRHO.py m1_00_Celecoxib-GFN1_01.dat GR_25_4_1```. This will generate corresponding ```*.td``` file ```m1_00_Celecoxib-GFN1_01.td```. More on our thermochemistry program can be read here: https://github.com/QuantumChemistryGroup/thermochemistry
  - file ```SI_S.txt``` contains the data in the following format ```298.15    GR_25_4_1 m1_00_Celecoxib-GFN1_01.xyz  0.19    14 173.45  -0.14   4.12 177.43```. ```298.15```- is Temperature in K, ```GR_25_4_1``` - thermochemistry protocol, i.e. nsRRHO(t=25), ```m1_00_Celecoxib-GFN1_01.xyz``` - filename of the most dG stable according to specific thermochemistry protocol structure, ```0.19``` - Boltzmann weight, ```14``` - number of conformers Nconf, ```173.45``` - entropy of the most stable structure according to SE method, ```-0.14``` - entropy correction stemming from Boltzmann averaging', ```4.12``` - Gibbs-Shannon entropy, ```177.43``` - the sum of entropy of the most stable structure, Boltzmann averaging correction and Gibbs-Shannon entropy.
  - file ```SI_H.txt``` contains similar data for enthalpic correction
  - files ```SI_S.txt``` and ```SI_H.txt``` can be obtained as follows. Download both scripts (```ensemble_B97-3C.py``` and ```thermochemistry_mmRRHO.py```) to any folder on your Linux PC. Then run: ```python3 /path/to/scripts/ensemble_B97-3C.py 298.15``` in the folder with ```*.xyz``` and ```*.dat``` files.
  - files with ```B97-3C-TZ``` name in it. These are DFT refined structures with corresponding energies & dat files.
  
3. Folder ```Scripts``` contains a few scripts to perform the Boltzmann averaging as well as conformational entropy calculation
4. Folder ```CREST``` contains data obtained with the CREST meta-dynamic sampling. Each compound & method specific folder contains:
- The most dE stable CREST predicted conformer that was subjected to B97-3c refinement. ```m1_00_Celecoxib_best-B97-3C-TZ.xyz``` Contains Cartesian coordinates of the DFT optimized geometry and energy. ```m1_00_Celecoxib_best-B97-3C-TZ.dat``` contains thermochemistry-related data. ```m1_00_Celecoxib_best-B97-3C-TZ.H``` - CREST H(T)-H(0) correction. ```m1_00_Celecoxib_best-B97-3C-TZ.S``` - contains two contirubutions to Sconf: first stemming from the Boltzmann averaging and second from Gibbs-Shannon entropy as predicted by CREST.

For any inquiries do not hesitate to contact us: Yury.Minenkov'at'gmail.com or Yury.Minenkov'at'chph.ras.ru 
