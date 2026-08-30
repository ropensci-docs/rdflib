# Changelog

## rdflib 0.2.9

CRAN release: 2024-08-17

- Address CRAN vignette building.

## rdflib 0.2.8

CRAN release: 2023-12-19

- tests fail gracefully on CRAN without internet resources

## rdflib 0.2.7

CRAN release: 2023-09-16

make jsonld an optional dependency

## rdflib 0.2.6

CRAN release: 2023-03-09

- bugfix vroom warning

## rdflib 0.2.5

CRAN release: 2022-02-09

- bugfix UTF-8

## rdflib 0.2.4

CRAN release: 2022-01-03

- bugfix in write_nquads() for rdf method

## rdflib 0.2.3 2020-01-10

CRAN release: 2020-01-10

- Drop import of deprecated redland method, getNextResult
  ([\#33](https://github.com/ropensci/rdflib/issues/33))

## rdflib 0.2.2 2019-01-15

CRAN release: 2019-01-15

- Minor patch to fix license file
- Updates documentation with hex

## rdflib 0.2.1 2018-11-25

CRAN release: 2018-11-25

- Minor patch to make test compatible with breaking change in readr
  1.2.0 ([\#30](https://github.com/ropensci/rdflib/issues/30))

## rdflib 0.2.0 2018-11-13

CRAN release: 2018-11-13

### New Features

- [`rdf()`](https://docs.ropensci.org/rdflib/reference/rdf.md) supports
  all major storage backends: Virtuoso, SQLite, Postgres, MySQL, in
  addition to existing support for BDB and memory-based storage.
- [`length()`](https://rdrr.io/r/base/length.html) method added to
  report length of triplestore
- [`print()`](https://rdrr.io/r/base/print.html) method gains
  `rdf_max_print()` option and does not print huge triplestores
- [`print()`](https://rdrr.io/r/base/print.html) method sumarizes total
  number of triples and backend

## rdflib 0.1.0 (2018-03-02)

CRAN release: 2018-03-09

### New Features

- [`rdf()`](https://docs.ropensci.org/rdflib/reference/rdf.md) supports
  BDB backend for disk-based storage for large triplestores
  [\#6](https://github.com/ropensci/rdflib/issues/6)
- [`rdf_parse()`](https://docs.ropensci.org/rdflib/reference/rdf_parse.md)
  gains an argument `rdf` to append triples to existing graph
- adds [`c()`](https://rdrr.io/r/base/c.html) method to concatenate
  `rdf` objects
- Performance improvements make it possible to handle triplestores with
  millions of triples
- Two new vignettes better introduce RDF and package functions.

### Minor Improvements

- `rdf_query` now bypasses the very slow iteration over `getNextResult`
  approach and uses an internal redland function call to access all
  results at once in csv format.

- experimental `as_rdf` method now uses a poor-man’s nquad serializer to
  rapidly generate rdf (instead of slowly iterating over `add_rdf`).

- `rdf_add` argument for `object` can now take all atomic types
  (numeric, integer, string, Date, POSIX, logical) and will
  automatically declare the appropriate `datatype_uri` if the user has
  not manually specified this.

- Numerous improvements to documentation from rOpenSci onboarding
  feedback, see [\#9](https://github.com/ropensci/rdflib/issues/9) and
  [\#10](https://github.com/ropensci/rdflib/issues/10)

- both functions and unit tests are broken out into separate files in
  their respective directories.

- Additional example RDF data added in `extdata`

- `rdf_serialize` passes `...` arguments to serializeToFile (e.g. to set
  a `baseUri`)

### Bug Fixes

- [`rdf_free()`](https://docs.ropensci.org/rdflib/reference/rdf_free.md)
  will also remove the object from the parent frame, reducing the
  potential for crashing R by referring to a freed pointer.
- fix encoding with UTF-8 characters (coming from nquads & ntriples)
- [`rdf_query()`](https://docs.ropensci.org/rdflib/reference/rdf_query.md)
  now coerces data into appropriate type if it recognizes the data URI
  and can match that to an R type (a few XMLSchema types are recognized,
  otherwise still defaults to character string)
- Memory management: All methods free memory from any temporary objects
  they initialize, tests free memory. (e.g. parsers, serializers, query,
  statement)
- extend unit tests to cover new features, check UTF-8
- `turtle` parser/serializer fixed

### Deprecated

- `trig` support removed (not working in redland without optional
  libraries and alternative compile configuration)

## rdflib 0.0.3 (2018-01-02)

### Bug Fixes

- add paper.md
- add package level documentation
- set base uri when serializing json-ld to rdf
  ([\#5](https://github.com/ropensci/rdflib/issues/5))

## rdflib 0.0.2 (2018-01-02)

### New Features

- Added a `NEWS.md` file to track changes to the package.
- sparql query returns a data.frame format
- added a vignette
- added pkgdown website for vignette

## rdflib 0.0.1 (2017-12-09)

- Initial prototype
