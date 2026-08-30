# Concatenate rdf Objects.

All subsequent rdf objects will be appended to the first rdf object
Note: this does not free memory from any of the individual rdf objects
Note: It is generally better to avoid the use of this function by
passing an existing rdf object to and rdf_parse or rdf_add objects.
Multiple active rdf objects can cause problems when using disk-based
storage backends.

## Usage

``` r
# S3 method for class 'rdf'
c(...)
```

## Arguments

- ...:

  objects to be concatenated
