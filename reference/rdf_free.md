# Free Memory Associated with RDF object

Free Memory Associated with RDF object

## Usage

``` r
rdf_free(rdf, rm = TRUE)
```

## Arguments

- rdf:

  an rdf object

- rm:

  logical, default TRUE. Remove pointer from parent.frame()? Usually a
  good idea since referring to a pointer after it has been removed can
  crash R.

## Details

Free all pointers associated with an rdf object. Frees memory associated
with the storage, world, and model objects.

## Examples

``` r
rdf <- rdf()
rdf_free(rdf)
rm(rdf)
#> Warning: object 'rdf' not found
```
