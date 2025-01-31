<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the ODPi Egeria project. -->

# Delete processes

Delete a Process, with the associated port implementations, port aliases and lineage mappings.
For each port, it will delete the associated schema type and columns.

Check [delete-port-implementation](delete-port-implementation.md) and [delete-schema-types](delete-schema-type.md) 
for examples of the more granular payloads.

More examples can be found in the
[sample collection](samples/collections/DataEngine-process_endpoints.postman_collection.json)
```
DELETE {serverURLRoot}/servers/{serverName}/open-metadata/access-services/data-engine/users/{userId}/processes

{
    "qualifiedName": "(process)=CopyColumsFlow::(process)=CopyColumns",
    "guid": "processGUID",
    "externalSourceName": "(organization)=Company::(project)=ExternalDataPlatform"
}
```

`externalSourceName` - qualifiedName of the external data engine tool.<br>
`guid` - optional property describing the unique identifier of the process to be deleted
`qualifiedName` - optional property describing the qualifiedName of the process to be deleted<br>
Note that you must provide either the qualifiedName or the guid of the port implementation <br>
`VoidRespone` - void response with status and error message if failing

---8<-- "snippets/abbr.md"








