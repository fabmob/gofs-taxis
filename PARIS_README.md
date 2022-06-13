# Paris GTFS-On demand (GOFS) example
Created by [La Fabrique des Mobilités](https://fabmob.io)

This is very much a work in progress, usage is not recommended.

## Notes on how files are populated

### feed_info.txt
Start and end dates are chosen to be from june 2022 to end of year. Taxis offer being pretty stable, it might still be valid later in the future

### agency.txt
For simplicity sake, only large taxis aggregators are considered, they are called "centrales" and 3 operating in paris can be identified ([source](https://www.taxis-paris.fr/centrale-reservation-taxis.htm)):

* Alpha Taxis (~1200 taxis)
* Taxis G7 (~7500 taxis) (Merged with Taxis Bleus in 2017)
* Belem Taxis 7000

TODO: taxi banlieue: ABC Taxis : centraltaxi93.com 01 43 83 64 00

### routes.txt
As a start, we only define one route per agency. This will later be extended with larger vehicle types.
Route colors are chosen based on brand colors if available.

### calendar.txt
We define an unique service available every day of the week for the whole year

### trips.txt
With only one service, we have direct match between routes and trips.
As a start, only luggage is allowed in taxis, with no place for wheelchair, bicyle or animals.

### capabilities.txt
One capability of service is defined, with no special driver training.

### vehicle_categories.txt
Each agency has one type of vehicle, with 3 available regular seats. Propulsion is set to combustion. Electrical and hybrid vehicles will be added later.

### locations.geojson
One location "Paris Intra Muros" is defined using the https://geojson.io tool. If needed, regions can be defined with https://france-geojson.gregoiredavid.fr/
We also divide paris into two locations: ParisRiveDroite and ParisRiveGauche. These will later be used for Airport fares.

### stop_times.txt
One stop per agency for now. wait times are set to 12 min average, 20min safe. See https://www.g7.fr/tarifs-taxis-paris for extension

### booking_rules.txt
G7 can be booked up to 30 days in advance, Alpha can be booked 2 month in advance, not sure about belem.

### rider_categories.txt
One category of riders is defined: AllRiders

### stops.txt
We define the two airports as stops since they have specific fare rates, lat lng are rough

### wait_rules.txt
We have no details yet about specific waiting times, so wait rules are not set.

### fare_leg_rule.txt
Default fare is set to 2.60€ for all agencies, taxes included
We also defined fixed prices fares between airports and paris

### fare_variable_rules.txt
We define a fare for each km traveled at 1.10€ per km (computed every km?), no matter the distance [Source](https://www.economie.gouv.fr/files/files/directions_services/dgccrf/documentation/guide_voyageur/tarifs-taxi-2022.pdf?v=1644575578), fares are actually dependant on the time of day ([see g7 fares](https://www.g7.fr/tarifs-taxis-paris)), but it is unclear how to define that.
We define an extra fare of 4€ for each person starting from the 5th
There is also an extra fare "forfaits d'approche"