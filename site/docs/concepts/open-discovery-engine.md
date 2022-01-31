---
hide:
- toc
---

<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the ODPi Egeria project. -->

# Open Discovery Engines

An *open discovery engine* describes a set of related [open discovery services](./guides/developer/open-discovery-services/overview). Each open discovery service implements a specific type of analysis.  This analysis is looking into the content of a [digital resource](./concepts/resource) and storing its findings in annotations within a [discovery analysis report](./concepts/discovery-analysis-report) that is linked of the resource's [Asset](./concepts/asset) in the metadata repository.

An open discovery engine is hosted in the [Asset Analysis Open Metadata Engine Service (OMES)](./services/omes/asset-analysis/overview) running on one or more [Engine Host OMAG Servers](./concepts/engine-host).

When an open discovery engine is called, it is passed a governance request type and request parameters. This is mapped to a call to an open discovery service through the [open discovery engine definition](./concepts/governance-engine-definition).

![Open Discovery Engine Definition Structure](./guides/developer/open-metadata-archives/open-discovery-engine-definition.svg)
> Logical structure of an open discovery engine definition showing how the governance request types map to the open discovery service definitions

??? education "Further information"

    The Open Metadata Types used to define the open discovery engines are located in [model 0601 Open Discovery Engines](./types/6/0601-Open-Discovery-Engine).


---8<-- "snippets/abbr.md"