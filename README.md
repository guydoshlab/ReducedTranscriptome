# ReducedTranscriptome
Python3 code to analyze ribosome profiling data aligned to a reduced transcriptome

The code in this Python3 repository can be used for analyzing ribosome profiling data from any organism with an annotated transcriptome. Footprint data needs to be first mapped to a set of transcripts (1 isoform per gene), such as those provided by the MANE project. The output SAM files can then be used by mammalian_builddense.py to create data structures in Python to hold the sequence and mapped footprint information for each gene (both 5' and 3' end assignments). These are then pickled in python and saved to disk. 

The code in tools_m.py can then be used with associated input text files to analyze this data for quantitation (counting reads), metagene, metacodon, or localized pause analysis. The code can also be used to determine dORFs and to write out footprint density from a spliced gene to file. Most of these tasks can be performed by using the associated "wrapper" function to read in the input file and pickled density file.

Input files:

metagene.txt
Creates an average of reads from all genes after aligning spliced transcripts by start codon or stop codon. There are various options for weighting and thresholding available, as well as sizes of windows.

genelist.txt
Counter that adds reads up for various regions of transcripts (5'UTR, main ORF, 3'UTR), taking shift for P site, A site, etc into account.

posavg.txt
Multifaceted function that computes average reads in a region around particular sites of interest (such as AUG codons or Pro amino acids), or all permutations of a given length, such as 3 amino acids. Options available for normalization or thresholding.

posstats.txt
A function that computes pause scores (peak height/background) for particular sites of interest. Options available for choice of the windows around the peak.

writegene2.txt
Code to write out reads mapping to a spliced gene in a csv file, mainly for presentation purposes.

dorflist.txt
Experimental function that helps find small ORFs in UTR regions by reporting in-frame reads in the small ORF and main ORF. Relies on well-RNased ribosome footprint data and precise shift values.



