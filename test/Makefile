.PHONY: all clean train simulate

all: simulate
#all: train simulate

train: model_ecoli_model_profile

model_ecoli_model_profile: ecoli_R7_2D.fasta ecoli_K12_MG1655_ref.fa
	nanosim-h-train -i ecoli_R7_2D.fasta ecoli_K12_MG1655_ref.fa profile_ecoli

simulate: ecoli_K12_MG1655_ref.fa
	nanosim-h -n 10 --circular -o sim1 ecoli_K12_MG1655_ref.fa
	nanosim-h -n 10 --circular -o sim2 ecoli_K12_MG1655_ref.fa
	diff sim1.fa sim2.fa

ecoli_R7_2D.fasta:
	curl ftp://ftp.bcgsc.ca/supplementary/NanoSim/$@ | head -n 200 > $@

ecoli_K12_MG1655_ref.fa:
	wget ftp://ftp.bcgsc.ca/supplementary/NanoSim/$@

clean:
	rm -f *.fa *.maf model_* ref_genome.* *.log *.fasta simulated_error_profile
