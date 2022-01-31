<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the ODPi Egeria project. -->

# Governance Service

A governance service is a specialized [connector](./concepts/connector) that implements a specific [type of governance action](./concepts/governance-action).

--8<-- "docs/concepts/governance-service-types.md"

## Catalog of governance services

* [Open Discovery Service Catalog](./connectors/#open-discovery-services)
* [Governance Action Service Catalog](./connectors/#governance-action-services)
* [Archive Service Catalog](./connectors/#archive-services)

## Implementing your own governance services

Instructions for implementing your own governance services are in the developer guide under the following sections: 

* [Writing Open Discovery Services](./guides/developer/open-dicovery-services/overview)
* [Writing Governance Action Services](./guides/developer/governance-action-services/overview)
* [Writing Archive Services](./guides/developer/archive-services/overview)

## Support for running governance services

The [Governance Engine OMAS](./services/omas/governance-engine/overview) provides:

* The API to create [governance engine definitions](./concepts/governance-engine) for the governance services.
* The API to link governance services together into [governance action processes](./concepts/governance-action-process).
* The metadata support for the [Engine Host Services](./services/engine-host-services) to drive the governance services in an [Engine Host](./concepts/engine-host) OMAG Server.


--8<-- "snippets/abbr.md"