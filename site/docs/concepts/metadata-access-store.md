---
hide:
- toc
---

<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the Egeria project 2020. -->

# Metadata access store

A *metadata access store* is an [OMAG Server](./concepts/omag-server) that hosts a metadata repository with native support for open metadata types and instances. It is able to be a [member of a cohort](./concepts/cohort-member) and so can exchange metadata with other members of the cohort.  It is important to have at least one metadata access store in each cohort in order to support all types of metadata.

![Metadata access store in the open metadata ecosystem](metadata-access-store.svg)

Similar to the [metadata access point](./concepts/metadata-access-point), the metadata access store typically has the [access services](./services/omas) configured. 

--8<-- "snippets/abbr.md"
