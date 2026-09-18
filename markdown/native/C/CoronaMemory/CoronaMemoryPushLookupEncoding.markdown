# CoronaMemoryPushLookupEncoding()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaMemory.h, CoronaMemoryPushLookupEncoding
> __See also__			[CoronaMemory.h][native.C.CoronaMemory]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

int CoronaMemoryPushLookupEncoding( lua_State *L, unsigned short id, unsigned short context )

/**
	Encode an ID / context pair as a light userdata.
	If `CoronaMemoryAcquireInterface()` encounters such a value, it will use the proxy bound to the ID. Furthermore, before
	`getObject()` is called, its workspace is pre-populated: `vars[0].u` will be non-0, and `vars[1].u` and `vars[2].u` will be set
	to `id` and `context`, respectively.
	This API is meant, via `context`, to allow multiple values to be provided from a common data source, e.g. an array.
	@param L Lua state pointer.
	@param id An ID returned by `CoronaMemoryBindLookupSlot`.
	@param context 16-bit user-defined value to pair with the ID.
	@return If non-0, success, and the userdata will be on top of the stack.
*/
