makeblastdb -in all_pilon2_polished.fasta -dbtype nucl -out mel_blastdb

blastn -db mel_blastdb -query mel_aur_refND2.fasta -out nd2blast.csv -outfmt "10 qseqid staxid sacc slen length pident evalue" -max_target_seqs 1
