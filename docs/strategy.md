# Sewer Atlas Data Curation and Maintenance Strategy

*Updated 21 December 2018*

# BACKGROUND

3 Rivers Wet Weather (3RWW) hosts the Sewer Atlas, a web map for the visualization of and interaction with regional sewer network data in the ALCOSAN service area. It is the successor to Landbase Systems' "WebMap". The Sewer Atlas is an evolving product, with plans to iteratively roll out improvements to both the web mapping application and the underlying regional sewer network data.

The regional sewer network data shown on the Sewer Atlas web map is derived from the same data used in the One Overall Map: the 2011 data created by Landbase Systems for 3 Rivers Wet Weather. With the exception of an attempted update of the new regional sewer network dataset in 2014, no changes had been made to this data until August 2016.

## THE NEED FOR A DATA MAINTENANCE STRATEGY

Currently, a number of organizations are working with regional sewer network data. The figure below describes very generally how some of these organizations are using regional sewer network data and/or contributing to it:

| ORGANIZATION | DATA USAGE, MAINTENANCE ROLE, AND/OR SCOPE OF WORK |
| --- | --- |
| 3 Rivers Wet Weather w/ CivicMapper | Manages and maintains Sewer Atlas web mapping application (formerly "Landbase Systems WebMap") and regional sewer network data ("One Overall Map") Responsible for municipal outreach, data coordination, and data maintenance |
| Municipalities/Agencies w/ consultants | Each manage and maintain local municipal sewer network data. Some municipal consultants manage the data for more than one municipality |
| ALCOSAN | Internal mapping capability to support operations |
| ALCOSAN w/ AECOM | Currently updating location and physical attributes of those sewer segments that will regionalized to support the regionalization project using existing regional data to compare/validate new data |
| ALCOSAN w/ CDM Smith | modeling flows to interceptors / points of connection using existing regional data and new data (received via AECOM) for modeling |

## SPECIFIC NEEDS AND CONSIDERATIONS

Through the work being completed by these organizations, 3RWW has noted a range of immediate needs and/or
long term considerations for maintaining and improving the regional network data. These include but are not limited
to:

* facilitating ongoing/continuous municipal updates to maintain overall data accuracy and precision, allowing for increased confidence in the results of system analysis
* updating missing pipe attributes as in the data to support CDM Smith's flow capacity modeling work
* ensuring that new field data collected by AECOM for ALCOSAN's regionalization efforts integrates with  existing regional sewer network data (i.e., maintain topological connectivity of the data) from municipalities and agencies
* addressing the existing legacy data model from LBS' WebMap/OneOverall Map, which has fallen into disrepair, and recognizing that a NASSCO standards-compliant data model will better support long-term sewer network data maintenance efforts and modeling requirements.

With multiple organizations working with and improving the accuracy and precision of regional sewer network data, there is a clear need for a coordinated, accessible data curation and maintenance strategy that will enable the efficient maintenance of regional sewer network data into the future.

# STRATEGY

To support the continued evolution of the regional sewer network dataset, 3RWW has formalized its curation and maintenance strategy for maintaining regional sewer network data.

The strategy encompasses:

* The four guiding principles
* An illustration of the logistics of data curation and maintenance, as implemented technically

## PRINCIPLES

### 1. BUILD FROM THE NEWEST DATA MODEL: AECOM'S REGIONALIZATION-FOCUSED SCHEMA FROM INFONET (NASSCO STANDARDS-COMPLIANT)

* Retain a subset of the full data model at the regional-level, and select core attributes for which local maintenance will be expected:
    * The InfoNet-developed, NASSCO-compliant data model created by AECOM has 160  attributes in use for Regionalization. While not all are needed for regional municipal data maintenance, the NASSCO standard will ensure that those which are needed will be properly managed to a national standard.
    * Core attributes include the most important attributes that the Data Source Maintainers (the municipalities, agencies, and consultants working with the data) can be expected to maintain. This may be just 6-10 attributes, but must include attributes critical to modeling and risk management; metadata is also required.


