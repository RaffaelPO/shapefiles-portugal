# Shapefiles Portugal
 "Shapefiles Portugal" is the library containing the geospatial data files of the 3092 parishes (freguesias) and 308 municipalities (municípios) of Portugal.
 
 =============================================================================

## Usage
After cloning the library, the shapefile (.shp) - of municipalities or parishes - can be loaded into R Studio for geospatial analysis: 

```
# Install and load the necessary packages from CRAN: 

install.packages("tidyverse")
install.packages("sf")
library(tidyverse)
library(sf)

# Load the shapefiles from your file location:

map1 <- st_read("~/shapefiles-portugal/maps/freguesias/._rui_freguesias.shp")  
# We're using parishes (freguesias) as an example

# Visualizing the map:

ggplot(map1) + geom_sf() 


```

<p align="center">
  <img src="https://github.com/publico-data/shapefiles-portugal/blob/main/maps/freguesias/000012.jpg" />
</p>

=============================================================================
