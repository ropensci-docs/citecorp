# Methods for getting IDs from other IDs

Methods for getting IDs from other IDs

## Usage

``` r
oc_doi2ids(id, ...)

oc_pmid2ids(id, ...)

oc_pmcid2ids(id, ...)
```

## Arguments

- id:

  One or more digital object identifiers (DOI), PMID, or PMCID,
  depending on the function

- ...:

  curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

data.frame, with four columns:

- doi: digital object identifier

- pmid: pubmed identifier

- pmcid: pubmed central identifier

- paper: open citations corpus url

An empty data.frame (no columns or rows) when no results found

Column order will always be the same; note though that some columns may
be missing if, for example, there's no PMID for a DOI search.

## Examples

``` r
if (oc_lookup_check()) {
try(
  oc_doi2ids("10.1097/igc.0000000000000609", timeout_ms=10),
  silent = TRUE
)
}

### More examples
if (FALSE) { # \dontrun{
oc_doi2ids('10.1093/biomet/80.3.527')
oc_doi2ids('10.1093/biomet/79.3.531')
oc_pmid2ids("31857888")
oc_pmcid2ids("PMC6422012")

oc_doi2ids(id = oc_dois[1:3])
oc_pmid2ids(id = oc_pmids[1:3])
oc_pmcid2ids(id = oc_pmcids[1:3])
} # }
```
