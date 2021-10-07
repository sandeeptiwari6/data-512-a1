# A1: Data Curation
___

## Goal
__

The goal of this assignment is to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through August 30 2021. The data acquisition, preprocessing, and analyses can all be found in this [notebook](https://github.com/sandeeptiwari6/data-512-a1/blob/main/hcds-a1-data-curation.ipynb)

The purpose here is to demonstrate that I can follow best practices for conducting open research in designing and implementing an independent Data Science project, while documenting it to make it fully reproducible. This way, others can recreate each step from end to end.

## Licenses + API Documentation
__

The license for the source data can be found [here](https://creativecommons.org/licenses/by-sa/3.0/)

The terms of use for the Wikimedia REST API can be found [here](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions)

The Legacy Pagecounts API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts), [endpoint](https://wikimedia.org/api/rest_v1/#/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end)) provides access to desktop and mobile traffic data from December 2007 through July 2016.

The Pageviews API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews), [endpoint](https://wikimedia.org/api/rest_v1/#/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through last month.

## Data Overview
__

Data from both APIs were consolidated into one singular CSV file. This file can be found [here](https://github.com/sandeeptiwari6/data-512-a1/tree/main/data_clean), and follows this schema:

| Column                  | Value     |
|-------------------------|-----------|
| year                    | YYYY      |
| month                   | MM        |
| pagecount_all_views     | page count for all access types |
| pagecount_desktop_views | page count for desktop access type |
| pagecount_mobile_views  | page count for mobile access type |
| pageview_all_views      | page view count for all access types |
| pageview_desktop_views  | page view count for desktop access type |
| pageview_mobile_views   | page view count for mobile access type |

## Important Issues and other special considerations
__

- There was about 1 year of overlapping traffic data between the two APIs from around 2015-2016
- As much as possible, we're interested in organic (user) traffic, as opposed to traffic by web crawlers or spiders. The Pageview API (but not the Pagecount API) allows you to filter by agent=user.
