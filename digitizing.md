---
layout: page
title: Digitizing
permalink: /digitizing
nav_order: 3
---

On this page:

* TOC
{:toc}

# Digitizing features and editing attributes

Digitizing is the process of capturing areas of rasters (scanned maps, satellite images, etc.) in vector format. Attributes will need to be added to the captured features to properly describe and identify them.

## Digitizing in Google Earth

Google Earth has both desktop and online versions. For simplicity, we will use the online version.

* In your web browser (Edge/Chrome) go to [earth.google.com](https://earth.google.com){:target="_blank"}
* Drag and zoom the map to Dominica.
* Find an area of interest you wish to capture. Zoom in to this area.
* Click on the ```Add path or polygon``` icon at the top of the page.
* Draw a polygon around the feature/area you wish to digitize by clicking around the feature. To complete the process, double-click when you reach the start point again.
* Click ```Save to project```.
* Save feature to ```Local KML file```. Google's vector file type is KML/KMZ.
* Name the file.
* On the left, under ```Local KML files```, go to the current project and click the option icon (3 dots). Select ```Export as KML file```. This will download the file to your computer.

-----

* Try using placemarks instead of polygons to mark points on the map.
* Download the KML file.

-----

* Open the files in QGIS (drag them to the ```Layers Panel``` or add a vector layer).

## Convert KML/KMZ to Shapefile in QGIS
* Right-click the .kml/.kmz layer in the ```Layers Panel```. Select ```Export --> Save Featuers As...```
* In the pop-up window, select ```Format --> ESRI Shapefile```.
* For ```File name```, browse to save the shapefile.
* Leave ```CRS``` as the default ```EPSG:4326 - WGS 84```.
* Ensure ```Add saved file to map``` is checked.
* Leave all other default settings and click ```OK```.

The new shapefile will show in the ```Layers Panel```.

## Digitizing scanned maps/rasters in QGIS

[Download topographic map]({{site.url}}/assets/files/large-detailed-topographic-map-of-dominica.jpg){:download="topographic_map"}

The Layer will need to be [georeferenced]({{site.url}}/georeferencing) to appear correctly within the country map.

* Load the file into the ```Layers Panel```.
* On the menu bar, go to ```Layer --> Create Layer --> New Shapefile Layer...```.
* Name the file to save the layer to.
* Set the ```Geometry type``` to ```Polygon``` to digitize an area. Point features can be digitized as ```Point``` or ```MultiPoint```. Linear features such as paths and boundaries may be digitized as ```LineString```.
* Notice that the ```Fields List``` already has an integer ```id``` to identify each unique feature. Under ```New Field```, add a new ```string``` field for the name of the area to be digitized.
* Click ```OK``` when you are finished.
* Ensure the ```Digitizing Toolbar``` is active.
* On the map layer, zoom to the area to be digitized.
* Click the ```Toggle Editing``` (pencil) icon.
* Click the ```Add Polygon Feature``` (green) icon.
* Click each corner of the area to draw the polygon. Right click to complete the polygon.
* Enter the feature details when prompted.
* On the ```Digitizing Toolbar```, click ```Save Layer Edits```.


## Updating the Attribute Table in QGIS
You may need to add fields and data to a vector layer's attribute table. You can add and delete fields, edit data and perform various operations, using the attribute table's menu. To add a new field and data:
* ```Right-click``` the layer and select ```Open Attribute Table```.
* Click the ```New field``` icon.
* In the popup dialog box, give the field a name, select an appropriate data type and length. You may also add a comment to describe the field.
* Click ```OK``` when done.
* Enter the desired data into the new field of the attribute table.
* Click the ```Save edits``` icon.