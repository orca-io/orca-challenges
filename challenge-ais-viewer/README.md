Challenge - AIS viewer
=====

>The automatic identification system, or AIS, transmits a ship’s position so that other ships are aware of its position. The International Maritime Organization and other management bodies require large ships, including many commercial fishing vessels, to broadcast their position with AIS in order to avoid collisions. Each year, more than 400,000 AIS devices broadcast vessel location, identity, course and speed information. Ground stations and satellites pick up this information, making vessels trackable even in the most remote areas of the ocean.[1]


Task
-----

Build end to end AIS system that ingests AIS data from a free provider and displays the data in near real-time on a map.


Details
-----

### Backend

1. Ingest AIS data from aisstream.io[2]
2. For simplicity only handle AIS message PositionReport[3]
3. Keep in mind that there could be up to 30k vessels for full world coverage, and most of them relatively fresh (updated within 10 minutes)
4. Use database with a geospatial extension (PostGIS, SpatiaLite, MongoDB…) to store the vessels data
5. Vessels data should persist - backend reboot should keep previously processed data
6. You are free to choose how to expose the data from the database to the frontend, but keep in mind the possible amount of data

### Frontend

1. Use MapLibre GL JS[4] for displaying the map
2. Use markers to show vessels on the map
    - Choose marker icon that can reflect vessel's course e.g. arrow
    - Apply vessel's course to the vessel marker so that the course of the vessel is clear from the direction of the marker
3. Display vessels only when map zoom level is from 12 to 20 to avoid having to display large number of vessels at any given time
4. Displayed vessels should be near real-time - ~10 seconds delay from receiving it on the backend to being added/updated on the map
5. Displayed vessels should be fresh - don’t show vessels that haven’t been updated in the past 2 minutes


Notes
-----

We value simplicity and elegance as opposed to overengineering.

When designing vessels data retrieval API, consider that you only need to retrieve data for a current map view, which given the Frontend point 3 is only a small subset of the full dataset and never the full set. Retrieving the full set every 10 seconds would not be feasible.

The system should support multiple simultaneous map viewers.


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
