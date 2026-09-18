# pathExtension:getAttributeDetails()

> --------------------- ------------------------------------------------------------------------------------------
> __Type__              [Function][api.type.Function]
> __Object__            [PathExtension][api.type.PathExtension]
> __Library__           [display.*][api.library.display]
> __Return value__      [Table][api.type.Table]
> __Revision__          [REVISION_LABEL](REVISION_URL)
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

Query details about a given attribute belonging to the path extension.

If the attribute is missing, returns `nil`.

Otherwise, a table is returned, containing various properties:

##### type
Currently, this is one of the [strings][api.type.String] "byte" or "float".

##### components
This is the number of components belonging to the attribute, an integer from 1 to 4.

##### offset
An integer offset, indicating where the attribute is located in the underlying geometry.

(**TODO** native details... presumably this is in the local stream)

##### normalized

If the data is normalized (represented as an integer, but converted to float on the GPU),
this is a [boolean][api.type.Boolean] with value `true`.

## Syntax

	details = PathExtension:getAttributeDetails( name )

	##### name ~^(required)^~
	_[String][api.type.String]._ The name used when specifying the attribute in the [vertex extension][api.library.graphics.defineVertexExtension].



(**TODO**)

	Returns

	- nil, if attribute doesn’t exist.

	or

	{ type, components, offset[, normalized] }

	At the moment, type is either “byte” or “float”, components is the component count (1-4), offset says where the value is located in the appropriate vertex data (stock or instanced), normalized says if an integer type gets converted to floats. (TODO? More details would be useful, e.g. for instancing)

Extension.instances:

	When this property is read, returns the number of instances attached to this display object, or 0 if unsupported / unassigned.

	Otherwise, when assigned, updates the display object’s instance count. Any instance-rate streams are expanded as necessary, and filled with 0 values, to match the count.

	Instance-rate streams’ sizes may be calculated thus:

	valueCount = ceil(instanceCount / instancesToReplicate)

	if windowed
		size = valueCount + windowSize - 1
	otherwise
		size = valueCount
