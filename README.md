# ONT-data-analysis

<img src="img/ONT.png" width="1000" height="600">

Information focused on the analysis of data from Oxford nanopore technologies using EPI2ME workflows and in-house scripts.


## Requirements: 
* Nextflow
* Singularity
* Docker

## Basecaller

Readings from oxford nanopore technologies are delivered to the user in pod5 and fast5 format.

<p style="text-align: center;">
    <img src="img/epi2me.jpg" width="500" height="800">
</p>

Data can be analyzed via GUI by downloading [EPI2ME labs](https://labs.epi2me.io/downloads/) or via command line using nextflow modules from [GitHub](https://github.com/epi2me-labs). It is advisable to transform this data to other aligned formats such as BAM, SAM and CRAM or non-aligned such as __fastq__ for which it is possible to use the wf-basecalling workflow. This module can be executed as follows: 
```bash
nextflow run epi2me-labs/wf-basecalling \
  -profile singularity \
  --input /home/jpramosg/Desktop/genomic_analysis/wf-basecalling/input/ \
  --ref /home/jpramosg/Desktop/genomic_analysis/wf-basecalling/file.fasta \
  --dorado_ext pod5 \
  --out_dir output \
  --basecaller_cfg dna_r10.4.1_e8.2_400bps_hac@v4.1.0 \
  --remora_cfg "dna_r10.4.1_e8.2_400bps_hac@v4.1.0_5mCG_5hmCG@v2"
  ```

__Note__ : In case of more information about the configuration of the execution access the [wf-basecalling](https://github.com/epi2me-labs/wf-basecalling) workflow. Therefore, in case you do not meet certain specifications it is necessary to create a configuration file (e.g: __nextflow.config__): 

Results 

<img src="img/read_quality.png" width="1000" height="600">

## Transcriptome analysis in Musaceae

Once the fastq format is obtained it is necessary to perform a mapping and counting of transcripts and genes using the wf-transcriptomics workflow or it can be done by developing your own pipelines (in-house bash, python and R scritps), check [meta-analysis_musaceas](https://github.com/jpramosg/meta-analysis_musaceas) repository. 



