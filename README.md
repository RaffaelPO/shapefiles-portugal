# 🗺️ Mapping Portugal - Geospatial Data with R 🗺️

**This repository provides standardized geospatial files for Portugal's 3.092 parishes and 308 municipalities and was designed to bridge the gap between raw data and geographic visualization**. 


These files provide a reliable baseline for **mapping administrative trends in [RStudio](https://posit.co/download/rstudio-desktop/)**. They enable you to visualize how variables—including census results, election returns, and socioeconomic indicators—translate into geographic insights."

### Project Context

This repository was developed during my work with the **[PÚBLICO Data Unit](https://www.publico.pt/dados)** to solve a recurring problem: the lack of accessible, ready-to-use shapefiles for Portuguese administrative divisions.

Although the files are based on the **2014 CAOP (Official Administrative Map of Portugal)** standards, it remains a structural reference for longitudinal studies and mapping trends.

 ===========================================================================

## Usage

Once you have cloned this repository, you can import the shapefiles (available for both municipalities and parishes) into R for geospatial analysis and visualization. 

### 1. Environment Setup

To handle spatial data, we rely on the `sf` package. For data manipulation and visualization, we use the `tidyverse`. 

The following block ensures these dependencies are installed and present.

```
# Installing packages

install.packages("tidyverse")
install.packages("sf")

# Loading packages

library(tidyverse)
library(sf)

```
### 2. Importing the shapefiles

After loading the libraries, import the shapefiles using the `st_read()` function. 

To ensure your code is reproducible, it's recommended to use relative paths based on your project’s root directory.

```
# Importing the parish (freguesia) shapefiles

map_parishes_ <- st_read("~/shapefiles-portugal/maps/freguesias-files/freguesias_pt.shp")  

# For municipalities, use:
map_municipalities <- st_read("~/shapefiles-portugal/maps/municipios-files/municipios_pt.shp")

```

### 3. Visualizing the maps 

The quickest way to verify your data is to plot in R is by using `ggplot2`. The `geom_sf()` function is designed to handle "Simple Features" objects automatically, maintaining the correct aspect ratio of the map.

```
# Generate a basic plot of all 3,092 parishes

ggplot(data = map_parishes) +
  geom_sf() +
  labs(
    title = "Map of portuguese parishes",
    caption = "Source: CAOP 2014",
  )
```

<p align="center">
  <img src="https://github.com/RaffaelPO/shapefiles-portugal/blob/main/maps/freguesias-files/000012.jpg" />
</p>

===========================================================================


## Data Dictionary & Provenance

The primary source of these shapefiles is the **Carta Administrativa Oficial de Portugal (CAOP)- 2014**, from [Direcção-Geral do Território](https://www.dgterritorio.gov.pt/). While the original 2014 distribution is no longer hosted at its initial URL, the shapefiles remain a baseline for  longitudinal spatial analysis in Portugal.

The Direcção-Geral do Território has a section dedicated to [open data](https://www.dgterritorio.gov.pt/dados-abertos), where you can consult other databases.  

### Variable Definitions

| Header | Description | Data Type |
|---|---|---|
| `dicofre` or `dico` | The unique number assigned to an individual parish or municipality. | number |
| `freguesia` | The name of the corresponding parish. | character |
| `municipio` | The name of the corresponding municipality and, typically, it's a set of parishes. | character |
| `distrito` | Equivalent to the states, because it's a set of municipalities. | character |
| `nuts_i` | NUTS is the acronym for "Nomenclature of Territorial Units for Statistics", a hierarchical system for dividing up the territory into regions. `nuts_i` divides Portugal in 3 groups: Continente, Região Autónoma dos Açores, Região Autónoma da Madeira. | character |
| `nuts_ii` | Divides Portugal in 7 groups: Norte, Centro, Área Metropolitana de Lisboa, Alentejo, Algarve, Região Autónoma dos Açores, Região Autónoma da Madeira. | character |
| `nuts_iii` | Divides Portugal in 25 groups: Alto Minho, Cávado, Ave, Área Metropolitana do Porto, Alto Tâmega, Tâmega e Sousa, Douro, Terras de Trás-os-Montes, Oeste, Região de Aveiro, Região de Coimbra, Região de Leiria, Viseu Dão Lafões, Beira Baixa, Médio Tejo, Beiras e Serra da Estrela, Área Metropolitana de Lisboa, Alentejo Litoral, Baixo Alentejo, Lezíria do Tejo, Alto Alentejo, Alentejo Central, Algarve, Região Autónoma dos Açores, Região Autónoma da Madeira.	| character |
| `nuts1_id` | The corresponding number to identify the groups of `nuts_i` .| number |
| `nuts2_id` | The corresponding number to identify the groups of `nuts_ii` .| number |
| `nuts3_id` | The corresponding number to identify the groups of `nuts_iii` .| number |
| `geometry` | These are the primitive geometric shapes like points, lines, and polygons. These shapes, together with data attributes that are linked to each shape, create the representation of the geographic data. |  |
