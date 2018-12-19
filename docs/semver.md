# **Semantic Versioning for the Sewer Atlas **

Since beginning the quarterly update cycle in 2017Q2, we've used a [*semantic versioning* ("SemVer")](https://semver.org/) approach for tagging each data release&mdash;e.g., *v6.1.0*  for 2018-Q1.

SemVer was originally developed for software versioning as a way to indicate major, minor, and patch changes to software. With the Sewer Atlas, we use it o indicate the nature of changes to both the schema and the data itself.

## The SemVer Concept

The [Semantic Versioning](https://semver.org/) website provides a quick summary:

> Given a version number MAJOR.MINOR.PATCH, increment the:

> * MAJOR version when you make incompatible API changes,
> * MINOR version when you add functionality in a backwards-compatible manner, and
> * PATCH version when you make backwards-compatible bug fixes.

> Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

## SemVer as adapted for Sewer Atlas data versioning

In the context of a *data* versioning, we've adapted to concept of Semver to mean the following

### *MAJOR version*: when the database schema changes

> e.g. **6**.2.1

If the change requires a database migration, it's a major version change.

Most likely, software utilizing the database will need to be adjusted to handle the different data schema (e.g., ensuring that a web map is using the correct column in the table for renderning a label).

### *MINOR version*: when records in the database are added/updated

> e.g. 6.**2**.1

Planned changes to signifcant portions of records in the database, as is done in quarterly release cycles, represent MINOR version changes.

Software utilizing the database should continue to function as it would; no changes to schema occur in a MINOR version change.

### *PATCH version*: when edits are needed to address a problem with the data

> e.g. 6.2.**1**

Problems with the data that cannot wait for a quarterly release cycle are addressed with patch changes. The types of problems addressed with a *PATCH* version might include:

* fixing issues with geometric network connectivity (i.e., the topology of pipe network was not maintained in error, and needs to be fixed for tracing to work);
* incorporating timely changes to specific locations of interest to 3RWW partners between releases

The semi-automated QAQC process during the quarterly release cycle (typically MINOR version changes) largely lets us identify problems between releases, which is why these types of versions are rare.

## SemVer and Year-Quarter release tagging

We label releases with a Year-Quarter tag following a `YYYY-Q*n*` pattern, e.g., 2018-Q1.

How does this differ from SemVer, and why do we do both?

* The quarterly release tag merely indicates *when* updated data will be or was released
* SemVer indicates the *nature of the changes* since the last version at a high level

## Epilogue

Our use of SemVer for tagging database releases is largely experimental.

Our eventual goal is evolve the "standard" conveyed above into our editing post-processing toolchain, such that we can qualify changes in a semi-automated way.

For now, our use of SemVer within the context of database editing is a largely qualitative effort.