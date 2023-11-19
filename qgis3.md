---
layout: page
title: Converting vector and raster data
permalink: /vector_raster_conversion
nav_order: 4
---

On this page:

* TOC
{:toc}

# Converting vector and raster data

In this section, we will use the ```Processing Toolbox``` to access tools, rather than using the menu bar. Ensure that the ```Processing Toolbox Panel``` is visible.

## Convert vector to raster (rasterize)

Download: [Dominica rainfall vector file]({{site.url}}/assets/files/rainfall.zip)

* Load the vector file.
* In the ```Processing Toolbox``` search field, type ```rasterize```.
* Double-click ```Rasterize (vector to raster)```.
* Select ```rainfall``` as the input layer.
* Select ```RAINFALL``` as the ```Field to use for a burn-in value```. This will ensure that the rainfall values are added to the output.
* Select ```Pixels``` as the ```Output raster size units```.
* Enter ```100``` for the ```Width``` and ```Height```. A higher number produces a higher resolution and better visualization.
* Set ```Output extent --> Calculate from Layer --> coastline.shp```.
* Set the new file name under ```Rasterized```.
* Click ```Run``` to generate the raster layer.
* The new raster will be visible in the ```Layers Panel```.
* Click ```Close``` when finished.

## Convert raster to vector (vectorize)

Convert the new rainfall raster back to vector format.

* In the ```Processing Toolbox``` search field, type ```polygonize```.
* Double-click ```Polygonize (raster to vector)```.
* Select the rainfall raster as the input layer.
* The rainfall values used in the vector conversion above will be added to the new vector. Type ```rainfall``` in ```Name of the field to create```. 
* Set the new file name under ```Vectorized```.
* Click ```Run``` to generate the vector layer.
* The new vector will be visible in the ```Layers Panel```.
* Click ```Close``` when finished.