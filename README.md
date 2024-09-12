This repository contains Python code to calculate C6 and C8 parameters of dispersion force from Maximally Localized Wannier Functions (MLWFs) obtained from Ab-initio MD (AIMD) according to the theory developed by Silvestrelli (https://doi.org/10.1103/PhysRevLett.100.053002). To run the calculation, MLW centers and their spreads have to calculated from AIMD. In CP2K this can be done by the following lines of commands:
```
&LOCALIZE
     METHOD JACOBI
     EPS_LOCALIZATION 1.0E-8
     MAX_ITER 2000
       &WANNIER_CENTERS
            IONS+CENTERS
            FILENAME =water_wannier.xyz
            &EACH
               MD 1
            &END EACH
       &END WANNIER_CENTERS
       &WANNIER_SPREADS
          &EACH
            MD 1
          &END EACH
          FILENAME ./wannier-spreads
          COMMON_ITERATION_LEVELS               3
        &END WANNIER_SPREADS
     &END PRINT
  &END LOCALIZE
```
The repository contains the following files:
1. test.zip - file containing example input files to run the code. Note that the wannier centers and spreads have to be sorted according to the atoms before running the code
2. Wan_2_disp.ipynb - Python code to calculate C6, C8 parameters from MLW centers and spreads
