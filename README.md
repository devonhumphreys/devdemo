
<!-- README.md is generated from README.Rmd. Please edit that file -->

# devdemo

<!-- badges: start -->
<!-- badges: end -->

The goal of devdemo is to demonstrate the development of a simple R
package (IUO).

## Step 1: Install RTools

Begin by downloading and installing RTools for Windows from
<https://cran.r-project.org/bin/windows/Rtools/rtools44/rtools.html>

To avoid issues, change the download directory to
C:\Users\\\<your.profile\>  
Open RStudio, and type the following code into the console:

``` r

file.edit(file.path("~", ".Rprofile"))
```

Once the .Rprofile file opens in the editor, add the following code and
save the file:

``` r

Sys.setenv(PATH = paste("C:/Users/<your.profile>/rtools44/usr/bin", Sys.getenv("PATH"), sep=";"))
```

Close the file and restart RStudio. Check that the changes were saved
using:

``` r

file.edit(file.path("~", ".Rprofile"))
```

What was previously a blank file should now contain the code you added
and make RTools available each time you open a new R session.

## Step 2: Determine a Package Name

Use available function to determine if the name already is taken or has
a slang meaning you do not intend. This function searches Github, CRAN,
and Bioconductor to determine whether the name is already in use, and
searches Wikipedia, Urban Dictionary, and Abbreviations.com to identify
unintended meanings.

``` r
library(available)
available('name')
#> ── name ────────────────────────────────────────────────────────────────────────
#> Name valid: ✔
#> Available on CRAN: ✖ 
#> Available on Bioconductor: ✔
#> Available on GitHub:  ✖ 
#> Abbreviations: http://www.abbreviations.com/name
#> Wikipedia: https://en.wikipedia.org/wiki/name
#> Wiktionary: https://en.wiktionary.org/wiki/name
#> Sentiment:???
```

## Step 3: Initiate New Package

Go to File \> New Project \> New Directory \> R Package.

Input your package name. Click “Create a git repository”, add a
description, then click ‘Create’.

## Step 4: Edit DESCRIPTION

Add details as prompted using the DESCRIPTION shell.

## Step 5: use Roxygen to provide function details

Place cursor within a function. Go to Code \> Insert Roxygen skeleton.
Fill in the blanks to help users (and self) know how to use the code.

``` r

#' @param x provide explanation of what x is
#' @return provide explanation of what the function outputs once run
#' @examples provide examples of how to run the function
```

## Step 7: Create README R Markdown

Enter the following code to create a README.Rmd to accompany the
package:

``` r

library(usethis)
use_readme_rmd()
#> ✔ Setting active project to 'C:/Users/Devon.Humphreys/Desktop/RWG/devdemo'
#> ✔ Leaving 'README.Rmd' unchanged
```

## Step 8: Install package

Go to Build \> Install Package.

## Step 7: Commit to Git repo

If you haven’t set up your RStudio with Github credentials, see [GitHub
Basics](https://github.com/devonhumphreys/devdemo/blob/master/GitHub%20Basics.Rmd).

Note: R creates what is called a .git pre-commit hook between Rmd and
regular markdown. Both are needed to be able to commit properly without
error. To ensure this, follow this workflow:

1.  Edit README.Rmd  
2.  Run devtools::build_readme()

Now your files should be synced and the Commit will take as expected. Be
sure to stage all project files before committing.

Go to Tools \> Version Control \> Commit. Then push to github:

``` r

#' use_github(protocol = 'https')
```
