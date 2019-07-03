# SNP_genotyping
##Compare_obs_exp_genotypes.py
This file was created to assess the performance of the SNP genotyping kit.

The SNP genotyping samples should have been processed through a version of MokaPipe without mark duplicates (see 003_190614_M02631_0153_000000000-G42LT_SNP_assay).
gVCFS should be created, and variant calling restricted to just the SNP positions.

These VCFs should be decomposed using vt.

The expected VCFs should be created by taking the BAM file from previous testing and repeating variant calling to create a gVCF as described above (with markduplicates as appropriate).

This script can then be run after pointing the file paths as required (the filepaths are specified in multiple places).

The script populates two dictionaries - one for samples with na in the identifier - which seperates GIAB samples from diagnostic samples.

For each SNP it records the alt allele, genotype and the DP. Only genotypes that does contain "." are recorded as the alt allele for that row is not considered to be part of the genotype for that postition.

These are used to create a genotype result, with one row per SNP and three columns per sample - showing the expected allele/genotype, observed allele/genotype and if these match.

The DP is listed for each observed sample in a seperate coverage output.

At the moment the GIAB VCF doesn't have a result for one SNP so this is excluded from the GIAB output.
