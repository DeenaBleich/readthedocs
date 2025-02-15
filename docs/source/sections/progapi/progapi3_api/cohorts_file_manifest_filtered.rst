cohorts().file_manifest_filtered()
#####################################
Takes a cohort id as a required parameter and a filter set as a required data payload, and returns a manifest of all files associated with all the samples in that cohort, as well as their metadata, up to a default limit of 50,000 files. Authentication is required. User must have READER or OWNER permissions on the cohort.

**Example**::

	python isb_curl.py --data '{"disease_code": ["LUAD","AML"]}' https://api-dot-isb-cgc.appspot.com/_ah/api/isb_cgc_api/v3/cohorts/{COHORT ID}/file_manifest

**API explorer example**:

Click `here <https://apis-explorer.appspot.com/apis-explorer/?base=https://api-dot-isb-cgc.appspot.com/_ah/api#p/isb_cgc_api/v3/isb_cgc_api.cohorts.file_manifest_filtered>`_ to see this endpoint in Google's API explorer.

**Python API Client Example**::

	from googleapiclient.discovery import build
	from oauth2client.client import OAuth2WebServerFlow
	from oauth2client import tools
	from oauth2client.file import Storage
	import httplib2
	import os

	CLIENT_ID = '907668440978-0ol0griu70qkeb6k3gnn2vipfa5mgl60.apps.googleusercontent.com'
	CLIENT_SECRET = 'To_WJH7-1V-TofhNGcEqmEYi'
	EMAIL_SCOPE = 'https://www.googleapis.com/auth/userinfo.email'
	DEFAULT_STORAGE_FILE = os.path.join(os.path.expanduser('~'), '.isb_credentials')

	def get_credentials():
		oauth_flow_args = ['--noauth_local_webserver']
		storage = Storage(DEFAULT_STORAGE_FILE)
		credentials = storage.get()
		if not credentials or credentials.invalid:
			flow = OAuth2WebServerFlow(CLIENT_ID, CLIENT_SECRET, EMAIL_SCOPE)
			flow.auth_uri = flow.auth_uri.rstrip('/') + '?approval_prompt=force'
			credentials = tools.run_flow(flow, storage, tools.argparser.parse_args(oauth_flow_args))
		return credentials

	def get_authorized_service():
		api = 'isb_cgc_api'
		version = 'v3'
		site = 'https://api-dot-isb-cgc.appspot.com'
		discovery_url = '%s/_ah/api/discovery/v1/apis/%s/%s/rest' % (site, api, version)
		credentials = get_credentials()
		http = credentials.authorize(httplib2.Http())
		if credentials.access_token_expired or credentials.invalid:
			credentials.refresh(http)
		authorized_service = build(api, version, discoveryServiceUrl=discovery_url, http=http)
		return authorized_service

	service = get_authorized_service()
	data = service.cohorts().file_manifest(cohort_id=1, body={"disease_code": ["BRCA"]}).execute()


**Request**

HTTP request::

	POST https://api-dot-isb-cgc.appspot.com/_ah/api/isb_cgc_api/v3/cohorts/{cohort_id}/file_manifest
{
 "disease_code": [
  "LUSC",
  "BRCA"
 ]
}

**Parameters**

.. csv-table::
    :header: "**Parameter name**", "**Value**", "**Description**"
    :widths: 50, 10, 50

    cohort_id,string,"Required. "
	genomic_build,string,"Optional, The build for which to obtain file entries, default=hg19 "
	offset,string,"Optional, The number of file entries to skip before collecting for retrieval (eg. offset 5 = start at 6), default=0 "
	fetch_count,string,"Optional, The number of file entries to retrieve, default=50000 "

	data_category,string,"Optional. "
	data_format,string,"Optional. "
	data_type,string,"Optional. "
	experimental_strategy,string,"Optional. "
    platform,string,"Optional. "
    disease_code,string,"Optional. "


**Response**

If successful, this method returns a response body with the following structure:

.. code-block:: javascript

  {
    "file_list": [
        {
            "program": string,
            "case_barcode": string,
            "case_gdc_uuid": string,
            "file_path": string,
            "file_gdc_uuid": string,
            "disease_code": string,
            "project_short_name": string,
            "experimental_strategy": string,
            "platform": string,
            "data_category": string,
            "data_type": string,
            "data_format": string,
            "access": string
        }
    ],
    "total_file_count": integer,
    "files_retrieved": integer
  }

.. csv-table::
    :header: "**Parameter name**", "**Value**", "**Description**"
    :widths: 50, 10, 50

    file_list[{...}], list, "List of file detail entries of files associated with the cohort."
    total_file_count, integer, "Total number of file entries found for this cohort."
    files_retrieved, integer, "Total number of file entries retrieved in this response."