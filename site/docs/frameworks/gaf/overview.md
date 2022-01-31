<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the Egeria project. -->

--8<-- "snippets/content-status/tech-preview.md"

# Governance Action Framework (GAF)
  
The *governance action framework (GAF)* provides the interfaces and base implementations for components (called [governance action services](#governance-action-services)) that take action to:

- detect, report and eventually correct a situation that is harmful to the data or the organization in some way or 
- to enhance the metadata to improve its use.

The governance action framework can be used for three purposes:

- Provide the complete implementation and orchestration of a governance process.
- Provide coordination between processes run by specialized governance systems. For example, coordinating a DevOps pipeline with a data movement and quality process and security incident management.
- Provide contextual metadata plus an audit trail of actions managed by an external governance process.

## Governance action

A *governance action* describes a specific governance activity that needs to be performed on one or more metadata elements, or their counterparts in the digital landscape.

A [governance action is represented as a metadata entity](./types/4/0463-Governance-Actions/#governanceaction) in the open metadata repositories and linked to:

- The source (cause) of the governance action.
- The target elements that need to be acted upon.
- The [governance engine](./concepts/governance-engine) that will run the [governance service](./concepts/governance-service) that implements the desired behavior.

The `GovernanceAction` metadata entity is used to coordinate the desired activity in the governance engine, record its current state and act as a record of the activity for future audits.

Governance actions can be created through the [Governance Engine OMAS](./services/omas/governance-engine/overview). Some governance services (for example, the [watchdog governance action service](#watchdog-governance-service)) can create governance actions when they run.

Governance services produce output strings called [*guards*](#guard) that indicate specific conditions or outcomes. These guards can be used to trigger new governance actions. Triggered governance actions are linked to their predecessor so it possible to trace through the governance actions that ran.

The [governance action process](#governance-action-process) defines the flow of governance actions. It uses [governance action types](#governance-action-type) to build up a template of possible governance actions linked via the guards. When the process runs, its linked governance action types control the triggering of new governance actions.

If the start date of the governance action is in the future, the [engine host services](./services/engine-host-services) running in the same [engine host](./concepts/engine-host) as the nominated governance engine will schedule the governance service to run soon after the requested start date. If the start date is left blank, the requested governance service is run as soon as possible.

### Governance action process

A *governance action process* defines a prescribed sequence of [governance actions](#governance-action). Its definition consists of a linked set of [governance action types](#governance-action-type). Each governance action type describes which [governance action service](#governance-action-services) to run from which [governance action engine](#configuring-governance-action-services) along with the *request type* and *request parameters* to pass. The linkage between the governance action types shows the [guards](#guard) that must be true to initiate the next governance action in the flow.

- The [0461 governance action engines](./types/4/0461-Governance-Engines) model shows how the request type links the governance action engine to the governance action service via the `SupportedGovernanceActionService` relationship.
- The [0470 incident reporting](./types/4/0470-Incident-Reporting) model shows the structure of the incident report. It is a [Referenceable](./types/0/0010-Base-Model/#referenceable) so it can support comments and have [governance actions](#governance-action) linked to it.

!!! education "Further information"
    - Governance action processes are defined using the [Governance Engine OMAS](./services/omas/governance-engine/overview).
    - The [Open Metadata Engine Services (OMES)](./services/omes) provide the mechanisms that support the different types of [governance action engines](#configuring-governance-action-services). These engines run the [governance action services](#governance-action-services) that execute the [governance actions](#governance-action) defined by the governance action process.

### Governance action type

A *governance action type* is a template for a [governance action](#governance-action). A set of linked governance action types form the definition of a governance action process.

Governance action types are defined through the [Governance Engine OMAS](./services/omas/governance-engine/overview) and this OMAS also coordinates the creation of a governance action from the governance action type as part of its execution of the governance action process.

The governance action type is defined in the [0462 governance action type](./types/4/0462-Governance-Action-Types) model.

## Guard

*Guards* are labels that are created by [governance action services](#governance-action-services) and are used by the [Governance Engine OMAS](./services/omas/governance-engine/overview) to determine which governance action service to run next.

## Incident report

An *incident report* describes a situation that is out of line with the governance definitions (such as policies and rules). It provides a focus point to coordinate efforts to resolve the situation.

As the incident is handled, details of the cause, affected resources and actions taken are attached to the incident report to create a complete record of the incident for future analysis.

Incident reports are typically created by [governance watchdog services](#watchdog-governance-service).

The [0470 incident reporting](./types/4/0470-Incident-Reporting) model shows the structure of the incident report. It is a [`Referenceable`](./types/0/0010-Base-Model/#referenceable) so it can support comments and linked classifications and tags.

## Governance action services

A *governance action service* is a specialized [connector](./concepts/connector) that performs monitoring of metadata changes, validation of metadata, triage of issues, assessment and/or remediation activities on request.

There are five types of governance action services, each of which supports a specialist governance activity (see subsections).

These are often used in conjunction with the [open discovery services](./concepts/open-discovery-service) from the [Open Discovery Framework (ODF)](./frameworks/odf/overview). Collectively they are called the *governance services* and they can be linked together into [governance action processes](#governance-action-process).

Some governance action services invoke functions in external engines that are working with data and related assets. The GAF offers embeddable functions and APIs to simplify the implementation of governance action services, and their integration into the broader digital landscape, whilst being resilient and with good performance.

### Watchdog governance service

The *watchdog governance service* monitors changes in the metadata and initiates one of the following as a result:

- [governance action](#governance-action)
- [governance action process](#governance-action-process)
- [incident report](#incident-report)

One example of a watchdog governance service is to monitor for new [assets](./concepts/asset). Another example is to monitor the addition of open discovery reports and take action on their content.

![Governance context for the watchdog governance service](watchdog-governance-service-context.svg)

### Verification governance service

*Verification governance services* test the properties of specific open metadata elements to ensure they are set up correctly and do not indicate a situation where governance activity is required. The results returned from the verification governance service can be used to trigger other governance services as part of a [governance action process](#governance-action-process).

![Governance context for the verification governance service](verification-governance-service-context.svg)

The verification services may also publish [guards](#guard) to report on any errors it finds.

For example, it may check that a new asset has an owner, is set up with zones and includes a connection and a schema.

### Triage governance service

*Triage governance services* run triage rules to determine how to manage a situation. This could be to initiate an external workflow, wait for manual decision or initiate a remediation request through either an external workflow or by creating a [`ToDo`](./types/1/0137-Actions/#todo) for a specific person.

![Governance context for the triage governance service](triage-governance-service-context.svg)

### Remediation governance service

The *remediation governance services* perform updates to metadata. Examples of remediation services are duplicate linking and consolidation.

![Governance context for the remediation governance service](remediation-governance-service-context.svg)

### Provisioning governance service

A *provisioning governance service* invokes a provisioning service whenever a provisioning request is made. Typically, the provisioning service is an external service. It may also create lineage metadata to describe the work of the provisioning engine.

![Governance context for the provisioning governance service](provisioning-governance-service-context.svg)

## Implementing governance action services

Governance action services are [open connectors](./frameworks/ocf) that support the interfaces defined by the GAF. They may produce [audit log records](./frameworks/alf) and exceptions, and they may make changes to metadata through the [Open Metadata Access Services (OMAS)](./services/omas).

A governance action service is passed a *context* as it is started. This provides access to the request type and associated parameters (name-value pairs) used to invoke the governance action service, along with a client to access open metadata through the [Governance Engine OMAS](./services/omas/governance-engine/overview).

![Structure of the governance context](governance-context.svg)

This context is then specialized for each type of governance action service. Details of the specific context for each service can be found in the links above to the various governance action service types.

## Configuring governance action services

A collection of related governance action services are grouped into governance action engines for deployment. The governance action engine maps *governance action request types* to the governance action service that should be invoked along with.

![Structure of a governance engine definition](governance-action-engine-definitions.svg)

These definitions are created through the [Governance Engine OMAS](./services/omas/governance-engine/overview) and are stored in the open metadata repositories.

Governance action engines are hosted in an [Open Metadata Engine Service (OMES)](./services/omes) running on one or more [engine hosts](./concepts/engine-host). The Open Metadata Types used to define the governance action engines are located in [0461 governance action engines](./types/4/0461-governance-engines).

## Running governance action services

Governance action engines are hosted by the [Governance Action OMES](./services/omes/governance-action/overview).

The engine services run in dedicated OMAG Server called the [*engine host*](./concepts/engine-host). You can find [instructions for configuring the engine services in the engine host](./guides/admin/servers/configuring-an-engine-host/#configure-the-engine-host-services) in the administration guide.

The [Governance Engine OMAS](./services/omas/governance-engine/overview) provides the services for:

- setting up the definitions of a governance action engine.
- configuring [governance action processes](#governance-action-process).
- managing [governance actions](#governance-action) and [incident reports](#incident-report).

## Governance pack

A *governance pack* is a collection of pre-defined governance engines and services definitions plus governance service implementations.

![Governance pack](governance-pack.svg)

A team can use the governance pack to distribute the governance engine function to different metadata ecosystems.

--8<-- "snippets/abbr.md"
