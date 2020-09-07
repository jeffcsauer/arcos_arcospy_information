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

In the early 2000s governmental agencies across the United States began to observe increases in the number of all-cause opioid-involved deaths [@rudd]. The Centers for Disease Control (CDC) describe this Opioid Overdose Epidemic as occuring in three waves, with the first wave attributed to the widespread distribution of prescription opioids, reaching an opioid prescribing rate as high as 81.3 per 100 persons in 2012 [@cdcweb]. While waves two and waves three of the Opioid Overdose Epidemic are largely attributed to illicit opioids like heroin and fentanyl, prescribing rates and prescription misuse remain at a high level [@Guy2017;@ko2020]. 

Researchers, journalists, and government agencies are still actively investigating the myriad impacts of prescription opioids on the Opioid Overdose Epidemic. One powerful tool for understanding prescription opioid distribution is the Drug Enforcement Administration's (DEA) Automation of Reports and Consolidated Orders System (ARCOS). ARCOS tracks the commercial distribution of controlled substances in the United States. The data is highly detailed, tracking commercial origin, pharmacy order frequency, point-of-sale distribution, and more. For a variety of reasons ranging from patient confidentiality to protecting trade secrets, access to sub-state ARCOS data is available only for approved requests (e.g. research or litigation) [@arcosprivacy]. Recent litigation efforts by *The Washington Post*, HD Media, and local journalists allowed for the public release of an anonymized, large portion of the ARCOS database from 2006 to 2012, with additional data for 2013 and 2014 now also available. `arcos` and `arcospy` are open source API wrappers in `R` and `Python`, respectively, that allow researchers and interested citizens to easily access this newly available portion of the ARCOS database.

## Statement of Need

Previously, researchers wanting to use ARCOS data relied on what was made available by the DEA, typically in the form of state-level estimates, or submitted special access data requests to the DEA [@Kenan2012;@reisman_2009]. While alternative data on prescription records are offered by the Centers for Medicare & Medicaid Services in the [Medicare Provider Utilization and Payment Datasets](https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Medicare-Provider-Charge-Data), this data pertains to a specific sample of the population and spans a different set of years (2011 to 2017). In addition, the level of detail in the ARCOS data offers substantial opportunity for commodity analysis about prescription opioids including market dynamics, product demand, supply chain flow, and more. This relationship between commercial distribution and the Opioid Overdose Epidemic is an important area for future study to define and recognize the warning signs of potentially problematic prescribing practices [@VanZee2009]. The release of national, longitudinal, sub-state ARCOS data is a major contribution for researchers interested in the distribution of prescription opioids and the subsequent sociomedical impacts.

In raw format, the ARCOS database is more than 130 gigabytes and includes several hundred columns. Thus, the purpose of `arcos` and `arcospy` are meant to:

-   Simplify access to an open, large, robust prescription opioid database
-   Provide measures of prescription opioid distribution relevant to both the medical and social sciences 
-   Promote analytical flexibility and reproducibility through mirrored functionality across `R` and `Python` 

## API Structure

