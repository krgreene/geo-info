---
layout: page
title: Introduction to GIS
permalink: /intro/
nav_order: 2
has_children: True
has_toc: False
---

# Introduction to GIS

Geographic Information Systems (GIS) refers to the technology used for the effective collection, storage, retrieval, processing and display of geospatial data. These data may include:
* topographic data relating to physical characteristics of the earth, e.g. streams and mountains, roads, etc.
* political data, e.g. administrative boundaries
* land use data, e.g. farm lands and crops, housing, etc.

and several others. Geospatial data have coordinates such as latitude and longitude which allow spatial features to be located on the earth.

The technology includes hardware devices and supporting software applications which are used throughout the data cycle. Satellites, drones, field sensors, GPS devices, mobile phones, computers, spatial databases and GIS applications all fit into GIS. As an example, you may consider using a soil moisture sensor to collect data from a farm and then transfer it automatically over the internet to be stored in a database which would later be analysed by a user, using a GIS desktop application.

## GIS applications
There are several desktop applications, supporting tools and web-based applications. Some well-known applications are:
* QGIS
* ArcGIS
* Google Earth

## GIS data

GIS data fall into two categories:

1. Vector data
1. Raster data

### Vector data

![roseau-vector](/assets/images/roseau-vector.png)<br/>
In the vector model, features on the ground are represented as either points, lines or polygons.

![points, lines, polygons](/assets/images/points-lines-polygons-vector-data-types.png)<br/>Credit:[earthdatascience.org](https://www.earthdatascience.org/courses/earth-analytics/spatial-data-r/intro-vector-data-r/)


### Raster data

![raster](/assets/images/raster.png) ![roseau-raster](/assets/images//roseau-raster.png)<br/>
The raster model uses a grid of cells where each cell represents an attribute of a feature. Think of an image which is made up of cells called pixels. A point can be represented as a pixel while lines and polygons would be sets of adjacent pixels. Scanned maps and satellite images are examples of raster data.