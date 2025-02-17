---
id: connectivity-customizers
title: Connectivity Customizers
pagination_label: Connectivity Customizers
sidebar_label: Customizers
sidebar_position: 7.1
sidebar_class_name: saasConnectivity
keywords: ['connectivity', 'connectors', customizers]
description: Connectivity customizers can customize out of the box SaaS connectors. 
slug: /docs/saas-connectivity/customizers
tags: ['Connectivity']
---

# Overview

SaaS Connectivity Customizers are cloud-based connector customizers that make customizing out of the box SaaS connectors possible. The customizers allow you to customize the out of the box connectors in a similar way to how you can use rules to customize VA (virtual appliance) based connectors. By using a customizer, you can change a connector's input before the connector ingests the data, or you can change the connector's output before to the output is sent to IdentityNow.

## How do they work?

SaaS Connectivity Customizers work by sitting in between IdentityNow and the connector. They intercept calls from IdentityNow to the connector and calls from the connector to IdentityNow. When the customizer intercepts a call, it can call custom code to mutate the data in any way necessary to change the connector behavior. 

This chart shows an example of this interception process - the ```stdAccountRead``` command is implemented with the customizer in place: 

<div align="center">

```mermaid
sequenceDiagram
    autonumber
    participant IDN as IdentityNow
    participant CUS as Customizer
    participant CON as SaaS Connector

    IDN->>CUS: StdAccountRead Request
    CUS->>CON: Mutated StdAccountRead Request
    CON->>CUS: StdAccountRead Response
    CUS->>IDN: Mutated StdAccountRead Response

```

</div>