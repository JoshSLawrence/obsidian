---
tags:
  - HADR
---
## Acronyms

| Term | Meaning | Details |
| ---- | ---- | ---- |
| HADR | High Availability and Disaster Recovery | A solution concept for services |
| RTO | Recovery Time Objective | The time it takes to reover |
| RPO | Recovery Point Objective | The amount of acceptable data loss |
## Overview

When implementing a soluiton, different services within the solution should be evalatued for any HADR need.

If a services requires a HADR solution, you need to be able to:

- Identity RTO
- Identity RPO
- HADR Options Available in Azure
- When to choose an option over another
## Recovery Objectives

### RTO

When determining RTO, RTO should be viewed in 2 formats: Per service, and for the entire solution.

If a single service fails, the RTO to get the service up an running again is sufficient. In the event of multiple service failure... even if a SQL database is restored, if other components are still pending restoration then the solution as a whole is not available.

### RPO

A backup solution must meet the requirements of the objective. These seems simple, but keep in mind if you have a 15 minute RPO but backup a SQL database every 30 minutes, your RPO is not 15 minutes.

Additionally, restores should be executed regularly. Despite backing up services, there is not guarantee those backups will work.

Testing the restoration process will build team familiarity with the process resulting in a refined process, in addition to confirming the functionality of the backups and backup solution.

### Defining Recovery Objectives

To help define recovery objectives, the following should be considered:

- Business Requirements
- Skillset of Administrators
- Cost of Downtime

Cost of downtime and business requirements are especially important. Scoping how much money the business losing for each minute of downtime can help identity and justify the cost of the solution required to meet a desired RTO/RPO.

#### Differentiating between HA and DR

When defining recovery objectives it is important to define objectives for individual services, the solution as a whole, *and* for both HA and DR scenarios individually.

HA implies failover and redundancy within a region. Objectives can be very short and be handled automatically by features of services within Azure.

DR implies a data center failure, or in the concept of Azure a region failure. While some recovery can be automated, the implementation and failover process is significantly more complex.

As such, recovery objectives for both scenarios should be defined.

## Designing HADR for IaaS and PaaS

IaaS solutions allow for the most control of what the HADR solution *can* look like. With that said, PaaS solutions are typically designed with HADR in mind. Often this results in minimal configuration being required, just the HADR solution will need to be enabled.
