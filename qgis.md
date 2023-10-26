---
layout: page
title: Introduction to QGIS
permalink: /intro/qgis
parent: Introduction to GIS
nav_order: 1
---

# Introduction to QGIS

QGIS is one of many Geographic Information Systems (GIS) applications. It is an opensource software that is free to use and has several plugins to improve functionality.

* Launch the QGIS application by opening **QGIS Desktop 3.28.xx** from the Windows Start Menu.

The main interface will be similar to the one below, with the menu bar, toolbars and panels. The panels and toolbars can be dragged around the interface or docked to the sides.

![QGIS main interface](/assets/images/qgis_main.png)

## Panels and Toolbars

Panels and toolbars allow easy access to functions and tools. They can be activated or deactivated from the menu bar or by right-clicking any toolbar. We will add a few useful toolbars. On the menu bar, go to ```View --> Toolbars``` and select the following toolbars:
* Data Source Manager Toolbar
* Digitizing Toolbar
* Manage Layers Toolbar
* Snapping Toolbar

You can go to ```View --> Panels``` or right-click any toolbar to add these panels:
* Browser Panel
* Identify Results Panel
* Layers Panel

## Creating/Saving a project

* On the menu bar, go to ```Project --> Save``` or use the save icon on the Project Toolbar.
* Navigate to a preferred folder and create a new folder called ```Dominica-training```.
* Save the project as ```dominica.qgz```.

## Adding vector data

* Download the following files to the project folder:

[Dominica ADM-0 boundary](/files/geoBoundaries-DMA-ADM0-all.zip) Level 0 Administrative Boundary (country outline)<br/>
[Dominica ADM-1 boundaries](/files/geoBoundaries-DMA-ADM1-all.zip) Level 1 Administrative Boundary (parish boundaries)

* Drag the files into the Layers Panel. Alternatively, you can go to ```Layer --> Add Layer --> Vector Layer```. You can also use the ```Manage Layers Toolbar```.

![add vector file](/assets/images/qgis-add-vector.png)<br/>
* Under source, press the overflow icon (3 dots) to browse for the vector file.
* Click ```Add```. Browse for the second file. Click ```Add```, click ```Close```.

The files will appear in the Layers Panel.

![layers panel](/assets/images/layers-panel.png)

### About layers

![layers](/assets/images/layers.jpg)<br/>
In a GIS application, data are managed in layers stacked on each other, e.g. farmlands over the admin boundaries stacked on top of a basemap. The order of the layers will influence their visibility. The layers can be reordered by dragging them up and down in the ```Layers Panel```.

* Reorder the layers so that ADM1 is above ADM0.

The zip files contain several files. 
* Expand each group by clicking the arrow on the left.
* Use the ```Manage Map Themes``` icon (eyeball) on the Layers Panel to ```Hide All Layers```.
* We will select the shapefiles. Check the boxes next to ```ADM1-simplified.shp``` and ```ADM0-simplified.shp``` layers.
* If the layer is out of focus in the view pane, right-click the layer and choose ```Zoom to Layer(s)```.
* Remove the unused layers from the ```Layers Panel``` by selecting them and clicking the ```Remove Layers/Group``` icon. (Use CTRL + click to select multiple layers).

### Vector file types
Vector files come in several formats including the popular Shapefile (.shp, .dbf, .shx), .geojson, Google KML (.kml, .kmz), etc.

### Styling vector layers

There are several styles that can be applied to layers to enhance visibility. We will change the symbology of each layer to our preference.

* Double-click the ```ADM0-simplified.shp``` layer to launch the layer properties window. Alternatively, right-click the layer and choose ```Properties```.
* Select the ```Symbology``` tab.
* Change the ```Simple Fill``` to ```Outline: Simple Line``` and change the color.
* Click ```Apply```. When done click ```OK```.
* Save the project.

### Attribute table

The attribute table displays the data in the vector file.

* To open the attribute table, right-click the ```ADM1-simplified.shp``` layer and select ```Open Attribute Table```.

![attribute table](/assets/images/attribute-table.png)

Notice that each feature is identified by a unique ID which is essential for any data storage application. From here you can see information for each boundary, including the parish names.

* Click the right-most icon to dock the attribute table.

### Identify features tool

![identify features](/assets/images/identify-features-tool.png)

The ```Identify Features Tool``` on the ```Attribute Toolbar``` will show data in the ```Identify Results``` panel for any selected feature.

* Click the ```Identify Features Tool``` to enable it.
* Click any parish to see the data in the ```Identify Results``` panel.

![identify results](/assets/images/identify-results-panel.png)

## Adding raster data

* Download the following file to your project folder:

[Sentinel images zip file](/files/dominica-sentinel.zip)

The dataset contains several processed satellite images showing indices relating to moisture and vegetation health.

* Use the ```Browser Panel``` to locate the downloaded file.
* Drag the file from the ```Browser Panel``` to the ```Layers Panel```. Alternatively, you can go to ```Layer --> Add Layer --> Raster Layer```. You can also use the ```Manage Layers Toolbar```.
* Arrange the layers so that ```dominica-sentinel.zip``` is at the bottom.
* Expand the ```dominica-sentinel``` group and activate the different raster layers to visualize them.
* Save the project.

![QGIS raster loaded](/assets/images/qgis-raster.png)

### Raster file types

The most common file type used for raster data is the GeoTIFF (.TIFF). This is the general format for satellite imagery.

### Styling raster layers

Notice that each raster layer is made up of 3 bands: red, green and blue. Rasters can be composed of 1 or more bands containing different data. These bands can be styled to produce the required visualization.

* Activate the ```Moisture_index.tiff``` layer.
* Double-click the layer to open its properties and switch to the ```Symbology``` tab.
* Notice the ```Render type``` is set to ```Multiband color``` displaying the red, green and blue bands in order. Change the ```Render type``` to ```Singleband pseudocolor```. 
* At ```Band```, select ```Band 3 (Blue)```.
* At ```Interpolation```, select ```Discrete```.
* Use a blue ```Color ramp```.
* Click ```Apply``` and ```OK``` when finished.
* Use the ```Identify Features``` tool to click on the map and view the results in the ```Identify Results``` panel.

![raster symbology](/assets/images/raster-symbology.png)

![raster singleband pseudocolor](/assets/images/raster-pseudocolor.png)

### Area of interest

The extent of the raster is larger than the island. We do not need the ocean area in the image so we'll clip it to coasts of Dominica. For this process we'll use the raster image and clip it using the ```ADM0.shp``` file.

* From the menu bar, select ```Raster --> Extraction --> Clip Raster by Mask Layer```.
* Select the ```Moisture_index.tiff``` as the ```Input Layer```.
* Select the ```ADM0-simplified.shp``` file as the ```Mask Layer```.
* Set the nodata value to 0.
* Select ```Match the extent of the clipped raster...``` and ```Keep resolution of the input raster```.
* By default, the output is saved to a temporary file. Saved the clipped mask as ```dominica_moisture-index.tif``` to your project folder.
* Click ```Run``` to generate the output raster, then ```Close```.

### Copying styles

You will notice that the new raster has lost the pseudocolor styling from the original and has defaulted to the multiband color. To fix this, copy the style from the original layer.

* Right-click the ```Moisture_index.tiff``` layer and select ```Styles --> Copy Style```.
* Right-click the clipped raster layer and select ```Styles --> Paste Style```.
* Be sure the disable the original layer.

![raster extraction](/assets/images/raster-extraction.png)

![clipped raster](/assets/images/clipped-raster.png)

Next, we will create a map layout for printing.