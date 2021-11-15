<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the Egeria project. -->

# Metadata Sharing Profile

The functionality necessary to share metadata with other members of the cohort.

## Cohort registration

The technology under test is able to register with a cohort.

???+ assertion "Assertions"
    | ID | Description |
    |---|---|
    | [`repository-server-ids-01` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/connector/TestRepositoryServerIds.java){ target=gh } | Repository connector can be retrieved from cohort registration. | 

## Repository connector

The technology under test provides a connection to a valid repository connector.

???+ assertion "Assertions"
    | ID | Description |
    |---|---|
    | [`repository-test-case-base-01` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/RepositoryConformanceTestCase.java){ target=gh } | Repository connector supplied to conformance suite. |
    | [`repository-server-ids-02` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/connector/TestRepositoryServerIds.java){ target=gh } | Retrieved helper object for building TypeDefs and metadata instances from repository connector. |
    | [`repository-server-ids-03` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/connector/TestRepositoryServerIds.java){ target=gh } | Retrieved validator object to check the validity of TypeDefs and metadata instances from repository connector. |
    | [`repository-server-ids-04` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/connector/TestRepositoryServerIds.java){ target=gh } | Retrieved correct local user Id from repository connector. |
    | [`repository-server-ids-05` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/connector/TestRepositoryServerIds.java){ target=gh } | Retrieved correct max page size from repository connector. |

## Metadata collection id

The technology under test broadcasts a unique metadata collection identifier.

???+ assertion "Assertions"
    | ID | Description |
    |---|---|
    | [`repository-metadata-collection-01` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/connector/TestMetadataCollectionId.java){ target=gh } | Metadata collection id retrieved from cohort registration. |
    | [`repository-metadata-collection-02` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/connector/TestMetadataCollectionId.java){ target=gh } | Metadata collection id retrieved from cohort repository connector. |
    | [`repository-metadata-collection-03` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/connector/TestMetadataCollectionId.java){ target=gh } | Metadata collection id retrieved from cohort repository connector's metadata collection. |
    | [`repository-metadata-collection-04` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/connector/TestMetadataCollectionId.java){ target=gh } | Metadata collection id retrieved from cohort repository connector matches registration. |
    | [`repository-metadata-collection-05` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/connector/TestMetadataCollectionId.java){ target=gh } | Metadata collection id retrieved from cohort repository connector's metadata collection matches registration. |

## Supported type queries

The technology under test is able to respond appropriately to queries about its supported types.

