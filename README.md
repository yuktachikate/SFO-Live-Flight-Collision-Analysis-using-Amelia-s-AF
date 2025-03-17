# SFO Live Flight Collision Analysis
This project demonstrates a high-level analysis of live flight data in the San Francisco International Airport (SFO) airspace by identifying potential collision risks among aircraft. The analysis is inspired by the techniques discussed in Amelia: A Large Model and Dataset for Airport Surface Movement Forecasting and similar ideas presented in the AIAA paper (DOI: 10.2514/6.2024-4251).

# Table of Contents

Introduction
Features
Data Source
Project Structure
Requirements
Installation
Usage
Analysis and Visualization
Limitations and Future Work
References


# Introduction
This project uses live ADS-B flight data from the OpenSky Network to analyze the positions of aircraft in the SFO airspace. It then computes pairwise distances using the Haversine formula and flags flights that are within a specified threshold distance (e.g., 1 km) as potential collision risks. The aim is to visualize and quantify the collision risk percentage among flights, using both static charts (histograms, scatter plots, bar charts) and interactive maps.

The project takes inspiration from the work presented in the AIAA paper and Amelia's airport surface movement forecasting framework to highlight the importance of data-driven analysis in aviation safety and operations.

# Features
Live Data Acquisition:
Retrieve real-time aircraft state vectors from the OpenSky Network API within a defined SFO bounding box.

Collision Analysis:
Compute pairwise distances between flights and flag those under a threshold (1 km) as potential collisions.

# Visualization:
# Static Charts:
Histogram of pairwise distances (with collision threshold).
Scatter plot of flight positions (red for potential collisions, blue for safe).
Bar chart showing the percentage of flights flagged as potential collision risks.

# Interactive Map:
Display live flight markers on a cropped Folium map of SFO’s airspace.

# Extensibility:
The project design is modular, allowing you to refine filtering criteria, adjust thresholds, or extend the analysis with additional parameters (e.g., flight heading, velocity, altitude differences).

# Data Source
Live aircraft data is sourced from the OpenSky Network API. The API returns real-time ADS-B data (state vectors) such as callsign, longitude, latitude, altitude, and vertical rate.

# Note:
The OpenSky public API has rate limits and sometimes limited data availability. For more detailed analysis or higher frequency data, consider subscribing to a commercial feed.

# Project Structure
The project is implemented as a single notebook (or set of cells) in Google Colab. The main components include:

# Data Acquisition:
Fetches live flight data from OpenSky.
# Collision Analysis:
Computes pairwise distances using the Haversine formula and flags potential collision risks.
# Visualization:
Generates static charts using Matplotlib and interactive maps using Folium and ipyleaflet.
# High-Level Analysis:
Displays the percentage of flights with potential collision risks and overlays flight markers on SFO’s map.
# Requirements:
Python 3.x
Google Colab (recommended for interactive map support)

# Required Python packages:
requests
numpy
matplotlib
folium
ipyleaflet
nest_asyncio
ipywidgets

# Installation
In a Google Colab notebook, install the necessary packages by running:

python
Copy
!pip install requests numpy matplotlib folium ipyleaflet nest_asyncio ipywidgets
Usage

# Launch the Notebook:
Open the notebook in Google Colab.

# Run Cells Sequentially:
The notebook is structured in cells. Run cells to:

Fetch live flight data for SFO.
Analyze potential collision risks.
Display static charts (histogram, scatter plot, bar chart).
Render an interactive map with flight markers.

# Adjust Parameters:
Modify the bounding box coordinates if necessary.
Change the collision threshold in the code.
Update filtering criteria or add new analysis (e.g., incorporating altitude differences).
Analysis and Visualization
The collision analysis consists of the following steps:

# Data Extraction:
Retrieve up to 15 live flight markers from the OpenSky API in the SFO area.

# Pairwise Distance Computation:
Use the Haversine formula to compute distances between every pair of flights.

# Collision Flagging:
Flag flights as potential collisions if they are within 1 km of another flight.

# Visualization:
1. A histogram shows the distribution of pairwise distances, with a red dashed line indicating the collision threshold.
2. A scatter plot marks flights with potential collisions in red and safe flights in blue.
3. A bar chart summarizes the number of flights flagged as potential collisions versus safe flights.
4. An interactive Folium map displays live flight markers, with red markers indicating potential collision risks.
   
# Limitations and Future Work
# Simplified Analysis:
This project only considers horizontal distances. For more robust collision risk prediction, consider incorporating flight headings, speeds, and altitude differences.

# Data Frequency:
The OpenSky API may not update frequently enough for real-time dynamic analysis. For high-resolution tracking, consider dedicated ADS-B data feeds.

# Extending the Model:
Future improvements could include:
Using a dynamic trajectory prediction model (inspired by the Amelia-TF model).
Incorporating additional contextual data such as runway layout, taxiway maps, and weather conditions.
Enhancing visualization with real-time updates using ipyleaflet in a local Jupyter Notebook environment.

# References
Amelia: A Large Model and Dataset for Airport Surface Movement Forecasting
OpenSky Network API: https://opensky-network.org
