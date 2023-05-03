# 1) Custom NCBI genome assembly statistics fetcher

## Dependencies
Entrez

## Input
Taxonomic ID

## Output
Assembly statistics in .csv format, including fields:
Organism name
Assembly-ID, 
taxonomic ID, 
Genbank release date, 
Coverage, 
Assembly status, 
ContigN50, 
ScaffoldN50, 
BioSampleAccn,
Isolate 

 
# 2) Fast custom Gbk format and sequence name converter

Bio, eqIO
glob
os
Bio, Entrez
(time)

## Input
GenBank files, located in a single folder.

## Output
- Concatenated sequences in .fasta format and IDs with 3-letter species code in .txt format, 
- Concatenated nucleotide sequences in .fasta format


Created on Thu Aug 25 18:18:35 2022  
  
@author: FWolters
  
  
> Custom script to extract concatenated protein fasta files with 3-letter species code from a set of .gbk files & retrieve nucleotide fasta files with corresponding IDs via Entrez search  
  
  
  
 ## Main function: 
 1) Concatenate all extracted files (Genbank format .gbk) into 1 fasta     
> Important: Assigns three-letter code of organism-names, and file-names to each sequence 
 2) Concatenate all protein IDs into one .txt file. Needed to fetch nucleotide sequences from NCBI.    
> However, nucleotide-sequences can also be retrieved from available CDS in .gbk file 
 3) Input format: GenBank files, located in a single folder. 
 4) Output concatenated sequences and IDs:       
	 1) i) 'concatenated_sequences_protein.fasta'  
            Extracted protein-sequences with assigned three-letter code for organism-name &            '
> file-name for each record in single .gbk files (one file per .gbk file & concatenated file)  
            ii) 'concatenated_protein_IDs.txt'            
            Concatenated file of all .gbk file sequence record IDs       
            iii) 'conc_IDs_Nucleotide_mrna.fasta'            
            Concatenated mRNA IDs to fetch nucleotide sequences from NCBI, using ELink:            
            If corresponding nucleotide IDs link to whole genome/chromosome assemblies,            
> Entrez EFetch may crash for >20 sequences.        
            iv) 'concatenated_mRNA.fasta'  
            = Concatenated fetched nucleotide fasta sequences retrieved via Entrez search       
             v) 'Concatenated_CDS.txt'            
             = Concatenated complete CDS of all given .gbk files5) Output per .gbk file:  
> Protein fasta sequences, protein IDs & CDS, and location on CDS per given .gbk file 
