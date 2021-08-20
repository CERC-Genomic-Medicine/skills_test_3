# skills_test_3

This repository stores input files, example output files, and description of the problem which is designed to assist in the evaluation of computational skills of job candidates and prospective MSc/Ph.D. students.

## Problem description

Given sequencing data for 10 individuals in CRAM file format (one file per individual) inside `input/` directory, implement an automatic workflow which for each indiviual:
1. **Estimates DNA contamination**. To estimate DNA contamination levels, use the [VerifyBamID](https://github.com/Griffan/VerifyBamID) tool and 1000 Genome Project (1000g) GRCh38 reference panel, which is provided together with the `VerifyBamID` tool. Specify 4 Principal Components with the `--NumPC` option, e.g.:
```
${VERIFY_BAM_ID_HOME}/VerifyBamID.Linux.x86-64 --SVDPrefix ${VERIFY_BAM_ID_HOME}/resource/1000g.phase3.100k.b38.vcf.gz.dat --Reference Homo_sapiens.GRCh38.fa --BamFile `input/..` --NumPC 4 ...
```

The human genome reference file can be downloaded from [here](ftp://ftp-trace.ncbi.nih.gov/1000genomes/ftp/technical/reference/GRCh38_reference_genome/GRCh38_full_analysis_set_plus_decoy_hla.fa).


3. **Assigns most likely super population**. Using 4 Principal Components estimated by `VerifyBamID` and 4 Principal Components from the reference panel and labels from reference panel, assign most likely genetic ancestry for each individual.


## Requirements

To implement this workflow you may:
- use any workflow system of your choice, which is compatible with HPC (e.g. [Nextflow](https://www.nextflow.io), [Snakemake](https://snakemake.readthedocs.io/en/stable/), [Luigi](https://github.com/spotify/luigi), [Cromwell](https://cromwell.readthedocs.io/en/stable/))
- use any existing published open source sowtware tools and libraries (e.g. R and Python libraries for plotting such as matplotlib, ggplot)
- use any scripting/programming language (or any combination of them) of your choice (e.g. Python, C/C++, Java, Perl, R, shell scripting)

