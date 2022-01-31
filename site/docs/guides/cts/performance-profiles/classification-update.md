---
hide:
- toc
---

<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the Egeria project. -->

# Classification Update Profile

The performance of programmatically updating existing classifications.

The [Open Metadata Repository Services (OMRS)](./services/omrs) interface for a metadata repository defines optional methods for updating classifications:

| Method | Description |
|---|---|
| `updateEntityClassification` | changes one or more values of the properties on an existing classification |

???+ assertion "Assertions"
    | ID | Description |
    |---|---|
    | `repository-classification-update-performance-updateEntityClassification` | See (2) in detailed logic below. |

For every classification type supported by the technology under test, this profile does the following (in order):

1. Searches for `instancesPerType` entities with that classification. (This uses `findEntitiesByClassification` with a condition on the classification's name only and its performance is recorded as part of the [classification search](classification-search.md) profile.)
1. For each of these entity instances, `updateEntityClassification` is called to update the existing property values of the classification, using a new generated set of properties.

!!! example "Example"
    So, for example, if the technology under test supports 50 classification types, and the `instancesPerType` parameter is set to 100, then this profile will update 50 (types) x 100 (instances per type) = 5000 classifications. (And it will run `findEntitiesByClassification` 50 times.)

The properties of each of these instances will be fully-populated with:

- Any string properties containing a value representative of the property name itself (and where unique, they will be made unique through appending a unique sequence)
- Any non-string properties will be randomly generated, in a simple attempt to represent data that is not entirely uniform

!!! attention "Caveats"
    Note the following caveats:

    - Classification type definitions that have no properties will not be updated, since there are no properties to update.

--8<-- "snippets/abbr.md"
