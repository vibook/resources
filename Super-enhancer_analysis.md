1. GenomeSpace import
```
chip-seq data
Shi_5_S13_L002_R1_001.fastq.gz
```

2. Convert fastq.gz files to fastq
```
dbkey - hg19
```

3. Map with BWA - map short reads(<100 bp)
```
Using reference genome : Human (Homo sapiens) (b37) : hg19
Select input type : Single fastq
Select fastq dataset : Convert fastq.gz files to fastq
Select analysis mode : Simple Illumina mode
```

4. Bowtie2 - map reads against reference genome <- no use
```
Single-end
FASTQ file : Converted fastq.ga files to fastq
Using reference genome : Human (Homo sapiens) (b37) : hg19
```

5. SenomeSapce import : control file
```
MEC2_Input.bam
```

6. Macs2 callpeak Call peaks from alignment results
```
ChIP-Seq Treatment File : aligned reads (sored BAM) with Bowtie2
ChIP-Seq Control File : MEC2_Input.bam
Effective genome size : H.sapiens (2,451,960,000)
Band width for picking regions to compute fragment size : 300
Mfold settings
Set lower mfold bound : 5
Set upper mfold bound : 50
Peak detection based on : q-value
Minimum FDR(q-value) cutoff for peak detection : 0.05

Peaks as tabular file, Peak summits, Scores in bedGraph files, Summary page, Plot in PDF
```

7. BED-to-GFF converter
