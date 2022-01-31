---
hide:
- toc
---

<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the ODPi Egeria project 2020. -->

--8<-- "snippets/content-status/released.md"

# OCF Metadata Management

OCF metadata management provides common services for
[Open Metadata Access Services (OMASs)](./services/omas) that are supporting [Open Connector Framework (OCF)](./frameworks/ocf/overview) connectors to [digital resources](./concepts/resource).  These resources are catalogued in open metadata as [Assets](./concepts/asset).

## Client-side support for connectors

OCF metadata management provides a common base class for OMAS clients that supports the retrieval of [Connection](./concepts/connection) objects from the open metadata repositories and the creation of OCF connector instances.  It is used by:

- [Asset Consumer OMAS](./services/omas/asset-consumer/overview)
- [Asset Owner OMAS](./services/omas/asset-owner/overview)
- [Data Engine OMAS](./services/omas/discovery-engine/overview)

## Connected Asset Services

An OCF connector supports a method called [`getConnectedAssetProperties`](./concepts/connected-asset-properties).  It is intended to return metadata about its resource.  By default this method returns null because it needs to be configured with the location of the metadata repositor(y/ies) it is to call. If the connector is created by one of the OMAS clients listed above, this method is configured to retrieve metadata from the same open metadata repository as the OMAS.  This metadata includes details of the structure, origin, meaning and governance requirements associated with the resource.


--8<-- "snippets/abbr.md"