???+ assertion "Assertions"
    | ID | Description |
    |---|---|
    | [`repository-find-attribute-typedefs-by-category-01` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestFindTypeDefsByCategory.java){ target=gh } | All attribute type definitions returned by category. This tests the [`findAttributeTypeDefsByCategory` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-find-types-by-external-standard-identifiers-01` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestFindTypeDefByExternalId.java){ target=gh } | All type definitions returned for external standard name `<name>`. This tests the [`findTypesByExternalID` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-find-types-by-external-standard-identifiers-02` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestFindTypeDefByExternalId.java){ target=gh } | All type definitions returned for external standard organization name `<name>`. This tests the [`findTypesByExternalID` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-find-types-by-external-standard-identifiers-03` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestFindTypeDefByExternalId.java){ target=gh } | All type definitions returned for external standard type name `<name>`. This tests the [`findTypesByExternalID` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-find-typedefs-by-category-01` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestFindTypeDefByExternalId.java){ target=gh } | All type definitions returned by category. This tests the [`findTypeDefsByCategory` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-get-typedef-gallery-01` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestGetTypeDefGallery.java){ target=gh } | TypeDefGallery retrieved. This tests the [`getAllTypes` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |

## Supported type notifications

The technology under test is able to send out notifications for its supported types.

???+ assertion "Assertions"
    | ID | Description |
    |---|---|
    | [`repository-consistency-of-attribute-typedef-01` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestConsistentAttributeTypeDef.java){ target=gh } | `<attributeTypeDefName>` attribute type definition from event is consistent with API. This tests the [`getAttributeTypeDefByGUID` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-consistency-of-typedef-01` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestConsistentTypeDef.java){ target=gh } | `<typeDefName>` type definition from event is consistent with API. This tests the [`getTypeDefByGUID` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-type-definition-event-01` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestValidTypeDefEvent.java){ target=gh } | Event is not null. |
    | [`repository-type-definition-event-02` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestValidTypeDefEvent.java){ target=gh } | Event timestamp is present. |
    | [`repository-type-definition-event-03` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestValidTypeDefEvent.java){ target=gh } | Event type is valid. |
    | [`repository-type-definition-event-04` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestValidTypeDefEvent.java){ target=gh } | Event originator is set. |
    | [`repository-type-definition-event-05` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestValidTypeDefEvent.java){ target=gh } | Metadata collection id is set. |
    | [`repository-type-definition-event-06` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestValidTypeDefEvent.java){ target=gh } | Metadata collection id matches technology under test. |
    | [`repository-type-definition-event-07` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestValidTypeDefEvent.java){ target=gh } | Server name is set. |
    | [`repository-type-definition-event-08` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestValidTypeDefEvent.java){ target=gh } | Server name matches technology under test. |
    | [`repository-type-definition-event-09` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestValidTypeDefEvent.java){ target=gh } | TypeDef supplied for TypeDef event. |
    | [`repository-type-definition-event-10` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestValidTypeDefEvent.java){ target=gh } | AttributeTypeDef null for TypeDef event. |
    | [`repository-type-definition-event-11` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestValidTypeDefEvent.java){ target=gh } | AttributeTypeDef supplied for AttributeTypeDef event. |
    | [`repository-type-definition-event-12` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestValidTypeDefEvent.java){ target=gh } | TypeDef null for AttributeTypeDef event. |
    | [`repository-type-definition-event-13` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/types/TestValidTypeDefEvent.java){ target=gh } | TypeDefPatch supplied for update event. |

## Consistent types

The technology under test supports entity, relationship and classification types that link together.

???+ assertion "Assertions"
    | ID | Description |
    |---|---|
    | [`repository-classification-entities-01` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestClassificationHasSupportedEntities.java){ target=gh } | `<classificationName>` classification can attach to at least one supported entity. |
    | [`repository-classification-entities-02` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestClassificationHasSupportedEntities.java){ target=gh } | `<classificationName>` supported for classification. |
    | [`repository-graph-queries-00` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestGraphQueries.java){ target=gh } | `<typeName>` relationship type matches the known type. |
    | [`repository-entity-reference-copy-lifecycle-00` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedEntityReferenceCopyLifecycle.java){ target=gh } | `<typeName>` entity type definition matches known type |
    | [`repository-entity-property-search-01` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedEntitySearch.java){ target=gh } | `<typeName>` entity type matches the known type from the repository helper. |
    | [`repository-relationship-lifecycle-00` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedRelationshipLifecycle.java){ target=gh } | `<typeName>` relationship type definition matches known type |
    | [`repository-relationship-reference-copy-lifecycle-00` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedRelationshipReferenceCopyLifecycle.java){ target=gh } | `<typeName>` relationship type definition matches known type |
    | [`repository-relationship-reidentify-00` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedRelationshipReidentify.java){ target=gh } | `<typeName>` relationship type definition matches known type |
    | [`repository-relationship-property-search-01` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedRelationshipSearch.java){ target=gh } | `<typeName>` relationship type matches the known type from the repository helper. |

## Metadata instance access

The technology under test supports the retrieval of the current state of specific metadata instances from its repository.

???+ assertion "Assertions"
    | ID | Description |
    |---|---|
    | [`repository-entity-lifecycle-09` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedEntityLifecycle.java){ target=gh } | `<typeName>` new entity is known. This tests the [`isEntityKnown` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-entity-lifecycle-10` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedEntityLifecycle.java){ target=gh } | `<typeName>` new entity summarized. This tests the [`getEntitySummary` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-entity-lifecycle-11` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedEntityLifecycle.java){ target=gh } | `<typeName>` new entity retrieved. This tests the [`getEntityDetail` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-entity-reference-copy-lifecycle-02` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedEntityReferenceCopyLifecycle.java){ target=gh } | `<typeName>` reference entity can be retrieved as EntitySummary. This tests the [`getEntitySummary` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-entity-reference-copy-lifecycle-03` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedEntityReferenceCopyLifecycle.java){ target=gh } | `<typeName>` reference entity can be retrieved as EntityDetail. This tests the [`getEntityDetail` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-relationship-lifecycle-09` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedRelationshipLifecycle.java){ target=gh } | `<typeName>` new relationship is known. This tests the [`isRelationshipKnown` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-relationship-lifecycle-10` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedRelationshipLifecycle.java){ target=gh } | `<typeName>` new relationship retrieved. This tests the [`getRelationship` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |

## Instance notifications

The technology under test sends out events when metadata changes in its repository.

!!! attention "Not yet implemented"

## Instance versioning

The technology under test supports incrementing version numbers within metadata instances as they change.

???+ assertion "Assertions"
    | ID | Description |
    |---|---|
    | [`repository-entity-lifecycle-08` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedEntityLifecycle.java){ target=gh } | `<typeName>` new entity has version greater than zero. This tests the [`addEntity` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-entity-lifecycle-15` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedEntityLifecycle.java){ target=gh } | `<typeName>` entity with new status version number is `<nextVersion>`. This tests the [`updateEntityStatus` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-entity-lifecycle-18` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedEntityLifecycle.java){ target=gh } | `<typeName>` entity with min properties version number is `<nextVersion>`. This tests the [`updateEntityProperties` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-entity-lifecycle-21` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedEntityLifecycle.java){ target=gh } | `<typeName>` entity deleted version number is `<nextVersion>`. This tests the [`deleteEntity` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-entity-lifecycle-08` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedRelationshipLifecycle.java){ target=gh } | `<typeName>` new relationship has version greater than zero. This tests the [`addRelationship` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-entity-lifecycle-13` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedRelationshipLifecycle.java){ target=gh } | `<typeName>` relationship with new status version number is `<nextVersion>`. This tests the [`updateRelationshipStatus` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-entity-lifecycle-16` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedRelationshipLifecycle.java){ target=gh } | `<typeName>` relationship with min properties version number is `<nextVersion>`. This tests the [`updateRelationshipProperties` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |
    | [`repository-entity-lifecycle-19` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-conformance-suite/open-metadata-conformance-suite-server/src/main/java/org/odpi/openmetadata/conformance/tests/repository/instances/TestSupportedRelationshipLifecycle.java){ target=gh } | `<typeName>` relationship deleted version number is `<nextVersion>`. This tests the [`deleteRelationship` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/OMRSMetadataCollection.java){ target=gh } method of the `OMRSMetadataCollection` interface. |

## Type enforcement

The technology under test ensures metadata instances conform to their type definition.

!!! attention "Not yet implemented"

## Unsupported type errors

The technology under test will not create metadata instances for unsupported types.

!!! attention "Not yet implemented"

## Type conflict management

The technology under test receives/handles and sends type conflict events when type errors are detected.

!!! attention "Not yet implemented"

--8<-- "snippets/abbr.md"