# Step-by-Step Tableau Project Guide

This guide documents the process used to build the AirBnB Tableau dashboard. The project follows a guided Tableau workflow and focuses on turning raw Airbnb data into a clean, interactive dashboard for business analysis.

## 1. Load the Excel Workbook

The project begins by connecting Tableau to the Excel workbook:

```text
Tableau Full Project.xlsx
```

The workbook contains three sheets:

| Sheet | Purpose |
| --- | --- |
| Listings | Listing-level property details, location fields, bedrooms, and price |
| Calendar | Daily listing availability and pricing records |
| Reviews | Guest review records connected to listings |

## 2. Review the Data Model

Before creating charts, the tables were reviewed to understand how they connect.

Important fields:

- `Listings.id` represents the unique Airbnb listing.
- `Calendar.listing_id` connects calendar records to each listing.
- `Reviews.listing_id` connects reviews to each listing.
- `Reviews.id` represents a review ID, not a listing ID.

This step is important because joining tables on the wrong field can create incorrect results.

## 3. Join Listings and Calendar Data

The main dashboard uses listing and calendar data. The key join is:

```text
Listings.id = Calendar.listing_id
```

This connection allows listing attributes, such as zip code and bedroom count, to be analyzed alongside calendar-based pricing and revenue.

## 4. Create Average Price by Zip Code

The first worksheet compares average Airbnb listing price by zip code.

Steps:

- Drag `Zipcode` into the view.
- Drag `Price` into the view.
- Change the aggregation from sum to average.
- Exclude null zip codes.
- Sort zip codes by average price.

Purpose:

This chart helps identify which Seattle zip codes have higher average Airbnb prices.

## 5. Create Price by Zip Code Map

The second worksheet displays average price geographically.

Steps:

- Use `Zipcode` as the geographic field.
- Add average `Price` to the map.
- Display zip code labels and average price labels.
- Use color to separate zip code areas.

Purpose:

This map provides location context for the pricing analysis.

## 6. Create Revenue by Year

The third worksheet analyzes revenue trends over time using the calendar table.

Steps:

- Drag `Date` into the columns area.
- Drag `Price` into the rows area.
- Use weekly date granularity.
- Filter the view to 2016 to avoid incomplete future-year data.
- Format the line chart for readability.

Purpose:

This chart shows how Airbnb revenue changes throughout the year and highlights seasonal patterns.

## 7. Create Average Price by Bedrooms

The fourth worksheet compares average listing price by bedroom count.

Steps:

- Use `Bedrooms` as a dimension.
- Drag average `Price` into the view.
- Exclude null and zero-bedroom records.
- Add labels to show average price values.

Purpose:

This chart shows how pricing changes as property size increases.

## 8. Create Bedroom Listing Count

The fifth worksheet counts the number of distinct listings by bedroom category.

Steps:

- Use `Bedrooms` as the category.
- Count distinct listing IDs.
- Exclude null and zero-bedroom records.
- Format the result as a compact table.

Purpose:

This view shows supply and competition by property size.

## 9. Build the Final Dashboard

The final dashboard combines the completed worksheets:

- Average price per bedroom
- Distinct count of bedroom listings
- Price per zip code map
- Price by zip code bar chart
- Revenue for year line chart

Dashboard layout decisions:

- Place the bedroom price chart at the top because it gives a quick summary of pricing by property size.
- Keep the bedroom listing count beside it to compare price with competition.
- Place the map and zip code bar chart together so location-based insights are easy to compare.
- Place revenue trends beside location analysis to show seasonality.

## 10. Publish to Tableau Public

After the dashboard was completed, it was published to Tableau Public so it could be shared as part of a data analytics portfolio.

Live dashboard:

https://public.tableau.com/app/profile/nicanor.jr.peril/viz/AirBnBFullProject_17798355555580/Dashboard1?publish=yes

## Key Takeaways

- Zip code analysis helps identify higher-priced Seattle areas.
- Average price generally increases as bedroom count increases.
- One-bedroom listings have the highest listing count, suggesting stronger competition in that category.
- Revenue changes throughout the year, making seasonality important for Airbnb analysis.
- Data modeling and correct joins are essential before building visualizations.
