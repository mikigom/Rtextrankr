## Test environments
* local OS X install, R 3.2.1
* ubuntu 14.04, R 3.2.1
* win-builder (devel and release)

## R CMD check results

0 errors | 0 warnings | 1 note

* This is a new release.

```
build_graph: no visible binding for global variable ‘sentence’
Undefined global functions or variables:
  sentence
```
The above note is from the following 'foreach' loop. This note is inevitable but not fatal.

```R
invisible(capture.output(foreach::foreach(sentence = sentences) %do%
{
  graph <- graph + vertices(sentence)
}))
```

## Reverse dependencies

This is a new release. Then, there is no revdep like the following log.

```
> devtools::use_revdep()
* Creating `revdep`.
* Adding `revdep` to `.Rbuildignore`.
* Creating `revdep/check.R` from template.
> source('~/Rtextrankr/revdep/check.R')
Reverse dependency checks for Rtextrankr ==============================================================================
Saving check results in `revdep/checks/`
Computing reverse dependencies
Installing Rtextrankr 1.0.0 and dependencies to /tmp/Rtmp88Qu57/R-lib
Setting env vars ------------------------------------------------------------------------------------------------------
NOT_CRAN    : false
RGL_USE_NULL: true
DISPLAY     : 
Saving check results to `revdep/check.rds` ----------------------------------------------------------------------------
Cleaning up -----------------------------------------------------------------------------------------------------------
No ERRORs or WARNINGs found :)
```
