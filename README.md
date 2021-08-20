# skills_test_3

This repository stores input files, example output files, and description of the problem which is designed to assist in the evaluation of computational skills of job candidates and prospective MSc/Ph.D. students.

## Problem description

Given sequencing data for 10 individuals in CRAM file format (one file per individual) inside `input/` directory, implement an automatic workflow which for each indiviual:
1. **Estimates DNA contamination**. To estimate DNA contamination levels, use the [VerifyBamID](https://github.com/Griffan/VerifyBamID) tool and 1000 Genome Project (1000g) GRCh38 reference panel, which is provided together with the `VerifyBamID` tool. Specify 4 Principal Components with the `--numPC` option. Example:
```

```

3. **Assigns most likely super population**. Using 4 Principal Components estimated by `VerifyBamID` and 4 Principal Components from the reference panel and labels from reference panel, assign most likely genetic ancestry for each individual.
