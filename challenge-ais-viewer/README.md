Challenge - AIS viewer
=====

>The automatic identification system, or AIS, transmits a ship’s position so that other ships are aware of its position. The International Maritime Organization and other management bodies require large ships, including many commercial fishing vessels, to broadcast their position with AIS in order to avoid collisions. Each year, more than 400,000 AIS devices broadcast vessel location, identity, course, and speed information. Ground stations and satellites pick up this information, making vessels trackable even in the most remote areas of the ocean.[1]


Task
-----

Build an end-to-end AIS system that ingests AIS data from a free provider and displays the data in near real-time on a map.


Details
-----

### Backend

1. Ingest AIS data from aisstream.io[2]
2. For simplicity only handle AIS message PositionReport[3]
3. Keep in mind that there could be up to 30k vessels for full world coverage, and most of them are relatively fresh (updated within 10 minutes)
4. Use a database with a geospatial extension (PostGIS, SpatiaLite, MongoDB…) to store the vessel data
5. Vessel data should persist and fresh data should instantly be available for the front end. Backend reboot should keep previously processed data.
6. You are free to choose how to expose the data from the database to the front end, but keep in mind the possible amount of data

### Frontend

1. Use MapLibre GL JS[4] for displaying the map
2. Show vessels on the map
    - Show the vessel's course so that the course of the vessel is clearly visible via the direction of the marker
3. Display vessels only when map zoom level 12 or more to set a boundary for client-side performance
4. Displayed vessels should be near real-time - ~10 seconds delay from receiving it on the backend to being added/updated on the map
5. Displayed vessels should be fresh - don’t show vessels that haven’t been updated in the past 2 minutes


Notes
-----

We value simplicity and elegance as opposed to over-engineering.

Consider that the client side only needs to retrieve data for a current map view, which given the Frontend point 3 is only a small subset of the full dataset. Retrieving the full set every 10 seconds would not be feasible.

The system should support a significant amount of simultaneous map viewers.


Deliverable
-----

1. Video demonstrating the system
2. Source code.


References
-----

- [1] https://globalfishingwatch.org/faqs/what-is-ais
- [2] https://aisstream.io/documentation
- [3] https://aisstream.io/documentation#PositionReport
- [4] https://maplibre.org/maplibre-gl-js/docs/
