# Geography for Google Mobility reports

## 04/09/2020
Last week Google started including additional geographic granularity in the data published for the UK. This is great news.

The data can continue to be analysed at the previous level of granularity using the *sub_region_1* column in the [Global_Mobility_Report.csv](https://www.google.com/covid19/mobility/) and the files refered to in the 07/05/2020 update below.  

By using a combination of the *sub_region_1* and *sub_region_2* columns the data can also now be used at Local Authority level. This is an increase in granularity from the 151 areas the UK is split into at *sub_region_1* level to 383 Local Authorities. However, it is not as straightforward as just using the *sub_region_2* column to carry out analysis at the LA level due to some of the *sub_region_1* areas being the LA (in which case the *sub_region_2* column is empty). 

To analyse the data at the LA level join the **google_mobility_lad_lookup_200903.csv** table to the Global_Mobility_Report.csv data on both the *sub_region_1* and *sub_region_2* columns and use the *la_name* or *lad19cd* column as the unique identifier, excluding the rows in the data which represent the coarser granularity data and don't have a *la_name*. 

To map the LA level data the **google_mobility_lad_boundary_200903.shp** or **google_mobility_lad_boundary_200903.gpkg** can be used and the mobility data joined using the *country_region_code*, *sub_region_1* and *sub_region_2* columns

Further notes:  
* Most of the LAs in the Google mobility data are the 2019 areas, but there are a few which are from 2018 (e.g. the Google mobility data contains "West Somerset District" & "Taunton Deane", which were replaced with "Somerset West and Taunton" in 2019, and "Suffolk Coast" and "Waveney" which were replaced with "East Suffolk"). The *flag_2018* column in the google_mobility_lad_lookup_200903.csv indicates where the 2018 boundaries have been used as this may cause complications if joining the mobility data to other data at LA level.

* The formatting of the names in the Google mobility data is not consistent with standard LA names; this is why the *sub_region_2* column differs from the *la_name* column in places.

* Dorset is both a *sub_region_1*, where we believe the data covers the ceremonial county (and therefore includes Bournemouth, Christchurch and Poole), and also split into 2 LAs at the *sub_region_2*, one of which is also called "Dorset" which we believe to be the current LA.

* The Isles of Scilly is an LA that's not in the Google mobility data so is not included in the shapefile.

* In the Google mobility data there is *sub_region_1* data for Cornwall but also a *sub_region_2* split for Penryn but it's a very small place with mostly disclosive data and Cornwall is the LA level.

It is possible that the geographies used in the Google mobility data will change again in the future. The above is accurate to the best of our knowledge on 03/09/2020.

## 07/05/2020 
Revised lookup tables and boundaries file have been provided to reflect the changes made in the published Google Mobility data in the separation of Nottingham and Nottinghamshire.

The latest files are:

* Google_Places_Lookup_Table_200417.csv

* Google_Places_All_UK_2018_Population_Estimates_200417.csv

* Google_Places_UK_Boundaries_BGC_200417.gpkg

* Google_Places_Lookup_Table_200417_Metadata.csv
