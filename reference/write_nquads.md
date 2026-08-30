# write object out as nquads

write object out as nquads

## Usage

``` r
write_nquads(x, file, ...)
```

## Arguments

- x:

  an object that can be represented as nquads

- file:

  output filename

- ...:

  additional parameters, see examples

## Examples

``` r
tmp <- tempfile(fileext = ".nq")
library(datasets)

## convert data.frame to nquads
write_nquads(iris, tmp)
#> Warning: prefix not declared, using df:
rdf <- read_nquads(tmp)

## or starting a native rdf object
write_nquads(rdf, tempfile(fileext = ".nq"))
```
