# Contributing

Contributions are welcome to both `arcos` and `arcospy`! For major contributions, please fork the master `arcos` or `arcospy` branch and open a pull request with the suggested changes. The appropriate team will then review the changes and determine if there is a generalizable solution to both `R` and `Python`. If there is no generalizable solution we will strive to make your contribution visible on the appropriate Github page.

Issues posted to the specific `arcos` and `arcospy` repositories will be cross-posted and centralized on the `arcos_arcospy_information` so that users in both languages can be made aware of happenings in the software. These issues will be adapted into issue formatted Github templates by the `arcos` and `arcospy` maintainers. Users may also post issues directly on the `arcos_arcospy_information` repository.

## Documentation

Improvements to the documentation for `arcos` and `arcospy` are welcome. As stated above, we will try to generalize all contributions to both packages. For example, if the description or working for a specific command is unclear we can improve in the documentation in both packages. Additionally, if there are features of a command that you think should be included in the documentation, please let us know so we can improve the user experience.

## Contributing to the core dataset

Presently, the core functionality of the data and API is maintained by the Data Reporting Team at *The Washington Post*. Questions and suggestions regarding the underlying data may be posted on either Github repository, although additional communication with members of the Data Reporting Team at *The Washington Post* may be necessary. 

## Contributing to the API functionality

There is ample room for users to suggest functions that can be added to `arcos` and `arcospy`. As stated above, the API itself is maintained by the Data Reporting Team at *The Washington Post*. Well-described functions with clear use cases can be posted to Github and then considered for integration by the Data Reporting Team at *The Washington Post*. 

It should be noted that existing functions in the `arcos` and `arcospy` functions have flexibility to be used in other functions and loops. Please take this into consideration before requesting a new API command. For example, users interested in downloading data for the entire nation at the county level might consider downloading all of the data (using the `raw_data()` command) and then processing it to own their needs locally. Alternatively, users could also loop the `county_summarized_annual()` over a nationwide FIPS list.

## Issues

Trackable issue pages are available on both the `arcos` and `arcospy` Github pages. Issues may be related to anything from malfunctioning commands to inconsistent data. We encourage an active discussion and hope to readily address any errors. We recommend that when submitting an issue users provide specific tags and examples of the aberrant behavior. If you are able to solve an issue with the code independently, please open a pull request with the corrected code and a short explanation for the bug fix.
