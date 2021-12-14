#MVP
##Real-time Road Accident Risk Predictor

### Client

- UK Governmental Department: The Department for Transport 

### Motivation for project

- The Road Safety Division of the UK Department for Transport is approaching makers of the most popular GPS navigation apps to see if there is appetite for participating in a joint pilot project. The aim would be to investigate whether added functionality in a GPS navigation app could be used to help reduce the number of road accidents on UK roads each year.

### Question
- Can a navigation app usefully predict moments of heightened accident risk for a road user in real-time using:
  - historical accident data,
  - data previously collected by the navigation app (e.g. data related to sharp braking), and
  - live data such as speed, weather conditions, time of day and traffic conditions?

### Impact hypothesis
- Moments of high risk on the road can be identified using relevant data. Being warned just before such moments will allow drivers to act in such a way as to lessen the accident risk. Thereby road accidents, and the tremendous suffering they cause, can be reduced.

### Data Description

 - The UK government publishes extensive road accident data.
 - This consists of detailed data on accidents on public roads since 1979 reported to the police involving any kind of personal injury.
 - It is available [here](https://data.gov.uk/dataset/cb7ae6f0-4be6-4935-9277-47e5ce24a11f/road-safety-data) for download in csv file format 
 - For example, the UK government has just published data for the first six months of 2021, with 42,539 accidents recorded. 
 - Individual sample/unit of analysis is a specific accident.
 - Example relevant features available:
   - Date
   - Time
   - Location
   - Severity (e.g. 'fatal', 'serious', 'slight')
   - Type of junction (e.g. 'crossroads', 'not at junction or within 20 metres')
   - Location in relation to junction (e.g. 'approaching junction', 'entering main road')
   - Weather conditions (e.g. 'fog or mist')
   - Road surface conditions (e.g. 'wet or damp', 'snow')
   - Light conditions (e.g. 'darkness - lights lit')
   - Special conditions (e.g. 'roadworks')
   - Carriageway hazards (e.g. 'dog on road')
   - Vehicle type
   - Towing and articulation (e.g. 'single trailer')
   - Vehicle Manoevre (e.g. 'waiting to turn left', 'changing lane to right', 'overtaking moving vehicle - offside')
   - Vehicle Direction From (e.g. 'north east') 
   - Vehicle Direction To
   - Journey purpose of driver (e.g. 'commuting', 'taking pupil to/from school')
   
### Solution Path
 - Supervised learning: classification. 
 - Specifically, classifying each 'moment' on the road as high enough risk to warn driver, or not. 
 - A moment here is a combination of location on the road, direction of travel, speed plus a set of conditions.

### Criteria for success
- The success of this project would be evaluated by A/B testing.
- If the project gets far enough, a successful ultimate A/B test might be:
  - Actual road users with the 'accident risk warning' functionality switched on in their navigation app are involved in fewer accidents, and in accidents of less severity, than a control group, or: 
  - Road users with the functionality have fewer instances of sharp braking than a control group.
- However there would also need to be a series of A/B tests leading up to this stag in the project, for example checking any warnings from the app did not adversely affect safety in a simulated road environment.

### Assumptions and Risks
- Road accidents are predictable from road circumstances and conditions (and therefore from historical accident data). They are not just due to random human or mechanical error.
- To train a classification model, we would need data on 'non-accidents' as well as 'accidents'. It may well be that even if we could come up with such data, the data would be too unbalanced to create a viable model.
- Being warned just prior to a moment of high accident risk reliably causes a driver to take action to lessen the risk of an accident. The warnings don't, for example, cause anxiety and therefore result in worse driving: equally the warnings don't just get ignored because they are too common.
- If the project is only marginally successful, it may then be necessary to weigh up significant financial cost against loss of life. This could lead to very difficult decisions for the organisations involved; and reputational risk if information was leaked into the public domain.

### Tools for pitch

- Google Sheets
- Tableau

### MVP Visualisation
- [This visualisation](https://public.tableau.com/app/profile/will7441/viz/RoadSafety_16388111470050/RoadAccidents2020-EastDorsetUK) adds some support to the idea that road accidents are predictable. Certain stretches of road and certain junctions in Bournemouth, UK, saw numerous accidents in 2020; whereas comparable stretches and junctions in the same area saw none.
- On a similar point certain stretches of road saw a series of accidents that happened in the dark.
- More investigation is needed on this.

### Reference for context
- ["The Deadly Myth That Human Error Causes Most Car Crashes"](https://www.theatlantic.com/ideas/archive/2021/11/deadly-myth-human-error-causes-most-car-crashes/620808) - Article from The Atlantic Magazine, Nov 2021
