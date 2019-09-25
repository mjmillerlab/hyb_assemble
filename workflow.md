# Processing ON reads

### All reads were seperated by read_pass vs. read_fail using guppy, this was done by the Davis sequencing lab for the Promethion data, I did it for the Minion data by running current guppy. We only took the pass_reads into the workflow
- First run = run1 (25.6 Gb, fastq.gz)
- Second run, Preflush = run2_preflush (16.8 Gb, fastq.gz)
- Second run, Postflush = run2_postflush (16.0 Gb, fastq.gz)
- Minion two runs, merged = minion (2.3 Gb, fastq.gz)

# QC and filter of ON reads

### Read length distribution, Q score, and other metrics were obtained using NanoFilt, on each run seperately
