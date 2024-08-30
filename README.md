# MIMIC Metagenome Simulator

The MIMIC Metagenome simulator creates simulated Oxford Nanopore (ONT) reads from any existing metagenomic community
by taking in a fastq file and analyzing the naturally occurring microbial abundances. 

This project was conceptualized and built during the
Baylor College of Medicine Human Genome Sequencing Center (HGSC) 2024 Hackathon. 


![alt text](docs/img/logo_small.png)

## Table of Contents 
1. [Introduction](#introduction) 
2. [Installation](#installation) 
3. [Dependencies](#dependencies)
4. [How to use It](#how-to-use-it) 
6. [MIMIC workflow](#mimic-workflow) 
7. [Contributors](#contributors) 
8. [References](#references) 


## Introduction

Oxford Nanopore (ONT) sequencing is rapidly becoming a widely used sequencing technology in metagenomic studies due to its cost, long reads, and significantly improved error rate[^1]. We built The MIMIC Metagenome simulator to create a simple tool to facilitate the benchmarking and testing of metagenomic profiles and taxonomic classifiers on compositions that mimic real-world microbiome samples (sequenced with ONT reads). Specifically,  MIMIC will simulate Oxford Nanopore (ONT) reads from any existing metagenomic community by taking in an ONT FASTQ file and analyzing it with Lemur and Magnet[^2]. It will then simulate reads based on the Lemur and Magnet mimicked profile with Nanosim[^3]. Once the truth tables are generated for simulated data based on real microbiome samples, MIMIC offers a simple-to-use evaluation framework for comparing the results of existing methods to the known truth data simulated by Nanosim.

## To do list

- [x] Implement mimic.py script with basic functionality
- [x] Create workflow diagram depicting the main components of MIMIC
- [x] Generate simulated data for two ONT soil metagenome samples (SRR30413550, SRR29660113)
- [ ] Get MIMIC set up and running in DNAnexus environment
- [ ] Run Kraken2+Bracken and Sourmash on the MIMIC output for an ONT soil metagenome sample
- [ ] Plot recall and precision and L1/L2 metrics for the ONT soil metagenome simulated data
- [ ] Add installation and usage details to readme
- [ ] Add awesome features

## Installation
Mimic can be installed using the following steps: 
`````
## Clone the git repository
git clone https://github.com/collaborativebioinformatics/Mimic.git

## cd into the repository
cd Mimic/

## Setup the conda environment
conda env create -f mimic_env.yml
conda activate mimic
`````

## Usage
Mimic can be run using the following command:
`````
python mimic.py -i [fastq] -o [output_loc] -r [num_reads] --db [lemur_db] -t [threads]

arguments:
  -h, --help            show help message and exit
  -i FASTQ, --fastq FASTQ
                        Path to first fastq file (required)
  -I FASTQ2, --fastq2 FASTQ2
                        Path to second fastq file for paired-end reads
  -o OUTPUT, --output OUTPUT
                        Path to the output directory (required)
  --db DB               Lemur database location (required)
  -t THREADS, --threads THREADS
                        Number of threads for multithreading (Default: 1)
  -r READS, --reads READS
                        Number of simulated reads to generate (Default: 100)
`````


## Dependencies

### To generate simulated reads

- Python 3.9
- NCBI Datasets v15.27.1
- Minimap2 v2.24-r1122
- Samtools v1.15.1
- Biopython
- Pandas
- Ete3 v3.1.2
- BWA v0.7.17
- FastANI
- Nanosim

### To generate truth table

### Other 


## How to use It


### MIMIC Workflow
![alt text](docs/img/flowchart_v3.png)

## Contributors

Hackathon team: Todd	Treangen, Shwetha	Kumar, Ryan	Doughty, Sumaiya	Khan, Iva	Kotásková, Arthur	Shem Kasambula, Mike	Nute

## References 

[^1]: Agustinho, Daniel P., Yilei Fu, Vipin K. Menon, Ginger A. Metcalf, Todd J. Treangen, and Fritz J. Sedlazeck. "Unveiling microbial diversity: harnessing long-read sequencing technology." Nature Methods (2024): 1-13.

[^2]: Sapoval, Nicolae, Yunxi Liu, Kristen Curry, Bryce Kille, Wenyu Huang, Natalie Kokroko, Michael G. Nute et al. "Lightweight taxonomic profiling of long-read sequenced metagenomes with Lemur and Magnet." bioRxiv (2024): 2024-06.

[^3]: Yang, Chen, Justin Chu, René L. Warren, and Inanç Birol. "NanoSim: nanopore sequence read simulator based on statistical characterization." GigaScience 6, no. 4 (2017): gix010.
