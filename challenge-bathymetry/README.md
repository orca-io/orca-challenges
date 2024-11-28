Challenge - Bathymetry
=====

Marine maps are a core component of the Orca experience, with bathymetry (underwater topography) being a key feature. Orca sources bathymetry data from various hydrographic offices (HOs) such as NOAA[1]. However, the quality of this data varies based on coverage, resolution, and freshness.

The US Army Corps of Engineers (USACE)[2] provides high-resolution, up-to-date bathymetric survey data, including Digital Elevation Models (DEMs) from multibeam sonar surveys. While USACE also provides contour polygons, these are often jagged and not ideal for visualization.


Task
-----

Your task is to build an **end-to-end** solution that processes DEM data from USACE, generates smoothed bathymetric contours, and displays these contours on a vector map.


Details
-----

Your solution should include the following key elements:

1. #### Data Download
   - Retrieve a small subset of **USACE survey data** (e.g., DEM files for a specific region).

2. #### Data Processing
   - Process the **DEM** data to generate **smoothed contour polygons** at reasonable depth intervals (e.g., 0m, 0.5m, 1m, 2m, 5m, 10m).
   - USACE hydro survey data contains DEMs and processed contour polygons. We don’t want their contour polygons as they are jagged in many cases. Come up with a way to produce non-jagged contours from the DEMs.
   - Store the processed bathymetry contours in a **PostGIS database**.

3. #### Vector Tile Serving

   - Serve the bathymetric contours as **Mapbox Vector Tiles (MVT)** directly from the PostGIS database.

4. #### Map Visualization

   - Create a web-based map using **Mapbox GL-JS** or **MapLibre GL-JS**.
   - Add a bathymetry layer styled in shades of blue to represent different depth intervals.
   - Overlay this layer on a default Mapbox basemap.


Notes
-----
- We value **simplicity** and **elegance** as opposed to over-engineering. Focus on **functional**, **efficient** solutions over perfect code quality.
- You are encouraged to **use existing tools and libraries** to focus on solving the core problem efficiently. Document tool choices and rationale in the README.
- The solution should demonstrate **reasonable performance** in generating contours from the DEM data, generating vector tiles from the contour polygons and loading and rendering the map.
- Provide **basic documentation** in the form of a **README file** with clear setup and execution instructions (dependencies, database setup, configs, etc.).
- Include strategies (if applicable) for optimizing processing workflows (e.g., leveraging PostGIS functions, batch processing).


Deliverable
-----
1. **Code Repository**: Preferably a GitHub repository.
2. **Video Demo**: A short video demonstrating how the solution works end-to-end including the final map visualization.


References
-----

- [1] https://www.ncei.noaa.gov/products/bathymetry
- [2] https://www.mvr.usace.army.mil/Missions/Navigation/Hydrographic-Surveys/
