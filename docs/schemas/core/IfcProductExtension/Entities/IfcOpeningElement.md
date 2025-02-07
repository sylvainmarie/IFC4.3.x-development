# IfcOpeningElement

The opening element stands for opening, recess or chase, all reflecting voids. It represents a void within any element that has physical manifestation. Openings can be inserted into walls, slabs, beams, columns, or other elements.

> NOTE  Definition according to ISO 6707-1: void in a building element

There are two different types of opening elements. The attribute _PredefinedType_ should be used to capture the differences:

* an opening, where the thickness of the opening is greater or equal to the thickness of the element &mdash;
  the attribute _PredefinedType_ is set to OPENING
* a recess or niche, where the thickness of the recess is smaller than the thickness of the element  &mdash;
  the attribute  _PredefinedType_ is set to RECESS for a recess or niche.

If the value for _PredefinedType_ is omitted, or the value is set to NOTDEFINED, no specific information of whether it is an opening or recess shall be assumed.

An _IfcOpeningElement_ has to be inserted into an _IfcElement_ by using the _IfcRelVoidsElement_ relationship. It may be filled by an _IfcDoor_, _IfcWindow_, or another filling element by using the relationship _IfcRelFillsElements_. Depending on the type of the _IfcShapeRepresentation_ of the _IfcOpeningElement_ the voiding relationship implies:

*  if the _IfcShapeRepresentation_.RepresentationIdentifier = 'Body', then the Body shape representation of the opening has to be subtracted from the body shape representation of the voided element - implicit Boolean difference operation.
*  if the _IfcShapeRepresentation_.RepresentationIdentifier = 'Reference', then the Reference shape representation of the opening is not subtracted, it is provided in addition to the hole in the Body shape representation of the voided element.

The _IfcOpeningElement_ shall not participate in the containment relationship, i.e. it is not linked directly to the spatial structure of the project. It has a mandatory _VoidsElements_ inverse relationship pointing to the _IfcElement_ that is contained in the spatial structure. The inverse relationship _ContainedInStructure_ shall be NIL.

> NOTE  See _IfcRelVoidsElement_ for a diagram on how to apply spatial containment and the voiding relationship.

> HISTORY  New entity in IFC1.0

{ .change-ifc2x}
> IFC2x CHANGE  The intermediate ABSTRACT supertypes _IfcFeatureElement_ and _IfcFeatureSubtraction_ have been added.

{ .change-ifc2x4}
> IFC4 CHANGE  The attribute _PredefinedType_ has been added at the end of attribute list. It should be used instead of the inherited attribute _ObjectType_ from now on.

## Attributes

### PredefinedType
Predefined generic type for an opening that is specified in an enumeration. There may be a property set given specifically for the predefined types.
{ .change-ifc2x4}
> IFC4 CHANGE The attribute has been added at the end of the entity definition.

### HasFillings
Reference to the Filling Relationship that is used to assign Elements as Fillings for this Opening Element. The Opening Element can be filled with zero-to-many Elements.

## Formal Propositions

### CorrectPredefinedType
Either _PredefinedType_ is unset or the inherited attribute _ObjectType_ shall be provided, if the _PredefinedType_ is set to USERDEFINED or _PredefinedType_.

## Concepts

### Body Geometry

The 'Body' representation of IfcOpeningElement can be represented using the representation types 'SweptSolid'. The following attribute values for the IfcShapeRepresentation holding this geometric representation shall be used:

* _IfcShapeRepresentation.RepresentationIdentifier_: 'Body'
* _IfcShapeRepresentation.RepresentationType_: 'SweptSolid'

The following constraints are recommended:

* _IfcShapeRepresentation.Items_ may include a single, or multiple, instances of IfcExtrudedAreaSolid.
* _IfcExtrudedAreaSolid.SweptArea_ shall support IfcRectangleProfileDef, IfcCircleProfileDef and IfcArbitraryClosedProfileDef.
* If multiple instances of IfcExtrudedAreaSolid are used, the extrusion direction of each extrusion should be equal.

There are two main extrusion directions: perpendicular and parallel.

**Perpendicular Swept Solid Representation Type**

For a perpendicular swept solid, _IfcExtrudedAreaSolid.ExtrudedDirection_ shall extrude the profile perpendicular to the element it is voiding. This may be horizontal for wall openings, or vertical for floor openings.

![standard opening](../../../../figures/ifcopeningelement_horizontal-layout1.png "Figure FULLEXTRUSION &mdash; Opening with full extrusion")

![recess](../../../../figures/ifcopeningelement_recess-layout1.png "Figure RECESS &mdash; Opening with recess extrusion")

> NOTE  The local placement directions for the IfcOpeningElement in Figure FULLEXTRUSION and Figure RECESS are only given as an example, other directions are valid as well.

> NOTE  Rectangles are now defined centrally, so the placement location has to be set to IfcCartesianPoint(XDim/2,YDim/2)

**Parallel Swept Solid Representation Type**

For a parallel swept solid,_IfcExtrudedAreaSolid.ExtrudedDirection_ shall extrude the profile parallel to the element it is voiding. This may be vertical in the case of walls.

Parallel extrusions shall be used when an opening or recess has a non rectangular foot print geometry that does not change along the height of the opening or recess.

Figure VERTEXTRUDE shows a vertical extrusion with multiple extrusion bodies for the opening. Each extrusion body has a different extrusion length.

![vertical extrusion](../../../../figures/ifcopeningelement_vertical-layout1.png "Figure VERTEXTRUDE &mdash; Opening with multiple extrusions")

> NOTE  The local placement directions for the IfcOpeningElement in Figure VERTEXTRUDE are only given as an example, other directions are valid as well.

### Product Local Placement

The local placement for IfcOpeningElement is defined in its supertype IfcProduct. It is defined by the IfcLocalPlacement, which defines the local coordinate system that is referenced by all geometric representations.

* The PlacementRelTo relationship of IfcLocalPlacement should point to the local placement of the same element, which is voided by the opening, i.e. referred to by _VoidsElement.RelatingBuildingElement_.

### Property Sets for Objects



### Quantity Sets



### Reference Geometry

Since there are no Boolean operations, either as IfcBooleanResult or implicitly by IfcRelVoidsElement the geometry of the IfcOpeningElement shall not be used to subtract the opening from the 'Body' shape representation of the voided element.

### Reference SweptSolid PolyCurve Geometry

Since there are no Boolean operations, either as IfcBooleanResult or implicitly by IfcRelVoidsElement the geometry of the IfcOpeningElement shall not be used to subtract the opening from the 'Body' shape representation of the voided element.

### Reference Tessellation Geometry

Since there are no Boolean operations, either as IfcBooleanResult or implicitly by IfcRelVoidsElement the geometry of the IfcOpeningElement shall not be used to subtract the opening from the 'Body' shape representation of the voided element.

