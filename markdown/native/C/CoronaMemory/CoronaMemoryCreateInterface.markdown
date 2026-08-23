# CoronaMemoryCreateInterface()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaMemory.h, CoronaMemoryCreateInterface
> __See also__			[CoronaMemory.h][native.C.CoronaMemory]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

wIP WIP WIP

/**
	Create an interface that may be used to provide access to objects' memory.
	Details may be found under `CoronaMemoryInterfaceInfo` and `CoronaMemoryAcquireInterface()`.
	The interface is made available through a proxy object. Each proxy receives a unique environment
	table, whose integer keys are reserved for internal use; other keys are free for custom use.
	@param L Lua state pointer.
	@param info Callback and interface-specific data information.
	@return If non-0, success, and a memory interface proxy will be on top of the stack.
*/
