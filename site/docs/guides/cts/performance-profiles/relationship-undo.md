---
hide:
- toc
---

<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the Egeria project. -->

# Relationship Undo Profile

The performance of programmatically reversing the latest update to an existing relationship instance.

The [Open Metadata Repository Services (OMRS)](./services/omrs) interface for a metadata repository defines an optional method for reverting updates on relationship instances:

| Method | Description |
|---|---|
| `undoRelationshipUpdate` | reverts the last update that was made to a relationship |

???+ assertion "Assertions"
    | ID | Description |
    |---|---|
    | `repository-relationship-undo-performance-undoRelationshipUpdate` | See (2) in detailed logic below. |

For every relationship type supported by the technology under test, this profile does the following (in order):

1. Searches for `instancesPerType` relationships of that type that have at least one change. (This uses `findRelationships` with a condition on both `metadataCollectionId` and `version` being greater than `1`, and its performance is recorded as part of the [relationship search](relationship-search.md) profile.)
1. For each of these relationship instances, `undoRelationshipUpdate` is called to revert the last change.

!!! example "Example"
    So, for example, if the technology under test supports 50 relationship types, and the `instancesPerType` parameter is set to 100, then this profile will update 50 (types) x 100 (instances per type) = 5000 relationships. (And it will run `findRelationships` 50 times.)

!!! attention "Caveats"
    Note the following caveats:

    - Relationship type definitions that have no properties will not be reverted: since there are no properties to update, there will not have been any updated version (and thus nothing to revert).

--8<-- "snippets/abbr.md"
