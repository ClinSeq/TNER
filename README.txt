###############################################################################
README

TNER: Tri-Nucleotide Error Reducer

TNER is a novel background error suppression tool that provides a robust 
estimation of background noise to reduce sequencing errors using tri-nucleotide 
context data for better identification of low frequency somatic mutations in
ctDNA (Circulating tumor DNA).

Version: 1.1
Last updated: Oct/04/2018
Contact: shibing.deng {at} pfizer.com or tao.xie {at} pfizer.com
Pfizer Early Clinical Development Biostatistics
Pfizer Oncology Research & Development
###############################################################################

Pre-requisites/Installation:
----------------------------
Download and install R (version 3 or later)
Download and install R package optparse (version 1.2.0 or later)
Download and install PERL (version 5.8 or later)
Download and install the TNER package and unzip the files

----------------------------
Test the TNER main function using the demo dataset
----------------------------
"Rscript TNER_main.R TNER_example_input_file.txt hs_ave_bg_error.csv hs_depth.csv"

Note: “TNER_example_input_file.txt” is the example input data to be analyzed; the 2nd argument (default:
“hs_ave_bg_error.csv“) is a csv file with the average background error rate from healthy subjects; the
last argument (default: “hs_depth.csv”) is a csv file with the base coverage in healthy subjects. TNER 
report the nosiy bases detected in the input data which can be used as a filter to apply to the variant
calls from any existing pipeline. 
Output files are a polished freq file (default: “INPUT.clean.txt“) and a "noise" file (default: 
“INPUT.noise.txt“) describing what was polished away. Output file names can be set with options 
-o/--output and -n/--noise.


----------------------------
Build background error profile using "Create_background_error_rate.R” 
----------------------------
"Rscript Create_background_error_rate.R"

Note: "Create_background_error_rate.R” creates an average background error rate file from individual healthy 
subject data. By default the healthy subject files are searched for in the subfolder named "healthy_subjects", 
with file endings "freq$", but search dir and pattern can be set with options -i/--inputdir and -p/--pattern. 
File format is the same as "TNER_example_input_file.txt". The function outputs by default “hs_ave_bg_error.csv” 
and “hs_depth.csv” for the main function “TNER_main.R”. Output file names can be set with options -b/--background 
and -d/--depth.


----------------------------
Process pileup files for TNER using "pileup2actg.pl"
----------------------------
"perl pileup2actg.pl 

Note: this perl script processes a pileup file to generate a tab-delimited txt file for running “TNER_main.R”.


----------------------------
Citation
----------------------------
TNER: A Novel Bayesian Background Error Suppression Method for Mutation Detection in Circulating Tumor DNA
Shibing Deng, Maruja Lira, Donghui Huang, Kai Wang, Crystal Valdez, Jennifer Kinong, Paul A. Rejto, Jadwiga Bienkowska, James Hardwick, Tao Xie
doi: https://doi.org/10.1101/214379 
###############################################################################


 