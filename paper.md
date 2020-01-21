---
title: 'arcos and arcospy: R and Python packages for accessing the DEA ARCOS database from 2006 - 2012'
tags:
  - R
  - Python
  - API
  - Open science
  - Health
authors:
  - name: Steven Rich
    affiliation: 1
  - name: Andrew Ba Tran
    affiliation: 1
  - name: Aaron Williams
    affiliation: 1
  - name: Jason Holt
    affiliation: 1    
  - name: Jeffery Sauer  
    orcid: 0000-0002-8581-6919
    affiliation: 2
  - name: Taylor M. Oshan
    affiliation: 2
affiliations:
 - name: The Washington Post
   index: 1
 - name: University of Maryland, College Park, Department of Geographical Sciences
   index: 2
date: 31 January 2020
bibliography: paper.bib
---

# Summary

The ongoing Opioid Crisis in the United States presents a complex sociomedical epidemic. Researchers, journalists, and government agencies are actively investigating the myriad causes of the crisis. One powerful tool for understanding trends in prescription opioid distribution is the Drug Enforcement Agency's (DEA) Automation of Reports and Consolidated Orders System (ARCOS). ARCOS tracks the commercial distribution of controlled substances in the United States. The data is highly detailed, tracking commercial origin, pharmacy order frequency, point-of-sale distribution, and more. For a variety of reasons ranging from patient confidentiality to protecting trade secrets, access to the ARCOS data is normally restricted. Recent litigation efforts by *The Washington Post*, HD Media, and local journalists allowed for the public release of a large portion of the ARCOS database from 2006 to 2012. `arcos` and `arcospy` are open source API wrappers in R and Python, respectively, that allow researchers and interested citizens to easily access the ARCOS database.

## Data availability

In raw format, the available portion of the ARCOS database is more than 130 gigabytes and includes several hundred columns. Thus, `arcos` and `arcospy` are meant to simplify access to the database and gather relevant measures of prescription opioid distribution. Data can be gathered at the pharmacy, distributor, county, or state as the geographic unit of analysis. Depending on the geographic level, there may be raw, summarized, or supplemental data available. For example, the `county_raw()` command returns each individual ARCOS record for a given county from 2006 to 2012. However, the `summarized_county_annual()` command returns the annual summarized totals for a given county for each year of 2006 to 2012. Full documentation on how data is collected by the DEA is available in the [ARCOS Registrant Handbook](https://www.deadiversion.usdoj.gov/arcos/handbook/full.pdf).Supplemental commands return relevant data - such as county population - gathered from the American Community Survey.

There are several ways to conceptualize the unit of analysis for opioids from the present data. These include the total number of records, the total number of all opioid pills, the total number of specific opioid pills (i.e. oxycodone versus hydrocodone), or total amount (in weight) of all or specific opioid pills. Other common units of analysis that may be of interest include morphine milligram equivalents (MMEs) or prescription counts (@stopka), although these are not directly observable in the present data. Users should choose a unit of analysis that has precedent in their discipline and take appropriate steps to standardize the data when necessary.

Outputs from all of the functions are delivered in popular formats - as `data.frames` in `R` and `pandas.DataFrame` in `python` -  to enable statistical, spatial, network, or other types of analysis.

## API structure

All commands share the same name between `arcos` and `arcospy`. This allows users to rapidly switch between languages if the need arises. Both `arcos` and `arcospy` use parameter delivery - `urltools` in `R` and `requests` in `Python` - to build the API query. Checks are in place to ensure that invalid inputs are not passed to the API. For example, a series of integers cannot be passed as a county name. Corrective warning messages are returned to users who provide invalid inputs. The API itself is also accessible on [swagger](https://arcos-api.ext.nile.works/__swagger__/).

## Conclusion

``arcos`` and ``arcospy`` allows both researchers and citizens to access a substantial amount of previously unavailable data on prescription opioid distribution in the United States during the years leading up to the present Opioid Crisis. Data from the DEA ARCOS database has been used in scientific publications in health and criminology [@gilson; @joranson]. Combining the ARCOS data with existing survey products available through packages like ``tidycensus`` in ``R`` and ``cenpy`` in ``Python`` enables complex analysis. Additionally, the data can be made spatial in either point or polygon format, opening numerous doors for research and teaching exercises. Examples of these possibilities are available on the Github repositories for [``arcos``](https://github.com/wpinvestigative/arcos) and [``arcospy``](https://github.com/wpinvestigative/arcos). The flexibility to query the ARCOS DEA database using commands of the same name enhances reproducibility across languages and ease of access. Expanding the ways in which researchers and journalists can analyze robust datasets like ARCOS – while still maintaining individual medical privacy – is an important step towards understanding how the United States arrived at the present Opioid Epidemic.

# Availability

``arcos`` is available on [CRAN](https://cran.r-project.org/web/packages/arcos/index.html) as well as [Github](https://github.com/wpinvestigative/arcos).

``arcospy`` is available on [PyPI](https://pypi.org/project/arcospy/) as a pip installable package as well as [Github](https://github.com/wpinvestigative/arcos).

# Citations
