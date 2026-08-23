# CoronaObjectsBuildMethodStream()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectsBuildMethodStream
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

/**
 Build an immutable stream that may be shared among multiple objects.
 @param head The first in a chain of parameters, ending when a `next` of `NULL` is found.
            Any elements with `kAugmentedMethod_None` as their `method` are ignored;
            otherwise, any value of `method` must occur at most once.
 @return If successful, a Lua reference to the built stream; else `LUA_REFNIL`.
*/
