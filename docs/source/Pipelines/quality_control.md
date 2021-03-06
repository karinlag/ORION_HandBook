# Quality control and preprocessing

## Fastqc / Multiqc analysis
After sequence data is delivered to the analyst / researcher it first needs to
be checked to assure that the data is of good enough quality to work with. This
is mostly done by performing an analysis with the program
[Fastqc](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/). The
software Fastqc summarizes the fastq file data, and displays information about
read length, average quality score along the read, GC-content, number of
ambiguous bases, the presence of sequencing adapters, and various other
parameters useful to determine the quality of the raw sequence data. The
program [Multiqc](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5039924/) can be
used to combine the output of multiple fastqc output files, or many other
programs, so that many datasets can be inspected simultaneously.

## Controlling contamination
Besides general inspection of the data, it is also wise to check for possible
contaminants )present in the sequence data files. These contaminants can be due
to several factors. A very common and serious contaminant in experiments where
illumina sequencing has been performed is the inclusion of the phage genome PhiX
([Sanger et al., 1977](https://pubmed.ncbi.nlm.nih.gov/870828/)). The phage
genome is used in illumina sequencing for quality and calibrations purposes,
but when not detected in the sequence data it can contaminate such data with
far reaching consequences
([Mukherjee et al., 2015](https://environmentalmicrobiome.biomedcentral.com/articles/10.1186/1944-3277-10-18)).
In the case of whole genome sequencing, contaminants are often due to pure
cultures containing an additional bacterial species or the culture is a
different species than expected. In addition, microbial contamination from
laboratory chemicals ([Salter et al., 2014](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4228153/))
or Human DNA contamination due to sample handling can also occur. Depending on
the subsequent usage of the data a decision needs to be made if these
contaminating sequences should be removed or not.

Contamination is commonly detected by either comparing the sequence data to a
reference genome and calculating a distance measure as done by the program
[Mash](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4915045/), by mapping the
reads to the human genome, or by classifying the reads against a database
containing reference genomes and identifying if there are reads that do not
belong to the target species. This is often done with tools from metagenomics
such as [Kraken2](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6883579/),
[Centrifuge](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5131823/), etc.
