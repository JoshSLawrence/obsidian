---
tags:
  - ComputerScience/Databases
---

Normalization is the process of (or set of steps for) breaking a table or relation with more than one theme into a set of tables such that each has only one theme.

### Quick Notes

- A **Functional Dependency** (FD) is denoted by the arrow symbol: ->
- A **Multi-valued Dependency** (MVD) is denoted by the double arrow symbol: ->->

## The First Normal Form ~ 1NF

A relation (table) is in **1NF** if: 

- There are only Single Valued Attributes.
- Attribute Domain does not change.
- There is a unique name for every Attribute/Column.
- The order in which data is stored does not matter.

## The Second Normal Form ~ 2NF

The second normal form evaluation applies to relations with a composite, primary key.

A relation (table) is in **2NF** if:

- The relation is in 1NF.
- The relation does not contain any partial dependencies.

A partial dependency is an attribute (column) that is not determined by the entirety of the composite, primary key.

## The Third Normal Form ~ 3NF

A relation (table) is in **3NF** if:

- The relation is in 2NF
- There are no transitive dependencies for non-prime attributes

In other words, If a relation is made up of attributes: (A *primary key*, B, C) An attribute cannot be determined by another attribute.

 - Illegal A->B, B->C
 - Legal A->B, A->C

## Boyce-Codd Normal Form ~ BCNF

A relation (table) is in **BCNF** if:

- The relation is in 3NF
- X should be a superkey for every functional dependency (FD) X->Y in a given relation.

BCNF is very similar to 3NF in that there can be no transitive dependencies as function dependencies must have the primary key as the determinient.

For example, this is legal in 3NF

- A->B, A->C, B->C

In this example there are no transitive dependencies. However, while the superkey (primary key) A, determines C, B can also sometimes determine C. This is not allowed in BCNF.

You may think, "But C is determined by B which is determined by A, so that this is not in 3NF!" This is not correct as C is directly determined by A, just not 100% of the time.

An easier way to visualize this may be:

- A->B, A->C, D->E

## The Fourth Normal Form ~ 4NF

A relation (table) is in **4NF** if:

- The relation is in BCNF
- There are no non-trivial multi-valued dependencies other than a candidate key

In short, if A->B and B can vary resulting if numerous records (rows), then a multi-value dependency exits. These must be resolved for the dataset to be in 4NF.

| CustomerID | FirstName | Lastname | PurchasedGuitar |
| ---- | ---- | ---- | ---- |
| 0001 | Josh | Lawrence | Martin 000-18 |
| 0001 | Josh | Lawrence | Epiphone Les Paul Custom |
Note that OwnedGuitars can have multiple values for the same customer.