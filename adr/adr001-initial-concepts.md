---
id: adrs-adr001
title: ADR001: Initial concepts for a booking core service
description: Architecture Decision Record (ADR) for design a genric book core service
---

# Initial design

## Context
Create a generic booking ticket to be used in several cases, for example:
- Book ticket shows
- Book ticket flight
- Book accomodation

### Use cases
The idea is the book that can be reused in different contexts, in which another services enrich this core driven features, for example:

**Ticket show**
- An show has a date
- An show happens in some place
- An show is about something
- An show has variable prices tickets

**Ticket flight**
- An flight has a date
- An flight has a inital place and a final destination
- An flight has variable price tickets

**Book accomodation**
- An accomodation has a start and end date
- An accomodation has some location
- An accomodation has variable price 

## Decision

At first moment, it is considered create two entities: resource and ticket.
1. A resource is a generic piece that can be anything, a show, flight, accomodation, etc that should be manipulated according the domain.
2. A ticket is the part that can be purchased for someone according the resource.

- Resource
  - Has some location (location can be a primary and secondary places)
  - Has a date (date can be a start and end date)
  - Contains limited tickets (resource should list limited tickets)
  - Contain dinamics details given an resource (metada should be considered be persisted)
  - Can group tickets
  - Can be tagged

- Ticket
  - Contain a atomic status (status machine: cancelled, suspended, unstarted, started, processing, paid)
  - Contain a business status by resource 
  - Has a type to be grouped
  - Has a price
  - Is bought for someone
  - Can be tagged