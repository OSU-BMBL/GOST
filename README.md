# GOST: orthology mapping between any pair of bacterial genomes

## Abstract ##

Existing methods for orthologous gene mapping suffer from two general problems: (i) they are computationally too slow and their results are difficult to interpret for automated large-scale applications when based on phylogenetic analyses; or (ii) they are too prone to making mistakes in dealing with complex situations involving horizontal gene transfers and gene fusion due to the lack of a sound basis when based on sequence similarity information. We present a novel algorithm, Global Optimization Strategy (GOST), for orthologous gene mapping through combining sequence similarity and contextual (working partners) information, using a combinatorial optimization framework. Genome-scale applications of GOST show substantial improvements over the predictions by three popular sequence similarity-based orthology mapping programs. Our analysis indicates that our algorithm overcomes the intrinsic issues faced by sequence similarity-based methods, when orthology mapping involves gene fusions and horizontal gene transfers. Our program runs as efficiently as the most efficient sequence similarity-based algorithm in the public domain.

**Citing us** Li, G., Ma, Q., Mao, X., Yin, Y., Zhu, X., & Xu, Y. (2011). Integration of sequence-similarity and functional association information can overcome intrinsic problems in orthology mapping across bacterial genomes. *Nucleic Acids Research*, 39(22), e150–e150. doi:10.1093/nar/gkr766 


## Environment ##

Linux system is recommanded. 

# Usage #

## Installation

Simply put 'GOST.tar.gz' in any directory.
```
tar zxvf GOST.tar.gz 
```
Enter the folder 'GOST2.0'  
```
./INSTALL
```
## For basic usage of orthlogy mapping

Use the packed PERL script 'gost_pipeline.pl', which is a pipeline for GOST to generate an orthology mapping between two given species, using '.faa' files from NCBI and operon prediction from DOOR database.
```
perl gost_pipeline.pl target_species_dir ref_species_dir output_dir target_operon(optional) ref_operon(optional)
```
For example, to identify the orthology between E. coli and C. therm

```
perl gost_pipeline.pl example/ncbi_data/Escherichia_coli_K_12_substr__MG1655_uid57779/ example/ncbi_data/Clostridium_botulinum_B_Eklund_17B_uid59159/ example_output example/operon/Ecoli.opr example/operon/NC_010674.opr
```

If you don't have operon files, we will generate fake operon files with fake_operon.pl based on the ".faa" files:


```
perl gost_pipeline.pl example/ncbi_data/Escherichia_coli_K_12_substr__MG1655_uid57779/example/ncbi_data/Clostridium_botulinum_B_Eklund_17B_uid59159/example_output_no_opr
```

## For advanced usage of orthology mapping

Use the compiled code GOST in ./GOST/build/bin/

```
 ./GOST OperonU OperonV Homology RBH_OUTPUT_File GOST_OUTPUT_File evalue-cutoff
```

For example
```
./GOST/build/bin/GOST GOST/data_test/Escherichia_coli_K12.gi.operon GOST/data_test/NC_000853.gi.operon GOST/data_test/NC_000853.homology result.RBH result.GOST 1e-2
```

## Inputs and outputs

Input format
- species_directory: the directory containing the species information downloaded from NCBI
- operon file format (operon id: a list of gene ids)
