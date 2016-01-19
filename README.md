# monocot_specific_miRDeep2
monocot specific miRDeep2 with replaced scripts in which parameters were optimized for monocot plants

############################################################
Software Dependencies

1) miRDeep2
http://www.mdc-berlin.de/en/research/research_teams/systems_biology_of_gene_regulatory_elements/projects/miRDeep/index.html

replacement of some scripts
sanity_check_reads_ready_file.pl
mapper.pl
miRDeep2.pl
excise_precursors.pl
excise_precursors_iterative_final.pl
miRDeep2_core_algorithm.pl

2) Vienna RNA Package 1.8.4 or above

http://www.tbi.univie.ac.at/~ivo/RNA/

3) randfold 2.0 or above

http://bioinformatics.psb.ugent.be/software/details/Randfold

4) fastx-toolkit
http://hannonlab.cshl.edu/fastx_toolkit/

5) bowtie
http://bowtie-bio.sourceforge.net/index.shtml

############################################################
Working Environment

1) 64 bit Unix or Linux OS

2) perl 5 is preferred

perl modules required by miRDeep2

############################################################
Input Files

1) sequenced short reads
reads.fa

2) genome sequece
cel_cluster.fa

3) genome index built by bowtie
cel_cluster.1.ebwt
cel_cluster.2.ebwt
cel_cluster.3.ebwt
cel_cluster.4.ebwt
cel_cluster.rev.1.ebwt
cel_cluster.rev.2.ebwt

3) mature miRNA sequences
mature_ref_this_species.fa
mature_ref_other_species.fa

4) miRNA precursor sequences
precursors_ref_this_species.fa

############################################################
Command Line Example

1)
perl mapper.pl reads.fa -c -j -k TCGTATGCCGTCTTCTGCTTGT -l 15 -m -p cel_cluster -r 20 -s reads_collapsed.fa -t reads_collapsed_vs_genome.arf -v -o 8

Outputs:
reads_collapsed.fa
reads_collapsed_vs_genome.arf

2)
perl miRDeep2.pl reads_collapsed.fa cel_cluster.fa reads_collapsed_vs_genome.arf mature_ref_this_species.fa mature_ref_other_species.fa precursors_ref_this_species.fa -t C.elegans 2>report.log

Outputs:
result.csv
result.html
output.mrd
