# CoronaObjectParamsHeader

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectParamsHeader
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

This header structure is found as the first member of all object method param types, and is used to chain them together
as a list (or "stream") of methods, containing a set of custom behaviors.

A pointer to the first item in the chain may be supplied either through a [CoronaObjectParams][native.C.CoronaObjects.CoronaObjectParams] argument
to a `CoronaObjectsPush*()` function, or when [building a method stream][native.C.CoronaObjects.CoronaObjectsBuildMethodStream].

(**TODO** deprecating CoronaObjectParams, etc.)

## Syntax

``````c
typedef struct CoronaObjectParamsHeader {
    struct CoronaObjectParamsHeader * next;
    unsigned short method;
} CoronaObjectParamsHeader;
``````

##### next ~^(optional)^~
Pointer to the next params header in the stream. If absent, this is the last item.

##### method ~^(required)^~
A [method type][native.C.CoronaObjects.CoronaObjectAugmentedMethod] indicating what params type is being supplied.

If this is `kAugmentedMethod_None`, this entry will be ignored. Otherwise, this must be the only instance of the method type
present in the chain.
