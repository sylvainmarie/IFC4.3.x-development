# IfcRailing

The railing is a frame assembly adjacent to human or vehicle circulation spaces and at some space boundaries where it is used in lieu of walls or to complement walls. Designed as an optional physical support, or to prevent injury or damage, either by falling or collision.

> HISTORY  New entity in IFC2.0

## Attributes

### PredefinedType


## Formal Propositions

### CorrectPredefinedType
Either the _PredefinedType_ attribute is unset (e.g. because an _IfcRailingType_ is associated), or the inherited attribute _ObjectType_ shall be provided, if the _PredefinedType_ is set to USERDEFINED.

### CorrectTypeAssigned
Either there is no railing type object associated, i.e. the _IsTypedBy_ inverse relationship is not provided, or the associated type object has to be of type _IfcRailingType_.

## Concepts

### Axis 2D Geometry



### Material Constituent Set

The material of the IfcRailing is defined by the IfcMaterialConstituent or as fallback by IfcMaterial, and it is attached either directly or at the IfcRailingType.

### Object Typing



### Property Sets for Objects



### Quantity Sets



### Spatial Containment

The IfcRailing, as any subtype of IfcBuildingElement, may participate alternatively in one of the two different containment relationships:

* the _Spatial Containment_ (defined here), or
* the _Element Composition_.

#### IfcBuildingStorey

Default spatial container

#### IfcBuilding

Spatial container for the element if it cannot be assigned to a building storey

#### IfcSite

Spatial container for the element in case that it is placed on site (outside of building)

