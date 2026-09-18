# CoronaObjectValueParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectValueParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

These params are used to augment and / or override retrieval of a display object property in Lua, e.g `object.x` with key `"x"`.
It may be used to provide custom properties, as well as either suppress or reinterpret existing ones.

(**TODO** examples)

## Syntax

``````c
typedef struct CoronaObjectValueParams {
    CoronaObjectParamsHeader header;
    CoronaObjectValueBookend before, after;
    int ignoreOriginal, disallowEarlyOut, earlyOutIfZero, separateScopes;
} CoronaObjectValueParams;
``````

These params implement the [EarlyOutableIgnorableMethodParams][native.C.CoronaObjects.EarlyOutableIgnorableMethodParams] interface for
Lua-side property-getting on a display object, available through a [handle][native.C.PublicTypes].

The only novelty beyond the interface is this property:

##### disallowEarlyOut
If non-0, early-outs are avoided.

The bookends have signature:

``````c
void (*method)( const CoronaDisplayObject * self, void * userData, lua_State * L, const char key[], int * result )`
``````

with `*result` defaulting to 0; its value after each call is interpreted as a boolean result, with non-0 meant to indicate
a value is on the stack.
