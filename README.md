## arcos (R) and arcospy (Python): twin software packages to access the DEA ARCOS database from 2006 to 2012
Welcome to an informaitonal landing page for the R `arcos` and Python `arcospy` software. This landing page acts as a homebase for background information on the software and a high-level overview of its features. Specific information on the R or Python versions can be found at their respective Github repositories. 

[**arcos** repository](https://github.com/wpinvestigative/arcos)

[**arcospy** repository](https://github.com/jeffcsauer/arcospy)

## Motivation
A short description of the motivation behind the creation and maintenance of the project. This should explain **why** the project exists.

## Development history
`arcos` is the result of efforts by the data reporting team at *The Washington Post* to make a large portion of the DEA ARCOS more easily accessible to the public. `arcos` was released on CRAN in August of 2019. Shortly thereafer, health geographers working at the University of Maryland translated the package to python under the name `arcospy`. Due to this development timeline and the fact that `arcospy` is a translation of `arcos`, at times we defer to the built-out documentation of `arcos` to avoid redundancy.

## Build status
Build status is evaluated via CRAN for `arcos` and travis for `arcospy`.

**arcos**: ![CRAN Badge](http://www.r-pkg.org/badges/version/arcos) 

**arcospy**: ![Build Status](https://travis-ci.com/jeffcsauer/arcospy.svg?token=sRx5dHJBVzwnJnFuh3p9&branch=master)

## Dependencies

**arcos**: R (≥ 3.3.0), stringr, magrittr, jsonlite, dplyr, urltools, vroom

**arcospy**: Python (≥ 3.0.0), pandas, urltools

## Features

**arcos** and **arcospy** offer 24 functions for users to access DEA ARCOS data using pharmacies, distributors, counties, or states as the unit of analysis. These functions have the exact same name in both pieces of software to rapidly switch between languages if the need arises (i.e. if a certain type of analysis is available in R or Python).

## Example(s)

Several examples of using both `arcos` and `arcospy` are available on their respective Github pages. These examples include querying the data, combining the data with other census products at different geographic levels, and making the data spatial. Additional examples are provided to show how users can make use of base commands in loops to expand the functionality of the software.

[**arcos** examples](https://github.com/wpinvestigative/arcos/tree/master/vignettes)

[**arcospy** examples](https://github.com/jeffcsauer/arcospy/tree/master/demos)

## Installation

**R: installing arcos**

`arcos` is available via CRAN. 

Two common options include:

```R
install.packages("arcos")
```

Or the development version from GitHub: 

```R
# install.packages("devtools")
devtools::install_github('wpinvestigative/arcos')

`install.packages("arcos")`
```

**Python: installing arcospy**

`arcospy` is available on PyPI. 

```python
pip install arcospy
```

## How to use?
If people like your project they’ll want to learn how they can use it. To do so include step by step guide to use your project.

## Contribute

Contributing guidelines are outlined in [contributing.md](https://github.com/jeffcsauer/arcos_arcospy_information/contributing.md).

## Credits

**arcos**: Steven Rich (The Washington Post), Andrew Ba Tran (The Washington Post), Aaron Williams (The Washington Post), Jason Hold (The Washington Post)

**arcospy**: Jeffery Sauer (University of Maryland, College Park), Dr. Taylor Oshan (University of Maryland, College Park)

## License

MIT
