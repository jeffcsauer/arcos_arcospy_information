---
title: 'arcos and arcospy: R and Python packages for accessing the DEA ARCOS database from 2006 - 2014'
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
date: 09 July 2020
bibliography: paper.bib
---

# Summary

The ongoing Opioid Overdose Crisis in the United States presents a complex sociomedical epidemic. Researchers, journalists, and government agencies are actively investigating the myriad impacts of the crisis. One powerful tool for understanding trends in prescription opioid distribution is the Drug Enforcement Agency's (DEA) Automation of Reports and Consolidated Orders System (ARCOS). ARCOS tracks the commercial distribution of controlled substances in the United States. The data is highly detailed, tracking commercial origin, pharmacy order frequency, point-of-sale distribution, and more. For a variety of reasons ranging from patient confidentiality to protecting trade secrets, access to sub-state ARCOS data is normally restricted. Recent litigation efforts by *The Washington Post*, HD Media, and local journalists allowed for the public release of a large portion of the ARCOS database from 2006 to 2012. `arcos` and `arcospy` are open source API wrappers in `R` and `Python`, respectively, that allow researchers and interested citizens to easily access this newly available portion of the ARCOS database.

## Statement of need

Previous analyses that sought to use ARCOS data had to make use of what data the DEA chose to make available (typically state-level estimates, as is the case of [@reisman_2009]) or submit special data requests to the DEA [@Kenan2012]. While alternative data on prescription records are offered by the [Medicare Provider Utilization and Payment Datasets](https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Medicare-Provider-Charge-Data) provided by the Centers for Medicare & Medicaid Services,  these datasets pertain to a specific sample of the population and cover a different set of years (2011 to 2017). The release of national, longitudinal, sub-state ARCOS data is a major contribution for researchers interested in the distribution of prescription opioids and the subsequent sociomedical impacts.

In raw format, the the ARCOS database is more than 130 gigabytes and includes several hundred columns. Thus, the purpose of `arcos` and `arcospy` are meant to:
- Simplify access to an open, large, robust prescription opioid database
- Provide measures of prescription opioid distribution relevant to both the medical and social sciences 
- Promote analytical flexibility and reproducibility through mirrored functionality across `R` and `Python` 

## API Structure

All commands share the same name between `arcos` and `arcospy`. This allows users to rapidly switch between languages if the need arises. Outputs from all of the functions are delivered in popular formats - `data.frames` in `R` and `pandas.DataFrame` in `python` -  to enable statistical, spatial, network, or other types of analysis.