### 2. FOCUSED, INCREMENTAL UPDATES

* Update with a purpose: Prioritize, scope, and focus data updates to meet clearly defined needs. For example, a single update might either:
    * address a data gap required to support an analysis (e.g., pipe diameters)
    * integrate a set of changes to the data based on real system change (e.g., add new pipes recently put in the ground)
* Leverage extensive working knowledge of other organizations working with the data (e.g., AECOM, CDM Smith) to identify where the existing data needs to be fixed the most
* Record the "change-set": Utilize the data versioning and archiving tools embedded in modern  geospatial database technology, ensuring that the record of data change is captured simply through the process of editing
    * Document rules and assumptions for each round of change in such a way that the documentation is part of/associated with the data change-set itself
* Emphasize improving overall data quality over time: Emphasize improving key data attributes and data geometry incrementally as a way to improve the data's overall accuracy and precision, which allow overall data quality improvement to be illustrated over time

### 3. PRO-ACTIVE COORDINATION

* Keep on top of changes to local and project data by pro-actively work with the Data Source Maintainers to exchange data updates. This is something 3RWW is already well-positioned to do.
* Keep the channels of communication open during the process in order to validate changesand ensure decisions and assumptions about the changes are agreed upon; keep it open after the process to ensure regional updates are being incorporated back into locally-maintained datasets.
* Provide derivative data products back to Data Source Maintainers in the formats they need (e.g., CAD, shapefile, pdf).

### 4. STANDARDIZED AND CENTRALLY-MAINTAINED DATA (LONG-TERM)

* Identify opportunities to expand the attributes for which Data Source Maintainers are responsible
* Ensure that maintained attributes are supporting modeling and analytical requirements of all
municipalities
  * look to state and federal analytical reporting requirements to inform data standards, and focus on completing attributes required for analysis
  * identify required attributes, prioritize for completion
* Ensure that data model can transition or translate to an asset management system
* Provide tools for facilitating centralized data collection and maintenance by the municipalities; this could be achieved, for example, by:
  * Implementing data upload and editing capability to an editing-focused Sewer Atlas web app, so partners could maintain data online
  * Enabling municipalities/consultants to asynchronously edit regional data, make updates, and "push" back to a central database
  * Enabling data download/extraction functions so that regional data can easily be used for more detailed, local initiatives

## DATA EXCHANGE, CURATION, AND DISTRIBUTION LOGISTICS

The implementation of the strategy described above can be understood as the cyclical flow of data through a three-
step process

### 1. DATA SOURCE MAINTAINERS

*	Data is maintained at a local or project-level by various partners: the municipalities within the
ALCOSAN service area (and their consultants), ALCOSAN's consultants (e.g., CDM Smith,
AECOM), and internal ALCOSAN data staff.
*	These organizations can continue to use their data in the format and with the software they are
most comfortable with.

### 2. CENTRALIZED INTEGRATION

*	Data from the Data Source Maintainers is integrated into a centralized GeoStore, where it is
curated, versioned, and archived in change-sets.
*	Metadata, documentation, and assumptions about each change-set is both automated and
manually linked to each change.
*	Changes integrated into the GeoStore are validated with Data Source Maintainers during this part
of the process.

### 3. DATA (RE)DISTRIBUTION:
*	Curated data is distributed back to the Data Source Maintainers via standard secure web geodata
endpoints,
*	From these endpoints, the data can be consumed by other web and desktop software, such as the
3RWW Sewer Atlas web app, desktop GIS software, or CAD software.
*	Additionally, static snapshots of the data, including extracts showing only the geodata that has
changed, are generated for redistribution to the Data Source Maintainer.
This process is illustrated and annotated generally in the following diagram:

This process has several notable benefits:

*	It is scalable:
    * Any volume or scope of data change can be accommodated: whether it is all data generated from
