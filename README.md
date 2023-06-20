# Analysing-UFO-Sightings-Data

In this guide, we'll walk through a step-by-step analysis of a UFO sightings dataset. We'll cover data loading, cleaning, analysis, and visualization. This guide is designed for beginners, so we'll explain each step in detail.

## Step 1: Load the Dataset

The first step in any data analysis project is to load the dataset. We'll use the `pandas` library in Python, which provides powerful data manipulation and analysis capabilities.

```python
import pandas as pd

# Load the dataset
ufo_df = pd.read_csv('ufo_fullset.csv')

# Display the first few rows of the dataset
ufo_df.head()
```

## Step 2: Clean the Dataset

Data cleaning is an essential step in the data analysis process. It involves handling missing values and removing unnecessary columns. In this case, we'll remove the 'firstName' and 'lastName' columns.

```python
# Drop the 'firstName' and 'lastName' columns
ufo_df = ufo_df.drop(['firstName', 'lastName'], axis=1)
```

## Step 3: Analyse the Data

Next, we'll analyze the data to find the locations with the highest frequency of UFO sightings. This involves grouping the data by location and counting the number of sightings at each location.

```python
# Group by location (latitude and longitude) and count the number of sightings
sightings_by_location = ufo_df.groupby(['latitude', 'longitude']).size()

# Display the locations with the highest frequency of UFO sightings
sightings_by_location.sort_values(ascending=False).head(10)
```

## Step 4: Visualise the Data

Data visualization is a powerful tool for understanding the patterns and trends in data. We'll use the `folium` library to create an interactive map of the top 10 locations for UFO sightings.

```python
import folium

# Create a world map
world_map = folium.Map(location=[0, 0], zoom_start=2)

# Top 10 locations with the highest frequency of UFO sightings
locations = [
    [47.6064, -122.331],
    [40.7142, -74.0064],
    [32.7153, -117.156],
    [33.4483, -112.073],
    [34.0522, -118.243],
    [29.7631, -95.3631],
    [36.175, -115.136],
    [41.5733, -87.7844],
    [37.775, -122.418],
    [25.7739, -80.1939]
]

# Add markers to the map
for location in locations:
    folium.Marker(location).add_to(world_map)

# Display the map
world_map
```

And that's it! You've just completed a basic analysis of a UFO sightings dataset. You've learned how to load and clean data, perform simple data analysis, and create an interactive map visualization. Happy analyzing!
