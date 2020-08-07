## arcos (R) and arcospy (Python): twin software packages to access the DEA ARCOS database from 2006 to 2014
Welcome to an informational landing page for the R `arcos` and Python `arcospy` software. This landing page acts as a home base for background information on the software and a high-level overview of its features. Specific information on the R or Python versions can be found at their Github repositories.

[**arcos** repository](https://github.com/wpinvestigative/arcos)

[**arcospy** repository](https://github.com/jeffcsauer/arcospy)

**We recommend reading [the vignette](https://github.com/jeffcsauer/arcos_arcospy_information/tree/master/docs/R_Python_arcos_vignette.html) that provides an overview of the API, a quick start guide, and demonstration of R/Python dual functionality!**

## Motivation
The ongoing Opioid Crisis in the United States poses serious public health issues. Understanding *how* the United States arrived at the present crisis is crucial to avoid future crises. One powerful tool for understanding trends in prescription opioid distribution is the Drug Enforcement Agency's (DEA) Automation of Reports and Consolidated Orders System (ARCOS). In raw format, the available portion of the ARCOS database is more than 150 gigabytes and includes several hundred columns. Thus, `arcos` and `arcospy` are meant to simplify access to the available data so researchers and interested citizens can rapidly gather relevant measures of prescription opioid distribution. The data available in `arcos` and `arcospy` spans the years 2006 to 2014. These are the years leading up to the now widely recognized Opioid Crisis. The data has been featured in a series of investigative reporting articles by both national and regional newspapers. There are numerous potential applications of this data to the study of health sciences, criminology, medical sociology, and more.  

## Development history
`arcos` is the result of efforts by the data reporting team at *The Washington Post* to make a large portion of the DEA ARCOS more easily accessible to the public. `arcos` was released on CRAN in August of 2019 (note: `arcos` has been temporarily removed from CRAN due to COVID-19, there is intention to get the package back on CRAN as soon as possible - it remains `devtools` installable). Shortly thereafer, health geographers working at the University of Maryland translated the package to python under the name `arcospy`. Due to this development timeline and the fact that `arcospy` is a translation of `arcos`, at times we defer to the built-out documentation of `arcos` to avoid redundancy.

## Build status
Build status is evaluated via CRAN for `arcos` and travis for `arcospy`.

**arcos**: ![CRAN Badge](http://www.r-pkg.org/badges/version/arcos)

**arcospy**: ![Build Status](https://travis-ci.com/jeffcsauer/arcospy.svg?token=sRx5dHJBVzwnJnFuh3p9&branch=master)

## Dependencies

**arcos**: R (≥ 3.3.0), stringr, magrittr, jsonlite, dplyr, urltools, vroom

**arcospy**: Python (≥ 3.0.0), pandas, urltools

## Features

**arcos** and **arcospy** offers nearly 30 functions for users to access DEA ARCOS data using pharmacies, distributors, counties, or states as the unit of analysis, as well as useful supplementary information. These functions have the exact same name in both `R` and `Python`, allowing users to rapidly switch between languages if the need arises (i.e. if a certain type of analysis is available only in R or Python).


__Functions and the available datasets (Read the [reference page](https://wpinvestigative.github.io/arcos/reference/index.html) for more info):__

| Function                                                                  | What                                                                            | Type         | Years       | Drugs                   | Buyers                                             |
|---------------------------------------------------------------------------|---------------------------------------------------------------------------------|--------------|-------------|-------------------------|----------------------------------------------------|
| [buyer_addresses()](https://wpinvestigative.github.io/arcos/reference/buyer_addresses.html)                       | Get DEA designated addresses for each pharmacy                                  | Raw          |             | All                     | All                                                |
| [buyer_details()](https://wpinvestigative.github.io/arcos/reference/buyer_details.html)                           | Get monthly summarized pill totals by county                                    | Summarized   | 2006 - 2014 | Oxycodone & Hydrocodone | Retail Pharmacy, Chain Pharmacy, and Practitioners |
| [buyer_list()](https://wpinvestigative.github.io/arcos/reference/buyer_list.html)                                 | Get list of business types listed in the BUYER_BUS_ACT in the ARCOS database    | Raw          | 2006 - 2014 |                         | All                                                |
| [combined_buyer_annual()](https://wpinvestigative.github.io/arcos/reference/combined_buyer_annual.html)           | Get annual total pills for each buyer (pharmacy, etc) in a county               | Summarized   | 2006 - 2014 | Oxycodone & Hydrocodone | Retail Pharmacy, Chain Pharmacy, and Practitioners |
| [combined_buyer_monthly()](https://wpinvestigative.github.io/arcos/reference/combined_buyer_monthly.html)         | Get annual total pills for each buyer (pharmacy, etc) in a county               | Summarized   | 2006 - 2014 | Oxycodone & Hydrocodone | Retail Pharmacy, Chain Pharmacy, and Practitioners |
| [county_list()](https://wpinvestigative.github.io/arcos/reference/county_list.html)                               | Get list of counties and states and fips codes represented in the ARCOS data    | Raw          | 2006 - 2014 |                         |                                                    |
| [county_population()](https://wpinvestigative.github.io/arcos/reference/county_population.html)                   | Get annual population for counties between 2006 and 2012                        | Supplemental | 2006 - 2014 | Oxycodone & Hydrocodone | Retail Pharmacy, Chain Pharmacy, and Practitioners |
| [county_raw()](https://wpinvestigative.github.io/arcos/reference/county_raw.html)                                 | Download raw prescription data for specified county (by state and county names) | Raw          |             | Oxycodone & Hydrocodone | Retail Pharmacy, Chain Pharmacy, and Practitioners |
| [county_raw_fips()](https://wpinvestigative.github.io/arcos/reference/county_raw_fips.html)                       | Download raw prescription data for specified county (by county FIPS code)       | Raw          |             | Oxycodone & Hydrocodone | Retail Pharmacy, Chain Pharmacy, and Practitioners |
| [drug_county_biz()](https://wpinvestigative.github.io/arcos/reference/drug_county_biz.html)                       | Raw data by county and individual drug and business type                        | Raw          | 2006 - 2014 | All                     | All                                                |
| [drug_county_raw()](https://wpinvestigative.github.io/arcos/reference/drug_county_raw.html)                       | Raw data by county and individual drug and business type via fips code          | Raw          | 2006 - 2014 | All                     | All                                                |
| [drug_list()](https://wpinvestigative.github.io/arcos/reference/drug_list.html)                                   | Get list of the 14 drugs tracked in the ARCOS data                              | Raw          | 2006 - 2014 | All                     |                                                    |
| [not_pharmacies()](https://wpinvestigative.github.io/arcos/reference/not_pharmacies.html)                         | Get list of misidentified pharmacies by BUYER_DEA_NOs                           | Supplemental | 2006 - 2012 |                         | Retail Pharmacy, Chain Pharmacy                    |
| [pharm_cbsa()](https://wpinvestigative.github.io/arcos/reference/pharm_cbsa.html)                                 | Get the core-based statistical area GEOID for each pharmacy                     | Supplemental | 2006 - 2014 |                         | Retail Pharmacy, Chain Pharmacy                    |
| [pharm_counties()](https://wpinvestigative.github.io/arcos/reference/pharm_counties.html)                         | Get county GEOID for each pharmacy                                              | Supplemental | 2006 - 2014 |                         | Retail Pharmacy, Chain Pharmacy                    |
| [pharm_latlon()](https://wpinvestigative.github.io/arcos/reference/pharm_latlon.html)                             | Get latitude and longitude data for each pharmacy                               | Supplemental | 2006 - 2014 |                         | Retail Pharmacy, Chain Pharmacy                    |
| [pharm_tracts()](https://wpinvestigative.github.io/arcos/reference/pharm_tracts.html)                             | Get census tract GEOID for each pharmacy                                        | Supplemental | 2006 - 2014 |                         | Retail Pharmacy, Chain Pharmacy                    |
| [pharmacy_raw()](https://wpinvestigative.github.io/arcos/reference/pharmacy_raw.html)                             | Download raw prescription data for specified pharmacy into R                    | Raw          | 2006 - 2014 | Oxycodone & Hydrocodone | Retail Pharmacy, Chain Pharmacy                    |
| [raw_data()](https://wpinvestigative.github.io/arcos/reference/raw_data.html)                                     | Download raw ARCOS data                                                         | Raw          | 2006 - 2014 | All                     | All                                                |
| [reporter_addresses()](https://wpinvestigative.github.io/arcos/reference/reporter_addresses.html)                 | Get DEA designated addresses for each Reporter                                  | Raw          | 2006 - 2014 | All                     | All                                                |
| [state_population()](https://wpinvestigative.github.io/arcos/reference/state_population.html)                     | Get annual population for states between 2006 and 2014                          | Supplemental | 2006 - 2014 |                         |                                                    |
| [summarized_county_annual()](https://wpinvestigative.github.io/arcos/reference/summarized_county_annual.html)     | Get annual summarized pill totals by county                                     | Summarized   | 2006 - 2014 | Oxycodone & Hydrocodone | Retail Pharmacy, Chain Pharmacy, and Practitioners |
| [summarized_county_monthly()](https://wpinvestigative.github.io/arcos/reference/summarized_county_monthly.html)   | Get monthly summarized pill totals by county                                    | Summarized   | 2006 - 2014 | Oxycodone & Hydrocodone | Retail Pharmacy, Chain Pharmacy, and Practitioners |
| [total_distributors_county()](https://wpinvestigative.github.io/arcos/reference/total_distributors_county.html)   | Get total pills for each distributor in a county                                | Summarized   | 2006 - 2014 | Oxycodone & Hydrocodone |                                                    |
| [total_distributors_state()](https://wpinvestigative.github.io/arcos/reference/total_distributors_state.html)     | Get total pills for each distributor in a state                                 | Summarized   | 2006 - 2014 | Oxycodone & Hydrocodone |                                                    |
| [total_manufacturers_county()](https://wpinvestigative.github.io/arcos/reference/total_manufacturers_county.html) | Get total pills for each manufacturer in a county                               | Summarized   | 2006 - 2014 | Oxycodone & Hydrocodone |                                                    |
| [total_manufacturers_state()](https://wpinvestigative.github.io/arcos/reference/total_manufacturers_state.html)   | Get total pills for each manufacturer in a state                                | Summarized   | 2006 - 2014 | Oxycodone & Hydrocodone |                                                    |
| [total_pharmacies_county()](https://wpinvestigative.github.io/arcos/reference/total_pharmacies_county.html)       | Get total pills for each pharmacy in a county                                   | Summarized   | 2006 - 2014 | Oxycodone & Hydrocodone | Retail Pharmacy, Chain Pharmacy, and Practitioners |
| [total_pharmacies_state()](https://wpinvestigative.github.io/arcos/reference/total_pharmacies_state.html)         | Get total pills for each pharmacy in a state                                    | Summarized   | 2006 - 2014 | Oxycodone & Hydrocodone | Retail Pharmacy, Chain Pharmacy, and Practitioners |

## Examples

Several examples of using both `arcos` and `arcospy` are available on their respective Github pages. These examples include querying the data, combining the data with other census products at different geographic levels, and making the data spatial. Additional examples are provided to show how users can make use of base commands in loops to expand the functionality of the software.

[**arcos** examples](https://github.com/wpinvestigative/arcos/tree/master/vignettes)

[**arcospy** examples](https://github.com/jeffcsauer/arcospy/tree/master/demos)

## Installation

**R: installing arcos**

```R
#Get the latest stable release from CRAN:
install.packages("arcos")

#...or via devtools:

# install.packages("devtools")
devtools::install_github('wpinvestigative/arcos')
```

**Python: installing arcospy**

`arcospy` is available via PyPI:

```python
pip install arcospy
```

## Contribute

Contributing guidelines are outlined in [contributing.md](https://github.com/jeffcsauer/arcos_arcospy_information/blob/master/contributing.md).

## Credits

**arcos**: Steven Rich (The Washington Post), Andrew Ba Tran (The Washington Post), Aaron Williams (The Washington Post), Jason Hold (The Washington Post)

**arcospy**: Jeffery Sauer (University of Maryland, College Park), Dr. Taylor Oshan (University of Maryland, College Park)

## License

MIT (2019); The Washington Post and The Charleston Gazette-Mail (2019)
