# CoRNS.py: A Python utility for Complementary Reserve Network Selection

CoRNS.py version 1.0.1 -- 12 December 2016  
[![DOI](https://zenodo.org/badge/75750500.svg)](https://zenodo.org/badge/latestdoi/75750500)

CoRNS.py is a Python script for performing a simple greedy-richness algorithm on a site by species presence-absence matrix to select sites to include as part of a reserve network. The method is a complementary based approach, so the most diverse site will be selected first, followed by the site that adds the greatest number of species considering the taxa that have already been preserved. The process is repeated until all sites have been ordered for selection. In the case that one or more sites add the same number of species, the site that is encountered first is selected. For full description see algorithm 1 in Csuti et al. 1997. Biological Conservation 80(1): 83--97. A second site by species matrix can be optionally provided to assess how well reserves selected for the taxa in the first provided matrix also confer protection for the taxa in the second provided matrix. This could be useful for conservation purposes in assessing whether one organismal groups serves as an effective surrogate group for a second organismal group.


The output (see `my_run.csv` for example) is a csv file containing the following columns:

1. Order -- 1 to n sites. The order in which sites were selected.

2. Site_name -- The site names ordered for the purpose of conservation.

3. \<first dataset name\>\_species_count -- The cumulative alpha-diversity of
species in the first dataset.

4. \<first dataset name\>\_percent_diversity -- Cumulative percent of total
diversity of species from the first dataset.

The output in the first four columns is all based on the first site-by-species
dataset (designated by the option `-i`). If a second site-by-species dataset is
provided (with the option `-m`) to test whether the reserve set based on the
organisms in the first dataset effectively conserve the species in the second
dataset, then the output also contains:

5. \<second dataset name\>\_species_count -- The corresponding cumulative
alpha-diversity of species in the second dataset.

6. \<second dataset name\>\_percent_diversity -- The corresponding cumulative
percent of total diversity of species in the second dataset.

================================================================================
## CITATION

If you use this program, please cite:

Dorey, J.E. & N.R. Salinas. 2016. CoRNS.py v. 1.0.1 A Python utility for Complementary Reserve Network Selection. doi: 10.5281/zenodo.200391

================================================================================
## REQUIREMENTS

* A Python 2.7 interpreter.

================================================================================
## INSTRUCTIONS

1. One or two site by species matrices should be provided in CSV file format.
The first column should contain taxon names, beginning in the second row. The
first row should contain site names, beginning in the second column.

2. All taxon names and all site names should be unique. Every taxon must be
present at least once. Every site must contain at least one species.

3. Do not include commas, single quotes, or double quotes in any of the cells in
your CSV files---quotes will be deleted and in-text commas will cause problems reading the file.

4. The site by species matrix is presence-absence only. Abundance is not taken
into consideration. Enter **only** ones and zeros to represent whether a species is
present or absent at each site. See example files `angio_matrix.csv` and
`fern_matrix.csv` for further specification.

5. For a complete list of options execute `python corns.py -h`

6. Version 1.0 cannot process input files with Mac end of line characters ("\r").

================================================================================
## EXAMPLE

python corns.py -i angio_matrix.csv -m fern_matrix.csv -o my_run

================================================================================
## CONTACT

Jenna E. Dorey  
Graduate Fellow  
The New York Botanical Garden  
jedorey@umich.edu

Nelson R. Salinas  
Gerstner Postdoctoral Fellow  
Division of Invertebrate Zoology  
American Museum of Natural History  
nrsalinas@gmail.com
