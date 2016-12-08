# 3RWW Sewer Atlas User Guide:<br>**Identifying Sewersheds**

*Note: this documentation is in active development*

This user guide describes how to use the Sewer Atlas to support desktop and field workflows.

## Method A. Use the *Sewersheds* layer

1. Turn on the sewersheds layer
2. Find the desired sewershed
	* pan and zoom
	* search with attribute table
	* use search tool to enter the basin number

## Method B. Trace network upstream from a specific sewer outfall

This method is more involved than the previous method, but has the added benefit of revealing all infrastructure in the sewershed.

1. Find a sewer outfall
	* pan and zoom
	* search with attribute table
	* use search tool to enter the basin number
2. Tracing is initiated from one (or more) `Flag` inputs that the user places on the map. Open the widget, click the `Flag` button, and select the desired location(s) on the map. Note that the location you pick does not need to be ultra-precise; the point you place will be automatically snapped to the nearest pipe once the trace is initiated.
3. Click `Run` and the trace will commence.
4. The results of the trace are added to the map in 4 new layers: upstream pipes, upstream structures, downstream pipes, and downstream structures. These new layers are effectively copies of the traced pipes and structures from the wastewater network dataset. Each layer is accessible in the both the **Map Layers** widget and the **Attribute Table**, and contains all attributes of the wastewater network dataset.
	>5. By clicking the `Clear' button, the result layers and any `Flag` inputs will be removed from the map.



---
```
## Searching for Locations

The Search widget is located in the upper left hand corner of the map; it enables end users to find locations on the map. Use it to enter:

* Coordinates, entered as Longitude, Latitude (i.e., *X, Y*)
* Addresses (e.g., 3901 Penn Avenue, Pittsburgh, PA 15224)
* Place Names (e.g., Pittsburgh)

The arrow on the left side of the search box allows you to use a specific geocoding service:

* *AC EAMS AP and ST Locator:* a geolocation service provided by Allegheny County, which uses up-to-date addressing maintained by the County for supporting 911 emergency service dispatching.
* *Esri World Geocoder:* a geolocation service with worldwide coverage that includes place names and some points of interest; address accuracy in Allegheny County may not be as refined as the AC EAMS AP and ST Locator.

By default, searches will use both services ('All') to find the location you're looking for.

## Identifying Coordinates

There are two ways to quickly identify real-world coordinates in the application:

* The coordinates of the location of the mouse on the map are displayed in real-time in the bottom left-hand corner of the map window. A button to the left of these values acts as a toggle; when clicked, it allows the user to then move to a point on the map, click it, and see the coordinates for that point in the lower left. The coordinates will not update until the user clicks on the map again or toggles the button.

* The ***Measurement*** widget, located in the top right corner of the map window, provides the ability to place a temporary flag on the map. The coordinates are reported for this flag in the Measurement widget window.

Note that the Sewer Atlas displays data in the WGS 1984 Web Mercator Auxilary Sphere coordinate reference system (CRS). All coordinates reported in the application are in this CRS.

## Changing Map Layers

Clicking the **Map Layers** widget displays all layers shown on the map (except for the basemap)

A number of data layers are available for viewing on the map in addition to the sewer data. This includes

* regional flow monitoring points and their estimated catchment areas
* several map services provided by Allegheny County, which include geodata ranging from parcel boundaries to recent aerial imagery
* "Virtual laterals" to help identify the pipe to which a given parcel is linked in the wastewater network (note that improvements to this data is ongoing)

The user can opt to turn layers and sub-layers on or off as needed by clicking the `checkbox` to the right of each item.

Clicking the `down arrow` on the right side of a layer displays a context menu, which includes the following functions:

