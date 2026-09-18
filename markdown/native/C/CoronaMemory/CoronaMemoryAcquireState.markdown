# CoronaMemoryAcquireState

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaMemory.h, CoronaMemoryAcquireState
> __See also__			[CoronaMemory.h][native.C.CoronaMemory]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

(**TODO** this sounds like an action, and is extra-confusing given the presence of CoronaMemoryAcquireInterface...
maybe something like CoronaMemoryAcquisitionState would be better? the existing name could be deprecated typedef'd
to that in the meantime...)

/**
	This structure maintains some details needed by the memory interface after an acquisition, as well
	as the workspace provided for the underlying methods.
*/
typedef struct CoronaMemoryAcquireState {
	/**
	 This is the "proper" way to use the interface's callbacks, rather than directly invoking them.
	 An example raw call, given an instance `state`: `state.methods.resize(&state, newSize, 0)`.
	 See also `CORONA_MEMORY_IFC` and related macros.
	*/
	CoronaMemoryInterface methods;

	/**
	 Callbacks used by the interface methods.
	*/
	const CoronaMemoryCallbacks *callbacks;
	
	/**
	 Workspace for the current acquire, provided to underlying callbacks.
	 This will also be seen by `getObject()`; initial values may be supplied to it through `vars`. (N.B. a few
	 variables will be stomped on, however, q.v. the comments on `CoronaMemoryAcquireInterface()` and
	 `CoronaMemoryPushLookupEncoding()`.)
	*/
	CoronaMemoryWorkspace workspace;

	/**
	 Version of memory API known to the object, describing its feature set.
	 It is supplied by `CoronaMemoryCreateInterface()`, corresponding to the Solar library linked by its caller.
	 Currently, it is always 0 (base feature set), but would be incremented if important new features were added.
	 The upshot is that consumers and providers of memory might be in separate plugins, say, that were linked
	 against different feature levels. The version must therefore be consulted to provide a suitable  `interface`.
	*/
	int version;
} CoronaMemoryAcquireState;

