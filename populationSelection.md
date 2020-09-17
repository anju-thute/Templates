# Population Selection  

## Abstract
When running EpiHiper, it is necessary to specify target sets of indiviudals or their contacts. These are needed for initialization, interventions, and for analysis. To specify a target is to specify a subset of the population. In order to support this, EXCEADS must be able to dynamically build the corresponding query to specify the population subset, and must do that in the context established by the user through, e.g., his/her choice of region, population, network, and configurations. The set of fields and their values will depend on these particular choices, and are not known a priori. 

## Problem
Individuals have dynamic properties which are only available at simulation time, and static properties (including geo-spatial). The difference between the two types should be made transparent in the user interface, i.e., the user should not be made aware of these distinctions, they should just be properties from on list. This distinction, however, will impact the way in which query are built.

## Implementation
### Dynamic Properties
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
Static properties are given through an external read-only database containing two tables, one specifying node properties indexed by the node id and another specifying location properties indexed by the location id. The fields available in these tables will only be known to EXCEADS once the region and population are selected. After slection the fields, including types and labels, are specified in the JSON header of the associated CSV files.

### Queries for static properties
At this point, static queries are very limited. They return a set which contains values for only a single field; the returned field is either the id (node or location) in the case that the queries constraint (where clause) includes a field name, or the selected field when the constraint contains a list of ids. Please note that all returned values will be unique. 

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
