# skills_test_3

This repository stores input files, example output files, and description of the problem which is designed to assist in the evaluation of computational skills of job candidates and prospective MSc/Ph.D. students.

## Problem description

Given sequencing data for 10 study individuals in CRAM file format (one file per individual) inside `input/` directory, implement an automatic workflow which for each indiviual:
1. **Estimates DNA contamination and genetic ancestry**. To estimate DNA contamination levels and genetic ancestry, use the [VerifyBamID](https://github.com/Griffan/VerifyBamID) tool and 1000 Genome Project (1000g) GRCh38 reference panel, which is provided together with the tool. Specify 4 Principal Components (PC) with the `--NumPC` option, e.g.:
    
    ```
    VerifyBamID.Linux.x86-64 --SVDPrefix ${VERIFY_BAM_ID_HOME}/resource/1000g.phase3.100k.b38.vcf.gz.dat --Reference GRCh38_full_analysis_set_plus_decoy_hla.fa --BamFile `input/HGDP00082.GRCh38.low_coverage.cram` --NumPC 4 ...
    ``` 
    The human genome reference file and its index can be downloaded from
    ```
    ftp://ftp-trace.ncbi.nih.gov/1000genomes/ftp/technical/reference/GRCh38_reference_genome/GRCh38_full_analysis_set_plus_decoy_hla.fa
    ```
    and
    ```
    ftp://ftp-trace.ncbi.nih.gov/1000genomes/ftp/technical/reference/GRCh38_reference_genome/GRCh38_full_analysis_set_plus_decoy_hla.fa.fai
    ```
    , correspondingly.
    
    This step will generate `*.Ancestry` and `*.selfSM` output files for each study individual. The DNA contamination values are stored in `*.selfSM` files in the *FREEMIX* column.

2. **Visualizes estimated ancestry PCs**. The `${VERIFY_BAM_ID_HOME}/resource/1000g.phase3.100k.b38.vcf.gz.dat.V` file stores pre-computed 4 PCs for each individual in the 1000g reference panel, the `input/1000G_reference_populations.txt` file stores population labels (EUR, EAS, AMR, SAS, and AFR) for each individual in the 1000g reference panel, and the `*.Ancestry` files from the (1) workflow step store estimated PCs for 10 study individuals (*IntendedSample* column).

3. **Assigns most likely super population**. Using 4 Principal Components estimated by `VerifyBamID` and 4 Principal Components from the reference panel and labels from reference panel, assign most likely genetic ancestry for each individual.


## Requirements

To implement this workflow you may:
- use any workflow system of your choice, which is compatible with HPC (e.g. [Nextflow](https://www.nextflow.io), [Snakemake](https://snakemake.readthedocs.io/en/stable/), [Luigi](https://github.com/spotify/luigi), [Cromwell](https://cromwell.readthedocs.io/en/stable/))
- use any existing published open source sowtware tools and libraries (e.g. R and Python libraries for plotting such as matplotlib, ggplot)
- use any scripting/programming language (or any combination of them) of your choice (e.g. Python, C/C++, Java, Perl, R, shell scripting)

