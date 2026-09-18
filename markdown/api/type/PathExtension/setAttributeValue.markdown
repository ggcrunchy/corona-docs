# pathExtension:setAttributeValue()

> --------------------- ------------------------------------------------------------------------------------------
> __Type__              [Function][api.type.Function]
> __Object__            [PathExtension][api.type.PathExtension]
> __Library__           [display.*][api.library.display]
> __Revision__          [REVISION_LABEL](REVISION_URL)
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

Sets the value for a given vertex's extended attribute.

## Syntax

    object:setAttributeValue( index, name, value1 )
    object:setAttributeValue( index, name, value1, value2 )
    object:setAttributeValue( index, name, value1, value2, value3 )
    object:setAttributeValue( index, name, value1, value2, value3, value4 )

##### index ~^(required)^~
_[Numbers][api.type.Number]_ For vertex-rate attributes, an integer from 1 to [object.fillVertexCount][api.type.ShapeObject.fillVertexCount] or
[object.strokeVertexCount][api.type.ShapeObject.strokeVertexCount] (**TODO** or line?), indicating which vertex has the attribute.

(**TODO** vertex order...)

For instance-rate attributes, an integer &ge; 1 (**TODO** max?) indicating which unit has the attribute.

(**TODO**)

	With window-style attributes, the position is relative: for attribute1, index = 1 is just that; for attribute2, index = 1 is at position 2; and so on.


##### name ~^(required)^~
	_[String][api.type.String]._ The name used when specifying the attribute in the vertex extension.

##### values ~^(required)^~
_[Numbers][api.type.Number]._ Components of the attribute.

If too few values are supplied for the components, the missing ones will be assigned 0. Extras will be discarded.
