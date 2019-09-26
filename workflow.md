### Processing ON reads

All reads were seperated by read_pass vs. read_fail using guppy, this was done by the Davis sequencing lab for the Promethion data, I did it for the Minion data by running current guppy. We only took the pass_reads into the workflow

- First run = run1 (25.6 Gb, fastq.gz; 	1,318,715 reads; median read length: 15,636; read length N50: 31,228; longest read: 274,775) 
- Second run, Preflush = run2_preflush (16.8 Gb, fastq.gz)
- Second run, Postflush = run2_postflush (16.0 Gb, fastq.gz)
- Minion two runs, merged = minion (2.3 Gb, fastq.gz)

### QC individual

Read length distribution, Q score, and other metrics were obtained using NanoPlot, on each run seperately

`NanoPlot -t 8 --fastq run1.fastq.gz  -o run1_qc`

### Merge all reads

`zcat *.fastq.gz > merged/all.fastq.gz`

### QC merged reads using NanoPlot
Read length distribution, Q score, and other metrics were obtained using NanoPlot, on each run seperately

`NanoPlot -t 8 --fastq all.fastq.gz  -o all_reads_qc`

### Filter reads

`gunzip -c all.fastq.gz | NanoFilt -l 10000 -q 7 | gzip > all_10k.fastq.gz`
