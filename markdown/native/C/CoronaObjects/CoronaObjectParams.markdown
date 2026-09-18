# CoronaObjectParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

This is used to supply a method stream to be picked up by a new display object, via one of `CoronaObjectsPush*()` functions.

(**TODO** This was poorly named; it sounds one of the method params struct. Also, while this union was meant to prevent
a combinatorial explosion of Push() functions + method lists, probably the way to go is a couple of functions, one each
for the two options below, and an enum of the stock display object types as an argument in each case, reducing the load
from this struct and 13 functions to an enum and 2 functions, with this and the Push()s then considered deprecated.)


## Syntax

``````c
typedef struct CoronaObjectParams {
    union {
        CoronaObjectParamsHeader * head;
        int ref;
    } u;
    int useRef;
} CoronaObjectParams;
``````

##### u.head ~^(optional)^~
A chain of method parameters, just as would be prepared to [build a method stream][native.C.CoronaObjects.CoronaObjectsBuildMethodStream].
This is suitable for one-shot custom objects and avoids the need to keep a stream reference.

##### u.ref ~^(optional)^~
A Lua reference as returned by [CoronaObjectsBuildMethodStream][native.C.CoronaObjects.CoronaObjectsBuildMethodStream], to use an existing set of methods.

##### useRef ~^(required)^~
If non-0, the `ref` representation is used, and required. Otherwise, `head` is used.
