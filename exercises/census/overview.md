# Untangling the US Census

* [Why Census data?](#Why-Census-data)
* [Census datasets](#Census-datasets)
   - [Decennial Census](#Decennial-Census)
   - [American Community Survey](#American-Community-Survey)
     * [1-year estimates](#1-year-estimates)
     * [5-year estimates](#5-year-estimates) 
* [Census geographies](#Census-geographies)
* [Margins of error](#Margins-of-error)
* [Picking the right dataset](#Picking-the-right-dataset)
* [Getting Census data](#Getting-Census-data)

   

## Why Census data?
Census data is perhaps one of the most important datasets in journalism. By itself we can learn more about population trends and see how demographics are changing within our community. When paired with other data, we can gain insight on the people impacted by the topics and issues we are reporting on.

## Census datasets

The U.S. Census Bureau publishes many different datasets, but the most common are the Decennial and American Community Survey.

### Decennial Census
The decennial census is taken every 10 years. It's official purpose is to be used for re-districting and to ensure adequate representation. Decennial data is currently released in the [Redistricting Data Summary File](https://www.census.gov/programs-surveys/decennial-census/about/rdo/summary-files.2020.html).

It's main advantage is that it's meant to be a full count of the population and there are no margins of error in the data. However, factors such as non-response rates and privacy protection measures contribute to undercounting and other issues in the data. Keep this in mind, especially when dealing with smaller populations.

Information on race and Hispanic or Latino origin are reported for both total population and voting age population. The data also includes information on housing status (occupied or vacant) and group quarters (dorms, correctional institutions, military housing, nursing homes and other group living facilities).

One example of how we can use decennial census data is [Census Mapper](https://censusmapper.biglocalnews.org/#/). The Associated Press also has a great site dedicated to [news coverage of the 2020 Census](https://apnews.com/hub/census-2020).

### American Community Survey

The [ACS](https://www.census.gov/programs-surveys/acs/library/handbooks/general.html) is a more timely and vastly richer dataset than the decennial census with thousands of variables providing detailed information on age, sex, race, ethnicity, income, education, living conditions and many more demographic measures. It is released annually rather than once every decade in [1-year](https://www.census.gov/data/developers/data-sets/acs-1year.html) and [5-year](https://www.census.gov/data/developers/data-sets/acs-5year.2021.html#list-tab-1036221584) estimates.

The drawback to the ACS is it is sample-based and not a full count of the population. This means there is some uncertanity in the data. These are estimates and as such have margins of error related to them (more on that below).

#### 1-year estimates
- Best used when you need to make year-to-year comparisons or need data from consecutive years.
- 1-year estimates have more uncertainity and are less reliable than 5-year estimates.
- Estimates are not released for geographies below counties and places with populations less than 65,000 people (More on Census geographies below).

#### 5-year estimates
- Based off of survey data collected over a five-year period. The 2022 ACS 5-year estimates include data from 2018 to 2022.
- This makes the estimates more reliable than 1-year estimates with less uncertainty.
- Care should be exercised when comparing 5-year estimates over time. The estimates should not contain overlapping years. For example, 2022 ACS 5-year estimates can be compared to those from the 2017 ACS 5-year, but not estimates from any of the years from 2018 on.

## Census geographies
Census counts and estimates are reported at a wide variety of geographic levels from nationwide down to individual blocks. More information on geographies including a list of geographic levels can be found [here](https://www.census.gov/data/developers/geography.html). Keep in mind there is more uncertainty in the data at smaller geographic levels. Here are some of the more common Census geographies:

- **State:** An individual state. This geographic level is commonly used in data journalism projects with a national or regional scope. It is often referred to in Census data by its FIPS code, a two-digit numeric code assigned to each state. California's FIPS code is `06`.
- **Metropolitan Statistical Area (MSA):** This is typically a collection of cities, counties or burroughs used to represent a metropolitan area. It is often used in national and regional stories.
- **County:** County-level geographies are subdivisions of states. They include counties, burroughs and other equivalent geographies. They are good for projects with a national, regional or state scope. Each county is represented by a three-digit FIPS code. Santa Clara County's FIPS code is `085`. County FIPS codes are often combined with state FIPS code - `06085` refers to Santa Clara County, California.
- **County Subdivisions and Places:** Places are commmonly used in Census data to represent individual cities. County subdivisions can also be used to represent municipalities in some states such as New Jersey.
- **Tracts:** Tracts are purely a Census concept meant to approximate neighborhoods. They typically have populations between 6,000 and 10,000 people in size. They do not correspond with actual neighborhood boundaries. Tracts change between decennial censuses, so comparison between decades and tracts will not work. Census tracts from 2010 to 2019 are different from tracts from 2020 onward, for example. They have small populations, so expect to see high margins of error in the data.
- **Blocks:** Blocks are the smallest census geography, meant to approximate a city block. They are the atomic unit of census geography used to build all other geographies. They are commonly used in redestricting and to draw up voting precincts. They have particularly small populations and most estimates have margins of error that render the data useless unless aggregated geographically. It is possible to use blocks to build custom geographies such as police precincts or school attendance boundaries, but error margins will need to be re-calculated for the aggregated data. You should only aggregate blocks that are physically adjacent to each other.

**NOTE:** The Census Bureau has a [decent tool](https://www.census.gov/library/reference/code-lists/ansi.html#cou) for looking up state and county FIPS codes. You can also find other resources throughout the Internet.

## Margins of error

Margins of error tell us the reliability of data collected from surveys where sampling is used. The smaller the sample size, the larger the margin of error. For more detail, see the [ACS handbook](https://www.census.gov/content/dam/Census/library/publications/2020/acs/acs_general_handbook_2020_ch07.pdf). Consider the median household income in Santa Clara County:

|Name|Dataset|Median Household Income|Margin of Error|
|---|---|---:|---:|
|Santa Clara County|2021 ACS 1-year|\$141,562|±\$2,669|

We can say the true median household income is within \\$2,669 of the published estimate of $141,562. If we subtract the margin of error from the published estimate, we get the lower bound of what is known as the confidence interval. Adding the margin of error to the estimate gives us the confidence interval's upper bound. The confidence interval is the range in which we can say with some degree of confidence the estimate's true value exists.

|Name|Dataset|Median Household Income|Margin of Error|Lower Bound|Upper Bound|
|---|---|---:|---:|---:|---:|
|Santa Clara County|2021 ACS 1-year|\$141,562|±\$2,669|\$138,893|\$144,231|

In this example, we can say with some degree of confidence that the true median household income is somewhere between \$138,893 and \\$144,231. Just how much confidence? The Census Bureau publishes their estimates at the 90 percent confidence level. So we can say the following:
> We are 90 percent confident the median household income for Santa Clara County is between \\$138,893 and \$144,231.

**IMPORTANT:** You should always keep an eye on the margin of error. Look for cases where the lower bound of the confidence interval is less than zero or no longer makes sense.

We can reduce the margin of error and make our estimates more reliable by increasing the sample size. There are a couple of ways to do that with Census data.
### Use a larger geography
The easiest way to increase sample size is to increase the size of the geography. In this case, let's add to the table the median household income for the state of California:

|Name|Dataset|Median Household Income|Margin of Error|Lower Bound|Upper Bound|
|---|---|---:|---:|---:|---:|
|Santa Clara County|2021 ACS 1-year|\$141,562|±\$2,669|\$138,893|\$144,231|
|State of California|2021 ACS 1-year|\$84,907|±\$542|\$84,365|\$85,449|

The margin of error is much lower at the state level, but not without cost. The state estimate also includes other counties, not just Santa Clara County. But the state estimate doesn't accurately reflect the county estimate. This can be problematic if the scope of the analysis needs to be at the county level.

If the analysis focuses on small geographies such as census tracts, consider switching to a county-level analysis to increase the reliability of the data.

### Use 5-year estimates
Another way of increasing sample size is to use 5-year estimates. These estimates are based on survey responses collected over a 5-year period, so the sample size is significantly larger.
|Name|Dataset|Median Household Income|Margin of Error|Lower Bound|Upper Bound|
|---|---|---:|---:|---:|---:|
|Santa Clara County|2021 ACS 1-year|\$141,562|±\$2,669|\$138,893|\$144,231|
|Santa Clara County|2021 ACS 5-year|\$140,258|±\$1,577|\$138,681|\$141,835|

The margin of error is much smaller and the estimates look closer to each other. Most times we opt to use 5-year estimates.

**IMPORTANT:**

- Remember year-to-year analysis should not be done because 5-year estimates containing data from overlapping years.
- Estimates at the tract level will still have high margins of error that need to be carefully considered when planning a methodology.

### Avoid segmenting the population
If possible, avoid segmenting the population into demographic subgroups. This can be difficult because we often want to look at things and consider other factors such as age, sex, race and/or ethnicity. 

However whenever we do so, the margin of error will most likely increase because the sample size is reduced. For example, the median income for multi-racial households in Santa Clara County has a much larger margin of error than the estimate for all households:

|Name|Dataset|Median Household Income|Margin of Error|Lower Bound|Upper Bound|
|---|---|---:|---:|---:|---:|
|Santa Clara County|2021 ACS 5-year|\$140,258|±\$1,577|\$138,681|\$141,835|
|Multi-racial households|2021 ACS 5-year|\$115,064|±\$6,828|\$108,236|\$121,892|

### Other ways to deal with error margins
In some cases we can still get meaningful information from an analysis of estimates with high margins of error. Going back to the previous example:
|Name|Dataset|Median Household Income|Margin of Error|Lower Bound|Upper Bound|
|---|---|---:|---:|---:|---:|
|Santa Clara County|2021 ACS 5-year|\$140,258|±\$1,577|\$138,681|\$141,835|
|Multi-racial households|2021 ACS 5-year|\$115,064|±\$6,828|\$108,236|\$121,892|

By looking at the upper and lower bounds of both estimates, we can safely make the following statement:
> Multi-racial households earn less than the county's median income.

This is because at no point would the estimated median income for multi-racial households be equal to, or greater than, the county estimate.

## Picking the right dataset
Picking the right dataset is based largely on the story you want to tell and the questions you need answered. Here are some questions you can ask to help determine which dataset to use:

- **What is the topic?** Remember most topics can only be found in sampled data - the ACS.
- **Do you need an actual count or are estimates ok?** If you need an actual count, then the decennial census is your only real option.
- **How timely does the data need to be?** Do you need to do a year-to-year analysis? How recent does the data need to be?
- **At what geographic level does then analysis need to be?** Remember ACS 1-year estimates are not available below the county level. Caution is recommended when working with 5-year estimates below county or places with fewer than 65,000 people.

## Getting Census data

There are several different ways to download data. Here are some of the most common ones:

- **[Data.census.gov](https://data.census.gov/):** The official source of Census data. All published census data is available here. However, the interface can be difficult to navigate. Downloaded data appears to come in three different formats, all of which require work to prepare the data for analysis.
- **[Census Reporter](https://censusreporter.org/):** Census Reporter provides many tools and resources for journalists, including data downloads and embeddable data visualizations. 
- **[The Census API](https://www.census.gov/data/developers/data-sets.html):** The Census API allows programmatic access to Census data, but requires some coding knowledge. It also requires knowing the identification number of the table containing the data you want.
- **[NHGIS](https://www.nhgis.org/)** The National Historic Geographic Information System is the best source for historic census data not found on data.census.gov.

### The importance of table IDs
[Table IDs](https://www.census.gov/programs-surveys/acs/data/data-tables/table-ids-explained.html) are what the Census Bureau uses to identify individual tables and columns within those tables. They are required to download data through the API.


Both data.census.gov and Census Reporter include the table numbers in the citations.

The first character of the table ID specifies the table type. We tend to mostly used the basic table type, identified by the letter `B`. Next come two digits which identify the topic. 

#### ACS Subject Numbers
|Number|Subject|
|:---|:---|
|01|Age; Sex|
|02|Race|
|03|Hispanic or Latino Origin|
|04|Ancestry|
|05|Citizenship Status; Year of Entry; Foreign Born Place of Birth|
|06|Place of Birth|
|07|Migration/Residence 1 Year Ago|
|08|Commuting (Journey to Work); Place of Work|
|09|Relationship to Householder|
|10|Grandparents and Grandchildren Characteristics|
|11|Household Type; Family Type; Subfamilies|
|12|Marital Status; Marital History|
|13|Fertility|
|14|School Enrollment|
|15|Educational Attainment; Undergraduate Field of Degree|
|16|Language Spoken at Home|
|17|Poverty Status|
|18|Disability Status|
|19|Income|
|20|Earnings|
|21|Veteran Status; Period of Military Service|
|22|Food Stamps/Supplemental Nutrition Assistance Program (SNAP)|
|23|Employment Status; Work Status Last Year|
|24|Industry, Occupation, and Class of Worker|
|25|Housing Characteristics|
|26|Group Quarters|
|27|Health Insurance Coverage|
|28|Computer and Internet Use|
|29|Citizen Voting-Age Population|
|98|Quality Measures|
|99|Allocation Table for Any Subject|

**IMPORTANT:**
- Make note of all table IDs for the data used in an analysis.
- When using multiple variables, the data should all come from the same table, do not try to mix data from different tables or topics.

### Using the API
The Census API is by far the easiest way to get data for analysis. It does come with a bit of overhead. You do need to know a bit of code and it can be challenging at times to find the right data. There are tools for downloading data from the API in both [R](https://walker-data.com/tidycensus/) and [Python](https://github.com/datamade/census). You will need to [get an API key](https://api.census.gov/data/key_signup.html) from the Census for both tools.