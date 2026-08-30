# Coerce an object into RDF

Coerce an object into RDF

## Usage

``` r
as_rdf(
  x,
  rdf = NULL,
  prefix = NULL,
  base = getOption("rdf_base_uri", "localhost://"),
  context = NULL,
  key_column = NULL
)
```

## Arguments

- x:

  an object to coerce into RDF (list, list-like, or data.frame)

- rdf:

  An existing rdf object, (by default a new object will be initialized)

- prefix:

  A default vocabulary (URI prefix) to assume for all predicates

- base:

  A base URI to assume for blank subject nodes

- context:

  a named list mapping any string to a URI

- key_column:

  name of a column which should be treated as the primary key in a
  table. must be unique

## Examples

``` r
as_rdf(mtcars)
#> Warning: prefix not declared, using df:
as_rdf(list(repo = "rdflib", owner = list("id", "ropensci")))
```
