# SyntheticSamplesWithDVGs

Collection of simulated fastq samples for the evaluation of the program DVGfinder. The code of the program is in https://github.com/MJmaolu/DVGfinder.


## Composition files

Each composition file contains the DVG population that conforms the sample. 

Each one of the DVG are identified by its ID (cID_DI). Also, the Breakpoint (BP), Reinitation site (RI) and sense of the fragments pre and post BP-RI junction are specified. 

The type of defective is more clearly defined in the 'DVG_type' column and the ratio of the genome in the sample ('proportion') and the total length of the defective ('length_dvg') are also inficated.


## Simulated fastq files

There are in total 24 fastq samples, 12 generated on SARS-CoV-2 genome and the other 12 in Turnip Mosaic Virus. The ratio of the DVG population in the sample is 0.6 and the remaining 0.4 is composed of the reference virus.

The exact composition is defined in the correspondent composition files and the fastqs are avalaible at [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.6411689.svg)](https://doi.org/10.5281/zenodo.6411689).

The simulated reads where generated using Wgsim (short read simulator) <https://github.com/lh3/wgsim> with the error/mutation parameters set to zero and a length read of 100 nts. The library sizes are: 100 K, 500 K, 1 M, 2 M, 3 M, 4 M, 5 M, 6 M, 7 M, 8 M, 9 M and 10 M reads.

# Evaluation of the synthetic datasets

DVGfinder was executed in all the samples. The results obtained by each program (ViReMa-a and DI-tector) and by each run mode (Metasearch, Consensus and Filtered) were separately assesed. The results of the evaluation for each genome (SARS-CoV-2 or TuMV based), each program/mode and each depth (from 100K to 10M reads) are available in the [evaluation directory](/evaluations).

In a first evaluation we labeled as TP the events detected which junction coordinates matched exactly with the ones introduced in the synthetic datasets. This label i

---
### Contact

María José Olmo-Uceda - mariajose.olmo@csic.es

PhD student

*EvolSysVir Group*, I<sup>2</sup>SysBio (CSIC-UV) 

---
Project Link: [https://github.com/MJmaolu/DVGfinder](https://github.com/MJmaolu/DVGfinder)

Page Link: [https://mjmaolu.github.io/DVGfinder/](https://mjmaolu.github.io/DVGfinder/)
