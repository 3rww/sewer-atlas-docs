# **Sewer Atlas Data Release Notes**

This page contains the cumulative data release notes for the Sewer Atlas.

## 2017-Q4 (v6.0.0)

### Summary

The 2017-Q4 update encompassed a major update to the data model, data updates from several community datasets, and one round of review with the source data maintainer, Glenn Engineering.

### Model Updates

> *The Sewer Atlas database schema is now better aligned with the ALCOSAN Regionalization database schema.*

The Sewer Atlas data model received a major house-cleaning for this update. This entailed the normalization of field values throughout the database.

The goal of this effort was to clean-up the way that data classifications are represented, and update them to match the latest standards in place by ALCOSAN (w/ AECOM) for the Regionalization project. Through this effort, we did not look to change the classification (i.e., we did not reclassify any records to represent something else) for any given record.

> *EXAMPLE: the values `Yes`, `YES`, `Y`, `True`, `1` were all found in the `ALCOSAN` field, which is a simple boolean-esque field indicating whether or not ALCOSAN owns the infrastructure; such values all become re-coded as `Y`.*

Where possible, the cleaned-up values were made to conform to the data model in use for ALCOSAN's RI initiative (developed by AECOM). In cases where values present in the Sewer Atlas database did not have a corresponding code/value in the ALCOSAN RI data model, we fell back to the original Landbase Systems data dictionary for the old One Overall Map. In the few remaining cases, we left the values as-is, and anticipate addressing them as we continue to make updates are made. Overall, the Sewer Atlas database schema is now better aligned with the RI database schema.

You can see the complete field and value mappings table [here](./resources/r2017Q4_LBS_clean_lookup.csv), which was used to crosswalk values in the previous version of the data model to a new, cleaned-up version.

### Data Updates in the 2017-Q4 Release

After the data model update described above, routine data maintainance was performed using data provided by Glenn Engineering for numerous communities

* Updates covered:
  * Aspinwall
  * Braddock
  * Chalfant
  * North Braddock
  * Sharpsburg
  * Turtle Creek
  * Trafford
* Emphasis on geometry matching and attritbute updates for key fields related to infrastructure dimensionality and typology
* Addressed specific request from data maintainer (Rich Hinkle @ Glenn Engineering) that for Glenn-managed data, the Sewer Atlas use the "local infrastructure ID" provided in the submission in the Sewer Atlas' structure ID field (`STRUCT_ID`)
* Only one round of review, addressing basic questions; additional review will be conducted as necessary in the next release cycle (2018-Q1)
* Did not rebuild Virtual Laterals for this release; will include in next release (2018-Q1)

#### Geometry

* Geometry edited to move the Sewer Atlas data coincident with submission in all cases, except for infrastructure within the ALCOSAN RI extents, or connected directly to it.
* No geometry-matching was explicitly performed on pipes/structures within the RI Extents (referencing November 2017 RI Extent data), *except* for changes related to the general data model update described above (in which case actual values were not changed, only how they were represented).

#### Attributes

* At the request of the data maintainer, we replaced values stored in the structure ID field (`STRUCT_ID`) on the Sewer Atlas with local infrastructure IDs, stored in the `LOCAL_ID` field in the submitted data
* The complete crosswalk of attributes between the source data and the Sewer Atlas database can be found [here](./resources/r2017Q4_source_lookup.csv).

### Next Update (2018-Q1)

The next update will focus on additional QAQC for some communities edited during 2017-Q4, the remaining datasets provided by Glenn Engineering, and portions of the PWSA service area.

## 2017-Q3 (v5.2.0)

### Summary

