# Aviation Accident Analysis
Authors: Brian Woo and Evan Rosenbaum

## Overview
Uber has decided that they would like to enter the aviation industry. In doing so, they are looking for new growth opportunities in an industry that has lagged behind other industries in their adoption of technology. 

Two different datasets were used for this anaylsis to gain insight into which aircraft has the best safety, durability, and lasting value. The results showed that commercial aircraft were involved in fewer accidents than business flights (exclusive of executive/corporate flights). As such, commercial aircraft were chosen as the type of aircraft to purchase and commercial flights the business to pursue.

Our recommendation to Uber is for them to pursue a fleet of either Airbus A330's, Airbus A321's, or Airbus A320's.

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

Once we had a merged data set, we filtered the data set down so that we were focussing on our stakeholder's concerns. We began with determining whether Uber should enter the commercial or private aviation industry. 

<img title="purpose_of_flight_analysis" alt="graph displaying a bar chart comparing different purposes of flight" src="/images/purpose_of_flight.png">

We found that commercial flights had fewer fatal injuries than private flights (labeled as business). As such, we chose to focus our data set on commercial flights to determine which aircraft met the criteria of our client. 

The next decision we made was how to clean the make and model columns. While there wasn't a lot of missing values in these columns, they proved to be hard to parse and glean insights from due to the number of unique values. The make column did not contain normalized casing and the model column contained the model and addition features. For instance there was the Airbus A320 and the A320-232. While the A320-232 has a different engine than the A320, it is in the A320 family of commercial aircraft. We decided to work with the overarching family of the aircraft. 

<img title="purpose_of_flight_analysis" alt="graph displaying a bar chart comparing different purposes of flight" src="/images/purpose_of_flight.png">

Once we determined that commerical aircraft were the safer option, we wanted to see which models were the most durable. To do so we looked at two key factors, if the model was in an accident, how damaged was the aircraft and the count of accidents that happened during a weather event. 

<img title="damage_analysis" alt="graph displaying a bar chart comparing different amounts of damage on commercial aircraft" src="/images/durability_of_aircraft.png">

While there are lot of unknown values, one thing is clear. When commercial aircraft get into accidents, they are rarely destroyed. Most of the time the damage is substantial but not beyond repair. 

<img title="weather_event_analysis" alt="graph displaying a bar chart comparing the amount of accidents that occurred due to different weather events" src="/images/weather_event.png">

This analysis lead us to find that weather conditions could lead to an accident however when an accident did occur, it was rare that it was in conditions where visibility was so low that pilots needed to rely on flight instruments. As such, most accidents occur when the pilot has sufficient visibility to fly the aircraft maintaining visual separation from terrain and other aircraft. 

<img title="human_error_analysis" alt="graph displaying a bar chart comparing if accidents on commercial aircraft were caused by human error" src="/images/human_error.png">

However, when we dug into this, all accidents on commercial aircraft were not the result of human error. It is worth noting that the 'report_staus' column did have ~7% missing values so there is the chance that an accident was the result of human error. 

This shows that regardless of the weather condition (IMC v VMC), pilots of commercial aircrafts are not the root cause of the accident. 

For our stakeholder, this is good news as it allowed a direct comparison of commercial aircraft as the accidents should all be caused by the aircraft itself and not the crew piloting the aircraft. 

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
- year
- month
- date
- make_model

### Columns Cleaned
- injury_severity
- make
- purpose_of_flight

        Three visualizations (the same visualizations presented in the slides and notebook)

## Recommendations

### Where and when?
We recommend starting business in October and in the Midwest as there have been the fewest fatal injuries to occur. 

### Pilot Training

We recommened going above and beyond the FAA mandated hour requirement for pilot training. The more hours spent training will produce better and safer pilots.

Specifically spend additional time in procedural aspects of the takeoff and approach as these had the highest cases of fatal injury. 

### Best Commercial Aircraft

<img title="safety_of_commercial_aircraft_analysis" alt="Alt text" src="/images/total_injuries.png">


Based on our findings we have concluded that these are the 3 top choices for your commerical airline company:

1. **Airbus A330**

- Pros:
    - Extensive service history with more than 65 million flight hours.
    - Still in production, ensuring continued support and parts availability.
    - Well-suited for long flying ranges (~8,300 miles)

- Cons:
    - Less fuel efficient, which can result in high operational costs.
    - Older model plane, less advanced technology and lower overall efficiency.
    - Poor engine performance, which can decrease fuel efficiency and cause cabin vibrations.

Verdict: The Airbus A330 is a proven, reliable aircraft for medium to long-haul routes with a strong operational track record.

2. **Airbus A321**

- Pros:
    - Common type rating with other A320-family variants, reducing pilot training costs.
    - Still in production, ensuring parts availability and support.
    - Suitable for short to medium-haul routes (~4,000 miles).

- Cons:
    - Limited range operations, designed for short to medium flights.

Verdict: The Airbus A321 is a versatile, cost-effective option for medium-haul routes, benefiting from commonality with other A320-family aircraft.

3.  **Airbus A320**

- Pros:
    - Has completed more than 176 million flights over 328 million block hours.
    - Long and proven track record for safety (1986 - present).
    - Offers up to 15% better fuel economy with new eco-engines.  

- Cons:
    -  Limited range operations, designed for short to medium flights.

Verdict: The Airbus A320 has a strong reputation for reliability and performance, making it an excellent choice for medium to long-haul flights.