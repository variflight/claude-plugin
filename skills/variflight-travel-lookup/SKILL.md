---
name: variflight-travel-lookup
description: Look up flights and air travel conditions with the VariFlight MCP tools. Use when the user asks about a flight's status or delay, flights between two places, connecting flights, airfare, flight comfort, airport weather, or where an aircraft is right now.
---

# VariFlight flight lookup

The plugin connects the **variflight-aviation** MCP server.

## Pick the tool

| User asks about | Tool |
|---|---|
| Status of a known flight (times, delay, gate, aircraft) | `searchFlightsByNumber` |
| Direct flights between two places on a date | `searchFlightsByDepArr` |
| Connecting flights when there is no good direct flight | `getFlightTransferInfo` |
| A short recommended itinerary with lowest fares | `searchFlightItineraries` |
| Fares between two cities, as raw data | `getFlightPriceByCities` |
| Comfort, punctuality, cabin, meals for a known flight | `flightHappinessIndex` |
| Airport weather for today and the next two days | `getFutureWeatherByAirport` |
| Where an aircraft is now, by registration (e.g. B2021) | `getRealtimeLocationByAnum` |

## Inputs

- **Dates** are always `YYYY-MM-DD`. When the user says "today", "tomorrow" or gives only a month and day, call `getTodayDate` first and work out the full date from it. Never guess the year.
- **Flight numbers** include the airline code, such as `MU5100` or `CA1501`.
- **Airport codes** are IATA three-letter codes (`PEK`, `PKX`, `SHA`, `PVG`). **City codes** are also three letters (`BJS` for Beijing, `SHA` for Shanghai). For `searchFlightsByDepArr`, use `depcity`/`arrcity` when the user names a city with several airports, and `dep`/`arr` when they name an airport.

## Cost

Every tool except `getTodayDate` uses credits on the user's VariFlight account. Make the one call the question needs, reuse earlier results in the conversation, and don't loop over dates or cities unless the user asks for that comparison.

## Errors

- `401` or an "Invalid API key" message: the VariFlight connection is not signed in or has expired. Ask the user to reconnect VariFlight.
- Insufficient balance: tell the user to top up at https://ai.variflight.com.
- `暂无数据` (no data): the source has no record for that query. Check the date and codes once, then tell the user plainly that no data was found.
