# PathExtension.instances

> --------------------- ------------------------------------------------------------------------------------------
> __Type__              [Number][api.type.Number]
> __Object__            [PathExtension][api.type.PathExtension]
> __Library__           [display.*][api.library.display]
> __Revision__          [REVISION_LABEL](REVISION_URL)
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

Reading this property will return the number of instances currently attached to this display object, or 0 if none have been.

Writing an integer &ge; 0 will update this count, although only if the [vertex extension][api.library.graphics.defineVertexExtension] includes instance-rate attributes or instancing by ID.

Instance-rate streams are expanded as necessary to match the count, being padded with 0 values.

An attribute stream's size, as expected by [setAtttributeValue][api.type.PathExtension.setAttributeValue], is effectively given by:

``````lua
local function AttributeStream( instanceCount, instancesToReplicate, windowed )
	local valueCount = ceil(instanceCount / instancesToReplicate)

	if windowed then
		return valueCount + windowSize - 1
	else
		return valueCount
	endif
end
``````
