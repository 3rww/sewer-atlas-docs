# **Sewer Atlas Data Changelog**

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
The changelog is maintained on [Github](https://github.com/civicmapper/3rww-sewers/blob/master/changelog.md).