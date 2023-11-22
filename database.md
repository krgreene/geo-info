---
layout: page
title: Geodatabase
permalink: /database
nav_order: 6
---

On this page:

[Introduction](#introduction)<br/>
[About GeoPackage](#about-geopackage-gpkg)<br/>
[Datatypes](#datatypes)<br/>
[Normalization](#normalization)<br/>
[Querying databases](#querying-databases)<br/>

# Geodatabase basics

## Introduction

A **database** is a collection of structured data on a computer system which is usually manipulated by **database management system (DBMS)** software. The DBMS allows editing and **querying** the database to produce the desired information. A **geodatabase** or **spatial database** is a special type of database for storing geographic or spatial data. This type of data includes geographic coordinates, such as latitude and longitude, and the geodatabase can store geometry parameters such as points, polygons and lines. The geodatabase also allows special functions such as spatial queries, e.g. finding features which are close to a point or enclosed within a polygon, and several over spatial functions.

The data in a database is normally arranged in tables, represented as rows and columns. A row represents a **record** which is all the data related to an **entity**, e.g.

| ID | Farm | Area |
| 1 | Roberts Plantation | 200 |
| 2 | Victoria Farms | 500 |

Each column in the data table represents an **attribute** of the entity. A single attribute within a row can be referred to as a **field**. Notice that each row has a unique ID which identifies it from any other row. Such an attribute is known as a **key**. In this table, ```ID``` is the **primary key**.

A table is also known as a **relation**. A database which uses the tabular structure with entities, attributes and keys is known as a **relational database**. A relational database contains several tables which are related to each other and are linked by their keys. There are several types of databases, each with their pros and cons and suitability for various purposes. We will focus on the relational database for the storage and retrieval of spatial data.

There are several databases systems with support for spatial data, including SpatiaLite and PostgreSQL with PostGIS.

As a database becomes very large, querying the data will become slower. Queries can be sped up by using **indexes**, e.g. in the previous table, an index can be created on ```Farm``` to allow faster searching by farm name.

## About GeoPackage (.gpkg)

GeoPackage is a light-weight spatial database file format which handles both vector and raster data. The single file format is easy to use across devices and supports spatial indexing to speed-up queries.

## Datatypes
Data stored in databases confirm to specific data types. Some common datatypes are:

* Integer (negative and positive numbers)
* Float (decimal numbers)
* Boolean (true/false)
* String (text)
* Date (formatted date values)
* Geometry (spatial features and coordinates)

## Normalization

A database must be properly structured to be useful and efficient. One way to do this is to ensure that data in fields are reduced to the simplest form, e.g. create separate fields for first name and last name rather than full name. Also, the data should not be redundant or duplicated, e.g. if several farms are under a farming project, data about the project should not be stored with the farm data but rather in a separate table containing project data. This separation and simplification is known as **normalization**.

## Querying databases

Databases may use graphical interfaces and/or coding to retrieve or update data. The standard code for querying relational databases is **SQL**. The syntax for SQL looks like this:

```SELECT * FROM Farms WHERE ProjectName = 'Cocoa and coffee'```

This statement reads as 'select all data from the table Farms that match the project name Cocoa and coffee'.

# Working with databases

QGIS can connect to and retrieve data from existing external databases. So if you have a PostgreSQL or other compatible database, QGIS can link with this database to perform spatial analysis. The ```Browser Panel``` provides built in functions for compatible databases. The GeoPackage is another convenient file type for creating a local database which can be easily shared. The GeoPackage can also be queried with SQL statements.

We will create, edit and query databases and integrate with QGIS.

## Creating a geopackage database

Geopackages are spatial database files which can store a variety of data associated with a project. We will save the project, layers and associated styles to a geopackage.

In QGIS, create a new project.

[Download and extract estates and soils vectors zip file]({{site.url}}/assets/files/estates_and_soils.zip)

* Rename the layers to estates and soils respectively.
* Apply a categorized symbology with random colors to each layer.

Package the layers:

* In the ```Processing Panel```, search for ```package``` and open ```Package layers```.
* Add the 2 layers, saving the style and metadata.
* Save the file.

Connect to the geopackage:

* In the ```Browser Panel```, right-click ```GeoPackage``` and select ```New connection...```
* Browse and connect to the geopackage.

Load the geopackage layers:

* Remove the original layers from the ```Layers Panel```.
* Add the layers from the geopackage. Notice they have kept all formatting.

Saving the project to the geopackage:

* Go to ```File --> Save to --> GeoPackage...``` and select the geopackage.
* Complete the dialog box.

* Close the project

## Opening a project saved in a geopackage

* Go to ```Project --> Open from --> GeoPackage...```

## Spatial queries

Apart from regular SQL queries, spatial databases allow special spatial queries such as proximity of features or whether they overlap. We will execute SQL queries on the geopackage layers.

* In the ```Browser Panel```, expand the geopackage.
* Right-click the ```estates``` layer and select ```Layer Properties...``` to preview the associated data.
* Close the dialog box.
* Right-click the ```estates``` layer and select ```Execute SQL...```.
* Execute the following SQL query:
> ```SELECT * FROM estates WHERE estate_typ = "Large Estates";```
* Load the result to visualize it.

## Working with POSTGIS

Go to https://www.alwaysdata.com/en/