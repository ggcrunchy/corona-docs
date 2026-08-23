# CoronaMemoryInterfaceInfo

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaMemory.h, CoronaMemoryInterfaceInfo
> __See also__			[CoronaMemory.h][native.C.CoronaMemory]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

/**
 This structure provides the information needed to create an interface.
*/
typedef struct CoronaMemoryInterfaceInfo {
	/**
	 Required
	 The callbacks to register with the interface.
	*/
	CoronaMemoryCallbacks callbacks;

	/**
	 Required
	 Called by `CoronaMemoryAcquireInterface()` to finish the acquire process.
	 Any state that will be needed by the methods may be assigned to `workspace` and / or the Lua stack. Once
	 this call begins, neither will be further modified internally.
	*/
	int ( *getObject )( lua_State *L, int arg, CoronaMemoryWorkspace *workspace );

	/**
	 Optional
	 This is used to associate some user-defined data with the interface, provided through `CoronaMemoryWorkspace`.
	 If `dataSize` is 0, `data` will be `NULL` and `dataSize` 0.
	 When `dataSize` > 0, the proxy will be created with `lua_newuserdata(L, dataSize`); its block address will be used as `data`
	 and `dataSize` will supply the workspace member of the same name.
	 When `dataSize` < 0 (any value), a userdata MUST be on top of the stack; it will be added to the proxy's environment. The
	 result of `lua_touserdata(L, -1)` will be supplied as `data`, and `lua_objlen(L, -1)` as `dataSize` (n.b. for light userdata,
	 this will be 0).
	*/
	int dataSize;
} CoronaMemoryInterfaceInfo;
