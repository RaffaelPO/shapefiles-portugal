# Shapefiles Portugal 🗺️
 "Shapefiles Portugal" is the repository of PÚBLICO Data Unit containing the geospatial data files of the 3092 parishes (freguesias) and 308 municipalities (municípios) of Portugal.
 
 ===========================================================================

## Usage
After cloning this repository, the shapefile (.shp) - of municipalities or parishes - can be loaded into R Studio for geospatial analysis: 

```
# Install and load the necessary packages from CRAN: 

install.packages("tidyverse")
install.packages("sf")
library(tidyverse)
library(sf)

# Load the shapefiles from your file location:

map1 <- st_read("~/shapefiles-portugal/maps/freguesias-files/freguesias_pt.shp")  
# We're using parishes (freguesias) as an example

# Visualizing the map:

ggplot(map1) + geom_sf() 


```

<p align="center">
  <img src="https://github.com/publico-data/shapefiles-portugal/blob/main/maps/freguesias-files/000012.jpg" />
</p>

===========================================================================


## Explanation

These files come from an open database from 2014 which is no longer available to consulte. The source is "Carta Administrativa Oficial de Portugal (CAOP)- 2014" from [Direcção-Geral do Território](https://www.dgterritorio.gov.pt/). The Direcção-Geral do Território has a section dedicated to [open data](https://www.dgterritorio.gov.pt/dados-abertos) where you can consult other databases.  

Based on our current files, we explain in the following table what each variable means:

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
