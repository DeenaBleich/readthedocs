**********************
Cloud-Hosted Data Sets
**********************

The ISB-CGC platform hosts the majority of the TCGA data set as well as other reference
and annotation datasets in different appropriate Google Cloud technologies:

    * low-level DNA- and RNA-Seq data are stored primarily in `Google Cloud Storage <https://cloud.google.com/storage/>`_;
    * high-level clinical, biospecimen, and molecular data are available in a series of carefully curated datasets and tables backed by the massively-parallel analytics engine `Google BigQuery <https://cloud.google.com/bigquery/>`_;
    * TCGA radiology and tissue image data are now also available in Google Cloud Storage;
    * TCGA proteomics (CPTAC PhaseII) data has also been uploaded to Google Cloud Storage;

The original mission of the ISB-CGC was to host the TCGA dataset.  We are now in midst
of adding data from the TARGET pediatric cancer.  Stay tuned for updates.

A note about legacy and harmonized data sets
++++++++++++++++++++++++++++++++++++++++++++
Programs like TCGA that pre-date the Genomic Data Commons will have both legacy data sets (data as originally generated by the program) and harmonized data sets created by the Genomic Data Commons.  Whiles these data sets do have much in common, as the GDC works through its harmonization process a number of changes can occur including removal or addition of cases and samples or changes in terminology.  One of the goals of the ISB-CGC is to stay current with changes introduced by GDC and therefore you may find differences between legacy data and harmonized data.

.. toctree::
   :maxdepth: 2

   data/NCI_Programs
   data/GDC_top
   data/Data_on_ISBCGC
   data/Reference-Data
   data/Releases-Plus

