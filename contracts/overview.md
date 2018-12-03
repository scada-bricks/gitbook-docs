---
description: >-
  This section outlines some of the key contracts, with their purpose and API
  definitions.
---

# Overview

## Contracts

SCADA Bricks is entirely modular, and consists exclusively of interchangeable modules \(**services**\).  These services can be written in any language or platform, but have some basic requirements.

Every service in SCADA bricks must implement one or more **contracts**, and expose an **HTTP** end point on a configurable port which conforms to the relevant rules of the implemented contract\(s\).

When a service implements a contract, all the **required** methods must be implemented.  Optional methods can be implemented if desired.

Some care should be taken not to reuse very common or core method names, as this could prevent a service from implementing the contract in addition to the others.



