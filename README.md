# aida-doi-site PHP and XSLT code to generate:

1. An index page with a list of the DOIs issued by AIDA (SND.AIDA)
2. A landing page for each issued DOI

Pages are automatically generated from the DOI metadata available at DataCite
(and crossref for referenced articles), as well as a local json file
(issued_dois.json) that holds the link to the data set files refered to by the
DOI.

## Index page
Generated by XSLT transforming the xml returned by querying
DataCite for datacenter=SND.AIDA.

## Landing pages
Generated by XSLT transforming the xml returned by querying
DataCite for the specified DOI. Links to data set files are taken from the
issued_dois.json file (see below). Referenced articles are taken from querying
crossref for information.

*Note!* If DataCite updates the schema version the landing page has to update
the xmlns assigment at the top of the file.

## Links to data sets
This information is taken from a file that must be accessible as **data/issued_dois.json**.

## Usage
Router page php application serving index page at / or /doi/. Everything after
that is expected to be a DOI, eg:

* https://doi.aida.medtech4health.se/10.23698/aida/drsk
* https://aida.medtech4health.se/doi/10.23698/aida/drsk
* https://localhost:8888/10.23698/aida/drsk
* https://localhost:8888/doi/10.23698/aida/drsk

Route all requests to index.php regardless of URI, similar to:

`php -S localhost:8888 router.php`

Some docs for Apache / local development here:

* https://stackoverflow.com/questions/5218213/create-a-catch-all-handler-in-php
* http://www.php.net//manual/en/features.commandline.webserver.php#example-413
