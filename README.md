# JHU CSSE COVID-19 Dataset
## covid19_data_analysis
Descriptive analysis of the COVID-19 problem in the United States. All analyzes are designed based on real COVID-19 data databases and answer specific questions from the project in GWU dnsc6305.

## Table of contents

 * [Daily reports (csse_covid_19_daily_reports)](#daily-reports-csse_covid_19_daily_reports)
 * [USA daily state reports (csse_covid_19_daily_reports_us)](#usa-daily-state-reports-csse_covid_19_daily_reports_us)
 * [Time series summary (csse_covid_19_time_series)](#time-series-summary-csse_covid_19_time_series)
 * [Data modification records](#data-modification-records)
 * [Retrospective reporting of (probable) cases and deaths](#retrospective-reporting-of-probable-cases-and-deaths)
 * [Large-scale back distributions](#large-scale-back-distributions)
 * [Irregular Update Schedules](#irregular-update-schedules)
 * [UID Lookup Table Logic](#uid-lookup-table-logic)
---

## [Daily reports (csse_covid_19_daily_reports)](https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_daily_reports)

This folder contains daily case reports. All timestamps are in UTC (GMT+0).

### File naming convention
MM-DD-YYYY.csv in UTC.

### Field description
* <b>FIPS</b>: US only. Federal Information Processing Standards code that uniquely identifies counties within the USA.
* <b>Admin2</b>: County name. US only.
* <b>Province_State</b>: Province, state or dependency name.
* <b>Country_Region</b>: Country, region or sovereignty name. The names of locations included on the Website correspond with the official designations used by the U.S. Department of State.
* <b>Last Update</b>: MM/DD/YYYY HH:mm:ss  (24 hour format, in UTC).
* <b>Lat</b> and <b>Long_</b>: Dot locations on the dashboard. All points (except for Australia) shown on the map are based on geographic centroids, and are not representative of a specific address, building or any location at a spatial scale finer than a province/state. Australian dots are located at the centroid of the largest city in each state.
* <b>Confirmed</b>: Counts include confirmed and probable (where reported).
* <b>Deaths</b>: Counts include confirmed and probable (where reported).
* <b>Recovered</b>: Recovered cases are estimates based on local media reports, and state and local reporting when available, and therefore may be substantially lower than the true number. US state-level recovered cases are from [COVID Tracking Project](https://covidtracking.com/). We stopped to maintain the recovered cases (see [Issue #3464](https://github.com/CSSEGISandData/COVID-19/issues/3464) and [Issue #4465](https://github.com/CSSEGISandData/COVID-19/issues/4465)).
* <b>Active:</b> Active cases = total cases - total recovered - total deaths. This value is for reference only after we stopped to report the recovered cases (see [Issue #4465](https://github.com/CSSEGISandData/COVID-19/issues/4465))
* <b>Incident_Rate</b>: Incidence Rate = cases per 100,000 persons.
* <b>Case_Fatality_Ratio (%)</b>: Case-Fatality Ratio (%) = Number recorded deaths / Number cases.
* All cases, deaths, and recoveries reported are based on the date of initial report. Exceptions to this are noted in the "Data Modification" and "Retrospective reporting of (probable) cases and deaths" subsections below.  

### Update frequency
* Since June 15, We are moving the update time forward to occur between 04:45 and 05:15 GMT to accommodate daily updates from India's Ministry of Health and Family Welfare.
* Files on and after April 23, once per day between 03:30 and 04:00 UTC. 
* Files from February 2 to April 22: once per day around 23:59 UTC.
* Files on and before February 1: the last updated files before 23:59 UTC. Sources: [archived_data](https://github.com/CSSEGISandData/COVID-19/tree/master/archived_data) and dashboard.

### Data sources
Refer to the [mainpage](https://github.com/CSSEGISandData/COVID-19).

### Why create this new folder?
1. Unifying all timestamps to UTC, including the file name and the "Last Update" field.
2. Pushing only one file every day.
3. All historic data is archived in [archived_data](https://github.com/CSSEGISandData/COVID-19/tree/master/archived_data).

---
## [USA daily state reports (csse_covid_19_daily_reports_us)](https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_daily_reports_us)

This table contains an aggregation of each USA State level data.

### File naming convention
MM-DD-YYYY.csv in UTC.

### Field description
* <b>Province_State</b> - The name of the State within the USA.
* <b>Country_Region</b> - The name of the Country (US).
* <b>Last_Update</b> - The most recent date the file was pushed.
* <b>Lat</b> - Latitude.
* <b>Long_</b> - Longitude.
* <b>Confirmed</b> - Aggregated case count for the state.
* <b>Deaths</b> - Aggregated death toll for the state.
* <b>Recovered</b> - Aggregated Recovered case count for the state.
* <b>Active</b> - Aggregated confirmed cases that have not been resolved (Active cases = total cases - total recovered - total deaths).
* <b>FIPS</b> - Federal Information Processing Standards code that uniquely identifies counties within the USA.
* <b>Incident_Rate</b> - cases per 100,000 persons.
* <b>Total_Test_Results</b> - Total number of people who have been tested.
* <b>People_Hospitalized</b> - Total number of people hospitalized. (Nullified on Aug 31, see [Issue #3083](https://github.com/CSSEGISandData/COVID-19/issues/3083))
* <b>Case_Fatality_Ratio</b> - Number recorded deaths * 100/ Number confirmed cases.
* <b>UID</b> - Unique Identifier for each row entry. 
* <b>ISO3</b> - Officially assigned country code identifiers.
* <b>Testing_Rate</b> - Total test results per 100,000 persons. The "total test results" are equal to "Total test results (Positive + Negative)" from [COVID Tracking Project](https://covidtracking.com/).
* <b>Hospitalization_Rate</b> - US Hospitalization Rate (%): = Total number hospitalized / Number cases. The "Total number hospitalized" is the "Hospitalized – Cumulative" count from [COVID Tracking Project](https://covidtracking.com/). The "hospitalization rate" and "Total number hospitalized" is only presented for those states which provide cumulative hospital data. (Nullified on Aug 31, see [Issue #3083](https://github.com/CSSEGISandData/COVID-19/issues/3083))

### Update frequency
* Once per day between 04:45 and 05:15 UTC.

### Data sources
Refer to the [mainpage](https://github.com/CSSEGISandData/COVID-19).

---
## [Time series summary (csse_covid_19_time_series)](https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_time_series)

See [here](https://github.com/CSSEGISandData/COVID-19/blob/master/csse_covid_19_data/csse_covid_19_time_series/README.md).

---
# Overall flow of the project
## Part 1 - Data Loading
1. Manually Upload files - required for the project: Cases, Vaccine, Vaccine P, Timeseries (Time table), Population
2. Stack file based on year
3. Spark

## Part 2 - Database Design
1. Create and clean the “Cases” Table 
2. Create and clean the “Times” Table 
3. Create and clean the “VaccineP” Table 
4. Create and clean the “Vaccine” Table
5. Merge the “Vaccine” table and “VaccineP” table into the “Vaccine”
 * VaccineP Table: About people vaccinated in the US with timeline (ex, people_fully_vaccinated, people_partially_vaccinated)
 * Vaccine Table: About vaccine data in the US with timeline (ex, vaccine_type, doses_alloc, doses_shipped, doses_admin, stage_one_doses, stage_two_doses)
6. State Dimension 
 * Create and add data to “State” table - with columns “State_ID”, “FIPS”, “Province_state”, “latitude”, “longitude”
 * Add a foreign key constraint to a table: State_ID Foreign Key for 3 tables (“cases”, “times”, “vaccine”)
7. Time Dimension 
 * Create and add data to the “date” table - with columns “Date_ID”, “hour”, “day”, “year”, “month_of_year_str”, “monthe_of_year”, “day_of_month”, “day_of_week_str”, “day_of_week”, “hour_of_day”, “quarter_of_year”
 * Add a foreign key constraint to a table: Date_ID Foreign Key for 3 tables (“cases”, “times”, “vaccine”)
8. Check Final Tables created - “cases”, “vaccine”, “state”, “date”, “times” 

## Part 3 - Questions
(Q1) What’s the percentage of people who are affected by COVID based on the state? 
(Q2) What are the “confirmed vs recovery vs death” cases by the state? 
(Q3) Do vaccines have an actual effect on covid cases? (by location, by year) 
(Q4) Do testing rates affect confirmed cases? (by state) 
(Q5) Were there any changes in confirmed cases before/after restrictions?  

## Part 4 - Dimensional Model
<b>Star Schema</b>
![image](https://github.com/itsIsabelle17/Covid-19-DA/assets/114459340/e0a1eaca-a9ab-403b-a0e7-9b729c221979)

## Part 5 - Queries to answer questions
All details and processes are described in detail in the following files: "Final Project - Group 7.jpynb", "Project Report.pdf", and "Final Project Presentation - Group 7.pdf"



Disclaimer: \*The names of locations included on the Website correspond with the official designations used by the U.S. Department of State. The presentation of material therein does not imply the expression of any opinion whatsoever on the part of JHU concerning the legal status of any country, area or territory or of its authorities. The depiction and use of boundaries, geographic names and related data shown on maps and included in lists, tables, documents, and databases on this website are not warranted to be error free nor do they necessarily imply official endorsement or acceptance by JHU.
