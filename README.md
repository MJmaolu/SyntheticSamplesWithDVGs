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

DVGfinder was executed in all the samples. The results obtained by each program (ViReMa-a and DI-tector) and by each run mode (Metasearch, Consensus and Filtered) were separately assesed. The results of the evaluation for each genome (SARS-CoV-2 or TuMV based), each program/mode and each depth (from 100K to 10M reads) are available in the [evaluations directory](/evaluationSD).

## Criteria to label as TP

1. In a first evaluation we labeled as TP the events detected which junction coordinates matched exactly with the ones introduced in the synthetic datasets (considering the swapp of the coordinates too). This label is represented as 'TP_exact' in the tables. 

2. A second more in-deep evaluation was performed taking into account that some junctions can be assigned to close but not exact coordinates. For achive that a reconstruction of the sequence around the identified junction was generated (column 'seq_around_junction' and 'seq_around_junction_reverseCompl') and was checked if the sequence (directly or as reverse complementary) was part of the whole sequence of any of the 'real' DVGs composing the synthetic samples. This info is showed in columns 'inWholeSeq', 'inWholeSeq_asRevCompl' and 'in_idSeq', been annotated the cID_DI of the real DVG. The new label with that criteria is in 'TP_seq' column. This was the value used to calculate the evaluation metrics.

### SARS-CoV-2 datasets

Each row is a program/mode and each column is the total size of the dataset.

<b> Sensitivity </b> 

||100000|500000|1000000|2000000|3000000|4000000|5000000|6000000|7000000|8000000|9000000|10000000|
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|ViReMa-a|0.37962962962962965|0.8981481481481481|0.9907407407407407|0.9907407407407407|0.9907407407407407|0.9953703703703703|1.0|0.9953703703703703|0.9907407407407407|0.9953703703703703|0.9953703703703703|0.9953703703703703|
|DI-tector|0.5231481481481481|0.9722222222222222|0.9953703703703703|0.9953703703703703|0.9953703703703703|0.9953703703703703|1.0|0.9953703703703703|0.9953703703703703|0.9953703703703703|1.0|0.9953703703703703|
|DVGfinder: Metasearch|0.5277777777777778|0.9814814814814815|0.9953703703703703|0.9953703703703703|0.9953703703703703|0.9953703703703703|1.0|0.9953703703703703|0.9953703703703703|0.9953703703703703|1.0|0.9953703703703703|
|DVGfinder: Consensus|0.22685185185185186|0.7638888888888888|0.9490740740740741|0.9861111111111112|0.9907407407407407|0.9907407407407407|0.9953703703703703|0.9907407407407407|0.9907407407407407|0.9907407407407407|0.9907407407407407|0.9907407407407407|
|DVGfinder: Filtered|0.37037037037037035|0.8888888888888888|0.9861111111111112|0.9861111111111112|0.9861111111111112|0.9907407407407407|0.9861111111111112|0.9907407407407407|0.9907407407407407|0.9953703703703703|0.9907407407407407|0.9907407407407407|

<b> Precision </b> 

||100000|500000|1000000|2000000|3000000|4000000|5000000|6000000|7000000|8000000|9000000|10000000|
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|ViReMa-a|1.0|1.0|1.0|1.0|1.0|1.0|1.0|1.0|1.0|1.0|1.0|1.0|
|DI-tector|0.9453125|0.8690095846645367|0.816711590296496|0.6881720430107527|0.6173285198555957|0.5636645962732919|0.5293276108726752|0.5027027027027027|0.5077319587628866|0.4876237623762376|0.47336561743341404|0.46490218642117376|
|DVGfinder: Metasearch|0.9578313253012049|0.9039812646370023|0.8653465346534653|0.7615131578947368|0.6958393113342898|0.6434010152284264|0.6097271648873073|0.583710407239819|0.5843307943416758|0.5651260504201681|0.5515463917525774|0.5409674234945706|
|DVGfinder: Consensus|1.0|1.0|1.0|1.0|1.0|1.0|1.0|1.0|1.0|1.0|1.0|1.0|
|DVGfinder: Filtered|1.0|0.9969230769230769|0.9974874371859297|1.0|1.0|1.0|1.0|1.0|1.0|1.0|1.0|1.0|

<b> F1-score </b> 

||100000|500000|1000000|2000000|3000000|4000000|5000000|6000000|7000000|8000000|9000000|10000000|
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|ViReMa-a|0.5503355704697986|0.9463414634146341|0.9953488372093023|0.9953488372093023|0.9953488372093023|0.9976798143851509|1.0|0.9976798143851509|0.9953488372093023|0.9976798143851509|0.9976798143851509|0.9976798143851509|
|DI-tector|0.6735467980295566|0.9177230442955608|0.8972337187441896|0.8137437535113398|0.7620399830035962|0.7197465739528192|0.6922357343311506|0.6680253244909209|0.6724510208617788|0.6545760825889407|0.6425636811832375|0.6337856030120503|
|DVGfinder: Metasearch|0.6805586843883759|0.9411385853939046|0.9258155266619696|0.8628775007801394|0.8190797871295878|0.7815883441125436|0.7575534266764923|0.7358813462635483|0.7363741600946498|0.7209369001022162|0.7109634551495017|0.700969470167746|
|DVGfinder: Consensus|0.369811320754717|0.8661417322834646|0.9738717339667459|0.993006993006993|0.9953488372093023|0.9953488372093023|0.9976798143851509|0.9953488372093023|0.9953488372093023|0.9953488372093023|0.9953488372093023|0.9953488372093023|
|DVGfinder: Filtered|0.5405405405405406|0.9398114575779549|0.9917666514197249|0.993006993006993|0.993006993006993|0.9953488372093023|0.993006993006993|0.9953488372093023|0.9953488372093023|0.9976798143851509|0.9953488372093023|0.9953488372093023|


---
### Contact

María José Olmo-Uceda - mariajose.olmo@csic.es

PhD student

*EvolSysVir Group*, I<sup>2</sup>SysBio (CSIC-UV) 

---
Project Link: [https://github.com/MJmaolu/DVGfinder](https://github.com/MJmaolu/DVGfinder)

Page Link: [https://mjmaolu.github.io/DVGfinder/](https://mjmaolu.github.io/DVGfinder/)
