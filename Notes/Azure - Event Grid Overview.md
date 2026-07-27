---
tags:
  - Microsoft/Azure
---
Event grid is ultimately an event routing service that manages the routing and delivery of event between sources and subscribers.

Being a publisher-subscriber model, event grid defines topics that services can subscribe to. When an event is published to a topic, it's subscribers are notified. Subscribers can then use this trigger to carryout any action needed.

This previous example is a push-model, but Event Grid supports pull scenarios as well.

Publishers can be Azure sources, or custom applications. Subscribers too, can be either.

## Topics

Topics are endpoints services can publish to, and subscribers can consume from.

To define a topic, and event grid subscription must be created.

There are 2 types of topics:

**System Topics** - used by azure services and cannot be published to by custom services

**Topics** - can used by any bespoke service as a endpoint is exposed.