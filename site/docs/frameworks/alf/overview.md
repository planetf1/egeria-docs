---
hide:
- toc
---

<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the Egeria project 2020. -->

--8<-- "snippets/content-status/released.md"

# Audit Log Framework (ALF)

The *audit log framework (ALF)* provides interface definitions and classes to enable connectors to support natural language enabled diagnostics such as exception messages and audit log messages.

The audit log framework provides the ability to route [audit log records](./concepts/audit-log) to multiple destinations where they can be stored or processed automatically. This second option is particularly important in today's world of continuous operations.

Figure 1 shows the main parts of the framework.

![Figure 1](audit-log-framework-overview.svg)
> **Figure 1:** Components of the Audit Log Framework (ALF)

When processing activity wishes to log a message to the audit log, it selects a message definition from a message set, optionally passing in the values to fill out the placeholders in the message template.

The message definition is passed to the audit log where it calls the message formatter, builds a log record and passes it on to the audit destination.

The [audit log destination](./concepts/audit-log) can be extended to allow routing to different destinations for review and processing.

## Usage

The [Open Metadata Repository Services (OMRS)](./services/omrs) provide an extension to the audit log destination that supports audit log store connectors. This means that an [OMAG Server](./concepts/omag-server) can be configured to route audit log messages to different destinations.

Details of the supported audit log store connectors and how to set them up are described in
[configuring the audit log](./guides/admin/servers/configuring-a-metadata-access-point/#configure-the-audit-log).

--8<-- "snippets/abbr.md"
