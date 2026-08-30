# Parse RDF Files

Parse RDF Files

## Usage

``` r
rdf_parse(
  doc,
  format = c("guess", "rdfxml", "nquads", "ntriples", "turtle", "jsonld"),
  rdf = NULL,
  base = getOption("rdf_base_uri", "localhost://"),
  ...
)
```

## Arguments

- doc:

  path, URL, or literal string of the rdf document to parse

- format:

  rdf serialization format of the doc, one of "rdfxml", "nquads",
  "ntriples", "turtle" or "jsonld". If not provided, will try to guess
  based on file extension and fall back on rdfxml.

- rdf:

  an existing rdf triplestore to extend with triples from the parsed
  file. Default will create a new rdf object.

- base:

  the base URI to assume for any relative URIs (blank nodes)

- ...:

  additional parameters (not implemented)

## Value

an rdf object, containing the redland world and model objects

## Examples

``` r
doc <- system.file("extdata", "dc.rdf", package="redland")
rdf <- rdf_parse(doc)
```
