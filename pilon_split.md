## Pilon is a huge memory hog. There is no easy way to run pilon without running into java memory errors on a vertebrate genome.
But we don't need to run it on the whole genome, just on each contig. So the following code splits the fasta, splits the bam, and runs pilon.
*Done this way, pilon can process an entire woodpecker genome on an i7 linux NUNC with 32 GB of RAM in about 8 hours!
Make sure that you edit the pilon wrapper to up memory from 1GB!

### Split the fasta using the associated shell file: splitfasta.sh

### Split the bam file (In this case, our BAM had headers in the form: contig_1_pilon, because this was the output from the first pilon correction)
`for i in {1..1315};do samtools view -bh mjm682_assembly2_cleaned_sorted.bam contig_${i}_pilon > out_bams/contig_$i.bam;done`

### Index each bam file
`for i in {1..1315};do samtools index contig_$i.bam;done`

### Run Pilon on each section of the bam file
`for i in {1..1315};do pilon --genome contig_$i.fasta --frags contig_$i.bam --output contig_$i --outdir pilon_out --threads 7 --changes;done`

### We run pilon twice. The first time as above, the second time with the `--diploid flag
Visual inspection of a few BAM show that most of the remaining variants to the reference are heterozyotic, not assembly error   
`for i in {1..1315};do pilon --genome contig_$i.fasta --frags contig_$i.bam --output contig_$i --outdir pilon_out2 --threads 7 --diploid --changes;done`
