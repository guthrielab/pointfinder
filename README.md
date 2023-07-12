
# Description

The PointFinder service contains one python script *PointFinder.py* which is the script of the latest version of the PointFinder service. The method detects chromosomal mutations predictive of drug resistance based on WGS data.

# Installation

```bash
# Go to wanted location for pointfinder
cd /path/to/some/dir

# Clone and enter the pointfinder directory
git clone https://git@bitbucket.org/genomicepidemiology/pointfinder.git
cd pointfinder


# Installing up the PointFInder database
# Go to wanted location for pointfinder database
cd /path/to/some/dir

# Clone and enter the pointfinder directory
git clone https://git@bitbucket.org/genomicepidemiology/pointfinder_db.git
cd pointfinder_db

```

#### Download Blastn and BioPython
```url
http://biopython.org/DIST/docs/install/Installation.html
```
```url
ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/
```
#### Install the cgecore module to python3
```bash
pip3 install cgecore
```

### Build docker image
```bash
# Build container
docker build -t pointfinder .
```

# Usage
An example of use with the provided test.fsa: 
```bash
./PointFinder.py -i test.fsa -o /path/to/output-dir/ -p /path/to/db/ -s escherichia_coli -m blastn -m_p /path/to/blastn
```

The program can be invoked with the -h option to get help and more information of the service.

```
# ./PointFinder.py -h
$ python3 PointFinder.py -h
usage: PointFinder.py [-h] -i INPUTFILES [INPUTFILES ...] -o OUT_PATH -s
                      SPECIES -p DB_PATH -m {kma,blastn} -m_p METHOD_PATH [-n]
                      [-t THRESHOLD] [-l MIN_COV] [-u]
                      [-g SPECIFIC_GENES [SPECIFIC_GENES ...]]
                      [-r {early,all,specified}]

This program predicting resistance associated with chromosomal mutations based on WGS data.

optional arguments:
  -h, --help            show this help message and exit
  -i INPUTFILES [INPUTFILES ...], --inputfiles INPUTFILES [INPUTFILES ...] Input file, for blast 1 fasta file, for KMA fastq file(s).
  -o OUT_PATH, --out_path OUT_PATH Path to existing output directory.
  -s SPECIES, --species SPECIES Species for point mutation detetion.
  -p DB_PATH, --databasePath DB_PATH Path to the databases.
  -m {kma,blastn}, --method {kma,blastn}
  -m_p METHOD_PATH, --method_path METHOD_PATH Path to kma or blastn program depending on the chosen method.
  -n, --no_Ns           Silence the output where Ns are found.
  -t THRESHOLD, --threshold THRESHOLD Blast threshold for identity.
  -l MIN_COV, --min_cov MIN_COV Minimum coverage.
  -u, --unknown_mut     Show all mutations found even if it is unknown to the resistance database.
  -g SPECIFIC_GENES [SPECIFIC_GENES ...], --specific_genes SPECIFIC_GENES [SPECIFIC_GENES ...] Specify genes existing in the database to search for. If none is specified all genes are used.
  -r {early,all,specified}, --stop_codons {early,all,specified} predict res on premature stop codons.
```


# Web Application

PointFinder program is available as a web application at the [CGE website](http://www.genomicepidemiology.org/) and can be found [here](https://cge.cbs.dtu.dk/services/ResFinder/).


# Citation

When using the method please cite:

**PointFinder: a novel web tool for WGS-based detection of antimicrobial resistance associated with chromosomal point mutations in bacterial pathogens.**
*Zankari, E., Allesøe, R., Joensen, K. G., Cavaco, L. M., Lund, O., & Aarestrup, F. M.*
Journal of Antimicrobial Chemotherapy. 19 July 2017
PMID: 29091202. doi: 10.1093/jac/dkx217

# License

Copyright (c) 2014, Ole Lund, Technical University of Denmark All rights reserved.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0) Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