The `arcos` and `arcospy` API is [publically available](https://arcos-api.ext.nile.works/__swagger__/) and hosted using the [OpenAPI specification](https://swagger.io/specification/). The primary maintainers of API database are members of the Data Reporting Team at *The Washington Post*. A key is required to use the API. The standard key is `WaPo` and additional keys may be sourced from [the Github repository](https://github.com/wpinvestigative/arcos).

All commands share the same name between `arcos` and `arcospy`. This allows users to rapidly switch between languages if the need arises. Outputs from all of the functions are delivered in popular formats - `data.frames` in `R` and `pandas.DataFrame` in `python` -  to enable statistical, spatial, network, or other types of analysis.

Both `arcos` and `arcospy` use parameter delivery - `urltools` in `R` and `requests` in `Python` - to build the API query. Checks are in place to ensure that invalid inputs are not passed to the API. For example, a series of integers cannot be passed as a county name. Corrective warning messages are returned to users who provide invalid inputs. 

## Data Availability and Basic Usage

 Data can be gathered at the pharmacy, distributor, county, or state as the geographic unit of analysis. Depending on the geographic level, there may be raw, summarized, or supplemental data available. For example, the `county_raw()` command returns each individual ARCOS record for a given county from 2006 to 2014. The following code chunk demonstrates this function in `R`:

 ```{.r}
library(arcos)
# Gather all ARCOS records for Hill County, Montana
HillRaw <- county_raw(county = "Hill", 
                      state = "MT", 
                      key = "WaPo")
head(HillRaw)
```

```
| REPORTER_DEA_NO | REPORTER_BUS_ACT | REPORTER_NAME        | ... | dos_str |
|-----------------|------------------|----------------------|-----|---------|
| PM0023046       | DISTRIBUTOR      | MCKESSON CORPORATION | ... | 5.0     |
| PM0023046       | DISTRIBUTOR      | MCKESSON CORPORATION | ... | 5.0     |
| PM0023046       | DISTRIBUTOR      | MCKESSON CORPORATION | ... | 5.0     |
| PM0023046       | DISTRIBUTOR      | MCKESSON CORPORATION | ... | 5.0     |
| PM0023046       | DISTRIBUTOR      | MCKESSON CORPORATION | ... | 7.5     |
| PM0023046       | DISTRIBUTOR      | MCKESSON CORPORATION | ... | 20.0    |
```

 However, the `summarized_county_annual()` command returns the annual summarized totals for a given county for each year of 2006 to 2012. The following code chunk demonstrates this function in `Python`:

 ```{.python}
from arcos import summarized_county_annual
# Gather summarized ARCOS records for Hill County, Montana
HillSummarized = summarized_county_annual(county = "Hill", 
                                          state = "MT", 
                                          key = "WaPo")
HillSummarized.head()
```
```
 	BUYER_COUNTY 	BUYER_STATE  year 	count 	DOSAGE_UNIT 	countyfips
0 	HILL 	        MT 	         2006 	1516 	594700 	        30041
1 	HILL 	        MT 	         2007 	1710 	505430 	        30041
2 	HILL 	        MT 	         2008 	2467 	715560 	        30041
3 	HILL 	        MT 	         2009 	3200 	851560 	        30041
4 	HILL 	        MT 	         2010 	3290 	803760 	        30041

 ```

 Given the number of records, users should anticipate that commands querying for raw data will take longer than commands querying for summarized data. Full documentation on how data is collected by the DEA is available in the [ARCOS Registrant Handbook](https://www.deadiversion.usdoj.gov/arcos/handbook/full.pdf). `arcos` and `arcospy` also include supplemental commands that relevant data - such as county population - gathered from the American Community Survey. A description of each of the functions currently offered, as well as examples in `R` and `Python` demonstrating functionality, are available on [the shared `arcos` and `arcospy` repository](https://github.com/jeffcsauer/arcos_arcospy_information).

There are several ways to conceptualize the unit of analysis for opioids from the present data. These include the total number of records, the total number of all opioid pills, the total number of specific opioid pills (i.e. oxycodone versus hydrocodone), or the total amount (in weight) of all or specific opioid pills. Other common units of analysis that may be of interest include morphine milligram equivalents (MMEs) or prescription counts [@stopka], although these are not directly observable in the present data. Users should choose a unit of analysis that has precedent in their discipline and take appropriate steps to standardize the data (e.g. by population or another stratum) when necessary.

## Conclusion

`arcos` and `arcospy` allows access to a substantial amount of previously unavailable data on prescription opioid distribution in the United States during the years leading up to the present Opioid Crisis. Data from the DEA ARCOS system has been used in scientific publications, primarily at the intersection of health and criminology, to investigate trends in analgesic use and potential abuse [@gilson; @joranson]. Additionally, the data made available by `arcos` has been used extensively by journalists at *The Washington Post* and local news outlets to report on trends in prescription opioid distribution [@diez_2019; @top_2020]. ARCOS data can be merged (non-spatially or spatially) with other United States statistical products through packages like ``tidycensus`` in ``R`` and ``cenpy`` in ``Python``, opening numerous doors for research and teaching exercises. Examples of these possibilities are available on the Github repositories for [``arcos``](https://github.com/wpinvestigative/arcos) and [``arcospy``](https://github.com/wpinvestigative/arcos). The flexibility to query the ARCOS DEA database using commands of the same name enhances reproducibility across languages and ease of access. Expanding the ways in which researchers and journalists can analyze robust datasets like ARCOS is an important step towards understanding how the United States arrived at the present Opioid Overdose Epidemic.

# Availability

``arcos`` is available on [CRAN](https://cran.r-project.org/web/packages/arcos/index.html) as well as [Github](https://github.com/wpinvestigative/arcos)

``arcospy`` is available on [PyPI](https://pypi.org/project/arcospy/) as a pip installable package as well as [Github](https://github.com/jeffcsauer/arcospy).

The repository for this article and additional information is stored on the shared the shared `arcos` and `arcospy` repository on [Github](https://github.com/jeffcsauer/arcos_arcospy_information).

# Citations
