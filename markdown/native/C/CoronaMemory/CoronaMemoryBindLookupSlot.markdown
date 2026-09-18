# CoronaMemoryBindLookupSlot()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaMemory.h, CoronaMemoryBindLookupSlot
> __See also__			[CoronaMemory.h][native.C.CoronaMemory]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

/**
	Given a memory proxy, as returned by `CoronaMemoryCreateInterface()`, on top of the stack,
	associates it with a lookup slot. While the proxy is bound to the slot, encodings may be made
	referencing it via calls to `CoronaMemoryPushLookupEncoding()`.
	N.B. A few bits are reserved, so there are fewer than 2^16 available slots. If all slots happen
	to be in use, the bind will fail.
	@param L Lua state pointer.
	@param id ID used to refer to the proxy / lookup slot.
	@return If non-0, success, `id` is populated, and the proxy is popped from the stack.
*/
