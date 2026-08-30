# read an nquads file

read an nquads file

## Usage

``` r
read_nquads(file, ...)
```

## Arguments

- file:

  path to nquads file

- ...:

  additional arguments to
  [`rdf_parse()`](https://docs.ropensci.org/rdflib/reference/rdf_parse.md)

## Value

an rdf object. See
[`rdf_parse()`](https://docs.ropensci.org/rdflib/reference/rdf_parse.md)

## Examples

``` r
tmp <- tempfile(fileext = ".nq")
library(datasets)
write_nquads(iris, tmp)
#> Warning: prefix not declared, using df:
read_nquads(tmp)
#> Total of 750 triples, stored in hashes
#> -------------------------------
#> <df:28> <df:Sepal.Width> "3.5"^^<http://www.w3.org/2001/XMLSchema#decimal> .
#> <df:3> <df:Sepal.Width> "3.2"^^<http://www.w3.org/2001/XMLSchema#decimal> .
#> <df:126> <df:Petal.Width> "1.8"^^<http://www.w3.org/2001/XMLSchema#decimal> .
#> <df:38> <df:Petal.Width> "0.1"^^<http://www.w3.org/2001/XMLSchema#decimal> .
#> <df:111> <df:Sepal.Length> "6.5"^^<http://www.w3.org/2001/XMLSchema#decimal> .
#> <df:149> <df:Sepal.Width> "3.4"^^<http://www.w3.org/2001/XMLSchema#decimal> .
#> <df:84> <df:Sepal.Length> "6"^^<http://www.w3.org/2001/XMLSchema#decimal> .
#> <df:87> <df:Petal.Width> "1.5"^^<http://www.w3.org/2001/XMLSchema#decimal> .
#> <df:42> <df:Species> "setosa"^^<http://www.w3.org/2001/XMLSchema#string> .
#> <df:138> <df:Petal.Width> "1.8"^^<http://www.w3.org/2001/XMLSchema#decimal> .
#> 
#> ... with 740 more triples
```