Both `arcos` and `arcospy` use parameter delivery - `urltools` in `R` and `requests` in `Python` - to build the API query. Checks are in place to ensure that invalid inputs are not passed to the API. For example, a series of integers cannot be passed as a county name. Corrective warning messages are returned to users who provide invalid inputs. The API itself is also accessible on [swagger](https://arcos-api.ext.nile.works/__swagger__/). A key is required to use the API. The standard key is `WaPo` and additional keys may be sourced from [here](https://github.com/wpinvestigative/arcos).   

## Data Availability and Basic Usage

 Data can be gathered at the pharmacy, distributor, county, or state as the geographic unit of analysis. Depending on the geographic level, there may be raw, summarized, or supplemental data available. For example, the `county_raw()` command returns each individual ARCOS record for a given county from 2006 to 2012. 

 ```
library(arcos)
# Gather all ARCOS records for Hill County, Montana
HillOpioids <- county_raw(county = "Hill", state = "MT", key = "WaPo")
head(HillOpioids)

| REPORTER_DEA_NO | REPORTER_BUS_ACT | REPORTER_NAME        | ... | Reporter_family            | dos_str |
|-----------------|------------------|----------------------|-----|----------------------------|---------|
| PM0023046       | DISTRIBUTOR      | MCKESSON CORPORATION | ... | McKesson Corporation       | 5.0     |
| PM0023046       | DISTRIBUTOR      | MCKESSON CORPORATION | ... | McKesson Corporation       | 5.0     |
| PM0023046       | DISTRIBUTOR      | MCKESSON CORPORATION | ... | McKesson Corporation       | 5.0     |
| PM0023046       | DISTRIBUTOR      | MCKESSON CORPORATION | ... | McKesson Corporation       | 5.0     |
| PM0023046       | DISTRIBUTOR      | MCKESSON CORPORATION | ... | McKesson Corporation       | 7.5     |
| PM0023046       | DISTRIBUTOR      | MCKESSON CORPORATION | ... | McKesson Corporation       | 20.0    |
```

 However, the `summarized_county_annual()` command returns the annual summarized totals for a given county for each year of 2006 to 2012. 

 ```
from arcos import summarized_county_annual
# Gather summarized ARCOS records for Hill County, Montana
HillOpioidsSummarized = summarized_county_annual(county = "Hill", state = "MT", key = "WaPo")
HillOpioidsSummarized.head()

 	BUYER_COUNTY 	BUYER_STATE 	year 	count 	DOSAGE_UNIT 	countyfips
0 	HILL 	        MT 	            2006 	1516 	594700 	        30041
1 	HILL 	        MT 	            2007 	1710 	505430 	        30041
2 	HILL 	        MT 	            2008 	2467 	715560 	        30041
3 	HILL 	        MT 	            2009 	3200 	851560 	        30041
4 	HILL 	        MT 	            2010 	3290 	803760 	        30041

 ```

 Given the number of records, users should anticipate that commands querying for raw data will take longer than commands querying for summarized data. Full documentation on how data is collected by the DEA is available in the [ARCOS Registrant Handbook](https://www.deadiversion.usdoj.gov/arcos/handbook/full.pdf). `arcos` and `arcospy` also include supplemental commands that relevant data - such as county population - gathered from the American Community Survey. A description of each of the functions currently offered, as well as examples in `R` and `Python` demonstrating functionality, are available on [the shared `arcos` and `arcospy` repository](https://github.com/jeffcsauer/arcos_arcospy_information).

There are several ways to conceptualize the unit of analysis for opioids from the present data. These include the total number of records, the total number of all opioid pills, the total number of specific opioid pills (i.e. oxycodone versus hydrocodone), or the total amount (in weight) of all or specific opioid pills. Other common units of analysis that may be of interest include morphine milligram equivalents (MMEs) or prescription counts [@stopka], although these are not directly observable in the present data. Users should choose a unit of analysis that has precedent in their discipline and take appropriate steps to standardize the data (e.g. by population or another stratum) when necessary.

## Conclusion

`arcos` and `arcospy` allows access to a substantial amount of previously unavailable data on prescription opioid distribution in the United States during the years leading up to the present Opioid Crisis. Data from the DEA ARCOS system has been used in scientific publications, primarily at the intersection of health and criminology, to investigate trends in analgesic use and potential abuse [@gilson; @joranson]. Additionally, the data made available by `arcos` has been used extensively by journalists at *The Washington Post* and local news outlets to report on trends in prescription opioid distribution [@diez_2019; @top_2020]. ARCOS data can be merged (non-spatially or spatially) with other United States statistical products through packages like ``tidycensus`` in ``R`` and ``cenpy`` in ``Python``, opening numerous doors for research and teaching exercises. Examples of these possibilities are available on the Github repositories for [``arcos``](https://github.com/wpinvestigative/arcos) and [``arcospy``](https://github.com/wpinvestigative/arcos). The flexibility to query the ARCOS DEA database using commands of the same name enhances reproducibility across languages and ease of access. Expanding the ways in which researchers and journalists can analyze robust datasets like ARCOS – while still maintaining individual medical privacy – is an important step towards understanding how the United States arrived at the present Opioid Overdose Epidemic.

# Availability

``arcos`` is available on [CRAN](https://cran.r-project.org/web/packages/arcos/index.html) as well as [Github](https://github.com/wpinvestigative/arcos)

``arcospy`` is available on [PyPI](https://pypi.org/project/arcospy/) as a pip installable package as well as [Github](https://github.com/jeffcsauer/arcospy).

The repository for this article and additional information is stored on the shared the shared `arcos` and `arcospy` repository on [Github](https://github.com/jeffcsauer/arcos_arcospy_information).

# Citations
