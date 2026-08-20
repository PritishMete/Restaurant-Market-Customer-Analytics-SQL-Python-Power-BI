Restaurant Analytics Project Dataset
=====================================

Purpose
-------
Synthetic, relational practice dataset designed around a restaurant analytics project using:
SQL + Python + Power BI.

It is intentionally messy so you can practice:
- joins
- missing-value treatment
- duplicate detection/removal
- inconsistent categorical values
- outlier/invalid coordinate detection
- data validation
- NLP on review text
- restaurant-chain analysis
- price/service comparisons
- geographic analysis

Files
-----
1. restaurants.csv
   Primary table. Restaurant-level attributes.
   Key: RestaurantID
   Important columns:
   Restaurant Name, LocationID, Price range, Aggregate rating,
   Rating text, Votes, Latitude, Longitude

2. locations.csv
   Location dimension.
   Key: LocationID
   Join: restaurants.LocationID = locations.LocationID

3. services.csv
   Restaurant service availability.
   Key: RestaurantID
   Join: restaurants.RestaurantID = services.RestaurantID

4. cuisines.csv
   Cuisine dimension.
   Key: CuisineID

5. restaurant_cuisines.csv
   Many-to-many bridge between restaurants and cuisines.
   Join:
   restaurant_cuisines.RestaurantID = restaurants.RestaurantID
   restaurant_cuisines.CuisineID = cuisines.CuisineID

6. reviews.csv
   Review-level table for text/NLP analysis.
   Key: ReviewID
   Join: reviews.RestaurantID = restaurants.RestaurantID

Suggested SQL joins
-------------------
restaurants
LEFT JOIN locations
  ON restaurants.LocationID = locations.LocationID

restaurants
LEFT JOIN services
  ON restaurants.RestaurantID = services.RestaurantID

restaurants
JOIN restaurant_cuisines
  ON restaurants.RestaurantID = restaurant_cuisines.RestaurantID
JOIN cuisines
  ON restaurant_cuisines.CuisineID = cuisines.CuisineID

restaurants
LEFT JOIN reviews
  ON restaurants.RestaurantID = reviews.RestaurantID

Intentional data-quality issues
--------------------------------
- exact duplicate restaurant rows
- duplicate bridge-table rows
- duplicate review rows
- missing restaurant names
- missing price ranges
- missing ratings
- missing votes
- missing coordinates
- missing city/country values
- missing review text
- inconsistent Yes/No values such as yes, YES, " Yes ", Y, N and blanks
- inconsistent capitalization/whitespace in restaurant names
- invalid price-range values such as 0, 5 and 9
- invalid latitude/longitude values outside valid geographic ranges
- rating value 0 used for some Not rated restaurants

Important
---------
This is a synthetic practice dataset, not a copy of a proprietary/customer dataset.
It is intentionally generated to support the requested analytics objectives.

Recommended project questions
-----------------------------
- Restaurant count and rating distribution
- Price range distribution
- Price range vs online delivery
- Price range vs table booking
- Higher-priced restaurants and service availability
- Rating vs online delivery
- Rating vs table booking
- Votes vs rating correlation
- Highest/lowest vote restaurants
- Top restaurant chains and outlet counts
- Chain ratings and popularity
- Most common cuisines
- Cuisine combinations and average ratings
- City/country restaurant concentration
- Geographic clusters using latitude/longitude
- Review length vs rating
- Positive/negative review keywords
- Data-quality assessment
- Optional rating prediction model
