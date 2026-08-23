# CoronaMemoryWorkVar

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaMemory.h, CoronaMemoryWorkVar
> __See also__			[CoronaMemory.h][native.C.CoronaMemory]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

/**
 A value available to various memory routines.
 In a few cases, described below, these will have an initial value.
 Otherwise, the value is to be user-provided.
*/
typedef union CoronaMemoryWorkVar {
	/**
	 Pointer value, e.g. from a `lua_touserdata()`. Does not take ownership.
	*/
	void* p;

	/**
	 Const pointer value, e.g. from a `lua_tostring()`. Does not take ownership.
	*/
	const void* cp;

	/**
	 Size value, e.g. from a `lua_objlen()`.
	*/
	size_t size;

	/**
	 Double-precision value, e.g. a Lua number.
	*/
	double n;

	/**
	 Unsigned integer value.
	*/
	unsigned int u;

	/**
	 Signed integer value.
	*/
	int i;
} CoronaMemoryWorkVar;
