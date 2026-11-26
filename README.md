# nyc_mobility_environment_project

# NYC Mobility & Environment

Microsoft Fabric project using NYC taxi trips, air quality, exchange rates and GDP data for 2023–2025

Bronze and Silver are completed  
Gold and visualizations are not finished yet

## What I used

Microsoft Fabric, Pipelines, Dataflows Gen2, Power Query, PySpark and Pandas

Data sources:
NYC TLC - Yellow Taxi trips and zone lookup
OpenAQ - PM2.5 measurements
EPA - NO2 measurements
ECB - USD/EUR exchange rates
World Bank - USA GDP

## What I did

### Bronze

Loaded 36 monthly taxi files, three EPA archives and the taxi zone lookup through Pipelines
Used Dataflows Gen2 to load OpenAQ, ECB and World Bank data
Stored the source data in the "lh_nyc_data" Lakehouse and checked that the files could be read

### Silver

Combined the taxi files and fixed differences in column names and types
Checked dates, missing values, duplicates, distances, amounts and zone IDs
Kept pickups within 2023–2025 and excluded trips with drop-off before pickup or duration above 24 hours
Replaced distances above 1,000 miles with null and excluded records with missing fare or total amount, or amounts above USD 10,000 in absolute value
These limits are my project rules  
Zero-duration trips and negative data were kept
Prepared local dates for PM2.5 and kept missing values and quality flags
Selected NYC records from EPA files and checked the NO₂ data
Prepared exchange rates and GDP tables

## Saved tables

Tables - rows

-silver_taxi_zones - 265 
-silver_taxi_trips - 128,195,301
-silver_openaq_measurements - 119,073
-silver_epa_no2_daily - 4,243 
-silver_fx_rates - 766
-silver_gdp - 3


## Things to consider

Taxi data does not cover all traffic in NYC
Air quality stations (PM2.5, NO2) are in different locations


