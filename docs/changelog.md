# 3RWW Sewer Atlas:<br>**Data Changelog**

Changelog maintained [here](https://github.com/civicmapper/3rww-sewers/blob/master/changelog.md) (auth required).

## v5.1.3 (2017-Q2)

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