* Data provided by Glenn Engineering on behalf of Whitaker and Forest Hills; this release focused on updates using this data, as well as several requested data fixes in other locations
* Emphasis on geometry matching and field normalization in key fields
* Addressed specific request from data maintainer (Rich Hinkle @ Glenn Engineering) that the Sewer Atlas use the local infrastructure IDs in the Sewer Atlas structure ID field (`STRUCT_ID`)
* All questions resolved during meeting with data maintainer:
    * dangling pipes in Whitaker: "non-structures" (e.g., end of pipe) maintained as point feature class separate from actual structures
    * some infrastructure included not owned by Whitaker (e.g., West Mifflin, Munhall): part of data maintainer's file used for reference (we'll use data from those municipalities to update that infrastructure)
    * notable differences in geometry in both Forest Hills and Whitaker: the data maintainer invested a significant effort in field verification since the last update to these areas made to 3RWW's data in 2011
    * the prefered local ID value in the submitted data (there are several ID fields): use values in the `LOCAL_ID` field from submitted data
* No geometry matching or attribute updates explicitly performed on pipes/structures within the RI Extents (referencing August 2017 RI Extent data), *except* for changes related to standardization of ownership values.

### Geometry

* Geometry edited to move the Sewer Atlas data coincident with submission in all cases, except for infrastructure within the ALCOSAN RI extents, or connected directly to it. RI extent data from August 2017
* New infrastructure added in both municipalities
* Some corrections to pipe flow direction made in Whitaker, necessitated by newer field-verfied data from Glenn Engineering

### Attributes

* Owner field cleaned up to standardize names in the owner field for both segments and nodes
* Pipe dimensions updated
* The various "type" fields updated
* Replaced values stored in the structure ID field (`STRUCT_ID`) on the Sewer Atlas with local infrastructure IDS, stored in the `LOCAL_ID` field from submitted data
* Upstream and Downstream Manholes updated to reflect new IDs

### Misc.

* For this round of edits, we implemented an automated attribute transfer process for key attributes: pipe dimensions, structure and segment ID fields, and infrastructure types. The application of process tool be will be refined and expanded over the next several releases.
* Revisited sewer structures and pipes in Collier (first updated in the 2017-Q2 release);  manually updated `GEO_TYP_PT` and 'PIPE_DIAM' values.

## 2017-Q2 (v5.1.3)

### Summary

* Data provided by NIRA on behalf of Collier Township; this release focused on updates with this data only.
* Estimate +90% agreement of submitted data with existing Landbase systems data
* Most of the changes focused on adding pipes not previously included.
    * Updates: primarily made to attributes, with emphasis on normalizing field values;
    * Inserts: geometry (new pipes) w/ corresponding attributes
    * Per curation strategy "ground rules": no geometry or attribute changes made to regionalization; EXCEPT where normalization of ownership field performed to match the ownership domain (just for Collier infrastructure)
    * Remaining questions regarding ownership attributes; some uncertainty about whether builder, owner, or maintainer is being recorded as owner (here and elsewhere), handling joint ownership, etc. This is something that will be addressed globally in future updates.
* After first round of edits, ~dozen locations where clarity on pipe location was needed
* Clarified most of those locations with NIRA in meeting on May 1 2017. Course of action/resolutions captured in notes layer.
* Second round of edits proceeded based on NIRA instruction. Geometry adjustment of existing pipes made to comply with NIRA data.

### Geometry

* Geometry edited to move the sewer atlas data coincident with submission in 99% of cases.  A new set of clarifications are being compiled for review where outstanding questions.
* Most cases did not require any adds or deletes, but just moving the nodes to match and using map topology editing to drag along the lines.

### Attributes: Ownership

* Owner field cleaned up to standardize names in the owner field for both segments and nodes.  The data submission included datasets for both CTMA owned and private structures.  The private structure data included information on the owners as well. The current datamodel is focued on government and authority ownership, so the owner field focused on four categories: 
    * CTMA – coincident features with the CTMA submission
    * COLL – Collier Township owned infrastructure as indicated in the Private structure data
    * Private – all other owners in the Private structure submission.
    * Unknown – structures in the current data but are not present in either the CTMA or Private Structures.
* The owner fields were also not updated or standardized for the large trunk bisecting Collier.  This was not included in the CTMA submission and the current data indicates the nodes are owned by Collier Township and the pipe by South Fayette.


<br><br><hr>
The changelog is maintained on [Github](https://github.com/3rww/sewer-atlas-docs/edit/master/docs/changelog.md).
