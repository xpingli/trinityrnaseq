SAMPLES="samples.txt"
TRINITY_FASTA="../../test_DATA/Trinity.fasta"

test: test_RSEM test_eXpress test_kallisto test_salmon

test_RSEM:
ifeq ("", "$(shell which rsem-calculate-expression)")
	echo WARNING: skipping RSEM test, cannot locate rsem-calculate-expression tool in PATH
else
	ln -sf ${TRINITY_FASTA}
	../../../util/align_and_estimate_abundance.pl  --transcripts Trinity.fasta --est_method RSEM --aln_method bowtie --trinity_mode --prep_reference --samples_file samples.txt --SS_lib_type R --seqType fq
	touch test_RSEM
endif

test_eXpress:
ifeq ("", "$(shell which express)")
	echo WARNING: skipping express test, cant locate express tool in PATH
else
	ln -sf ${TRINITY_FASTA}
	../../../util/align_and_estimate_abundance.pl  --transcripts Trinity.fasta --est_method express --aln_method bowtie2 --trinity_mode --prep_reference --samples_file samples.txt --SS_lib_type R --seqType fq
	touch test_eXpress
endif

test_kallisto:
ifeq ("", "$(shell which kallisto)")
	echo WARNING: cannot find kallisto installed in PATH, skipping kallisto test
else
	ln -sf ${TRINITY_FASTA}
	../../../util/align_and_estimate_abundance.pl  --transcripts Trinity.fasta --est_method kallisto --trinity_mode --prep_reference --samples_file samples.txt --SS_lib_type R --seqType fq
	touch test_kallisto
endif

test_salmon:
ifeq ("", "$(shell which salmon)")
	echo WARNING: cannot find salmon installed in PATH, skipping salmon test
else
	ln -sf ${TRINITY_FASTA}
	../../../util/align_and_estimate_abundance.pl  --transcripts Trinity.fasta --est_method salmon --trinity_mode --prep_reference --samples_file samples.txt --SS_lib_type R --seqType fq --salmon_idx_type quasi
	touch test_salmon
endif


clean:
	./cleanme.pl

