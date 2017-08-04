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
