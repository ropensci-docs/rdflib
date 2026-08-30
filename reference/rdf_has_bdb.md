# Check for BDB support

Detect whether Berkeley Database for disk-based storage of RDF graphs is
available. Disk-based storage requires redland package to be installed
from source with support for the Berkeley DB (libdb-dev on Ubuntu,
berkeley-db on homebrew), otherwise
[`rdf()`](https://docs.ropensci.org/rdflib/reference/rdf.md) will fall
back to in-memory storage with a warning.

## Usage

``` r
rdf_has_bdb()
```

## Value

TRUE if BDB support is detected, false otherwise

## Examples

``` r
rdf_has_bdb()
#> [1] TRUE
```
