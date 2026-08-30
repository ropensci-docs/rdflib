# Add RDF Triples

add a triple (subject, predicate, object) to the RDF graph

## Usage

``` r
rdf_add(
  rdf,
  subject,
  predicate,
  object,
  subjectType = as.character(NA),
  objectType = as.character(NA),
  datatype_uri = as.character(NA)
)
```

## Arguments

- rdf:

  an rdf object

- subject:

  character string containing the subject

- predicate:

  character string containing the predicate

- object:

  character string containing the object

- subjectType:

  the Node type of the subject, i.e. "uri", "blank"

- objectType:

  the Node type of the object, i.e. "literal", "uri", "blank"

- datatype_uri:

  the datatype URI to associate with a object literal value

## Value

Silently returns the updated RDF graph (rdf object). Since the rdf
object simply contains external pointers to the model object in C code,
note that the input object is modified directly, so you need not assign
the output of rdf_add() to anything.

## Details

`rdf_add()` will automatically 'duck type' nodes (if looks like a
duck...). That is, strings that look like URIs will be declared as URIs.
(See [URI](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier)).
Predicate should always be a URI (e.g. URL or a `prefix:string`), cannot
be blank or literal. Subjects that look like strings will be treated as
[Blank Nodes](https://en.wikipedia.org/wiki/Blank_node) (i.e. will be
prefixed with `_:`). An empty subject, `""`, will create a blank node
with random name. Objects that look like URIs will be typed as resource
nodes, otherwise as literals. An empty object `""` will be treated as
blank node. Set `subjectType` or `objectType` explicitly to override
this behavior, e.g. to treat an object URI as a literal string. NAs are
also treated as blank nodes in subject or object See examples for
details.

## References

<https://en.wikipedia.org/wiki/Uniform_Resource_Identifier>

## Examples

``` r
rdf <- rdf()
rdf_add(rdf, 
    subject="http://www.dajobe.org/",
    predicate="http://purl.org/dc/elements/1.1/language",
    object="en")
    
## non-URI string in subject indicates a blank subject
## (prefixes to "_:b0")
rdf_add(rdf, "b0", "http://schema.org/jobTitle", "Professor") 

## identically a blank subject.  
## Note rdf is unchanged when we add the same triple twice.
rdf_add(rdf, "b0", "http://schema.org/jobTitle", "Professor", 
        subjectType = "blank") 
        
## blank node with empty string creates a default blank node id
rdf_add(rdf, "", "http://schema.org/jobTitle", "Professor")   
                    

## Subject and Object both recognized as URI resources:
rdf_add(rdf, 
        "https://orcid.org/0000-0002-1642-628X",
        "http://schema.org/homepage", 
        "http://carlboettiger.info")  

 ## Force object to be literal, not URI resource        
rdf_add(rdf, 
        "https://orcid.org/0000-0002-1642-628X",
        "http://schema.org/homepage", 
        "http://carlboettiger.info",
        objectType = "literal")  
        
```
