# Identifying the Impacts of Extreme Weather: Houston, TX 2021 Blackouts

## Purpose
The analysis completed in this repository is intended investigate how many homes in Houston lost power during the February 2021 Texas winter storms, which were a series of three severe events (February 10–11, 13–17, and 15–20) that caused a statewide power crisis. By comparing night light intensity in the Houston metropolitan area before and during the storms, this analysis estimates the number of homes that experienced blackouts and maps where they are located.

## Repository Overview
- `houston_blackout.qmd`: Quarto document containing all code, maps, and written interpretation.
- `houston_blackout.pdf`: Rendered version of the Quarto document.
- `data/`: All data used in the analysis. This folder is listed in .gitignore.
  
```{r}
houston_power_crisis
│   README.md
│   houston_blackout.pdf
│   houston_blackout.qmd
├── .quarto
     └───typst
└───data
     └───gis_osm_buildings_a_free_1.gpkg
     └───gis_osm_roads_free_1.gpkg
     └───VNP46A1
         └───VIIRS data files
```

## Data Access
**Night Lights**

NASA's Worldview was used to explore the data. 2021-02-07 and 2021-02-16 provide two clear, contrasting images to visualize the extent of the power outage in Texas with no cloud cover. 

Visible Infrared Imaging Radiometer Suite (VIIRS) data is distributed through NASA's [Level-1 and Atmospheric Archive & Distribution System Distributed Active Archive Center (LAADS DAAC)](https://ladsweb.modaps.eosdis.nasa.gov/).

The following files were downloaded and are stored in the `VNP46A1` folder:

* `VNP46A1.A2021038.h08v05.001.2021039064328.tif`: tile h08v05, collected on 2021-02-07
* `VNP46A1.A2021038.h08v06.001.2021039064329.tif`: tile h08v06, collected on 2021-02-07
* `VNP46A1.A2021047.h08v05.001.2021048091106.tif`: tile h08v05, collected on 2021-02-16
* `VNP46A1.A2021047.h08v06.001.2021048091105.tif`: tile h08v06, collected on 2021-02-16


**Roads**

Highways typically account for a large portion of the night lights observable from space. To minimize falsely identifying areas with reduced traffic as areas without power, we will ignore areas near highways (within 200m).

[OpenStreetMap (OSM)](https://planet.openstreetmap.org/) creates publicly available geographic data of the world. We used [Geofabrik’s download sites](https://download.geofabrik.de/) to retrieve a shapefile of all highways in Texas and prepared a Geopackage (.gpkg file) containing just the subset of roads that intersect the Houston metropolitan area. 

* `gis_osm_roads_free_1.gpkg`



**Houses**

OpenStreetMap also contains building data. Once again, we downloaded from Geofabrick and prepared a GeoPackage containing only houses in the Houston metropolitan area.

* `gis_osm_buildings_a_free_1.gpkg`

## Author
Sarah A. Hinkley: [GitHub Profile](https://github.com/sarahhinkley)

## References
NASA LAADS DAAC. 2021. “VIIRS/NPP Daily Gridded Day Night Band 15 Arc-Second Linear Lat Lon Grid Night.” NASA Level-1; Atmosphere Archive & Distribution System Distributed Active Archive Center. https://ladsweb.modaps.eosdis.nasa.gov/missions-and-measurements/products/VNP46A1/.

OpenStreetMap Contributors. 2021. “OpenStreetMap Data Extracts.” Geofabrik GmbH. https://download.geofabrik.de/.
