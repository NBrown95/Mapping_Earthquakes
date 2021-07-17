# Earthquakes Analysis

## Overview of Project

For this project, we are mapping all earthquakes on Earth that occurred in the past seven days using Leaflet.js. To do this, we first create tile layers using the mapbox URL which is copied from the Leaflet documentation page. We created three tile layers so the map would contain a street view, satellite view, and a dark mode. We do this by editing the URL with each version we wish to apply.

Then, we create the map using L.map(). We set the center of the map at the coordinates [40.7, -94.5] with a zoom of 3 so we can see the entire map. The default layer for the map is the street view. We then create a baseMaps variable that holds all the three tile layers to the map. We then create three layer groups using “new L.LayerGroup()”. We add an overlays variable to hold an object which contains references to all three layer groups we just created. Finally, we add a control layer that includes our baseMaps and overlays objects and add them to the map.

We retrieve the earthquake data from the following url: https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/all_week.geojson. Then, we use d3.json().then() to access and retrieve the data. We add three functions inside this function to style the map with a color based on each earthquake’s magnitude and a radius of the circleMarker also depending on the magnitude of each earthquake. 

We then use L.geoJson(data, ) to create a geoJSON layer with the retrieved data. Inside this function, we turn each feature in the data into a circleMarker on the map. We set the style of these markers based on the earlier functions we defined. We then create a popup for each circleMarker to display the magnitude and location of the earthquakes. To do this, we must use onEachFeature and define a function that displays the magnitude and location and then bind that to the popup with .bindPopup().

We add this geoJSON layer to the allEarthquakes layer group and then we add that to the map. We repeat this process for the tectonic plate data which is retrieved from: https://raw.githubusercontent.com/fraxen/tectonicplates/master/GeoJSON/PB2002_boundaries.json. We also include major earthquake data from: https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/4.5_week.geojson which includes information about all earthquakes with a magnitude of over 4.5. 

Finally, we create a legend indicating the colors for certain ranges of magnitudes. We place the legend in the bottom right corner of the map using L.control() and loop through the intervals to generate a label with a colored square for each interval. We add this to the map, and we have our final product!
