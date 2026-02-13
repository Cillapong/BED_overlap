# BED_overlap: Comparison of Unix (Ad-hoc) vs bedtools Approaches

## Methods

Two approaches were used to identify overlapping indels between the DPure and LPure populations.

### Unix (Ad-hoc) Approach

An ad-hoc Unix pipeline was attempted using basic command-line tools including `awk`, `sort`, `uniq`, pipes (`|`), and output redirection (`>`). The intended workflow was to extract chromosome and coordinate columns from both BED files and then apply custom logic to compare genomic intervals and identify overlaps.

In practice, this approach required nested comparisons between large numbers of genomic features from both files. Due to the very large size of the datasets, the ad-hoc Unix pipeline became computationally inefficient and repeatedly hung during execution on the available compute resources. As a result, the pipeline did not complete successfully, and no reliable overlap count could be obtained using this approach.

### bedtools (Standardised) Approach

Overlapping indels were identified using the standardised bioinformatics tool `bedtools intersect`, which is specifically designed for efficient genomic interval overlap analysis. The following command was used:

```bash
bedtools intersect -a DPure_indels_mask.bed -b LPure_indels_mask.bed > overlapping_indels.bed
