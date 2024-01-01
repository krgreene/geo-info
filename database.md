---
layout: page
title: Geodatabase
permalink: /database
nav_order: 6
---

On this page:

* TOC
{:toc}

# Geodatabase basics

## Introduction

A **database** is a collection of structured data on a computer system which is usually manipulated by **database management system (DBMS)** software. The DBMS allows editing and **querying** the database to produce the desired information. A **geodatabase** or **spatial database** is a special type of database for storing geographic or spatial data. This type of data includes geographic coordinates, such as latitude and longitude, and the geodatabase can store geometry parameters such as points, polygons and lines. The geodatabase also allows special functions such as spatial queries, e.g. finding features which are close to a point or enclosed within a polygon, and several other spatial functions.

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
* Check the source to confirm that they came from the geopackage.

Saving the project to the geopackage:

* Go to ```Project --> Save to --> GeoPackage...``` and select the geopackage.
* Complete the dialog box.

* Close the project.

## Opening a project saved in a geopackage

* Go to ```Project --> Open from --> GeoPackage...```.

## Spatial queries

Apart from regular SQL queries, spatial databases allow special spatial queries such as proximity of features or whether they overlap. We will execute SQL queries on the geopackage layers.

* In the ```Browser Panel```, expand the geopackage.
* Right-click the ```estates``` layer and select ```Layer Properties...``` to preview the associated data.
* Close the dialog box.
* Right-click the ```estates``` layer and select ```Execute SQL...```.
* Execute the following SQL query:
> ```SELECT * FROM estates WHERE estate_typ = "Large Estates";```
* Load the result to visualize it.

* Execute the following SQL query:
> ```SELECT * FROM estates
JOIN soils
ON ST_EnvIntersects(estates.geom, soils.geom) 
WHERE estates.estate_typ = "Large Estates" AND soils.type = "Kandoid latosols";```

* Load the result to visualize it.



## Working with PostGIS

**alwaysdata** is a site which allows you to easily host online databases. We will use this site to demonstrate the basic workings of PostgreSQL database with PostGIS extension. The free account allows data storage up to 100 MB and will be terminated over a period of inactivity.

- Go to [https://www.alwaysdata.com/en/](https://www.alwaysdata.com/en/){:target="_blank"} and create a free account. Remember your passwords!

- Once the account has been created, select ```PostgreSQL``` under ```Databases``` and ```Add a database```. You can add databases and users for your account this way.
- On the database page, enter a name for the database under ```Details```.
- Under ```Options --> Extensions```, select ```PostGIS``` and ```Submit``` the form.
- Take note of the ```PostgreSQL host``` name at the top of the page, the database name, database username and password which you created.

The database is now setup and can be manipulated using the web program phpPgAdmin. You will see a link to this under the host name and version at the top of the page.

- Click the link to open phpPgAdmin.
- Use the user name and password you created for the database to login. If you forget the password, go back and change it on the users tab of the database account.
- In phpPgAdmin, view the navigation tree on the left and notice your PostgreSQL database. Expand to ```Schemas --> public --> Tables```. Note that no tables have been created in the database as yet. We will create a table with geometry to store farm data.
- To make a table to store data, click on ```Tables``` in the navigation tree and ```Create table``` in the main pane.
- Enter the following:
    - Name: farms
    - Number of columns: 4
    - Comment: Basic data for each farm plot.

- Click ```Next```.
- Now create the columns (column names must not have spaces). We'll give each column a name, data type and comment. Comments are descriptions to help users.
    1. id, serial, not null, unique key, comment: Primary key, auto-increments.
    1. name, text, not null, Name of the farm.
    1. type, text, Type of activity (arable, pastoral, mixed).
    1. geom, geometry, lon lat coordinates.
    1. description, text, General details.

- Click ```Create```.

- Once the table has been created, click on ```farms --> Insert``` to enter data. The **id** field will be generated by the database. Enter the name, type, geometry and description as shown below. After adding data for a row, click ```Insert & Repeat``` to add a new row and ```Insert``` after the last row.

Name | Type | Geometry | Description
Fresh Farm | Arable | POLYGON((-61.37360927550622 15.41470178191764, -61.37143506044097 15.41308112202391, -61.36730690626399 15.41465892839792, -61.36856720412191 15.4169977323299, -61.37360927550622 15.41470178191764)) | Vegetable farm with vending facility.
Henderson Rabbit Farm | Pastoral | POINT(-61.3281011 15.2668005) | Small rabbit farm.
Greyson's Farm | Mixed | POLYGON((-61.34845586256422 15.23028220735083, -61.34857223001723 15.22964621301943, -61.3483681718734 15.22930191070718, -61.34794025920919 15.22962960452875, -61.34845586256422 15.23028220735083)) | 

- Once the data has been added, select the ```farms``` table and click ```Browse``` to view the data. 
- Notice the ```geom``` column has been converted to Well Known Binary (WKB) format.

## Connecting QGIS

We will now link QGIS to the database and retrieve the table.
- Start a new project in QGIS.
- In the ```Browser Panel```, right-click ```PostgreSQL``` and select ```New Connection```.
- Enter the following:
    - Give the connection a name (this could be the database name on alwaysdata).
    - Leave Service empty.
    - Host: Enter the PostgreSQL host (found at the top of the database page on alwaysdata).
    - Leave the Port as 5432.
    - Database: Enter the database name from alwaysdata.
    - SSL mode: require.
    - Leave Session ROLE empty.

- Under ```Authentication --> Configurations```, click the plus sign.
    - Enter a name for the authentication configuration (this could be the database name).
    - Select ```Basic authentication```.
    - Enter the username and password for the **database user** you created on alwaysdata. You can view the password by clicking the gear icon next to the user on alwaysdata.
    - Click ```Save```.

- Click ```Test Connection```.
- Check the following boxes:
    - Only look in the 'public' schema
    - Also list tables with no geometry
    - Allow saving/loading QGIS projects in the database
    - Allow saving/loading QGIS layer metadata in the database

- Click ```OK```. Your database will be connected.

## Loading database tables

- In the ```Browser Panel```, under ```XYZ Tiles```, drag ```OpenStreetMap``` to the ```Layers Panel```.
- Expand ```PostgreSQL``` in the ```Browser Panel``` and drag the ```farms``` tables to the ```Layers Panel``` to visualize them on the map.
- Open the ```Attribute Table``` to view the data.

You have successfully loaded data from an online database.

## Saving the project to the database.

Saving the project to the database:

* Go to ```File --> Save to --> PostgreSQL...```.
* Select the Connection, Schema, give the Project a name and click ```OK```.
* Close the project
* Login to your phpPgAdmin on alwaysdata and expand to your database public schema.
* Under ```Tables```, click on ```qgis_projects```. You should see your farms project (you may need to click ```Browse```).

## Opening a project saved in a database

* Go to ```Project --> Open from --> PostgreSQL...```.
* Complete the dialog box and click ```OK```.