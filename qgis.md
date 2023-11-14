---
layout: page
title: Introduction to QGIS
permalink: /intro/qgis
parent: Introduction to GIS
nav_order: 1
---

On this page:

[Introduction to QGIS](#introduction-to-qgis)<br/>
[Panels and Toolbars](#panels-and-toolbars)<br/>
[Creating/Saving a projec](#creatingsaving-a-project)<br/>
[Adding vector data](#adding-vector-data)<br/>
[About layers](#about-layers)<br/>
[Vector file types](#vector-file-types)<br/>
[Styling vector layers](#styling-vector-layers)<br/>
[Attribute table](#attribute-table)<br/>
[Identify features tool](#identify-features-tool)<br/>
[Adding raster data](#adding-raster-data)<br/>
[Raster file types](#raster-file-types)<br/>
[Styling raster layers](#styling-raster-layers)<br/>
[Area of interest](#area-of-interest)<br/>
[Copying styles](#copying-styles)<br/>
[Labels](#adding-labels)

# Introduction to QGIS

QGIS is one of many Geographic Information Systems (GIS) applications. It is an opensource software that is free to use and has several plugins to improve functionality.

* Launch the QGIS application by opening **QGIS Desktop 3.28.xx** from the Windows Start Menu.

The main interface will be similar to the one below, with the menu bar, toolbars and panels. The panels and toolbars can be dragged around the interface or docked to the sides.

![QGIS main interface]({{site.url}}/assets/images/qgis_main.png)
<!-- ![QGIS main interface](D:\OneDrive - The University of the West Indies\Agri-geo-informatics\GIS\geo-info\assets\images\qgis_main.png) -->

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

* On the menu bar, go to ```Project --> Save``` or use the save icon on the ```Project Toolbar```.
* Navigate to a preferred folder and create a new folder called ```Dominica-training```.
* Save the project as ```dominica.qgz```.

## Adding vector data

* Download the following file to the project folder:

[Dominica administrative boundaries]({{site.url}}/assets/files/boundaries.zip) - country outline and parish boundaries.

* Drag the file into the Layers Panel.
* Click ```Add Layers``` in the popup window.

* Alternatively, you can go to ```Layer --> Add Layer --> Vector Layer```. You can also use the ```Manage Layers Toolbar```.
* Under source, press the overflow icon (3 dots) to browse for the vector file.
* Click ```Add```, click ```Close```.

The files will appear in the Layers Panel.

### About layers

![layers]({{site.url}}/assets/images/layers.jpg)<br/>
<!-- ![layers](D:\OneDrive - The University of the West Indies\Agri-geo-informatics\GIS\geo-info\assets\images\layers.jpg)<br/> -->
In a GIS application, data are managed in layers stacked on each other, e.g. farmlands over the admin boundaries stacked on top of a basemap. The order of the layers will influence their visibility. The layers can be reordered by dragging them up and down in the ```Layers Panel```.

* Reorder the layers so that ```parishes.shp``` is above ```coastline.shp```.

The zip file contain several files. Notice that the ```Layers Panel``` displays the shape files (.shp) as a group.
* Expand or collapse the group by clicking the arrow on the left.
* Use the ```Manage Map Themes``` icon (eyeball) on the Layers Panel to ```Hide All Layers```.
* We will select the shapefiles. Check the boxes next to ```parishes.shp``` and ```coastline.shp``` layers.
* If the layer is out of focus in the view pane, right-click the layer and choose ```Zoom to Layer(s)```.
* You can remove layers from the ```Layers Panel``` by selecting them and clicking the ```Remove Layers/Group``` icon. (Use CTRL + click to select multiple layers).

### Vector file types
Vector files come in several formats including the popular Shapefile (.shp, .dbf, .shx), .geojson, Google KML (.kml, .kmz), etc.

### Styling vector layers

There are several styles that can be applied to layers to enhance visibility. We will change the symbology of each layer to our preference.

* Double-click the ```coastline.shp``` layer to launch the layer properties window. Alternatively, right-click the layer and choose ```Properties```.
* Select the ```Symbology``` tab.
* Change the ```Simple Fill``` to ```Outline: Simple Line``` and change the color.
* Click ```Apply```. When done click ```OK```.
* Save the project.

### Attribute table

The attribute table displays the data in the vector file.

* To open the attribute table, right-click the ```parishes.shp``` layer and select ```Open Attribute Table```.

Notice that each feature is identified by a unique ID which is essential for any data storage application. From here you can see information for each boundary, including the parish names.

* Click the right-most icon to dock the attribute table.

### Identify features tool

![identify features]({{site.url}}/assets/images/identify-features-tool.png)
<!-- ![identify features](D:\OneDrive - The University of the West Indies\Agri-geo-informatics\GIS\geo-info\assets\images\identify-features-tool.png) -->

The ```Identify Features Tool``` on the ```Attribute Toolbar``` will show data in the ```Identify Results``` panel for any selected feature.

* Click the ```Identify Features Tool``` to enable it.
* Click any parish to see the data in the ```Identify Results``` panel.

## Adding raster data

* Download the following file to your project folder:

[Sentinel moisture index image]({{sitye.url}}/assets/files/moisture-index.tiff)
<!-- [Sentinel moisture index image](D:\OneDrive - The University of the West Indies\Agri-geo-informatics\GIS\geo-info\assets\images\moisture-index.tiff) -->

* Use the ```Browser Panel``` to locate the downloaded file ```moisture-index.tiff```.
* Drag the file from the ```Browser Panel``` to the ```Layers Panel```. Alternatively, you can go to ```Layer --> Add Layer --> Raster Layer```. You can also use the ```Manage Layers Toolbar```.
* Arrange the layers so that ```moisture-index``` is at the bottom.
* Save the project.

![QGIS raster loaded]({{site.url}}/assets/images/qgis-raster.png)
<!-- ![QGIS raster loaded](D:\OneDrive - The University of the West Indies\Agri-geo-informatics\GIS\geo-info\assets\images\qgis-raster.png) -->

### Raster file types

The most common file type used for raster data is the GeoTIFF (.TIFF). This is the general format for satellite imagery.

### Styling raster layers

Notice that raster layer is made up of 3 bands: red, green and blue. Rasters can be composed of 1 or more bands containing different data. These bands can be styled to produce the required visualization.

* Double-click the layer to open its properties and switch to the ```Symbology``` tab.
* Notice the ```Render type``` is set to ```Multiband color``` displaying the red, green and blue bands in order. Change the ```Render type``` to ```Singleband pseudocolor```. 
* At ```Band```, select ```Band 3 (Blue)```.
* At ```Interpolation```, select ```Discrete```.
* Use a blue ```Color ramp```.
* Click ```Apply``` and ```OK``` when finished.
* Select the ```moisture-index``` layer.
* Use the ```Identify Features``` tool to click on the map and view the results in the ```Identify Results``` panel.

![raster symbology]({{site.url}}/assets/images/raster-symbology.png)

### Area of interest

The extent of the raster is larger than the island. We do not need the ocean area in the image so we'll clip it to coasts of Dominica. For this process we'll use the raster image and clip it using the ```coastline.shp``` file.

* From the menu bar, select ```Raster --> Extraction --> Clip Raster by Mask Layer```.
* Select the ```moisture-index``` as the ```Input Layer```.
* Select the ```coastline.shp``` file as the ```Mask Layer```.
* Set the nodata value to 0.
* Select ```Match the extent of the clipped raster...``` and ```Keep resolution of the input raster```.
* By default, the output is saved to a temporary file. Saved the clipped mask as ```dominica-moisture-index.tif``` to your project folder.
* Click ```Run``` to generate the output raster, then ```Close```.

### Copying styles

You will notice that the new raster has lost the pseudocolor styling from the original and has defaulted to the multiband color. To fix this, copy the style from the original layer.

* Right-click the ```moisture-index``` layer and select ```Styles --> Copy Style```.
* Right-click the clipped raster layer and select ```Styles --> Paste Style```.
* Be sure the disable the original layer.
* Re-order the layers to show the details you want.
* Save your project.

<!-- ![raster extraction]({{site.url}}/assets/images/raster-extraction.png) -->

<!-- ![clipped raster]({{site.url}}/assets/images/clipped-raster.png) -->

### Adding labels
Labels can be added using the content of the vector layer's attribute table. We will add the parish names which were listed under ```NAME_1``` in the attribute table.

* Double-click the ```parishes.shp``` vector layer to open its properties.
* Go to the ```Labels``` tab.
* Select ```Single Labels``` from the dropdown.
* For ```Value```, select ```NAME_1```.
* Click ```Apply```.

The labels can be styled using the various options available such as ```Text```, ```Formatting```, ```Placement```, etc.
* Click ```Apply to see the changes``` and ```OK``` when done.
* In the main window, the labels can be activated by right-clicking the layer and selecting ```Show labels```.

Next, we will create a map layout for printing.