
<!-- README.md is generated from README.Rmd. Please edit that file -->

# readepi

*readepi* provides functions for importing epidemiological data into
**R** from common *health information systems*.

<!-- badges: start -->

[![License:
MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![R-CMD-check](https://github.com/epiverse-trace/readepi/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/epiverse-trace/readepi/actions/workflows/R-CMD-check.yaml)
[![Codecov test
coverage](https://codecov.io/gh/epiverse-trace/readepi/branch/main/graph/badge.svg)](https://app.codecov.io/gh/epiverse-trace/readepi?branch=main)
[![lifecycle-concept](https://raw.githubusercontent.com/reconverse/reconverse.github.io/master/images/badge-concept.svg)](https://www.reconverse.org/lifecycle.html#concept)
<!-- badges: end -->

## Installation

You can install the development version of *readepi* from
[GitHub](https://github.com/) with:

``` r
# install.packages("remotes")
remotes::install_github("epiverse-trace/readepi")
```

## Example

These examples illustrate some of the current functionalities:

``` r
library(readepi)

# example of read_stuff():
# (a placeholder function returning its own argument)
path_to_file <- "some_path_here"
read_stuff(path_to_file)
#> [1] "some_path_here"
```

## Development

### Lifecycle

This package is currently a *concept*, as defined by the [RECON software
lifecycle](https://www.reconverse.org/lifecycle.html). This means that
essential features and mechanisms are still being developed, and the
package is not ready for use outside of the development team.

### Contributions

Contributions are welcome via [pull
requests](https://github.com/epiverse-trace/readepi/pulls).

Contributors to the project include:

- Thibaut Jombart (author)

### Code of Conduct

Please note that the linelist project is released with a [Contributor
Code of
Conduct](https://contributor-covenant.org/version/2/0/CODE_OF_CONDUCT.html).
By contributing to this project, you agree to abide by its terms.

### Command line instructions: Create a new Github repository using a template

There’s a shortcut to this, which is provided here for people short on
time, but the scenic route follows.

**Github command line client**

Install the Github command line client `gh` following the instructions
for your OS here: <https://github.com/cli/cli>. Run `gh auth login` to
link your device with your Github account the first time you use the
CLI.

Once installed and authenticated, run:

``` sh
gh repo create epiverse-trace/mypackage --public --template=epiverse-trace/packagetemplate
```

Clone the repository as usual using your preferred method.

### Command line instructions: Create a repo and R package from scratch

#### Make an R project

``` sh
Rscript -e 'devtools::create("mypackage")'
```

or

``` sh
Rscript -e 'usethis::create_package("mypackage")'
```

#### Initialise a git repository

``` sh
cd mypackage
git init
```

#### Create a remote Github repository

**Github command line client**

Install the Github command line client `gh` following the instructions
for your OS here: <https://github.com/cli/cli>. Run `gh auth login` to
link your device with your Github account the first time you use the
CLI.

Create the package repository in the *Epiverse TRACE* organisation.

``` sh
# still in mypackage
gh repo create epiverse-trace/mypackage
```

#### Initial commit to main

``` sh
git push --set-upstream origin main
```

#### Get R-related .gitignore

Getting `R.gitignore` from <https://github.com/github/gitignore>, and
renaming it to `.gitignore`.

`wget` is cross platform and should be available on most systems.
Alternatives using `curl` exist.

``` sh
wget https://raw.githubusercontent.com/github/gitignore/main/R.gitignore
mv R.gitignore .gitignore
```

#### Set up R package components

These next steps are from the R command line. If you are prompted to
copy or edit text in the terminal (especially if you launched R from the
terminal using `$ R`), you might be in Vim. Exit by typing `:wq`, and
edit these files in a text editor.

1.  Populate fields in the DESCRIPTION and NAMESPACE

``` r
# e.g. using data.table
usethis::use_package("data.table")
```

Actually `data.table` requires a bit more configuration to use many of
its features, such as `:=` and `.SD`. Use instead:

``` r
usethis::use_data_table()
```

2.  Set up unit testing infrastructure

``` r
usethis::use_testthat()

# and a basic test file
usethis::use_test("basic-test")

# code coverage YAML for codecov
usethis::use_coverage("codecov")
```

3.  Set a licence

We prefer the MIT licence, primarily because it is short and easy to
read.

``` r
usethis::use_mit_licence()
```

4.  Make a README page

``` r
usethis::use_readme_rmd()
```

Readme.md can be updated manually from the Readme.Rmd created above,
using

``` r
devtools::build_readme()
```

or using a Github Actions setup (see the examples here
<https://github.com/r-lib/actions/tree/v2-branch/examples>).

5.  Set up continuous integration using Github Actions

``` r
# to check package installation
usethis::use_github_actions_check_standard()

# to report code coverage results to codecov
usethis::use_github_action("test-coverage")
```

6.  Set up documentation

<!-- -->

1.  Document the package as required using

``` r
devtools::document()
```

2.  Set up a `pkgdown` website.

``` r
# configure the pkgdown YAML.
# can be saved and edited later
usethis::use_pkgdown()

# build the website using
pkgdown::build_site()
```

Or set up a Github Actions job using
`usethis::use_github_action("pkgdown")`.
