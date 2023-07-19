# **Sewer Atlas Data Release Notes**

This page contains the cumulative data release notes for the Sewer Atlas.

*The changelog is maintained on [Github](https://github.com/3rww/sewer-atlas-docs/edit/master/docs/changelog.md).*

## 2023-Q2 (v6.9.0)

### Summary

The 2023 Q2 release is a maintenance release that included edits for a handful of municipalities with new muncipal data submissions, as well as a pass through the PWSA service area with their latest available data.

As always, edits emphasized geometry matching and attritbute updates for *key fields* related to infrastructure dimensionality and typology; ALCOSAN RI infrastructure was treated as "caution tape" even when municipal submissions suggested differences

Once edits were complete, we additionally double-checked network topology and system types across the entire system.

### Municipalities Edited 

Data submissions from the following municipalities were used to update the Sewer Atlas for this release:

* Munhall: complete update, with notable changes to geometry
* Monroeville: focused updates to account for changes in the latest municipal data submission
* Green Tree: complete update, with an emphasis on ensuring the SEWERTYPE field was completed for all municipal-owned assets within the boundary.
* PWSA: rolling update, with an emphasis on stormwater infrastructure added to the PWSA's IAM database since our last release.

## 2022-Q3 (v6.8.0)

### Summary

The 2022 Q3 release includes updates to a dozen municipalities whose submissions indicated a large number of system changes, as well as hotfixes in locations of interest to the ongoing Consent Order Agreement (COA) due-diligence process.

Edits emphasized geometry matching and attritbute updates for *key fields* related to infrastructure dimensionality and typology, primarily focusing on locations where edits would update the representation of network connectivity. Once edits were complete, we additionally double-checked network topology, system types, and ownership across the entire system.

Finally, this release is the first to be published with separate stormater infrastructure data that has been incorporated to-date.

### Municipalities Edited 

Data submissions from the following municipalities were used to update the Sewer Atlas for this release:

* Shaler
* Plum
* Monroeville
* Penn
* North Huntingdon
* Trafford
* North Versailles
* Wilmerding
* Wall
* East McKeesport
* Turtle Creek
* East Pittsburgh
* Chalfant
* Wilkins
* Churchill
* Forest Hills
* Crafton
* Ingram
* Carnegie
* South Fayette

### Municipalities Reviewed

In addition to the municipalities listed above, we reviewed a number of municipal data submissions in Chartiers Creek basin, comparing them to existing Sewer Atlas data:

* Collier
* Kennedy
* Robinson
* Bridgeville
* Scott
* Heidelberg
* Rosslyn Farms
* Thornburg
* Oakdale
* McDonald

Updates from these municipalities will be incorporated into the Sewer Atlas in a future release.

### Consent Decree-Related Fixes

In addition to the municipal data submission-driven editing work, the latest release includes edits made as a result of review undertaken as part of the due diligence process for the municipal COAs.

These edits tended to focus around cleaning up the representation of connections to outfalls, points of connection, and flow monitors. Of note, this work also included corrections to connectivity upstream of the following points of connection:

* T-05
* O-15

### QAQC Across the network

#### Field Value Clean-Up

This round of edits also cleaned up missing and non-standard field values across the entire Sewer Atlas database in the following fields:

* `SEWERTYPE`: filled in blanks based on the municipal submission, and/or updated based on Exhibit A/B inclusion.
* `OWNER_NAME`: filled in using contextual data, e.g., `SRC_*` fields from the original OOM data model
* `TYPE_PT`, `SUBTYPE_PT`: cleaned up to match the established field domains, which are based on ALCOSAN's Info Asset Management data schema.

Additionally, we took a pass through all of the main fields

* changing empty strings to NULL and renaming non-standard values to match their domain equivalent.

#### Connectivity Checks

As with all previous updates, this update prioritized maintainging the topological intergrity of the network model for reliable inter- and intra-municipal tracing.Even when the submitted data is not topologically clean (and it often isn't), the Sewer Atlas maintains the topology and connectivity that is *implied* in the data submission.

After the incorporation of municipal data, topology checks on the Sewer Atlas are largely handled by implementing Esri's *Geometric Network* data type, through which the topological rules required for maintaining the needed connectivity are implemented, and errors identified on network build.

As a final check, upstream tracing from the ALCOSAN plant is performed iteratively to identify and correct any remaining disconnected areas of the network that the geometric network topology rules do not account for. For this release, in a limited number of situations the following additional correctsion were made in order to maintain connectivity:

* Nodes marked as Abandoned by PWSA and, consequently, disabled from network trace, were in fact necessary for maintaining trace connectivity. To maintain connectivity in the Sewer Atlas, these nodes were re-enabled but still marked as Abandonded. During the next round of edits, we will verify with PWSA about how best to handle this kind of situation.
* Junctions between pipe segements not represented with a node in the municipal submission (point geometry) are automatically given a network junction node. However, in some cases the municipal submission also does not provide a break in one ore more the the lines at that junction. In those case we add the break.

### A note on future releases

Going forward from this release, the updates to the Sewer Atlas data will be pushed out at a higher frequency with smaller coverages to support the needs of the COA review process.

## 2020-Q2 (v6.7.0)

### Summary

The 2020 Q2 udpate completed the integration of ALCOSAN's detailed RI dataset into the Sewer Atlas. It also cleaned up type and status fields for features across the dataset, and incorporated database GUID values from PWSA's IAM

Edits emphasized geometry matching and attritbute updates for *key fields* related to infrastructure dimensionality and typology. Once edits were complete, we additionally double-checked network topology across the entire system.

### ALCOSAN RI

A data export from ALCOSAN's Info Asset Manager was provided in March 2020. It included coverage for the entire ALCOSAN service area; for this update it was filtered so that only those segments and nodes of the network that were updated through ALCOSAN's RI program were used to update the Sewer Atlas.

Most of the features (~80%) already aligned geographically with those in the Sewer Atlas; in those cases we automaticaly transfered updated attributes from the source tables to the target tables for matching geometries. For the remaining features we manually matched geometry and then automatically transferred attributes.

All ALCOSAN RI features updated in the Sewer Atlas include the GUID from ALCOSAN's Info Asset Manager software.

One issue of pipe directionality for RI infrastructure affecting Crafton, Ingram, and PWSA was the focus of a review with ALCOSAN's point of contact; this issue was logged and requires further. resolution.

### PWSA

All PWSA-owned features were updated to ensure they included the GUID from PWSA's Info Asset Manager software.

### Other

This round of edits also cleaned up non-standard field values across the entire Sewer Atlas database in the following fields:

* `SEWERTYPE`
* `PIPETYPE`
* `TYPE_LN`
* `STATUS_LN`
* `STATUS_PT`

This work included changing empty strings to NULL and renaming non-standard values to match their domain equivalent.

## 2019-Q4 (v6.6.0)

### Summary

The 2019 Q4 udpate completed the update of PWSA coverage within the Sewer Atlas. This includes separate stormwater infrastructure.

Edits emphasized geometry matching and attritbute updates for *key fields* related to infrastructure dimensionality and typology. Once edits were complete, we additionally double-checked network topology across the entire system, and batch-updated infrastructure status (i.e., abandoned) as it related to network tracing.

### PWSA

A fresh submission from PWSA (current through October 2019) was used for this latest release. It included complete exports of point and polyline datasets, `in_node` and `in_pipe`, respectively, as Esri shapefiles. These layers included all nodes and pipes as they are exported from PWSA's InfoAsset Manager (IAM) software and contain abandoned features as well as point features such as reducers and lateral connections (these are typically removed from the primary sewer layers already provided). Additionally, subsets of those two datasets were provided; e.g., `Sewers` and `Abandoned Sewers` were provided representing mutually-exclusive subsets of the `in_pipe` dataset derived from values in that table's `Status` field.

As PWSA's IAM database does not model network connectivity the same way the Sewer Atlas database does, we focused on testing network connectivity during the QAQC process. This was necessary specifically around the overflows and outfalls in the vicinity of ALCOSAN interceptors: while in the Sewer Atlas the overflow is represented with *virtual* network segments and nodes, that is not the case in PWSA's IAM database. To balance these approaches, we updated locations for non-virtual nodes and segments to match PWSA's data while preserving the network connectivity with the Sewer Atlas's existing virtual nodes and segments.


## 2019-Q2 (v6.5.0)

### Summary

The 2019 Q2 udpate included updates to coverage for Shaler Township, Ross Township, and the PWSA service area.

As always, the editing emphasis was on geometry matching and attritbute updates for *key fields* related to infrastructure dimensionality and typology.

### Ross

Ross data was provided in two file geodatabases: one for separate stormwater infrastructure, and one for wastewater (separate and combined) infrastructure. Each geodatabase contained feature classes prefixed with the system type (storm or sewer).

* The owner field for Ross contained numeric values; though these values appear to correlate with owner names on corresponding features in the Sewer Atlas (e.g., 1 in source data == "ROSS" in target), we did not explicitly pull these over during editing
* System (storm, sanitary) and type (manhole, outfall, etc.) information was inferred from the names of the point feature classes, as the data model did not always explicity contain that information in dedicated system or type fields.
* We pre-calculated a `SEWERTYPE` field on our composite source data, inferring this data from the source file geodatabase names and source feature class names

> [Ross crosswalk](./resources/r2019Q2_crosswalk_ross.csv)

### Shaler

The schema of the Shaler data appears to be derived from the original One Overall Map model. However, only a small subset of the fields were provided.

> [Shaler crosswalk](./resources/r2019Q2_crosswalk_shal.csv)

### PWSA

PWSA's data submission, which was used in several previous quarterly releases, included complete exports of point and polyline datasets, `in_node` and `in_pipe`, respectively, as Esri shapefiles. Additionally, thematic extracts of those datasets were provided; e.g., `Sewers` and `Abandoned Sewers` were provided representing mutually-exclusive subsets of the `in_pipe` dataset derived from values in that table's `Status` field.

Updated coverage in the Sewer Atlas for the PWSA service area now includes to all sewersheds from the City's eastern border between the Allegheny and Monongahela west to the Point. This also includes separate stormwater infrastructure data.

> [PWSA crosswalk](./resources/r2018Q3_crosswalk_pwsa.csv)

## 2019-Q1 (v6.4.0)

### Summary

The 2019 Q1 udpate included updates to coverage for McKees Rocks and Stowe Township. Additionally, some backfilling of PWSA separate stormwater infrastructure data was performed in previously edited areas in the M-47, A-42, and M-29 sewersheds.

As always, the editing emphasis was on geometry matching and attritbute updates for *key fields* related to infrastructure dimensionality and typology.

### McKees Rocks and Stowe Township Updates

Data for McKees Rocks and Stowe was provided by NIRA Engineering.

Stowe data was provided as two flat tables for point and linear features. McKees Rocks data was provided as an Esri File Geodatabase, with distinct feature datasets for Stormwater and Sanitary systems, each containing feature classes further separating components by function (e.g., stormwater inlets, sewer manholes, force mains, gravity mains, etc.)

#### Update Highlights

In McKees Rocks and Stowe, notable differences between existing Sewer Atlas data here (last updated in 2011) and the submitted data were identified along the CSX railroad corridor that bisects McKees Rocks and runs through Stowe. New stormwater infrastructure and improved precision of surrounding wastewater infrastructure locations contributed to these changes.

#### Data Preparation Notes

Prepping the McKees Rocks data for ingest into the Sewer Atlas presented some challenges. The provided data had be heavily conditioned *prior* to our standard editing pre-processing steps (where we crosswalk the schema of provided data to the Sewer Atlas schema). Stowe data did not require this additional step.

The complete field and value mappings table used to translate records to the Sewer Atlas schema can be viewed at these links:

* [McKees Rocks crosswalk](./resources/r20191Q1_crosswalk_mroc.csv)
* [Stowe crosswalk](./resources/r20191Q1_crosswalk_stow.csv)

Below summarizes some of the challenges of data preparation and editing specifically for McKees Rocks.

##### **System type**

The attribute indicating system type (e.g., separate sanitary, separate storm, combined) was found primarily in the `SEWERTYPE` field and several other fields. It was also de-facto established by feature classes into which data was originally provided. Sometimes this information conflicted. The source data did not make a great distinction between combine and separate sanitary systems (McKees Rocks is largely separate).

To accurately discern system type from the available data, we looked for in four different locations in the provided dataset for that information, falling back as necessary:

> `SEWERTYPE` field > `NETWORK` field > prefix of the name of the feature class (e.g., ss for separate sanitary, sw for stormwater) > feature dataset name (e.g., separate sewer, stormwater)

During editing, we also noted branches of the network that appear to have been mislabeled given the context: e.g., pipes shown as combined sanitary/storm flowing into pipes shown as separate sanitary, or storm flowing into separate sanitary. We confirmed with NIRA  that McKees Rocks has a combined sewer system; this means that the previous data (from 2011) and submitted data was not labeled according the data standards in use at that time.

##### **Local ID numbers**

This information was partially provided in several different fields; it appears to be in flux. We used `FACILITYID` in the source data when available.

#### Editing Notes

In general and consistent with our normal approach, we snapped Sewer Atlas geometries to the provided data.

However, we did note a number of locations where the submitted data did not provide topological connectivity, though the Sewer Atlas did. In those locations we left the Sewer Atlas data as-is. This was prevalent around overflow structures and pump stations, where the convention in the Sewer Atlas is to use schematic representations of connections to ensure that the network is traceable. The provided data does not appear to use that convention.

### PWSA Updates

PWSA's data submission, which was used in the previous two quarterly releases, included complete exports of point and polyline datasets, `in_node` and `in_pipe`, respectively, as Esri shapefiles. Additionally, thematic extracts of those datasets were provided; e.g., `Sewers` and `Abandoned Sewers` were provided representing mutually-exclusive subsets of the `in_pipe` dataset derived from values in that table's `Status` field.

#### Update Highlights

In the M-47, A-42, and M-29 sewersheds within the PWSA service area, we added separate stormwater infrastructure records.

The complete field and value mappings table used to translate PWSA records to the Sewer Atlas schema can be viewed [here](./resources/r2018Q3_crosswalk_pwsa.csv).

### Other Updates

Geometry matching or attribute updates were not explicitly performed on pipes/structures within the RI Extents (referencing currently available RI Extent data provided via ArcGIS Server feature services by AECOM). The RI data will be addressed explicitly in a later release.

## 2018-Q4 (v6.3.0)

### Summary

This release focused on continuing to integrate updated data from PWSA.

* portions of the `M-47` sewershed, a.k.a., 9-Mile Run, within the PWSA service area
* the `A-42` sewershed, a.k.a., Negley Run.

With the completion of these two sewersheds, we've provided coverage for the eastern side of the City of Pittsburgh from river to river. Note the 9-Mile run was also been partially tackled in the 2018-Q3 release (with Swissvale).

As always, the editing emphasis was on geometry matching and attritbute updates for *key fields* related to infrastructure dimensionality and typology.

### Submitted Data

PWSA's data submission included complete exports of point and polyline datasets, `in_node` and `in_pipe`, respectively, as Esri shapefiles. Additionally, thematic extracts of those datasets were provided; e.g., `Sewers` and `Abandoned Sewers` were provided representing mutually-exclusive subsets of the `in_pipe` dataset derived from values in that table's `Status` field.

### Geometry

* Geometry matching or attribute updates were not explicitly performed on pipes/structures within the RI Extents (referencing currently available RI Extent data provided via ArcGIS Server feature services by AECOM).

### Attributes

The complete field and value mappings table used to translate PWSA records to the Sewer Atlas schema can be viewed [here](./resources/r2018Q4_crosswalk_pwsa.csv).

### Meta

#### Stormwater data integration

PWSA's data includes separate stormwater infrastructure. Since the existing schema carried over from the original ACHD data model already accomodated separate stormwater infrastructure records, and stormwater data is of interest, we experimented with incorporating some of those records into the the Sewer Atlas database. The incorporation of this data was limited in geographic scope&mdash;mostly confined to the areas in and around the Summerset development in the 9-Mile Run watershed.

Those records *are* provided in the downloadable versions of the Sewer Atlas databases (e.g., FGDB, MPK, GPKG, SHP) but will not appear on the wastewater layers of Sewer Atlas web application (yet; you'll still find all separate stormwater data in the "stormwater atlas beta layer"). In the downloadable copies, you'll find them classified as `STM` in the `SEWERTYPE` field.

2019 releases will likely contain more of this data at a broader geographic scale.

## 2018-Q3 (v6.2.0)

### Summary

This release focused on beginning to integrate updated wastewater data from PWSA, along with additional edits for communities in previous releases.

* PWSA: the `M-29` sewershed, a.k.a., 4-Mile Run.
* Swissvale

Additionally, stormwater data from PWSA was added into a separate prototype "Stormwater Atlas" layer, which is available on the Sewer Atlas.

As always, the editing emphasis was on geometry matching and attritbute updates for *key fields* related to infrastructure dimensionality and typology.

### Submitted Data

PWSA's data submission included complete exports of point and polyline datasets, `in_node` and `in_pipe`, respectively, as Esri shapefiles. Additionally, thematic extracts of those datasets were provided; e.g., `Sewers` and `Abandoned Sewers` were provided representing mutually-exclusive subsets of the `in_pipe` dataset derived from values in that table's `Status` field.

While PWSA's submission included separate stormwater infrastructure, we *did not* (at this time) integrate it into the the connected geometric network in the Sewer Atlas.

For Swissvale wastewater infrastructure data, which is maintained by Glenn Engineering, we used data that was submitted for but not incorporated into the 2018Q1 release.

### Geometry

Geometry matching or attribute updates were not explicitly performed on pipes/structures within the RI Extents (referencing currently available RI Extent data provided via ArcGIS Server feature services by AECOM).

### Attributes

The complete field and value mappings table used to translate PWSA records to the Sewer Atlas schema can be viewed [here](./resources/r2018Q3_crosswalk_pwsa.csv).

The same mapping table used to translate Glenn Engineering records can be viewed [here](./resources/r2018Q1_crosswalk_glenneng.csv).

### Meta

#### Tooling development

If you're following along, you'll note that we've skipped 2018-Q2 and that 2018-Q3 is coming a bit late. To support integrating PWSA data into the database, we invested more time in 2018 in building more robust tooling that supports semi-automated editing workflows.

#### Stormwater Infrastructure Data

In addition to updating wastewater data, we also extracted separate stormwater infrastructure records from PWSA's submission and hosted those in a separate "Stormwater Atlas" layer. This data is provided as-is.

In the future this data is planned to be tightly coupled with the wastewater data to better reflect the real-world connectivity and relationship between the systems. That change will be accompanied by a major update to the database schema as we adapt it to better represent non-wastewater pipe infrastructure.

## 2018-Q1 (v6.1.0)

### Summary

This release is a continuation of 2017Q4 updates using data provided by Glenn Engineering. This release covers these municipalities:

  * Aspinwall
  * Braddock
  * Chalfant
  * Homestead
  * North Braddock
  * Sharpsburg
  * Turtle Creek
  * Trafford
  * East Pittsburgh
  * East McKeesport
  * North Versailes
  * Wall
  * Wilmerding

It also revisted the municipalities from the 2017Q4 release, and tightened up the edits made there.

As always, our emphasis was on geometry matching and attritbute updates for *key fields* related to infrastructure dimensionality and typology.

As with past releases that utilized data from Glenn Engineering, we addressed specific request from data maintainer that the Sewer Atlas use the "local infrastructure ID" provided in the submission in the Sewer Atlas' structure ID field (`STRUCT_ID`). We conducted in-person review of edits with the data maintainer on 21 March 2018.

### Geometry

* Updates reflect major infrastructure upgrades in Trafford, North Versailles/East McKeesport (5th Ave).
* Geometry matching or attribute updates was not explicitly performed on pipes/structures within the RI Extents (referencing November 2017 RI Extent data); note though that in several edge cases where connectivity issues cropped up with submitted data, we did make minor geometry edits merely to ensure geometric network connectivity was maintained.

### Attributes

* Correction to ownership: Pipes classified as `NVER` in the last release were done by mistake. North Versailles Township (`NVER`) does not own wastewater infrastructure. It is all owned/maintained by the municipal authority (`NVTS`). This has been corrected.
* Some submitted wastewater data included separate stormwater infrastructure, misclassified as `SAN`, which came up during review. We reclassified these as `STM` and changed `disabled` to `false`. The records are retained in this way, but won't show on the Sewer Atlas and won't be included in the network trace.

## 2017-Q4 (v6.0.0)

### Summary

The 2017-Q4 update encompassed a major update to the data model, data updates from several community datasets, and one round of review with the source data maintainer, Glenn Engineering.

### Model Updates

> *The Sewer Atlas database schema is now better aligned with the ALCOSAN Regionalization database schema.*

The Sewer Atlas data model received a major house-cleaning for this update. This entailed the normalization of field values throughout the database.

The goal of this effort was to clean-up the way that data classifications are represented, and update them to match the latest standards in place by ALCOSAN (w/ AECOM) for the Regionalization project. Through this effort, we did not look to change the classification (i.e., we did not reclassify any records to represent something else) for any given record.

> *EXAMPLE: the values `Yes`, `YES`, `Y`, `True`, `1` were all found in the `ALCOSAN` field, which is a simple boolean-esque field indicating whether or not ALCOSAN owns the infrastructure; such values all become re-coded as `Y`.*

Where possible, the cleaned-up values were made to conform to the data model in use for ALCOSAN's RI initiative (developed by AECOM). In cases where values present in the Sewer Atlas database did not have a corresponding code/value in the ALCOSAN RI data model, we fell back to the original Landbase Systems data dictionary for the old One Overall Map. In the few remaining cases, we left the values as-is, and anticipate addressing them as we continue to make updates. Overall, the Sewer Atlas database schema is now better aligned with the RI database schema.

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
