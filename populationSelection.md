# Population Selection  

## Abstract
For initialization, interventions, and analysis it is necessary to specify a subset of the population. In order to do this, EXCEADS needs to be able to dynamically build a query based on the currently given user context since not all fileds and their values are known a priori. 

## Problem
Individuals have dynamic properties which are only available at simulation time and static properties (including geo-spacial). The difference between the 2 types should not affect the user interface, i.e., the user must not made aware of these distinction and should just properties from on list, but will affect the way the query can be built.

## Implementation
### Dynamic Porperties
A node's (individual's) dynamic properties in EpiHiper are:
* __node id__: integer 
* __health state__: disease state of the currently selected disease model
* __susceptibility factor__: number 
* __susceptibility__: number
* __infectivity factor__: number
* __infectivity__: number
* __node traits__: all node features currently in the context (initializations, interventions) 
* __edges__: edges type

An edge's dynamic properties in EpiHiper are:
* __target node id__: integer
* __target activity__: all activity features defined in the selected network
* __source node id__: integer
* __source activity__: all activity features defined in the selected network
* __duration__: number
* __location id__: integer
* __edgeTrait__: all edge features currently in the context (initializations, interventions, network)
* __active__: Boolean (0, 1)
* __weight__: number

### Queries for dynamic properties
Operations returning a Boolean (true, false) result:
* __equal__: `A == B`
* __not equal__: `A != B`
* __less__: `A < B`
* __less or equal__: `A <= B`
* __greater__: `A > B`
* __greater or equal__: `A >= B`
* __within__: `A in [B1, B2, ..., Bn]`
* __not within__: `A not in [B1, B2, ..., Bk]`

Please note that the types of `A` and `B` must be compatible. Furthermore, the following operations returning a Boolean (true, false) are supported:
* __and__: `and [Boolean1, Boolean2, ..., Booleank]`
* __or__: `or [Boolean1, Boolean2, ..., Booleank]`
* __not__: `not Boolean`

### Static properties
Static properties are given through an external read-only database containing two tables, one specifying node properties indexed by the node id and another specifying location properties indexed by the location id. The fields available in these tables will only be known to EXCEADS through the selected region and population. The fields, including types and labels, are specified in the JSON header of the associated CSV files.

### Queries for static properties
At this point, static queries are very limited. They return a sets which contains only field values. The returned field is either the id (node or location) in case the queries constraint (where clause) a field name or a selected field when the constraint contains a list of ids. Please note that all returned values will be unique. 

### Queries constraints for static properties
* __equal__: `A == B`
* __not equal__: `A != B`
* __less__: `A < B`
* __less or equal__: `A <= B`
* __greater__: `A > B`
* __greater or equal__: `A >= B`
* __within__: `A in [B1, B2, ..., Bn]`
* __not within__: `A not in [B1, B2, ..., Bk]`

Please note that the types of `A` and `B` must be compatible. 

### Supporting `and` and `or` in static queries.
EpiHiper supports the set operations `union` and `intersection`. Since the return value of a static query is a set, these operations can be used to implement `or` (`union`)  and `and` (`intersection`).

### Encoding of the query
The query will be encoded in JSON following the [schemata](https://github.com/NSSAC/EpiHiper-Schema/tree/master/schema).

### Geo-spacial queries
Currently EpiHiper does not support geo-spacial queries based on shapes. This feature will be implemented in the future and the encoding will use JSON. This, however, does not mean that we cannot select locations. Locations of homes or activities will have admin levels 1 through 2 (country, state, county) in the location table, thus locations can be selected based on these field values. We will provide a JSON encoding for admin levels which represent a tree structure so that EXCEADS can map user understandable names to the appropriate admin levels. Since the admin levels are a static property, the above described implementation will suffice. 
