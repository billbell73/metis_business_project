# Metis Business Module Project

## Real-time road accident risk prediction

### Abstract

The Road Safety Division of the UK Department for Transport is approaching makers of the most popular GPS Navigation Apps to see if there is appetite for participating in a joint pilot project. The aim would be to investigate whether added functionality in a GPS navigation app could be used to help reduce the number of road accidents on UK roads each year.

### Design

The pitch seeks to raise the question of whether a navigation app might predict moments of heightened accident risk for a road user in real-time using:
historical accident data, data previously collected by the navigation app, and live data such as speed, weather conditions, and traffic conditions. The hope is that a way of warning app users / drivers can be found that enables them to act in such a way as to lessen the accident risk. Thereby road accidents, and the tremendous suffering they cause, could be reduced.

### Data
* The UK government publishes extensive road accident data.
* The data covers all road accidents reported to the police involving any kind of personal injury, dating back to 1979.
* I worked with the following files downloaded from [here](https://data.gov.uk/dataset/cb7ae6f0-4be6-4935-9277-47e5ce24a11f/road-safety-data):
    * dft-road-casualty-statistics-casualty-2020.csv
    * dft-road-casualty-statistics-accident-2020.csv
    * dft-road-casualty-statistics-vehicle-last-5-years.csv
    * dft-road-casualty-statistics-accident-last-5-years.csv
    * Road-Safety-Open-Dataset-Data-Guide.xlsx
* In terms of the size of datasets used, as an example `dft-road-casualty-statistics-accident-2020.csv` has 91,200 rows and 36 columns.

### Algorithms
#### Excel work
* Data cleaning: The csv files seem to be pretty clean as they are. I couldn't find any duplicate rows in any of the files I worked with. There were no blank cells. There were a few null values for location (i.e. latitude and longitude etc) in dft-road-casualty-statistics-accident-2020.csv but I didn't delete these rows because they didn't seem to cause tableau any problems for the visualisations I was creating.
* I did an advanced filter on the sizeable csv download: `dft-road-casualty-statistics-accident-last-5-years.csv`. With almost 600,000 rows, this made excel run slow on my local machine, so I filtered for rows where the longitude was between the values of -2.97 and -1.61 and the latitude was below 51.1 (I figured out these values - which cover the county of Dorset in the UK - using google maps). I then exported the filtered rows into the excel workbook `accidents_dorset_5_years.xlsx`. And this became the basis for much of my visual investigation of the data using Tableau mapping.
* I added a number of columns to `accidents_dorset_5_years.xlsx` using excel conditional functions and VLOOKUP functions. These calculated columns are shaded light blue.
* Many of the VLOOKUP functions reference the data from `Road-Safety-Open-Dataset-Data-Guide.xlsx` which is essentially a key for what many of the numeric values in the main data represent (e.g. a value of 6 for light conditions means 'Darkness - no lighting'. I eventually copied this lookup data into an extra tab on my `accidents_dorset_5_years.xlsx` workbook for ease of reference.
* The 'vehicle_manoeuvre_code' column at the far right of `accidents_dorset_5_years.xlsx` was created doing a VLOOKUP referencing the large csv file: `dft-road-casualty-statistics-vehicle-last-5-years.csv`. This VLOOKUP column made the workbook run really slow, so I did a copy and paste special with values only. That solved the performance problem. For the record, the VLOOKUP function was `=VLOOKUP(A2, 'dft-road-casualty-statistics-vehicle-last-5-years.csv'!$1:$1048576, 7, FALSE)`
* The statistics in the presentation for people killed and seriously injured in road accidents last year were calculated via a pivot table in `dft-road-casualty-statistics-casualty-2020.xlsx`.


#### Tableau Visualisations
Here are a selection of the visualisations I created in Tableau:
* [Road Accidents 2020 - Bournemouth, UK - light and weather conditions](https://public.tableau.com/app/profile/will7441/viz/RoadSafetyBournemouth/RoadAccidents2020-EastDorsetUK)
* [Road Accidents since 2016 - Bournemouth, UK - light and weather conditions](https://public.tableau.com/app/profile/will7441/viz/RoadSafetyv2/RoadAccidents-Past5years)
* [Junction A](https://public.tableau.com/app/profile/will7441/viz/RoadSafetyv2/junctionA)
* [Road Accidents since 2016 - Bournemouth, UK - with clustering on four features](https://public.tableau.com/app/profile/will7441/viz/RoadSafetyv2/clusters_1)
* [Road Accidents since 2016 - Bournemouth, UK - with clustering on weather and road surface conditions](https://public.tableau.com/app/profile/will7441/viz/RoadSafetyv2/clusters_2)
* [Road Accidents since 2016 - Bournemouth, UK - first vehicle manoeuvre](https://public.tableau.com/app/profile/will7441/viz/RoadSafetyv2/Manoeuvres)
* [Road Accidents since 2016 - Bournemouth, UK - day of the week](https://public.tableau.com/app/profile/will7441/viz/RoadSafetyv2/dayoftheweek)
* [Road Accidents since 2016 - Bournemouth, UK - accident severity](https://public.tableau.com/app/profile/will7441/viz/RoadSafetyv2/severity)

##### _Visualisations Notes_:
* I used the Road Accidents 2020 visualisation in the presentation because I thought it was a bit easier on the eye than the equivalent one with 5 years of data.
* I had hoped to find a series of map-based visualisations like the 'Junction A' one above, i.e. showing similar accidents at different times. This was the aim of much of the visualisation work listed above: I thought it would help the persuasiveness of the pitch if I could demonstrate for example, a number of accidents on the same stretch of road when the road surface is wet, or a number of accidents at the same corner in the dark. Tableau's in-built clustering functionality helped me investigate this. However, with the exception of 'Junction A', I really struggled to find locations with groupings of similar accidents (This surprised me, but may be because local government in the UK has been pro-active over the years at changing road layouts where accidents have occured repeatedly).

#### Suggested algorithm for pilot project
* Suggested algorithm for the envisaged pilot project is supervised learning: classification.
* Specifically, classifying each 'moment' on the road as high enough risk to warn driver, or not.
* A moment here is a combination of location on the road, direction of travel, speed plus a set of conditions.

### Tools

* Microsoft Excel
* Tableau

### Communication
The methodology and results of this project have been communicated via this document, and via a recorded presentation and its slide-deck.