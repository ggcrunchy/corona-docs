# CoronaMemoryAcquireInterface()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaMemory.h, CoronaMemoryAcquireInterface
> __See also__			[CoronaMemory.h][native.C.CoronaMemory]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

int CoronaMemoryAcquireInterface( lua_State *L, int arg, CoronaMemoryAcquireState *state )

/**
	Acquire a reference to the memory interface of an object on the stack, in order to read from and / or
	write to its memory.
	Strings are a special case, having a default interface. Its `getByteCount()` and `getReadableBytes()`
	will return `lua_objlen( L, arg )` and `lua_tostring( L, arg )`, respectively.
	Otherwise, a memory interface proxy, as created by `CoronaMemoryCreateInterface()`, must be found.
	Usually, object will be expected to have a proxy in the `__memory` key of their metatables. The exception
	are light userdata, described in `CoronaMemoryBindLookupSlot()` and `CoronaMemoryPushLookupEncoding()`.
	In the non-light userdata case, `vars[0].u` in the workspace will be set to 0 on a successful acquire.
	To complete the acquisition, the call `ok = getObject( L, arg, &workspace )` is performed, with `ok` being
	non-0 understood as success.
	Any changes to the stack made by `getObject()` are left intact.
	@param L Lua state pointer.
	@param arg Stack index of object that will provide the memory.
	@param state State used to interface with the acquired memory.
	@return If non-0, success, and `state` is populated. (On failure, a dummy interface will be assigned.)
*/
