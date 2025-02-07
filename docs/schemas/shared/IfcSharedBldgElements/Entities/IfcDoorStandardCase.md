# IfcDoorStandardCase

The standard door, _IfcDoorStandardCase_, defines a door with certain constraints for the provision of operation types, opening directions, frame and lining parameters, and with certain constraints for the geometric representation. The _IfcDoorStandardCase_ handles all cases of doors, that:

* are inserted into an opening, represented by _IfcOpeningElement_, using the _IfcRelFillsElement_ relationship;
* have a local placement relative to this opening, and with the y-axis of the placement pointing into the opening direction;
* have a profile geometry, represented by _IfcShapeRepresentation.RepresentationIdentifier_="Profile" as a closed curve to which the door parameters apply;
* have a reference to an _IfcDoorType_ to define the opening direction and the operation type (swinging, sliding, folding, etc.) of the door. The attribute _OperationType_ shall be provided and not being UNDEFINED, and the attribute _ParameterTakesPrecedence_ shall be "TRUE";
* have an _IfcDoorLiningProperties_ and _IfcDoorPanelProperties_ instances included in the set of _HasPropertySets_ at _IfcDoorType_.

> HISTORY  New entity in IFC4.

**_Geometric Representations_**

The geometric representation of _IfcDoorStandardCase_ is defined using the following multiple shape representations for its definition:

* **Profile**: a three-dimensional closed curve within a particular shape representation. The profile is used to apply the parameter of the parametric door representation. The profile around the edges of the opening is used to apply the door lining and door panel shape parameter.
* **MappedRepresentation**: A SweptSolid, SurfaceModel, Brep or a CSG representation additionally defining the 3D shape of the standard door in addition to the parametric representation by applying the _IfcDoorLiningProperties_ and an the _IfcDoorPanelProperties_ to the 'Profile' representation.

## Concepts

### Profile 3D Geometry

The door profile is represented by a three-dimensional closed curve within a particular shape representation. The profile is used to apply the parameter of the parametric door representation. The following attribute values for the IfcShapeRepresentation holding this geometric representation shall be used:

* RepresentationIdentifier : 'Profile'
* RepresentationType : 'Curve3D' or 'GeometricCurveSet', in case of 'GeometricCurveSet' only a single closed curve shall be contained in the set of _IfcShapeRepresentation.Items_.

The following additional constraints apply to the 'Profile' representation type:

* **Curve**: being an IfcPolyline defining a rectangle.
* **Position**: The curve shall lie in the xz plane of the object placement coordinate (the y coordinate values of the IfcCartesianPoint's shall be 0.).



<table summary="">

<tr valign="top">

  <td><img src="../../../../figures/ifcdoorstandardcase-01.png" alt="standard door" border="0" width="500" height="500"></td>

  <td>
<blockquote class="example">EXAMPLE  Figure 1 illustrates applying the door lining parameters to the
door profile shape representation. The profile defines the outer
boundary to which the door lining parameters relate as:</blockquote>
   <blockquote>
<ul>

    <li class="small"><em>IfcDoorLiningProperties.LiningDepth</em> starting at distance
defined by <em>LiningOffset</em> going into the positive y
direction.</li>

    <li class="small"><em>IfcDoorLiningProperties.LiningThickness</em> offset into the
inner side of the rectangle.</li>
    <li class="small"><em>IfcDoorLiningProperties.LiningOffset</em> distance along the
positive y direction to where the <em>LiningDepth</em> applies.</li>

<li class="small"><em>IfcDoorLiningProperties.ThresholdThickness</em> starting at
the bottom edge of the rectangle into the inner side of the
rectangle</li>

    <li class="small"><em>IfcDoorLiningProperties.ThresholdDepth</em> starting at
distance defined by <em>LiningOffset</em> going into the positive y
direction.</li>

    <li class="small"><em>IfcDoorLiningProperties.TransomOffset</em> starting at the
bottom edge of the rectangle (along local x axis) into the inner
side of the rectangle, distance provided as percentage of overall
height. Distance to the centre line of the transom.</li>

</ul></blockquote>

</td>

 </tr>

 <tr valign="top">

<td>
<p class="figure">Figure 1 &mdash; Door profile</p>
</td>

<td> </td>

 </tr>

</table>

