# IfcDistributionElement

This _IfcDistributionElement_ is a generalization of all elements that participate in a distribution system. Typical examples of _IfcDistributionElement_'s are (among others):

* building service elements within a heating systems
* building service elements within a cooling system
* building service elements within a ventilation system
* building service elements within a plumbing system
* building service elements within a drainage system
* electrical elements
* elements within a communication network
* within a sensor (monitoring) network

The _IfcDistributionElement_ is further specialized in the IFC specification. Direct instantiation of _IfcDistributionElement_ without an assigned subtype of _IfcDistributionElementType_ provides the meaning of an distribution element proxy.

> HISTORY  New entity in IFC1.5.

{ .change-ifc2x4}
> IFC4 CHANGE The entity is marked as deprecated for instantiation - will be made ABSTRACT in future releases.

## Attributes

### HasPorts
Reference to the element to port connection relationship. The relationship then refers to the port which is contained in this element.

{ .change-ifc2x4}
> IFC4 CHANGE  The inverse attribute is deprecated. Relationship to ports, contained within the _IfcDistributionElement_ is now realized by the inverse relationship _NestedBy_ referencing _IfcRelNests_.

## Concepts

### Component to Distribution System



### Object Typing

The IfcDistributionElement defines the occurrence of any HVAC, electrical, sanitary or other element within a distribution system. Common information about distribution element types (or styles) is handled by subtypes of IfcDistributionElementType. The IfcDistributionElementType (if present) may establish the common type name, usage (or predefined) type, common material, common set of properties and common shape representations (using IfcRepresentationMap). The IfcDistributionElementType is attached using the _IfcRelDefinedByType.RelatingType_ objectified relationship and is accessible by the inverse IsDefinedBy attribute.

The assignment of types to distribution element occurrences is vital for providing the additional meaning, or ontology, of the distribution element. Many specialized type are defined in other schemas of this specification.

### Property Sets for Objects



### Quantity Sets

The quantities relating to the IfcDistributionElement are defined by the IfcElementQuantity and attached by the IfcRelDefinesByProperties. A detailed specification for individual quantities is introduced at the level of subtypes of IfcDistributionElement.

### Spatial Containment

The IfcDistributionElement may be contained within the spatial containment tree. The IfcSpace is the default spatial container.

> NOTE  The 'Spatial Containment' concept is mandatory in many model view definitions.

#### IfcBuildingStorey

The container for distribution elements spanning through two or more spaces.

#### IfcSpace

The default container for distribution elements,

