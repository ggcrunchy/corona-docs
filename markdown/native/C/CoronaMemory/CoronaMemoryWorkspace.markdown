# CoronaMemoryWorkpace

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaMemory.h, CoronaMemoryWorkpace
> __See also__			[CoronaMemory.h][native.C.CoronaMemory]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

/**
 This structure contains the working state of an acquired interface.
*/
typedef struct CoronaMemoryWorkspace {
	/**
	 Scratch memory available to callbacks. This should be enough for most needs.
	 A few of these will be pre-populated by `CoronaMemoryAcquireInterface()` and `CoronaMemoryPushLookupEncoding()`,
	 per their docs. These values simply provide some information to users and may safely be overwritten.
	*/
	CoronaMemoryWorkVar vars[8];

	/**
	 Available for error reporting; `error[0]` is set to `\0` before `getObject()` is called.
	*/
	char error[64];

	/**
	 The interface's data, as described in `CoronaMemoryInterfaceInfo`.
	*/
	void* data;

	/**
	 The interface's data size, as described in `CoronaMemoryInterfaceInfo`.
	*/
	size_t dataSize;
} CoronaMemoryWorkspace;
