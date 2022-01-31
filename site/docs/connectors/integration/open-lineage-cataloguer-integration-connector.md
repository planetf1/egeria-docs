<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the ODPi Egeria project. -->

# Open Lineage Cataloguer Integration Connector

??? info "Connector details"
    - Connector Category: [Integration Connector](./connectors/integration-connector)
    - Hosting Service: [Lineage Integrator OMIS](./services/omis/lineage-integrator)
    - Hosting Server: [Integration Daemon](./concepts/integration-daemon)
    - Source Module: [lineage-integration-connectors :material-github:](https://github.com/odpi/egeria/tree/master/open-metadata-implementation/adapters/open-connectors/integration-connectors/lineage-integration-connectors){ target=gh }
    - Jar File Name: `lineage-integration-connectors.jar`

## Overview

The OpenLineage Cataloguer integration connector registers an OpenLineage listener with the Lineage Integrator OMIS and catalogues any processes described in the OpenLineage events it received that are not already known to the open metadata ecosystem.

![Figure 1](open-lineage-cataloguer-integration-connector.svg)
> **Figure 1:** Operation of the OpenLineage cataloguer integration connector


## Configuration

This connector uses the [Lineage Integrator OMIS](./services/omis/lineage-integrator/overview)
running in the [Integration Daemon](./concepts/integration-daemon).

This is its connection definition to use on the [administration commands that configure the API Integrator OMIS](./guides/admin//servers/configuring-an-integration-daemon/#configure-the-integration-services).

!!! example "Connection configuration"
    ```json linenums="1" hl_lines="14"
    {
       "connection" : 
                    { 
                        "class" : "Connection",
                        "qualifiedName" : "Egeria:IntegrationConnector:Lineage:OpenLineageCataloguer Connection",
                        "connectorType" : 
                        {
                            "class" : "ConnectorType",
                            "connectorProviderClassName" : "org.odpi.openmetadata.adapters.connectors.integration.lineage.OpenLineageCataloguerIntegrationProvider"
                        }
                    }
    }
    ```

---8<-- "snippets/abbr.md"