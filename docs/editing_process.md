# Editing and QAQC Process Overview

The Sewer Atlas database is updated on an ongoing basis, with (approximately) quarterly updates made available for download and published as web map services.

The editing process entails four general steps:

* **pre-processing**: source data, which is of various qualities, consistencies, and formats, is extracted, transformed, and loaded into a set of tables designed to transfer  record and attributes-level changes to the database directly.
* **editing**: the Sewer Atlas database is updated to match the source data
* **QA/QC**: check that edits are comprehensive, conflicts are resolved, and network connectivity has been maintained
* **post-processing**: a snapshot of the database is exported and transformed into formats for download and publication as web services

This page highlights the some of the steps in that process.

## Editing

When editing the Sewer Atlas data, we follow several general rules:

* Editing entails moving the Sewer Atlas geometry to match the source data geometry
  * Unless: matching the source data *exactly* would break the geometric network topology, in which case we balance geometric precision with network-correctness
* Never delete segments/nodes, only *disable* them
  * Unless: the segments/nodes are verified as erroneous by the data source maintainer
* When working through conflicts, defer to data authorities in this order:
  * ALCOSAN datasets (e.g., RI) **>** Municipal Source Dataset **>** Existing Sewer Atlas

## QAQC

Our QAQC process emphasizes a few things:

### Overall completeness of edits

As a first pass at QAQC, we compare the source tables to the editing database on geometry simply to identify any areas we might have missed.

### Connectivity

We run a series of upstream traces from strategic points on the network (e.g., the ALCOSAN plant) to help identify any areas on the network that may have been disconnected during editing.

### Missing/empty attributes

Occasionally, our conflation process does not work; we use a map with labels and symbology designed to call out edited features with attributes that didn’t transfer from the source.

### Conflict Resolution

If needed, we bring up with the data source maintainer ay conflicts between the source and editing database that have no obvious solution. Typically, the course of action is fairly clear, but occassionally it isn't. We flag those without a clear resolution as *Issues*, which appear in a layer shown on the Sewer Atlas Data Status Dashboard.
