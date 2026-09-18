# CoronaObjectSetValueParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectSetValueParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

These params are used to augment and / or override assignment to a display object property in Lua, e.g `object.x = value` with key `"x"`.
It may be used to provide useful side effects on custom properties, as well as either suppress or piggyback on assignment to existing ones.

(**TODO** examples)

## Syntax

``````c
typedef struct CoronaObjectSetValueParams {
	CoronaObjectParamsHeader header;
	CoronaObjectSetValueBookend before, after;
	int ignoreOriginal, disallowEarlyOut, separateScopes;
} CoronaObjectSetValueParams;
``````

These params implement most of the [EarlyOutableIgnorableMethodParams][native.C.CoronaObjects.EarlyOutableIgnorableMethodParams] interface for
Lua-side property-setting on a display object, available through a [handle][native.C.PublicTypes].

As opposed to the full interface, the early-out predicate is always "result is true".

The only novelty beyond the interface is this property:

##### disallowEarlyOut
If non-0, early-outs are avoided.

The bookends have signature:

``````c
void (*method)( const CoronaDisplayObject * self, void * userData, lua_State * L, const char key[], int valueIndex, int * result )`
``````

with `*result` defaulting to 0; its value after each call is interpreted as a boolean result, with non-0 meant to indicate that a result
was assigned. (**TODO** this might actually currently need to be 1?)
