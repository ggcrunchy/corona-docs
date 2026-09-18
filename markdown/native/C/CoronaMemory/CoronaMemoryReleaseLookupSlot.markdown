# CoronaMemoryReleaseLookupSlot()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaMemory.h, CoronaMemoryReleaseLookupSlot
> __See also__			[CoronaMemory.h][native.C.CoronaMemory]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

int CoronaMemoryReleaseLookupSlot( lua_State *L, unsigned short id )

/**
	Unbind a lookup slot and detach the proxy associated with it.
	It is up to the caller to handle any lingering encodings made from `id`, which this will invalidate.
	@param L Lua state pointer.
	@param id An ID returned by `CoronaMemoryBindLookupSlot`.
	@return If non-0, the slot was in use.
*/
