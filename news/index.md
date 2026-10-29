# Changelog

## citecorp 0.3.0

CRAN release: 2020-04-16

#### NEW FEATURES

- [`oc_coci_refs()`](https://docs.ropensci.org/citecorp/reference/oc_coci.md),
  [`oc_coci_cites()`](https://docs.ropensci.org/citecorp/reference/oc_coci.md),
  and
  [`oc_coci_citation()`](https://docs.ropensci.org/citecorp/reference/oc_coci.md)
  now support more than one DOI or COCI identifier passed in.
  [`oc_coci_meta()`](https://docs.ropensci.org/citecorp/reference/oc_coci.md)
  already supported more than one identifier; now all four `oc_coci*`
  methods support more than one identifier. The caveat is that the API
  route behindn
  [`oc_coci_meta()`](https://docs.ropensci.org/citecorp/reference/oc_coci.md)
  supports \>1 identifier in a single http request - whereas the API
  routes behind the other functions only support one identifier per
  request, so they make an http request for each identifier passed in
  ([\#6](https://github.com/ropensci/citecorp/issues/6))

#### MINOR IMPROVEMENTS

- added tests for Cloudflare http status codes
  ([\#7](https://github.com/ropensci/citecorp/issues/7))

## citecorp 0.2.2

CRAN release: 2019-12-09

#### BUG FIXES

- better check if http requests will work before running examples that
  require http requests
  ([\#5](https://github.com/ropensci/citecorp/issues/5))

## citecorp 0.2.0

CRAN release: 2019-11-07

#### NEW FEATURES

- the functions `oc_doi2ids`, `oc_pmid2ids`, and `oc_pmcid2ids` (see
  [`?oc_lookup`](https://docs.ropensci.org/citecorp/reference/oc_lookup.md))
  now all accept more than 1 identifier. the underlying SPARQL queries
  were modified to make this possible.
  ([\#1](https://github.com/ropensci/citecorp/issues/1))
- three new package datasets (oc_dois, oc_pmids, oc_pmcids) with vectors
  of identifiers of each of those types for testing and examples

#### BUG FIXES

- fixed an error in parsing results in `oc_lookup` functions - this fix
  was later changed as part of another fix, but still appreciated
  ([\#2](https://github.com/ropensci/citecorp/issues/2))
  ([\#3](https://github.com/ropensci/citecorp/issues/3)) thanks
  [@Selbosh](https://github.com/Selbosh)
- fix to parsing in `oc_lookup` functions: only retrieve data.frame
  columns if they exist - prevents error on retrieving a column that
  doesn’t exist ([\#4](https://github.com/ropensci/citecorp/issues/4))
  thanks [@Selbosh](https://github.com/Selbosh)

## citecorp 0.1.0

CRAN release: 2019-08-24

#### NEW FEATURES

- Released to CRAN
