# TODOs: Status quo and wishlist for `topmodels`

## 1. General
### 1.1 Description file
* Fix naming and description of package
* Check authors' contacts

### 1.2 Outlook
* Provide `geom_()` for `ggplot2` instead/additionally to `autoplot()`
* Provide infrastucture for `scoringRules`: in-sample vs. out-of-sample  and aggregated vs. observation-wise contributions
* Implement discretized log-score

## 2. Functions

### 2.1 Functions for forecasting: Summary

Function name | S3 classes supported | S3 classes planned | TODOs
--- | --- | --- | ---
`procast()` | `lm`, `crch`, `disttree` | `glm`, `countreg`, `betareg`, | many
 |  |  | `gam`, `gamlss`, `bamlss` | 
`procast_setup()` | none | none | none
`newresponse()` | `default` | no | few
`qresiduals()` | `default` | no | many 

### 2.2 Functions for forecasting: TODOs
* `procast()` 
    * Improve S3 method for `crch`: Use functions instead of `eval()` and `disttree`
    * Improve S3 method for `disttree`: Check compatability w/ forests and make usage of (not yet implemented) vectorized family functions
    * Extend S3 classes (maybe w/ more flexible default method)
    * Implement `at = data.frame(y = response, x = model.matrix)` for scores
* `newresponse()`
    * Remove censoring/truncation information.
    * Implement (correctly) weights
    * Use `expand.model.frame()` 
* `qresiduals()`
    * Fix `type = "quantile"`: Probably needs to be done on the transformed scale
    * Check if correctly working for discrete variables

### 2.3 Functions for graphical model assessment: Summary

Class | S3 classes | `c()` | `plot()` | `lines()` | `autoplot()` | TODOs
--- | --- | --- | --- | --- | --- | ---
`pithist` | `default` | yes | yes | yes | yes | few
`qqrplot` | no | no | no | no | no | many 
`reliagram` | `default`, `crch` | no | no | no | no | many
`rootogram` | `default`| yes | yes | yes | yes | few
`wormplot` | no | no | no | no | no | setup

### 2.4 Functions for graphical model assessment: TODOs
* `pithist()`
    * Streamline code and optional plotting arguments for the user
    * Implement `type = "proportional"`
    * Check again if we need two different CI computations
* `qqplot()`
    * Setup as a generic function and include S3 methods. 
* `reliagram()`
    * Remove S3 method for `crch`
    * Implement all S3 plotting methods
    * Get newest fancy version of Reto
* `rootogram()`
    * Move away from `countreg` default: Make argument `object` mandatory
    * Merge `rootogram_procast()` and `rootogram_glm`
* `wormplot()`
    * Start from scratch: Needs to be setup