* `Zoom to`: Sets the map extent to the extent of the layer.
* `Transparency`: Sets the transparency for the layer.
* `Move up`: Moves the layer one level up.
* `Move down`: Moves the layer one level down.
* `Open attribute table`:Opens the [**Attribute Table**](help_rsi.md#using-the-attribute-table) for the feature layer. This allows the user to view all attributes for features, and provides some other filtering and export abilities described further below.
* `Description / Show Item Details`: Opens the service description or the item details page for the service or the item associated with the layer, if available. This page includes information for linking to the feature service or downloading a static version of the data in one of several spatial or non-spatial formats. The ability to download varies by data source.

## Changing Basemaps

Clicking the ***Basemap Gallery*** widget displays all available basemaps.

The user can optionally select the base map shown underneath the map layers. By default, this is set to a global imagery map from Esri; however, other basemap options such as 'Dark Canvas' may provide the user with higher legibility and clarity especially when printing.

Note that graphically simpler basemaps tend to have smaller tile file sizes and consequently will load faster.

Clicking one of the basemap thumbnails sets it as the active basemap for the application. Click the `x` button in the upper right corner of the Basemap Gallery window to close it.



## Using the Attribute Table

The **Attribute Table** displays a tabular view of the map data and its attributes at the bottom of the map window. It is a powerful tool for searching, selecting, sorting, and exporting data from the map.

Please note that the wastewater network contains over 125,000 features. Certain operations conducted on the entire dataset in the **Attribute Table**, such as sorting, will take time to complete.

### Opening the table
The attribute table can be opened two ways:

* clicking the arrow/tab at the bottom of the map window
* though the **Map Layers** widget in the information window, clicking the down arrow on the right side of a layer, which will open a context menu with an *Open attribute table* option.

When more than one layer's attributes display, multiple tabs automatically generate in the attribute panel allowing you to switch among the attribute tables.

### Using the table

*Clicking a record* in the table selects it and highlights the corresponding feature in the map with the color specified in the Attribute Table widget configuration window. Press the Shift or Ctrl key to select multiple records.

By *Clicking a field heading*, the table will sort the records by the field.

Buttons at the top of table help manage the selection and the way the table displays:

* An *Options* menu provides advanced selection, filtering, and exporting options. More on this later.
* *Zoom to selected:* features—Clicking Zoom to resets the map extent to center around selected features.
* *Clear selections:*—Clicking the Clear Selection button clears all selections.
* *Refresh*—Clicking Refresh refreshes the tables.
* *Show or hide columns:*—Clicking the **+** icon on the right side of the Attribute Table panel opens the field visibility window. Check or uncheck the fields to set them to visible or invisible in the table.
Number of selected records—Shown on the lower left of the table. Can also be accessed from the *Options* menu.

### Selecting and Filtering records and features

The Attribute Table provides the user to dig deep into the data and manipulate what data is shown on the map. Through the `Options menu` on the table, you can select or filter records in the table, which in turn highlights or filters, respectively, the corresponding features on the map. The available options

* *Show Selected Records:* Only displays selected records. By hiding records you haven't selected, it may be easier to visually browse the table.
* *Show Related Records:* *Note: the Sewer Atlas does not currently have related tables.* Displays related records if a selected record has related table.
* *Filter:* Allows the user to specify a query that will filter records in the table.
* *Filter by Map Extent:* This option only displays attributes in the table for features within the current map extent.

### Exporting records from the table

The `Options menu` provides an *Export to CSV* tool, which creates a file that can be opened in Microsoft Excel, other spreadsheet software, or a text editor.

If records are selected and/or a filter is applied, only the selected and/or filtered records are exported. If no records are selected or filtered, all the records are exported.


## Selecting/Highlighting Features

The ***Select Features*** widget displays a list of predefined queries that you can run to highlight specific features on the map and simultaneously highlight the corresponding records in the attribute table.

Two options are provided when running queries:

* `Use spatial filter`: One of two spatial filters is applied on top of the query definition.
	* `Use current map extent`: Only features falling within the current map extent and meeting the query definition return.
	* `Draw a graphic on the map`: Only features falling within the graphic and meeting the query definition return.
* `Add result as operational layer`: When this option is checked, query results remain on the map until the Clear Results button is clicked.

Selected features will also be selected in the ***Attribute Table***.

*Note: several queries have been predefined for the application to start with; these can easily be expanded/modified to meet user requirements based on available data - just ask!*

## Filtering Map Features
See *Using the Attribute Table >>> Selecting and Filtering records and features* for instructions on how to filter features.

## Generating Summaries of Map Features

The **Summarize Features** widget displays quantitative attributes from a map layer as a graphical representation of data. It is intended to makes it easier for end users to observe possible patterns and trends out of raw data.

Click on the widget, opens a list of possible summary reports to run. Select the desired report. An options window will ask if you would like apply a spatial filter (i.e., to only report on features within a specific area). Select either:

* `Only features intersecting the current map area` -- only features in the current map view will be used in the summary
* `Only features intersecting a user-defined area` -- this will prompt the user to draw an area on the map, in which an features will be summarized

Clicking `Apply` will generate a chart.

*Note: a single report has been predefined for the application to start with; this can easily be expanded/modified to meet user requirements based on available data - just ask!*

## Adding Annotations

The **Annotate** widget allows the user place notes on the map. Open the widget, and select the pushpin. Click on the map where you would like to make a note. A pop-up window will appear, which provides a text box for entering text.

Annotations are stored in a single map layer and have an [**Attribute Table**](help_rsi.md#using-the-attribute-table). The layer can be found in the **Map Layers** widget. From that widget, annotations can be displayed or hidden on the map.

Select any notation on the map with the Annotate widget open to edit the notes. Alternatively, the notes can be edited in the *Attribute Table*.

## Editing Features
*To be completed*

## Tracing the Wastewater Network
The **Network Trace** widget allows the user to identify upstream and downstream wastewater pipes and structures from any given point. It automatically runs both upstream and downstream traces, returning connected wastewater pipes and structures in both directions. It provides a basic summary of these features along with the ability to download the complete results.

### Tracing from a point on the network

1. Tracing is initiated from one (or more) `Flag` inputs that the user places on the map. Open the widget, click the `Flag` button, and select the desired location(s) on the map. Note that the location you pick does not need to be ultra-precise; the point you place will be automatically snapped to the nearest pipe once the trace is initiated.

2. Click `Run` and the trace will commence.

3. The results of the trace are added to the map in 4 new layers: upstream pipes, upstream structures, downstream pipes, and downstream structures. These new layers are effectively copies of the traced pipes and structures from the wastewater network dataset. Each layer is accessible in the both the **Map Layers** widget and the **Attribute Table**, and contains all attributes of the wastewater network dataset.

4. By clicking the `Clear' button, the result layers and any `Flag` inputs will be removed from the map.

### Viewing and using tracing results

The tracing results are shown in the widget window in a series of expandable tabs. The first tab provides a summary count of upstream pipes, upstream structures, downstream pipes, and downstream structures for quick reference. The tabs that follow list pipes and structures that were traced upstream and downstream. Clicking on any item will highlight the item on the map.

The results can be downloaded by clicking the `download .csv` button.

```
