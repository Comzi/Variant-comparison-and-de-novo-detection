# Variant comparison and detection of de novo variants
This repositorium contains the recources for a course project in genome informatics.

Thr project aims to compare variants of 3 sample genomes of the Ashkenazi Trio (the mother, father and child) available through the Genome In A Bottle consortium. This comparison is done in order to detect *de novo* variants of the child - variants present in the child genome, but not in either of the parent genomes. 

## Step 1: GRAF Workflow genome reconstruction and variant calling
The 3 genomes are available in FASTQ formats, so they firstly needed to be aligned using the GRAF Germline Variant Detection Workflow. Then, also using the GRAF Workflow, variant calling is perfomed and the required VCF files obtained. 

## Step 2: Algorithm development in Python
The algorithm was implemented as a part of a Jupyter Notebook using Python version 3.8. The notebook was executed as an interactive analysis on the CGC platform. The algorithm heavily relies on the usage of PyVCF library, which allows for easy parsing of VCF files. 

The main function compares 2 VCF files and returns a new VCF file containing all variants present in the child VCF (ie. called variants) and not present in a parent VCF (ie. baseline variants). These results are then used as the called variants in the second usage of the function to be compared to the other parent's VCF.

## Step 3: Finding *de novo* variants using RTG Tools *vcfeval* 
In order to test the success of our algorithm, the same analysis was performed using a state of the art tool. RTG Tools *vcfeval* analysis was run on the CGC platform, using the same 2-step comparison as with the developed algorithm.  

## Step 4: Comparing the results
The developed algorithm found 142,685 (2.9% of all variants) *de novo* variants in the child genome, while the RTG Tools *vcfeval* found 83,438 (1.7%). The significant diference in the results can be attributed to the fact that *vcfeval* uses an advanced algorithm that is able to detect different representations of the same variant, ie. it is not comparing the VCF files simply line by line, like our developed algorithm does. 
For a detailed overview of the project you can view the project presentation available [here](url).
