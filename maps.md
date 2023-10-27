---
layout: page
title: Creating maps with QGIS
permalink: /intro/maps
parent: Introduction to GIS
nav_order: 2
---

# Creating maps with QGIS

QGIS can be used to create printable maps with borders, scales, etc.

* From the menu bar, go to ```Project --> New Print Layout```.
* Enter a name for the layout, e.g. ```dominica_moisture_index``` and click ```OK```. A new window will open.
* In the new window, go to the menu bar and click ```Add Item --> Add Map```. Draw a rectangle on the canvas to show the map. If you are not seeing the details you want, return to the main window and adjust the layers to display the required map details. Return to the layout window.
* To add a border, go to the ```Item Properties``` tab on the right and check ```Frame```. Style the frame as desired.
* To add a title or any text, on the menu bar click ```Add Item --> Add Label```. Draw the label text box. With the text box selected, go to ```Item Properties ---> Main Properties``` and type the desired text. The text can be styled under ```Appearance```.
* Add a scale bar.
* Add a north arrow.
* Add a legend to the map and style it as desired (edit, delete, spacing, etc.). Hint: the ```Auto update``` of ```Item Properties --> Lengend Items``` allows changes in the main window to be reflected on the map. Uncheck this if you are changing the legend entries yourself. Select ```Only show items inside linked map```.
* Save your map layout by clicking ```Layout --> Save Project``` on the menu bar.
* Export the map: ```Layout --> Export as Image``` or ```Export as PDF```.
* Close the map window when finished.
* You can reopen the layout from the main window menu bar: ```Project --> Layouts``` or use ```Project --> Layout Manager```.

![Dominica moisture index map](/assets/images/dominica-moisture-index.png)<br/>Sample map developed with QGIS.
