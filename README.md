# cliqueR
R Library used to calculate Maximal Cliques, Maximum Cliques, and Paracliques for graphs

# Dependencies
Libarary depends on Rcpp.
```
install.packages('Rcpp')
```

# Workflow:

1. Open cliqueR.Rproj in Rstudio
2. RStudio should automatically detect DESCRIPTION and NAMEPACE files, which tell R Studio this is a package - look at build tab
3. (first time) on the R console in R studio load the package (intall(cliqueR), require(cliqueR) - may not have to do this every time)
   or from your OS terminal go to the directory above /cliquR and enter ```R CMD INSTALL cliqueR```
4. Make desired changes.
5. Rebuild from the build tab.
6. You should see whatever Rcpp exported functions are in /src and R functions in /R loaded in the environment panel as well as cliqueR in the packages tab
7. Test those functions and rebuild, then test again.

For additional guidance see "Interface with R" in [this](http://dirk.eddelbuettel.com/code/rcpp/Rcpp-quickref.pdf) Rcpp quick guide [and this](https://stackoverflow.com/questions/13995266/using-3rd-party-header-files-with-rcpp) Stack Overflow post.
Only follow steps about making package, not cutting and pasting and sourcing one massive file

Examples
--------
Load the package.

    library(cliqueR)
   
There are three different function calls, each with their own set of parameters:
*  Maximal
*  Maximum
*  Paraclique

### Maximal

To find the maximal clique, you need the file name at a bare minimum.  The other parameters are the following:
*  least: Lower bound of clique size to include. (a value less than 3 will simply  return every edge in the graph).
*  most:  Upper bound of clique size to include.
*  profile:  Option to return a clique profile instead of all cliques.
By default, these values are 3, -1, and 0 respectively.

Example calls:

    cliqueR.maximal("graphs/bio-yeast.el")
    cliqueR.maximal("graphs/bio-yeast.el", 5)
    
### Maximum

To find the maximum clique, you need the file name at a bare minimum.  It also has an optional second parameter called `sizeOnly` which defaults to `FALSE`.  This option allows the user to return the size of the maximum clique.

Example calls:
    
    cliqueR.maximum("graphs/bio-yeast.el")
    cliqueR.maximum("graphs/bio-yeast.el", TRUE)
    
### Paraclique

Paraclique returns a list of paracliques ordered by size.  At a minimum, the file name is required as the first parameter.  It also has the following additional parameters:
*  igf:  Glom Factor, initialized to 1.0.
*  min_mc_size:  The minimum clique size to include.  Initialized to 5.
*  min_pc_size:  The minimum paraclique size to include.  Initialzed to 5.
*  max_num_pcs:  Max number of paracliques to include.  Initialized to -1.  
