# Aviation Accident Analysis
Authors: Brian Woo and Evan Rosenbaum

## Overview
Uber has decided that they would like to enter the aviation industry. Following the failed merger of JetBlue and Spirit airlines, Uber has decided diversify their business. In doing so, they are looking for new growth opportunities in an industry that has lagged behind other industries in their adoption of technology. 

Two different datasets were used for this anaylsis to gain insight into which aircraft has the best safety, durability, and lasting value. The results showed that commercial aircraft were involved in fewer accidents than business flights (exclusive of executive/corporate flights). As such, commercial aircraft were chosen as the type of aircraft to purchase and commercial flights the business to pursue.

Our recommendation to Uber is for them to pursue a fleet of either Boeign 787's, Airbus A321's, or Airbus A330's.

## Business Problem

### Priorities

#### Safety
Safety is the foremost concern for our client. They are looking for models with impeccable safety records. Further, they a preference for manufacturers with a proven track record of producing safe and reliable aircraft.

#### Durability
Our client is looking for an aircraft that has a long operational life. They want to ensure that their investment pays off and that their aircraft can withstand the wear and tear they put on it.

#### Lasting Value
Our client wants to be sure that the aircraft they purchase will not be outdated soon after their purchase. Further, they would prefer for their aircraft to be able to meet the current demands and potential future demands of the industry. 

## Data and Methods

### Source of Data
The first data set we analyzed came from the National Transportation Safety Board (NTSB). It includes aviation accident data from 1962 to 2023 about civil aviation accidents and selected incidents in the United States and international waters. The second was a csv file that contained US state codes. 

### Description of Data
After checking the NTSB data set to see the column names and null values, we merged the two data sets together using the state and abbreviation columns to ensure that we were only looking at accidents that occurred inside of the United States. This was important as the NTSB state column contained invalid US states. 

Once we had a merged data set, we filtered the data set down so that we were focussing on our stakeholder's concerns. We began with the columns that had no missing values inside of them. The investigation_type was of particular interest as it classified the event as either an accident or incident. After reviewing the Code of Federal Regulations we found that an incident is defined as "an occurrence other than an accident, associated with the operation of an aircraft, which affects or could affect the safety of operations(1)". Since an incident may or may not affect the safety of operations on the aircraft, it is hard to rely on this data as it does not give us concrete information about the event that occurred. To align with our stakeholder's priorities, we removed all incidents from the data set (~5% of the data).  

Following this, the next decision we made was how to clean the make and model columns. Through our review of the 'purpose_of_flight' column, we discovered that there were no aircrafts makred as commercial flights. Further, the columns labeled as 'personal' did not identify commercial flights but rather individuals flying personal planes. 

This lead us to research the commercial aircraft manufacturing industry. In doing so, we found that there are two major players, Boeing and Airbus. The two companies have held a duopoly over the commercial aircraft manufacturing industry since 1990. "Together account for 99% of all large aircraft orders (and these orders together account for 90% of all aircraft sales) (2)."

These insights lead us to working with the make and model columns. While there wasn't a lot of missing values in these columns, they proved to be hard to parse and glean insights from due to the number of unique values. The make column did not contain normalized casing and the model column contained the model and addition features. For instance there was the Airbus A320 and the A320-232. While the A320-232 has a different engine than the A320, it is in the A320 family of commercial aircraft. We decided to work with the overarching family of aircraft and label these aircraft as commercial flights so we could compare them against the personal aircrafts.

In that comparison, we found that commerical flights are slightly less risky than business flights. If we include executive/corporate flight purposes in with business flights, we see that commercial flights are the safer option between private or commercial flights. 

<img title="purpose_of_flight_analysis" alt="Alt text" src="/images/purpose_of_flight.png">

Once we determined that commerical aircraft were the safer option, we wanted to see which models were the most durable. To do so we looked at two key factors, if the model was in an accident, how damaged was the aircraft and the count of accidents that happened during a weather event. 

<img title="damage_analysis" alt="Alt text" src="/images/durability_of_aircraft.png">

<img title="weather_event_analysis" alt="Alt text" src="/images/weather_event.png">

Then, we worked to fill/impute as many missing values as we could. We also dropped columns that were not pertinent to our stakeholders priorities. 

### Columns with filled/imputed information
- location
- country
- injury_severity
- purpose_of_flight
- report_status
- aircraft_damage
- aircraft_category
- make
- model
- amateur_built
- number_of_engines
- engine_type
- total_fatal_injuries
- total_serious_injuries
- total_minor_injuries
- total_uninjured
- weather_condition
- broad_phase_of_flight
- report_status

### Columns Dropped
- event_id
- accident_number
- registration_number
- latitude
- longitude
- far_description
- schedule
- airport_code
- airport_name
- air_carrier
- publication_date

### Columns Added
- total_injuries
- year
- month
- date
- make_model

### Columns Cleaned
- injury_severity
- make
- purpose_of_flight

        Three visualizations (the same visualizations presented in the slides and notebook)

## Conclusion

<img title="safety_of_commercial_aircraft_analysis" alt="Alt text" src="/images/total_injuries.png">


Based on our findings we have concluded that these are the 3 top choices for your commerical airline company:

1. **Boeing 787**
- Pros:
    - Advanced technology and fuel efficiency (8,463 miles).
    - High passenger comfort with modern amenities.
    - No fatalities or hull losses reported.

- Cons:
    - Early operational issues with lithium-ion batteries.
    - Significant quality control issues and production slowdowns.
    - High program cost, requiring substantial sales to break even.

Verdict: Despite initial issues, the Boeing 787 is a reliable and modern aircraft suitable for long-haul flights, with a strong safety record post-battery redesign.

2. **Airbus A321**

- Pros:
    - Common type rating with other A320-family variants, reducing pilot training costs.
    - Still in production, ensuring parts availability and support.
    - Suitable for short to medium-haul routes (~4,000 miles).

- Cons:
    - Limited range operations, designed for short to medium flights.

Verdict: The Airbus A321 is a versatile, cost-effective option for medium-haul routes, benefiting from commonality with other A320-family aircraft.

3. **Airbus A330**

- Pros:
    - Extensive service history with more than 65 million flight hours.
    - Still in production, ensuring continued support and parts availability.
    - Well-suited for long flying ranges (~8,300 miles)

- Cons:
    - Less fuel efficient, which can result in high operational costs.
    - Older model plane, less advanced technology and lower overall efficiency.
    - Poor engine performance, which can decrease fuel efficiency and cause cabin vibrations.

Verdict: The Airbus A330 is a proven, reliable aircraft for medium to long-haul routes with a strong operational track record.
        
## Sources
1. https://www.ecfr.gov/current/title-49/subtitle-B/chapter-VIII/part-830/subpart-A/section-830.2
2. https://simpleflying.com/battle-of-big-planes/
