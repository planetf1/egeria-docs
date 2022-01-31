<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the Egeria project. -->

# OMRS Metamodel

![Overview of OMRS's metamodel](metadata-meta-model-overview.svg)

OMRS's metamodel defines the structures used to represent metadata, and can be broadly divided into the following two areas:

- Type Definitions (`TypeDef`s and `AttributeTypeDef`s)
- Instances

## Type definitions

`TypeDef`s define the general characteristics that are used to describe any general type -- whether native or not -- and typically fit into one of the following three general types (`TypeDefCategory`):

- `EntityDef`: the definition of a type of entity
- `RelationshipDef`: the definition of a type of relationship
- `ClassificationDef`: the definition of a type of classification

`TypeDef`s are implemented as Java classes in Egeria (those in *italics* are abstract).

![Type definitions](metadata-meta-model-typedef-detail.svg)

??? example "Examples of type definitions"
    For example, the native [open metadata types](./types) that Egeria defines include:

    - a generic [`Referenceable`](./types/0/0010-Base-Model/#referenceable) entity type,
    - a `GlossaryCategory` entity type,
    - a `GlossaryTerm` entity type,
    - (and many others!)

    Rather than being another set of classes that *inherit* from the general TypeDef classes (`EntityDef`, `RelationshipDef`, `ClassificationDef`), these open types are *instantiated objects* of one of those TypeDef classes (in the above examples, of the `EntityDef` class).

    A set of `TypeDefAttribute`s within the TypeDef defines the list of additional characteristics (properties) that each of these entity types can possess -- things like names, descriptions, etc -- which may naturally vary from one entity type to another. (These property-level definitions are `AttributeTypeDef`s.)

    An example of a `RelationshipDef` is the linkage between `GlossaryTerm` and `GlossaryCategory` known as a `TermCategorization`, which is further defined to allow any number of linkages between the two, in either direction. Again, the `TermCategorization` will be an instantiated object of the class `RelationshipDef`, with various properties configured on it to define the endpoints of the relationship.

    An example `ClassificationDef` is `Confidentiality`: that can apply to any `Referenceable` entity (hence including both `GlossaryTerm` and `GlossaryCategory`, as both of these extend the `Referenceable` entity type).

    ![Example type definitions](metadata-meta-model-typedef-examples.svg)

??? example "Example: `Referenceable`"
    For example, `Referenceable` is defined as follows:

    ```java linenums="1"
    final String guid            = "a32316b8-dc8c-48c5-b12b-71c1b2a080bf";
    final String name            = "Referenceable";
    final String description     = "An open metadata entity that has a unique identifier.";
    final String descriptionGUID = null;
    
    // The EntityDef object itself
    EntityDef entityDef = archiveHelper.getDefaultEntityDef(guid,
                                                            name,
                                                            null,
                                                            description,
                                                            descriptionGUID);
    
    List<TypeDefAttribute> properties = new ArrayList<>();
    TypeDefAttribute       property;
    
    final String attribute1Name            = "qualifiedName";
    final String attribute1Description     = "Unique identifier for the entity.";
    final String attribute1DescriptionGUID = null;
    final String attribute2Name            = "additionalProperties";
    final String attribute2Description     = "Additional properties for the element.";
    final String attribute2DescriptionGUID = null;
    
    // The TypeDefAttributes that define the properties of the Referenceable (EntityDef) object
    property = archiveHelper.getStringTypeDefAttribute(attribute1Name,
                                                       attribute1Description,
                                                       attribute1DescriptionGUID);
    property.setUnique(true);
    properties.add(property);
    property = archiveHelper.getMapStringStringTypeDefAttribute(attribute2Name,
                                                                attribute2Description,
                                                                attribute2DescriptionGUID);
    properties.add(property);
    
    entityDef.setPropertiesDefinition(properties);
    ```

    And this results in a JSON structure like the following:

    ```json linenums="1"
    {
      "class": "EntityDef",
      "guid": "a32316b8-dc8c-48c5-b12b-71c1b2a080bf",
      "name": "Referenceable",
      "version": 1,
      "versionName": "1.0",
      "category": "ENTITY_DEF",
      "description": "An open metadata entity that has a unique identifier.",
      "origin": "bce3b0a0-662a-4f87-b8dc-844078a11a6e",
      "createdBy": "ODPi Egeria (OMRS)",
      "createTime": 1516313040008,
      "validInstanceStatusList": [
        "ACTIVE",
        "DELETED"
      ],
      "initialStatus": "ACTIVE",
      "propertiesDefinition": [
        {
          "attributeName": "qualifiedName",
          "attributeType": {
            "class": "PrimitiveDef",
            "version": 1,
            "versionName": "1.0",
            "category": "PRIMITIVE",
            "guid": "b34a64b9-554a-42b1-8f8a-7d5c2339f9c4",
            "name": "string",
            "primitiveDefCategory": "OM_PRIMITIVE_TYPE_STRING"
          },
          "attributeDescription": "Unique identifier for the entity.",
          "valuesMinCount": 0,
          "valuesMaxCount": 1,
          "indexable": true,
          "attributeCardinality": "AT_MOST_ONE",
          "unique": true
        },
        {
          "attributeName": "additionalProperties",
          "attributeType": {
            "class": "CollectionDef",
            "version": 1,
            "versionName": "1.0",
            "category": "COLLECTION",
            "guid": "005c7c14-ac84-4136-beed-959401b041f8",
            "name": "map<string,string>",
            "description": "A map from String to String.",
            "collectionDefCategory": "OM_COLLECTION_MAP",
            "argumentCount": 2,
            "argumentTypes": [
              "OM_PRIMITIVE_TYPE_STRING",
              "OM_PRIMITIVE_TYPE_STRING"
            ]
          },
          "attributeDescription": "Additional properties for the element.",
          "valuesMinCount": 0,
          "valuesMaxCount": 1,
          "indexable": true,
          "attributeCardinality": "AT_MOST_ONE",
          "unique": false
        }
      ]
    }
    ```

## Instances

Instances define individual instantiations of the TypeDefs: for example, individual `GlossaryTerm` entities (like "Address Line 1") or `GlossaryCategory` entities (like "Coco Pharmaceuticals"), `Confidentiality` classifications (like "Sensitive"), etc.

Implemented instances will generally be objects of one of the following classes:

??? question "How are entities modeled? `EntitySummary`, `EntityProxy` and `EntityDetail`"
    Egeria models all entities using a general object -- [`EntitySummary` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/properties/instances/EntitySummary.java){ target=gh } -- from which more detailed representations (like [`EntityDetail` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/properties/instances/EntityDetail.java){ target=gh }) are derived. Note that there is a property called `type` within this object (inherited from [`InstanceAuditHeader` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/properties/instances/InstanceAuditHeader.java){ target=gh }) that defines the specific *type* of metadata the entity represents, rather than having a different type-specific object for every different type of entity.

??? question "How are relationships modeled? `Relationship` and `EntityProxy`"
    Egeria models all relationships using a general object -- [`Relationship` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/properties/instances/Relationship.java){ target=gh } -- which links together exactly two entities (using [`EntityProxy` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/properties/instances/EntityProxy.java){ target=gh }, itself an extension of EntitySummary).

    These `EntityProxy`s act as a sort of "stub" to which the relationship can point, without needing to be aware of the entire set of details of each entity involved in the relationship, and are therefore an important piece of ensuring that relationships are treated as "first-class" objects in their own right.

    As with entities, there is a property called `type` within this `Relationship` object (also inherited from [`InstanceAuditHeader` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/properties/instances/InstanceAuditHeader.java){ target=gh }) that defines the specific *type* of metadata the relationship represents, rather than having a different type-specific object for every different type of relationship.

??? question "How are classifications modeled? `Classification`"
    Egeria models all classifications using a general object -- [`Classification` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/properties/instances/Classification.java){ target=gh } -- any instance of which is possessed by exactly one entity (within the `EntitySummary`'s  `classifications` property).

    As with the other kinds of instances, note that there is a property called `type` within this `Classification` object (also inherited from [`InstanceAuditHeader` :material-github:](https://github.com/odpi/egeria/blob/master/open-metadata-implementation/repository-services/repository-services-apis/src/main/java/org/odpi/openmetadata/repositoryservices/connectors/stores/metadatacollectionstore/properties/instances/InstanceAuditHeader.java){ target=gh }) that defines the specific *type* of metadata the classification represents, rather than having a different type-specific object for every different type of classification.

    Furthermore, note that classifications in Egeria exist only as part of an entity: unlike `EntitySummary` and `Relationship`, they do **not** extend `InstanceHeader` and therefore are not assigned a GUID through which they could be independently retrieved or updated. Classifications are only retrievable or updatable *through* the entity by which they are possessed.

Each of these will typically be further described by an `InstanceProperties` object that instantiates one or more properties used to describe the entity, classification or relationship.

Instances as a concept are implemented as generic Java classes in Egeria (those in *italics* are abstract).

![Instances](metadata-meta-model-instances-detail.svg)

??? example "Examples of instances"
    Like TypeDefs, instances are managed as *instantiated objects* of the classes above (not as new classes that *inherit* from those above).

    For example, to represent an "Address Line 1" `GlossaryTerm`, there can be:

    - an instantiated `EntitySummary` object providing a headline set of information about "Address Line 1" (i.e. its classifications),
    - an instantiated `EntityDetail` object providing the full details of "Address Line 1" (all of its classifications and properties),
    - an instantiated `EntityProxy` object defining the unique properties of "Address Line 1" (i.e. a `qualifiedName` property inherited from `Referenceable` which must be unique across all instances of the object)

    The `InstanceProperties` associated with the `EntityDetail`, `Relationship` and `Classification` objects give the further detail on the object (ie. its name, summary, etc).

    - To represent a "Sensitive Confidentiality" concept that can be used to classify other information (like "Address Line 1"), we could have a "Confidentiality" `Classification` defined with a specific level ("Sensitive") through its `InstanceProperties`
    - To represent the linkage between "Address Line 1" and a specific category location (like "Coco Pharmaceuticals/Terms") we could have a `Relationship` representing the `TermCategorization` with one end pointing to an `EntityProxy` for "Address Line 1" and one end pointing to an `EntityProxy` for "Coco Pharmaceuticals/Terms"

    ![Example instances (using open metadata types)](metadata-meta-model-instances-examples.svg)

??? example "Code example for creating the various types"
    As code, this example could be implemented using something like the following:

    ```java linenums="1"
    // ENTITIES
    
    // Summary-level entity information (see end of CLASSIFICATION section for adding Classifications)
    EntitySummary summary = new EntitySummary();
    summary.setGUID(guid);
    summary.setCreatedBy("...user...");
    summary.setCreateTime(new Date(...));
    summary.setUpdatedBy("...user...");
    summary.setUpdateTime(new Date(...));
    
    // Detailed-level entity information (see end of CLASSIFICATION section for adding Classifications)
    EntityDetail detail = repositoryConnector.getRepositoryHelper().getSkeletonEntity(
            sourceName,
            omrsRepositoryConnector.getMetadataCollectionId(),
            InstanceProvenanceType.LOCAL_COHORT,
            userId,
            "GlossaryTerm"
    );
    
    detail.setStatus(InstanceStatus.ACTIVE);
    detail.setGUID(guid);
    detail.setCreatedBy("...user...");
    detail.setCreateTime(new Date(...));
    detail.setUpdatedBy("...user...");
    detail.setUpdateTime(new Date(...));
    
    InstanceProperties instanceProperties = new InstanceProperties();
    PrimitivePropertyValue propertyValue = new PrimitivePropertyValue();
    PrimitiveDef primitiveDef = new PrimitiveDef();
    primitiveDef.setPrimitiveDefCategory(PrimitiveDefCategory.OM_PRIMITIVE_TYPE_STRING);
    propertyValue.setPrimitiveValue("Address Line 1");
    propertyValue.setPrimitiveDefCategory(primitiveDef.getPrimitiveDefCategory());
    propertyValue.setTypeGUID(primitiveDef.getGUID());
    propertyValue.setTypeName(primitiveDef.getName());
    
    instanceProperties.setProperty("qualifiedName", propertyValue);
    
    propertyValue.setPrimitiveValue("Street and street number");
    instanceProperties.setProperty("summary", propertyValue);
    
    detail.setProperties(instanceProperties);
    
    // CLASSIFICATION
    
    InstanceProperties properties = new InstanceProperties();
    
    // The "Sensitive" level for the classification
    EnumPropertyValue level = new EnumPropertyValue();
    level.setSymbolicName("Sensitive");
    properties.setProperty("level", level);
    
    // Creating a new classification, of "Confidentiality", applying to "Referenceable", with
    // the "Sensitive" level defined above
    Classification classification = omrsRepositoryConnector.getRepositoryHelper().getNewClassification(
            sourceName,
            userId,
            "Confidentiality",
            "Referenceable",
            ClassificationOrigin.ASSIGNED,
            null,
            properties
    );
    
    ArrayList<Classificaton> classifications = new ArrayList<>();
    classifications.add(classification);
    
    // ... adding the Classification(s) to the Entity(Summary|Detail)
    summary.setClassifications(classifications);
    detail.setClassifications(classifications);
    
    // RELATIONSHIP
    
    // Define the qualifiedName property with the unique name for the first end of the relationship
    // (the GlossaryCategory end of the relationship)
    InstanceProperties uniqueProperties1 = new InstanceProperties();
    PrimitivePropertyValue propertyValue = new PrimitivePropertyValue();
    PrimitiveDef primitiveDef = new PrimitiveDef();
    primitiveDef.setPrimitiveDefCategory(PrimitiveDefCategory.OM_PRIMITIVE_TYPE_STRING);
    propertyValue.setPrimitiveValue("Coco Pharmaceuticals/Terms");
    propertyValue.setPrimitiveDefCategory(primitiveDef.getPrimitiveDefCategory());
    propertyValue.setTypeGUID(primitiveDef.getGUID());
    propertyValue.setTypeName(primitiveDef.getName());
    uniqueProperties1.setProperty("qualifiedName", propertyValue);
    
    EntityProxy entityProxy1 = omrsRepositoryConnector.getRepositoryHelper().getNewEntityProxy(
            sourceName,
            omrsRepositoryConnector.getMetadataCollectionId(),
            InstanceProvenanceType.LOCAL_COHORT,
            userId,
            "GlossaryCategory",
            uniqueProperties1,
            null
    );
    
    // Define the qualifiedName property with the unique name of the second end of the relationship
    // (the GlossaryTerm end of the relationship)
    InstanceProperties uniqueProperties2 = new InstanceProperties();
    primitiveDef.setPrimitiveDefCategory(PrimitiveDefCategory.OM_PRIMITIVE_TYPE_STRING);
    propertyValue.setPrimitiveValue("Address Line 1");
    propertyValue.setPrimitiveDefCategory(primitiveDef.getPrimitiveDefCategory());
    propertyValue.setTypeGUID(primitiveDef.getGUID());
    propertyValue.setTypeName(primitiveDef.getName());
    uniqueProperties2.setProperty("qualifiedName", propertyValue);
    
    EntityProxy entityProxy2 = omrsRepositoryConnector.getRepositoryHelper().getNewEntityProxy(
            sourceName,
            omrsRepositoryConnector.getMetadataCollectionId(),
            InstanceProvenanceType.LOCAL_COHORT,
            userId,
            "GlossaryTerm",
            uniqueProperties2,
            null
    );
    
    // Define the relationship between the two EntityProxy objects instantiated above
    Relationship omrsRelationship = new Relationship();
    InstanceProperties relationshipProperties = new InstanceProperties();
    PrimitivePropertyValue relationProperty = new PrimitivePropertyValue();
    
    relationProperty.setTypeGUID("...");
    relationProperty.setTypeName("???");
    relationshipProperties.setProperty("TermCategorization", relationProperty);
    omrsRelationship.setProperties(relationshipProperties);
    omrsRelationship.setEntityOneProxy(entityProxy1);
    omrsRelationship.setEntityTwoProxy(entityProxy2);
    omrsRelationship.setGUID("...");
    ```

--8<-- "snippets/abbr.md"
