# COCI: OpenCitations Index of Crossref open DOI-to-DOI references

AFAICT this API is a REST wrapper around the SPARQL service

## Usage

``` r
oc_coci_refs(doi, exclude = NULL, filter = NULL, sort = NULL, ...)

oc_coci_cites(doi, exclude = NULL, filter = NULL, sort = NULL, ...)

oc_coci_meta(doi, exclude = NULL, filter = NULL, sort = NULL, ...)

oc_coci_citation(oci, ...)
```

## Arguments

- doi:

  (character) one or more Digital Object Identifiers (DOIs)

- exclude:

  (character) a field_name; all the rows that have an empty value in the
  field_name specified are removed from the result set

- filter:

  `=<field_name>:<operator><value>:` only the rows compliant with
  `<value>` are kept in the result set. The parameter `<operation>` is
  not mandatory. If `<operation>` is not specified, `<value>` is
  interpreted as a regular expression, otherwise it is compared by means
  of the specified operation. Possible operators are "=", "\<", and
  "\>". For instance, `filter=title:semantics?` returns all the rows
  that contain the string "semantic" or "semantics" in the field title,
  while `filter=date:>2016-05` returns all the rows that have a date
  greater than May 2016.

- sort:

  `=<order>(<field_name>):` sort in ascending (`<order>` set to "asc")
  or descending (`<order>` set to "desc") order the rows in the result
  set according to the values in `<field_name>`. For instance,
  `sort=desc(date)` sorts all the rows according to the value specified
  in the field date in descending order.

- ...:

  curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

- oci:

  (character) one or more Open Citation Identifiers (OCIs)

## Value

data.frame, see http://opencitations.net/index/coci/api/v1 for
explanation of the resulting columns

## References

http://opencitations.net/index/coci/api/v1,
https://github.com/opencitations/api-coci

## Examples

``` r
doi1 <- "10.1108/jd-12-2013-0166"
doi2 <- "10.1371/journal.pgen.1005937"
oci1 <-
 "02001010806360107050663080702026306630509-0200101080636102704000806"
oci2 <-
 "0200101000836191363010263020001036300010606-020010003083604090301050910"

if (
crul::ok(
"http://opencitations.net/index/coci/api/v1/references/10.1108/jd-12-2013-0166",
timeout_ms = 1000L)
) {
try(
  oc_coci_cites(doi1),
  silent = TRUE
)
}
#> Timeout was reached [api.opencitations.net]:
#> Resolving timed out after 127 milliseconds

### More examples
if (FALSE) { # \dontrun{
# references
oc_coci_refs(doi1, exclude = "oci")
oc_coci_refs(doi1, filter = "date:>2016-05", verbose = TRUE)
oc_coci_refs(doi2)
oc_coci_refs(c(doi1, doi2))

# citations
oc_coci_cites(doi1, exclude = "oci")
oc_coci_cites(doi2)
oc_coci_cites(c(doi1, doi2))

# metadata
oc_coci_meta(doi2)
oc_coci_meta(c(doi1, doi2))

# citation - an OCI instead of a DOI
oc_coci_citation(oci1)
oc_coci_citation(c(oci1, oci2))
} # }
```
