# rdflib: Tools to Manipulate and Query Semantic Data

The Resource Description Framework, or RDF is a widely used data
representation model that forms the cornerstone of the Semantic Web.
'RDF' represents data as a graph rather than the familiar data table or
rectangle of relational databases.

## Details

It has three main goals:

- Easily read, write, and convert between all major RDF serialization
  formats

- Support SPARQL queries to extract data from an RDF graph into a
  data.frame

- Support JSON-LD format as a first-class citizen in RDF manipulations

For more information, see the Wikipedia pages for RDF, SPARQL, and
JSON-LD:

- <https://en.wikipedia.org/wiki/Resource_Description_Framework>

- <https://en.wikipedia.org/wiki/SPARQL>

- <https://en.wikipedia.org/wiki/JSON-LD>

To learn more about rdflib, start with the vignettes:
`browseVignettes(package = "rdflib")`

Configurations via [`options()`](https://rdrr.io/r/base/options.html)

`rdf_print_format`:

- NULL or "nquads" (default)

- any valid serializer name: e.g. "rdfxml", "jsonld", "turtle",
  "ntriples"

`rdf_base_uri`:

- Default base URI to use (when serializing JSON-LD only at this time)
  default is "localhost://"

`rdf_max_print`:

- maximum number of lines to print from rdf, default 10

## See also

Useful links:

- <https://github.com/ropensci/rdflib>

- Report bugs at <https://github.com/ropensci/rdflib/issues>

## Author

**Maintainer**: Carl Boettiger <cboettig@gmail.com>
([ORCID](https://orcid.org/0000-0002-1642-628X)) \[copyright holder\]

Other contributors:

- Bryce Mecum ([ORCID](https://orcid.org/0000-0002-0381-3766))
  \[reviewer\]

- Anna Krystalli ([ORCID](https://orcid.org/0000-0002-2378-4915))
  \[reviewer\]

- Viktor Senderov <vsenderov@gmail.com>
  ([ORCID](https://orcid.org/0000-0003-3340-5963)) \[contributor\]
