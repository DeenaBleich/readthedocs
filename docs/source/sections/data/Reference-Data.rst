**************
Reference Data
**************

ISB-CGC Hosted Reference Data
#############################

In order to facilitate working with the TCGA data tables that the ISB-CGC is hosting in BigQuery, additional
reference data tables have also been created, others are hosted by Google Genomics, 
and suggestions for more are welcome at feedback@isb-cgc.org.


Genome Reference Data
=====================

Reference data that describes or annotates the human (or other) genome(s) is described in this section.  
Reference data hosted by the ISB-CGC in BigQuery tables are available in the ``isb-cgc:genome_reference`` 
`dataset <https://bigquery.cloud.google.com/dataset/isb-cgc:genome_reference>`_.  Tables based on 
gene-sets such as Ensembl and GENCODE can be used to find the genomic coordinates and identifiers
for genes of interest, in order to perform queries that join tables with gene-symbol based data
to tables with genomic-coordinate based data or tables that use other gene identifiers, for example.

For additional details about each of these tables, please use the `BigQuery web UI <https://bigquery.cloud.google.com>`_ 
to access each of these tables and look at the information on the **Details** page.  (Look for the Details button
between the Schema and Preview buttons, beneath the table name.)

  * **Ensembl**
     - GRCh37 : Release 75, the final build of the Ensembl_ gene-set mapped to GRCh37
     - GRCh38 : Release 87, the most recent Ensembl_ gene-set mapped to GRCh38

  * **GENCODE**
     - GRCh37 : Release 19, the final build of the GENCODE_ gene-set mapped to GRCH37
     - GRCh38 : Releases 22, 23, and 24 from GENCODE_ are all available (because the TCGA data has been reprocessed by at least one center using each of these three different releases) 

  * **Gene Ontology Consortium** : Tables based on GO_ annotations and the GO_ ontology.

  * **Kaviar** : The latest hg19- and hg38-based Kaviar_ databases are available.  Kaviar_ is a compilation of SNVs, indels, and complex variants observed in humans, designed to facilitate testing for the novelty and frequency of observed variants.

  * **liftOver_hg19_to_hg38** : This table provides a mapping of each hg19 position to the corresponding position in hg38, and can be used to perform a liftOver_ operation in BigQuery

  * **miRBase**
     - GRCh37 : The human portion of version 20 of the miRBase_ database; including genomic coordinates for human microRNAs.
     - GRCh38 : The human portion of version 21 of the miRBase_ database; including genomic coordinates for human microRNAs.

  * **miRTarBase** The recently updated miRTarBase_ database (release 6.1)

  * **Reactome**
     - Ensembl2Reactome
     - miRBase2Reactome

.. _liftOver: https://genome.ucsc.edu/cgi-bin/hgLiftOver
.. _GO: http://www.geneontology.org/
.. _Ensembl: http://uswest.ensembl.org/index.html
.. _GENCODE: https://www.gencodegenes.org/releases/
.. _Kaviar: http://db.systemsbiology.net/kaviar/
.. _miRBase: http://www.mirbase.org/
.. _miRTarBase: http://nar.oxfordjournals.org/content/early/2015/11/19/nar.gkv1258.long


Platform Reference Data
=======================

Some reference data is necessary in order to work with data generated by specific platforms such as the
Illumina DNA Methylation array, or the Affymetrix Genome-Wide Human SNP Array 6.0.  This section will
provide links to existing sources of information elsewhere on the web, or will describe additional resources
that are hosted by the ISB-CGC.  If there are additional platform reference sources that you would like
to see hosted in BigQuery tables, please let us know at feedback@isb-cgc.org.

 * **DNA Methylation Platform**
    - Most of the DNA Methylation data produced by the TCGA project was obtained using the Illumina Infinium HumanMethylation450 (aka 450k) BeadChip array.  Some of the earlier tumor types were assayed on the older, 27k array.

    - Although additional details can be found at the `Illumina <https://www.illumina.com/>`_ webpage, we have uploaded the platform annotation information into the BigQuery table ``isb-cgc:platform_reference.methylation_annotation``

    - Each CpG locus is uniquely identified as described in this `technical note <http://www.illumina.com/content/dam/illumina-marketing/documents/products/technotes/technote_cpg_loci_identification.pdf>`_ and this unique identifier can be used to look up and cross-reference data between the TCGA DNA methylation data table and the platform annotation table. 

    - The original Illumina-provided CpG coordinates have been *"lifted over"* from hg19 to hg38


  * **Genome-Wide SNP Array**
    - The technical documentation for the Affymetrix Genome-Wide Human SNP Array 6.0 array can be found `here <http://www.affymetrix.com/catalog/131533/AFFY/Genome-Wide+Human+SNP+Array+6.0#1_3>`_


Other Reference Data Sources
############################

In collaboration with the Wellcome Trust Sanger Institute, the ISB-CGC is hosting the 
`COSMIC database <http://isb-cancer-genomics-cloud.readthedocs.io/en/latest/sections/COSMIC.html>`_.

Google Genomics maintains a list of 
`publicly available datasets <http://googlegenomics.readthedocs.org/en/latest/use_cases/discover_public_data/index.html>`_, 
including **Reference Genomes**, 
the **Illumina Platinum Genomes**, information about the **Tute Genomics Annotation** table, *etc*.


