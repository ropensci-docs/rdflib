# Initialize an `rdf` Object

Initialize an `rdf` Object

## Usage

``` r
rdf(
  storage = c("memory", "BDB", "sqlite", "postgres", "mysql", "virtuoso"),
  host = NULL,
  port = NULL,
  user = NULL,
  password = NULL,
  database = NULL,
  charset = NULL,
  dir = NULL,
  dsn = "Local Virtuoso",
  name = "rdflib",
  new_db = FALSE,
  fallback = TRUE
)
```

## Arguments

- storage:

  Storage backend to use; see details

- host:

  host address for mysql, postgres, or virtuoso storage

- port:

  port for mysql (mysql storage defaults to mysql standard port, 3306)
  or postgres (postgres storage defaults to postgres standard port,
  4321)

- user:

  user name for postgres, mysql, or virtuoso

- password:

  password for postgres, mysql, or virtuoso

- database:

  name of the database to be created/used

- charset:

  charset for virtuoso database, if desired

- dir:

  directory of where to write sqlite or berkeley database.

- dsn:

  Virtuoso dsn, either "Local Virtuoso" or "Remote Virtuoso"

- name:

  name for the storage object created. Default is usually fine.

- new_db:

  logical, default FALSE. Create new database or connect to existing?

- fallback:

  logical, default TRUE. If requested storage system cannot initialize,
  should `rdf()` fall back on memory (default) or throw an error
  (fallback=FALSE)?

## Value

an rdf object

## Details

an rdf Object is a list of class 'rdf', consisting of three pointers to
external C objects managed by the redland library. These are the `world`
object: basically a top-level pointer for all RDF models, and a `model`
object: a collection of RDF statements, and a `storage` object,
indicating how these statements are stored.

`rdflib` defaults to an in-memory hash-based storage structure. which
should be best for most use cases. For very large triplestores,
disk-based storage will be necessary. Enabling external storage devices
will require additional libraries and custom compiling. See the storage
vignette for details.

## Examples

``` r
x <- rdf()
```
