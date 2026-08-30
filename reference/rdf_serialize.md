# Serialize an RDF Document

Serialize an RDF Document

## Usage

``` r
rdf_serialize(
  rdf,
  doc = NULL,
  format = c("guess", "rdfxml", "nquads", "ntriples", "turtle", "jsonld"),
  namespace = NULL,
  prefix = names(namespace),
  base = getOption("rdf_base_uri", "localhost://"),
  ...
)
```

## Arguments

- rdf:

  an existing rdf triplestore to extend with triples from the parsed
  file. Default will create a new rdf object.

- doc:

  file path to write out to. If null, will write to character.

- format:

  rdf serialization format of the doc, one of "rdfxml", "nquads",
  "ntriples", "turtle" or "jsonld". If not provided, will try to guess
  based on file extension and fall back on rdfxml.

- namespace:

  a named character containing the prefix to namespace bindings.
  `names(namespace)` are the prefixes, whereas `namespace` are the
  namespaces

- prefix:

  (optional) for backward compatibility. See `namespace`. It contains
  the matching prefixes to the namespaces in `namespace` and is set
  automatically if you provide `namespace` as a named character vector.

- base:

  the base URI to assume for any relative URIs (blank nodes)

- ...:

  additional arguments to
  [`redland::serializeToFile`](https://docs.ropensci.org/redland/reference/serializeToFile.html)

## Value

rdf_serialize returns the output file path `doc` invisibly. This makes
it easier to use rdf_serialize in pipe chains with
[`rdf_parse`](https://docs.ropensci.org/rdflib/reference/rdf_parse.md).

## Examples

``` r
infile <- system.file("extdata", "dc.rdf", package="redland")
out <- tempfile("file", fileext = ".rdf")

some_rdf <- rdf_parse(infile)
rdf_add(some_rdf,
    subject = "http://www.dajobe.org/dave-beckett",
    predicate = "http://www.w3.org/1999/02/22-rdf-syntax-ns#type",
    object = "http://xmlns.com/foaf/0.1/Person")
rdf_serialize(some_rdf, out)

## With a namespace
rdf_serialize(some_rdf,
          out,
          format = "turtle",
          namespace = c(dc = "http://purl.org/dc/elements/1.1/",
          foaf = "http://xmlns.com/foaf/0.1/")
          )

readLines(out)
#>  [1] "@base <localhost://> ."                                         
#>  [2] "@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> ."   
#>  [3] "@prefix dc: <http://purl.org/dc/elements/1.1/> ."               
#>  [4] "@prefix foaf: <http://xmlns.com/foaf/0.1/> ."                   
#>  [5] ""                                                               
#>  [6] "<http://www.dajobe.org/>"                                       
#>  [7] "    dc:creator \"Dave Beckett\" ;"                              
#>  [8] "    dc:description \"The generic home page of Dave Beckett.\" ;"
#>  [9] "    dc:title \"Dave Beckett's Home Page\" ."                    
#> [10] ""                                                               
#> [11] "<http://www.dajobe.org/dave-beckett>"                           
#> [12] "    a foaf:Person ."                                            
#> [13] ""                                                               
```
