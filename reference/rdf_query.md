# Perform a SPARQL Query

Perform a SPARQL Query

## Usage

``` r
rdf_query(rdf, query, data.frame = TRUE, ...)
```

## Arguments

- rdf:

  an rdf object (e.g. from
  [`rdf_parse`](https://docs.ropensci.org/rdflib/reference/rdf_parse.md))

- query:

  a SPARQL query, as text string

- data.frame:

  logical, should the results be returned as a data.frame?

- ...:

  additional arguments to a redland initialize-Query

## Value

a data.frame of all query results (default.) Columns will be named
according to variable names in the SPARQL query. Returned object values
will be coerced to match the corresponding R type to any associated
datatype URI, if provided. If a column would result in mixed classes
(e.g. strings and numerics), all types in the column will be coerced to
character strings. If `data.frame` is false, results will be returned as
a list with each element typed by its data URI.

## Examples

``` r
doc <- system.file("extdata", "dc.rdf", package="redland")

sparql <-
'PREFIX dc: <http://purl.org/dc/elements/1.1/>
 SELECT ?a ?c
 WHERE { ?a dc:creator ?c . }'

rdf <- rdf_parse(doc)
rdf_query(rdf, sparql)
#> # A tibble: 1 × 2
#>   a                      c           
#>   <chr>                  <chr>       
#> 1 http://www.dajobe.org/ Dave Beckett
```