the regionalization project or just the addition of a new pipe in a single municipality, the process is
the same
*	It utilizes a well-supported software stack and common data standards:
    * Formats for data exchange are known and standard, and the software utilized (Esri ArcGIS, Git,
SQL, Box) are widely supported.
    * It is designed to enable exchange of data with other software utilized by project partners, such as
InfoNet (used by AECOM and PWSA), for example.
*	It is based on modular components:
    * This workflow embodies a modern micro-services and API-based approach to data management:
independent data exchange processes wrap internal editing and analysis processes, forming what
is called an "input/output sandwich".
    * Data is acquired from the source without requiring or forcing a specific brand of software or
adoption on Data Source Maintainers.
    * Individual components of the process can evolve to meet any changing needs of the Data Source
Maintainers, and technologies can be adapted as needed to support the overall goal of up-to-date,
high quality data.

## DATA OUTREACH/EXCHANGE METHODS

The publication of a secure, centralized regional network dataset (as with the existing One Overall Map hosted on
3RWW's Sewer Atlas) opens up the possibilities to exchange data with data source maintainers using several
methods beyond simply sharing static files:

*	Online editing. Data source maintainers "make changes" (i.e., suggest changes) to the data online, which
are then curated on the back-end and formally committed the master database by a data curator
*	Offline, asynchronous editing. Data source maintainers pull down a synchronized copy of the database to
their local editing environment, make changes, and then synchronize back to the main database.
Submissions can then be curated on the back-end before being formally committed the master database by
a data curator
*	Static file submission. this is the current method (utilizing either e-mail exchanges or submissions via
3RWW MDS); it is also the most time consuming from a technical perspective - new data is manually
integrated to the master database by the curator.

A combination of these is also possible, and prudent given that not all data source maintainers might have the
capability to do one or the other of these methods. The draft diagram below begins to illustrate how data might be
updated using these workflows.

###	REGIONALIZATION DATA EXCHANGE

For the ALCOSAN Regionalization project specifically:
*	AECOM SendFile
*	ArcGIS Online, via a group, if possible

##	DATA CURATION AND INTEGRATION

The act of data curation itself is the key piece to the overall data maintenance and curation strategy, as it ensures
that new data is maintained to standards and that the chain of decision-making regarding data change is maintained
within the data and metadata.

Data curation is broken into 3 steps:

*	Data Submission Tracking: at a high-level, tracking simply who, what, and when data was submitted by Data
Source Maintainers
*	Data Evaluation: comparing the adherence of submitted data to both the existing data standards and existing
records; this evaluation serves to guide the effort of data integration and additional data outreach efforts
*	Data Integration: the act of incorporating submitted data into the existing data, informed by the results of the
evaluation

## DATA SUBMISSION TRACKING

To facilitate ongoing data maintenance in cooperation with Data Source Maintainers, it is necessary to track who, what, and when data was submitted for integration into the regional database. In a sense, this is the "Sewer Atlas CRM". It will be comprised of two related objects:

### Table

This table will be separate from the regional sewer network data (the pipes, structures, and other infrastructure-
specific domains). The table will include:

*	Owner name (from data model Owner domain)
*	Date of Submission/Transfer
*	Submitter (person)
*	Submission Scope - simple descriptive note from submitter describing nature of data submitted (e.g. "supplemental to previous submission")
*	Submitted File List
*	Data Extents/geography (e.g., municipal or authority boundary)

This table will also be used to track status of curation and integration of the submitted data into the regional sewer
network dataset:

*	Data Evaluation Summary
*	Curation/Integration Status
*	Evaluation report (file)

This information will be opened up to partners to ensure that data curation is coordinated and consistently tracked. It
will be accessible as both a table and a map.

##	DATA EVALUATION

Data submitted by Data Source Maintainers for inclusion in the regional sewer network dataset will be evaluated by
3RWW against an established, authoritative data model: AECOM's InfoNET Data Dictionary ("Data Model"), which
employs a NASSCO-compliant schema.

By evaluating existing and future data submissions against the Data Model, adapting that data to the Data Model, and
providing it back to the agencies, 3RWW will:

*	enable maintenance of a datasets that are both NASSCO-compliant and consistent with the Data Model
across the region,
*	provide a data model that that can be used as a rudimentary asset information system for agencies that do
not have access to such a system; and,
*	ensure that NASSCO-compliant data is available to facilitate compliance reporting, system-wide.

### EVALUATION PROCESS

Submitted data will be evaluated against the Data Model, focusing on the following general criteria:

*	Feature Inventory: new or missing database records, tables, fields, domains, and network topology
classes
*	Attribute Completeness: which attributes are complete or incomplete, which are consistently utilized;
emphasis on completeness of required/key fields
*	Schema Comparison: check for matches to the Data Model of fields, field types, and field domains;
*	Feature Comparison (geo): check for changes in the geography of each record; can detect changes
made to the data topology (e.g., resulting from corrections made in database due to acquisition of higher
resolution GPS information), and/or actual changes to the infrastructure (e.g., addition, rerouting, removal of
pipes in the real world)
*	Feature Comparison (attributes): check for changes in attributes of each record; used primarily to detect
updates to infrastructure (e.g., a pipe segment replaced with one of new material and new width), but also
used to detect improvements made to the database (e.g., correction of attribute values with domains ); only
possible if schema matches and is enforced between data submitted and data model.
*	Metadata Completeness: check for metadata for datasets

Once data is received, it will be transformed into a working format on which evaluation tools (via ArcGIS data
reviewer extension) can be run. Analyses will be run to address the evaluation criteria described above. The results
of the evaluation will be summarized on an agency-by-agency basis. A qualitative summary, summary tables, and
data comparison maps can be provided to summarize the evaluation. The results of the evaluation will inform how
data is integrated back into the overall regional network dataset.

The following diagram indicates the workflow from receipt of data from one data source maintainer to integration of
changes back into the source database.

![workflow diagram]()

###	PRO-ACTIVE ENGAGEMENT DURING DATA CURATION AND INTEGRATION
Key to the data curation and integration process is proactive engagement with the data source maintainers. Ongoing
decentralized data maintenance work requires ongoing engagement in order to maintain momentum and keep data
up to date and up to standard. Though proactive engagement, the data source maintainers can help validate changes
and ensure decisions and assumptions about the changes are agreed upon. This will ultimately support the
maintenance of local datasets that mirror the standard set by the regional dataset.

## DATA INTEGRATION (EDITING)

After an evaluation (if possible/as needed), the work of integrating the submission from the data source maintainer will proceed. New submissions from data source maintainers do not necessitate starting from scratch for the data's extents.

The work of data integration will always start from the latest available version of the established regional sewer network dataset. The data integration and editing process will focus on updating records in the existing table with the geometry and attributes of the submission for the source maintainer, and/or adding new records where there is new infrastructure (or where previously undocumented infrastructure has been included).

Existing records will not be deleted and replaced with new records; existing records will be updated to reflect the
submission. This work can most reliably be performed manually, supported by the result of the data evaluation and/or
a data conflation analysis.

The wholesale clipping-out of existing data for the insertion of newly received data is to be avoided. Given the past experiences maintaining the One Overall Map and rebuilding the regional network for the Regionalization project, such a remove-and-replace approach leads to serious difficulties in reconciling new with old data. Importantly, such an approach eliminates the benefit of automatic, record-level edit tracking.


### CONFLICT AVOIDANCE TECHNIQUES

Key to the data curation and integration process is proactive engagement with the data source maintainers. Ongoing decentralized data maintenance work requires ongoing engagement in order to maintain momentum and keep data up to date and up to standard. Though proactive engagement, the data source maintainers can help validate changes and ensure decisions and assumptions about the changes are agreed upon. This will ultimately support the maintenance of local datasets that mirror the standard set by the regional dataset.

At a more granular level, data conflict editing avoidance might be achieved by the identification of infrastructure on and/or off-limits before editing and curation begins:

*	In general, the technique is to defer to the authority on the dataset
*	Communication is key: for an area of active work (e.g., modifying regionalization extents in a single
municipality, in which changes might occur daily), wait on the authority to complete work before integration
into One Overall Map / Sewer Atlas. For areas of "passive" work, or where updates come in chunks, then
coordination can happen as needed.
*	In integrating any given municipal data submission, avoid infrastructure that is part of the ALCOSAN
Regionalization project, plus 1 or 2 links of the network upstream, since that data is being actively managed
and refined separately

> Notes on Virtual Nodes
>
> * InfoNet, used by PWSA and AECOM for the RI project, includes virtual nodes for laterals and tie-ins to storm systems.
> *	One Overall Map also has virtual nodes, generated through the creation of the geometric network topology.
> *	Municipalities tend not to maintain this data, but it is needed for modeling.
> * It's considered a data by-product where it doesn't represent an actual sewer structure structure.

## CHANGE MANAGEMENT

The master database is a standard multi-user, versioned, archive-enabled RDBMS enterprise geodatabase. To
manage change at the resolutions required for both maintainers and consumers of the data, there are three levels of
change tracking.

### 1. Record-level edit tracking

Edits made to each record will be tracked by the user (automatically via database authentication) and by time
(automatically). This ensures the ability to track all changes to any given record, throughout the record's lifecycle.

### 2. Commits
As baskets of work are completed (e.g., completion of edits for a related to a specific submission from a data-
source maintainer), edits will be committed to the database. Each commit will be accompanied by concise,
human-readable message-to continue with the CRM analogy, the "call history" component-that captures the
nature of all the edits: where and what the editing effort focused on, why edits were made where they were
made, any lingering questions or follow up required.

### 3. Releases (dataset level-versioning)

Regular snapshots of the master database will capture batches of commits as a Release. Release are versions
of dataset ready for end-user consumption. The creation of each release will be automatically pushed to
endpoints for consumption in GIS and web mapping applications, and static file download. This includes (but is
not limited to):
*	ArcGIS Server Feature Services (vector data)
*	File Geodatabase (topology/geometric network-enabled) and shapefiles for static file download
*	Pre-rendered ArcGIS Server Tile Map Service (raster tiles, for Sewer Atlas cartography)
Each release will also come with Release Notes. This will in include a high level summary of what changed from the
previous release. The full record of commit messages (from #2 above) will be referenced in these notes.

# SHORT AND LONG-TERM DATA STORAGE AND MANAGEMENT

The primary goal for short and long term data storage management is to ensure that the master database and the
infrastructure on which it is hosted:

*	can be portable, in terms of ownership and infrastructure (local or cloud);
*	supports a wide array of end uses, via open data standards that do not limit use to a single piece of
software; and,
*	is secured.

Currently, 3RWW's core database is hosted and served with a combination of Esri ArcGIS Enterpise (formerly called
ArcGIS Server) and ArcGIS Online software, backed by a standard RDBMS enterprise geodatabase. Derived data
products are hosted on a combination of ArcGIS Online, ArcGIS Enterprise, and 3RWW Municipal Data Support web
sites, depending on use and access/sharing requirements.

# IMPLEMENTATION // TEST CASES

3RWW began implementing this strategy with 2015's transition to the Sewer Atlas, and has successfully
demonstrated its applicability and potential through test cases, descriptions of which are included on the following
pages.

## TEST CASE A: SYSTEM-WIDE ATTRIBUTE UPDATE EXAMPLE (PIPE DIAMETER)

Test Case A illustrates how a single attribute would be updated from multiple provider data
sources across the entire regional network dataset. This update serves as a successful test
case and model for managing the logistics of updates to the regional sewer network data.

###	GOALS

In July and August 2016, 3RWW, ALCOSAN, AECOM, CDM Smith, and CivicMapper successfully coordinated an
incremental update to the regional sewer network dataset.

This goal of this test update was to complete network-wide pipe diameter attributes to support CDM Smith's flow
capacity modeling work. The update process entailed:

1. Sharing new municipal sewer datasets acquired for the regionalization project (by AECOM on behalf of
ALCOSAN) with 3RWW/CivicMapper and CDM Smith
2. Reviewing new datasets to confirm content, data age, source, extent, positional accuracy, etc.
3. Identifying where pipe diameter information could or could not be derived from the new municipal datasets
4. Defining and applying assumptions for the assignment of diameter data in areas where complete pipe
diameter data was not available in the new datasets, based on engineering judgement and best practices,
and keeping record of where the assumptions were applied
5. Performing and documenting the update using available tools
6. Defining the channels for distributing the revised regional sewer network data

### RESULTS / LESSONS

CDM and CivicMapper coordinated the update; the work of updating the dataset was completed within one week.

This test case demonstrates that:
*	quick data update turnarounds are easily within reach when the need is clearly defined, allowing time and effort to be focused (in this case, the focus was on just the pipe diameter attribute)
*	incremental updates can be completed concurrently with larger data update efforts, without affecting localized data updates:
    * e.g., This update did not, for example, include the pipe attribute and location updates made by AECOM for the ongoing regionalization project, as those updates were not yet ready for distribution (and were not provided). However, when that data is ready, it can easily be integrated.
*	the use of similar tools by the source data maintainers (municipalities/consultants working within the Girty's Run sewersheds are using the same tools 3RWW/CivicMapper are using) makes updates to the regional dataset work smoothly

Importantly, this update process validated 3RWW and CivicMapper's curation-based approach to data maintenance
for regional sewer network data.

## TEST CASE B: DATA SUBMISSION EVALUATION (SWISSVALE)

Test Case B illustrates how the evaluation criteria would be applied process for a data submission from a provider to support integrating it with the regional network dataset.

###	GOALS

In December 2016, CivicMapper and AECOM coordinated an initial exchange or regional sewer network data in order
to test the Data Evaluation methodology (p. 7). The goal of this test case was to demonstrate how evaluation criteria
could be applied to assess a submission from a single data source maintainer for integration into the regional sewer
network database. The test only involved conducting the evaluation, not integrating the data.

### RESULTS
AECOM received data from Swissvale Borough in response to their request for files showing asset to be included in the Regionalization effort. Swissvale also included data for the entire system of 772 pipes and 646 nodes. This data was analyzed based on several characteristics to determine its fitness for inclusion in the regional network dataset update process. The geometric analysis of the linear features shows good matching with about 10% changes detected for a combination of add, removes and spatial updates. Using a set of key field for pipes and nodes derived from the InfoNET data exchange data dictionary, the analysis shows that most key fields are both available and fairly complete for key fields but the data is lacking in completeness of fields that would provide data confidence, including feature update date fields, feature location method, feature accuracy.

###	LESSONS

The Swissvale data as submitted was not provided in a database with enforced schema and as expected did not match the AECOM/InfoNet data model, which makes an evaluation based on comparison impossible-at least in a way that can be consistently and efficiently performed. This is expected to be the case for most data submissions until some momentum around ongoing data maintenance can be built among data source maintainers.

Two lessons can be learned from this test case:

*	The time spent to load and transform a custom database, clean it up enough for evaluation, and generate custom reporting reflective of the custom data model could also be better spent simply doing the work of the curation/update/integration. Through that process, the documentation of the changes made, along automatic data versioning and metadata generation, can provide the paper trail and rationale needed to support consistent integration of that data source maintainer's datasets in the future-at least until they adopt the regional data model.
*	Long-term, there is a clear need for proactive engagement before, during, and after the curation process, to
help build a case for the the data source maintainers to move to the regional data model-or at the very
least, adopt some of the standards of the data model (e.g., domains for key fields).