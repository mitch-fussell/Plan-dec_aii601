# Trip price data (redone 2026-11-15: economy fares, 3-star hotels)

All prices in USD. Two files, ready to load into the CSP model:

- `hotels_june.csv`: one price per night per city, for one room (covers both travelers).
- `fares.csv`: one fare per person for each city pair and mode. Multiply by 2 for both travelers. Treat fares as the same in both directions.

**Budget:** $4,000 total for both travelers. In the model: sum of nightly room prices + 2 x sum of per-person fares <= 4000.

## How the numbers were chosen

**Hotels: 3-star average.** Skyscanner's city pages give an average nightly price for 3-star hotels in each city. No site publishes 2-star averages for these cities, so the 3-star average is the "3 stars or less" figure; 2-star rooms would be cheaper. Prices were in GBP and converted at 1 GBP = 1.3212 USD (x-rates, 2026-11-15). They are not June-specific, and June is high season.

**Flights: economy.** KAYAK route pages give the current average one-way economy fare and how far below the route's typical average it is. The "typical" average is used here, computed as current / (1 - percent below). For example, Dublin to Paris: $55 is 40% below typical, so typical = $92. Rome to Amsterdam uses the Amsterdam to Rome page.

**Trains: standard (2nd) class.** Trainline's advance-purchase Standard Class fares, converted from GBP. These are "from" prices, which fits your assumption of booking in November for June. Dublin train routes (which include a ferry) aren't on Trainline, so they keep Rome2Rio's range midpoint with class unspecified; they are never the cheapest option anyway.

**Buses: single class.** Long-distance buses have one class, so these keep the midpoint of Rome2Rio's price range.

**Missing modes.** Dublin to Amsterdam and Dublin to Paris have no bus option, so those rows are left out (the CSP should treat them as unavailable).

## Sanity check

A brute-force search over every valid itinerary, using the trip rules (Dublin nights 1-2, Rome nights 9-10, Amsterdam night 13, Paris most nights, each city in one block), found 18 valid itineraries, and **all 18 fit the $4,000 budget**. The cheapest costs **$3,096 for two**: Dublin 2 nights, Paris 6, Rome 2, Prague 2, Amsterdam 1. Travel is flight Dublin to Paris, train Paris to Rome (about 14.5 hours), flight Rome to Prague, and train Prague to Amsterdam.

## Sources

- Hotels: Skyscanner city hotel pages, linked per row in `hotels_june.csv`
- Flights: KAYAK flight-route pages; trains: Trainline route pages; buses: Rome2Rio route pages, each linked per row in `fares.csv`
- Exchange rate: [x-rates.com USD table](https://www.x-rates.com/table/?from=USD)
