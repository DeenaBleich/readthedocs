samples().cloud_storage_file_paths()
#####################################
Takes a sample barcode as a required parameter and returns cloud storage paths to files associated with that sample.

**Example**::

	curl https://api-dot-isb-cgc.appspot.com/_ah/api/isb_cgc_ccle_api/v3/ccle/samples/CCLE-LS1034/cloud_storage_file_paths

**API explorer example**:

Click `here <https://apis-explorer.appspot.com/apis-explorer/?base=https%3A%2F%2Fapi-dot-isb-cgc.appspot.com%2F_ah%2Fapi#p/isb_cgc_ccle_api/v3/isb_cgc_ccle_api.samples.cloud_storage_file_paths?sample_barcode=CCLE-LS1034>`_ to see this endpoint in Google's API explorer.

**Python API Client Example**::

	from googleapiclient.discovery import build
	import httplib2

	def get_unauthorized_service():
		api = 'isb_cgc_ccle_api'
		version = 'v3'
		site = 'https://api-dot-isb-cgc.appspot.com'
		discovery_url = '%s/_ah/api/discovery/v1/apis/%s/%s/rest' % (site, api, version)
		return build(api, version, discoveryServiceUrl=discovery_url, http=httplib2.Http())

	service = get_unauthorized_service()
	data = service.samples().cloud_storage_file_paths(sample_barcode='CCLE-LS1034').execute()


**Request**

HTTP request::

	GET https://api-dot-isb-cgc.appspot.com/_ah/api/isb_cgc_ccle_api/v3/ccle/samples/{sample_barcode}/cloud_storage_file_paths

**Parameters**

.. csv-table::
	:header: "**Parameter name**", "**Value**", "**Description**"
	:widths: 50, 10, 50

	analysis_workflow_type,string,"Optional. "
	data_category,string,"Optional. "
	data_format,string,"Optional. "
	data_type,string,"Optional. "
	experimental_strategy,string,"Optional. "
	genomic_build,string,"Optional. "
	platform,string,"Optional. "
	sample_barcode,string,"Required. "


**Response**

If successful, this method returns a response body with the following structure:

.. code-block:: javascript

  {
    "cloud_storage_file_paths": [string],
    "count": integer
  }

.. csv-table::
	:header: "**Parameter name**", "**Value**", "**Description**"
	:widths: 50, 10, 50

	cloud_storage_file_paths[], list, "List of Google Cloud Storage paths of files associated with the cohort."
	count, integer, "Number of Google Cloud Storage paths returned for the cohort."
