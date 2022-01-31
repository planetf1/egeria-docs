<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the Egeria project. -->

# OMAG Server Platform

The OMAG Server Platform provides a runtime process and platform for four broad groups of services:

- **Server origin service** - used to determine the type and level of the OMAG Server Platform.
- **Platform services** - used to determine the servers and their services running on the platform.
- **Administration services** - used to configure and manage the [OMAG Servers](./concepts/omag-server) running inside the OMAG Server Platform.
- **Open Metadata and Governance (OMAG) services** - used to work with metadata and govern the assets of an organization.

The OMAG services are configured and activated in [OMAG Servers](./concepts/omag-server) using the [administration services](./guides/admin/guide). The configuration operations of the admin services create [configuration documents](./concepts/configuration-document), one for each OMAG Server. Inside a configuration document is the definition of which OMAG services to activate in the server. These include the [Open Metadata Repository Services (OMRS)](./services/omrs) (any type of server), the [Open Metadata Access Services (OMASs)](./services/omas) (for metadata access servers), [Open Metadata Engine Services (OMESs)](./services/omes) (for engine host servers) , [Open Metadata Integration Services (OMISs)](./services/omis) (for integration daemon servers) and [Open Metadata View Services (OMVSs)](./services/omvs) (for view servers).

Once a configuration document is defined, the OMAG Server can be started and stopped multiple times by the admin services server instance operations.

The OMAG Server Platform also supports some [platform services](./services/platform-services) to query details of the servers running on the platform.

The OMAG Server Platform can also host multiple OMAG Servers at any one time:

![OMAG Server deployment choices](egeria-operations-server-choices-no-description.svg)

The choices are as follows:

- **A** - Each OMAG Server has its own dedicated OMAG Server Platform - useful when only one server is needed in a deployment environment, or there is a desire to keep each server isolated in its own stack.
- **B** - Multiple OMAG Servers are hosted on the same OMAG Server Platform. The OMAG Server Platform routes inbound requests to the right server based on the server name specified in the request URL. The servers may all be of the same type (multi-tenant operation) or be a set of collaborating servers of different types consolidated onto the same platform.
- **C** - Multiple copies of same server instance running on different platforms to provide high availability and distribution of workload (horizontal scalability).

Each OMAG Server is isolated within the server platform and so the OMAG Server platform can be used to support [multi-tenant :material-dock-window:](https://en.wikipedia.org/wiki/Multitenancy){ target=wikipedia } operation for a cloud service, or host a variety of different OMAG Servers needed at a particular location.

??? education "Further reading"

    - [Configuring the OMAG Server Platform](./guides/admin/configuring-the-omag-server-platform)
    - [Installing the OMAG Server Platform Tutorial](./education/tutorials/building-egeria-tutorial/task-installing-egeria)
    - [Running the OMAG Server Platform Tutorial](./education/tutorials/omag-server-tutorial/overview)

## Inside the OMAG Server platform

The **OMAG Server Platform** provides the server environment for running open metadata
and governance services.  It hosts one or more **[OMAG Servers](./concepts/omag-server)**.  Each server is configured to support specific
open metadata and governance services.  Thus each server performance a specific role in an deployment landscape.

The OMAG Server platform is included in the [Egeria Distribution TAR file](https://github.com/odpi/egeria/tree/master/open-metadata-distribution/open-metadata-assemblies)
which can be installed on your machine by following the [Installing Egeria Tutorial](./education/tutorials/building-egeria-tutorial/task-installing-egeria).

The OMAG Server platform supports four broad groups of services:

* **Server Origin Service** - used to determine the type and level of the OMAG Server platform.
* **Platform Services** - used to determine the servers and their services running on the platform.
* **Administration Services** - used to configure and manage the OMAG Servers running inside the OMAG Server platform.
* **Open Metadata and Governance Services** - used to work with metadata and govern the assets of an organization.

Figure 1 shows the OMAG Server platform when it first starts up.

![Figure 1](omag-server-platform-start-up.svg)
> Figure 1: OMAG Server Platform at start up

The server origin service  is operational at this point.  It can be used by operational scripts to determine if the 
OMAG Server platform is still running.

The administration services are active at this point, while the open metadata and governance services
will return an error if called since there are no [OMAG Servers](./concepts/omag-server) running.

The configuration services are used to create [configuration documents](./concepts/configuration-document).  Each configuration document
describes the open metadata and governance services that should be activated in a OMAG Server.

Figure 2 shows the configuration services creating three configuration documents:

* one for the `cdoMetadataRepository` OMAG Server
* one for the `stewardshipServer` OMAG Server
* one for the `dataLakeDiscoveryEngine` OMAG Server

![Figure 2](omag-server-platform-configure.svg)
> Figure 2: Creating configuration documents for OMAG Servers

The [Administration Guide](./guides/admin/guide)
provides detailed instructions on creating configuration documents.

Once a configuration document for an OMAG Server is used by
the operational services initialize the requested services in the OMAG Server.
The OMAG Server can be started in any OMAG Server platform.
It does not have to be the same OMAG Server platform that created the configuration document.

Figure 3 shows an OMAG Server platform with the **cdoMetadataRepository** local OMAG Server
running.

![Figure 3](omag-server-platform-initialize-logical-omag-server.svg)
> Figure 3: Starting a OMAG Server through the operational services

Once the OMAG Server has initialized successfully, the open metadata and governance services
can route requests to it.

An OMAG Server platform can run multiple OMAG Servers at one time.  Figure 4 shows an OMAG Server platform
running multiple servers.

![Figure 4](omag-server-platform-overview.svg)
> Figure 4: An OMAG Server platform running multiple OMAG Servers



--8<-- "snippets/abbr.md"
