<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the ODPi Egeria project. -->

# Discovery Engine

A discovery engine is the execution environment for special types of connectors called
[discovery services](./concepts/open-discovery-service).
Each discovery service implements a specific type of analysis.  This analysis is looking
into the content of the physical real-world counterpart of an Asset in the metadata repository.
The result of its analysis is stored as [Annotations](discovery-annotation.md)
and linked off of the asset's description in the metadata repository.

The discovery engine configuration defines a set of discovery services.  Its definition is stored in
an open metadata repository and maintained through the
[Discovery Engine OMAS's configuration API](./services/omas/discovery-engine/overview).

Discovery engines are hosted in [discovery servers](discovery-server.md).
Discovery servers are deployed close to the physical assets they are analysing.
They connect to the [Discovery Engine OMAS](./services/omas/discovery-engine/overview)
running in a metadata server
to provide metadata about assets and to
store the results of the discovery service's analysis.

## Further reading

Egeria's implementation of the discovery engine is provided by the
[Asset Analysis Open Metadata Engine Service (OMES)](./services/omes/asset-analysis/overview).


---8<-- "snippets/abbr.md"