# ![LOGO](logo.png) VisibleThread **flow**ground Connector

## Description

A generated **flow**ground connector for the VisibleThread API (version 1.0).

Generated from: https://api.apis.guru/v2/specs/visiblethread.com/1.0/swagger.json<br/>
Generated at: 2019-05-07T17:44:43+03:00

## API Description

## Introduction
The VisibleThread b API provides services for analyzing/searching documents and web pages.
To use the service you need an API key. 

**Contact us at support@visiblethread.com to request an API key**. 

The services are split into **Documents** and **Webscans**.

### Documents
Upload documents and dictionaries so you can :
- Measure the readability of your document
- search a document for all terms from a dictionary
- retrieve all paragraphs from a document or only matching paragraphs

### Webscans
Analyze web pages so you can: 
- Measure the readability of your web content
- Identify & highlight content issues e.g. long sentences, passive voice

The VisibleThread API allows you to programatially submit webpage urls to be scanned, 
check on the results of a scan, and view a list of previous scans you have performed.
    
-------------

The VisibleThread API is a HTTP-based JSON API, accessible at https://api.visiblethread.com 
Each request to the service requires your API key to be successful.

## Getting Started With Webscans

Steps:
1. Enter your API key above and hit **Explore**. 
2. Run a new scan by submitting a **POST to /webscans** (title and some webUrls are required).
   The scan runs asynchronously in the background but returns immediately with a JSON response containing an "id" that represents your scan.
3. Check on the status of a scan by submitting **GET /webscans/{scanId}**, if the scan is still in progress it will return a HTTP 503. If 
   it is complete it will return a HTTP 200 with the appropriate JSON outlining the urls scanned and the summary statistics for each url.
4. Retrieve all your previous scan results by submitting **GET /webscans**.  
5. Retrieve detailed results for a url within a scan (readability, long sentence and passive language instances) by submitting 
   **GET /webscans/{scanId}/webUrls/{urlId}** (scanId and urlId are required)

## Getting Started With Document scans:

Steps:
1. Enter your API key above and hit **Explore**
2. Run a new scan by submitting a **POST to /documents** (document required). The scan runs asynchronously in the background but returns
   immediately with a JSON response containins an "id" that represents your scan
3. Check on the status of a scan by submitting **GET /documents/{scanId}**, if the scan is still in progress it will return a HTTP 503. If 
   it is complete it will return a HTTP 200 with the appropriate JSON outlining the document readability results. It will contain detailed
   analysis of each paragraph in the document
4. Retrieve all your previous scan results by submitting **GET /documents**

### Searching a document for keywords

The VisibleThread API allows you to upload a set of keywords or a 'dictionary'. You can then perform a search of a already uploaded document 
using that dictionary

Steps (Assuming you have uploaded your document using the steps above):
1. Upload a csv file to use as a keyword dictionary by submitting a **POST to /dictionaries** (csv file required). This returns a JSON 
   response with the dictionary Id 
2. Search a document with the dictionary by submitting a **POST to /searches** (document id and dictionary id required). 
3. Get the resuhlts of the search by submitting  **GET /searches/{docId}/{dictionaryId}" . This will return JSON response containing 
   detailed results of searching the document using the dictionary.
4. To view the list of all searches you have performed submit a **GET /searches**. 

Below is a list of the available API endpoints, documentation & a form to try out each operation.

## Authorization

Supported authorization schemes:
- API Key
## Actions

### Get your list of dictionaries

*Tags:* `Documents`

### Upload a dictionary (CSV)

> Upload a dictionary (CSV format) to your VisibleThread account.

*Tags:* `Documents`

### Get your list of documents

*Tags:* `Documents`

### Upload a document

> Upload a document to your VisibleThread account. <br/>
> We return a JSON response that contains a "docId" that represents your document.        <br/>
> You can use this id in other requests to check on the analysis status for the document and run a dictionary search and retrieve search<br/>
> results.

*Tags:* `Documents`

### Get data from a previously submitted document

> Get data from a previously submitted document identified by ***docId***

*Tags:* `Documents`

#### Input Parameters
* `docId` - _required_ - Id of document to fetch

### Get your list of searches

*Tags:* `Documents`

### Run a search

> Run a search on document **docId** using dictionary **dictId**

*Tags:* `Documents`

### Gets search results for a particular document/dictionary

> Get detailed results for a scan/url (readability, long sentence and passive language instances), identified by **scanId** & **urlId**

*Tags:* `Documents`

#### Input Parameters
* `docId` - _required_ - Id of document
* `dictionaryId` - _required_ - Id of dictionary
* `matchingOnly` - _required_ - Only returning paragraphs containing a match

### Get your list of scans

*Tags:* `Webscans`

### Run a new scan

> The scan runs in the background but returns immediately with a JSON response containing an "id" that represents your scan.        <br/>
> You can use this id in other requests to retrieve your scan result. <br/>
> <br/>
> Also, an "id" is returned for each url which can be used to retrieve detailed results for individual scan urls.

*Tags:* `Webscans`

### Get data from a previously run scan

> Get data from a previously run scan, identified by **scanId**

*Tags:* `Webscans`

#### Input Parameters
* `scanId` - _required_ - Id of scan to fetch

### Gets data for a particular scan/webUrl

> Get detailed results for a scan/url (readability, long sentence and passive language instances), identified by **scanId** & **urlId**

*Tags:* `Webscans`

#### Input Parameters
* `scanId` - _required_ - Id of scan
* `urlId` - _required_ - Id of url to fetch

## License

**flow**ground :- Telekom iPaaS / visiblethread-com-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
