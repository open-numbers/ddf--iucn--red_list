# sources

This dataset etl process (`script/etl.py`) currently expects 

- `source/bulk/assessments.csv` 
- `source/bulk/taxonomy.csv`

These files are not included due to [IUCN Red List Terms and Conditions](https://www.iucnredlist.org/terms/terms-of-use#4.%20No%20Reposting%20or%20Redistribution) and should thus be downloaded manually before running the script.

## `source/bulk/` folder - IUCN search bulk download

The IUCN Red List web site offers a "search -> download" functionality. Any search result can be downloaded by clicking on "download" in the top right corner. The site then prepares a zip download in your account which you can fetch a couple minutes later. This zip contains csv files which should be put in the `source/bulk/` folder.

Due to the needed login session and async download preparation it's not easily machine-accessible.

It is not possible to fetch historical assessments through this feature. 

There are undocumented limits on this download functionality. We encountered:
 - a limit on the amount of bird data. In March 2020 that meant you could download all animals twice before this limit was reached.


## Additional sources
These sources are currently not used in the etl script.

### `SummaryStatistics_Table7_ALL.xlsx`

Machine readable version of [summary table 7 PDF files](https://www.iucnredlist.org/resources/summary-statistics#Summary%20Tables) files published on the Red List web page.
File sent by email from IUCN Red List staff, containing status change reasons from 2006 to 2019-2. Many status changes are not genuine and thus don't represent actual change in population.  File available within Gapminder.

### Data API

Additionally, IUCN Red List provides a [data API](http://apiv3.iucnredlist.org/) which is currently on version 3. This API only serves a limited subsection of their data, not including the population trends we were interested in. It does serve historical assessments. Their frontend uses version 4 of the API and serves a lot more data. However, v4 has not been documented nor officially released for use by developers (confirmed by IUCN by email).

