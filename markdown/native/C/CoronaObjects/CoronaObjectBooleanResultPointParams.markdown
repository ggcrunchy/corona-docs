# CoronaObjectBooleanResultPointParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectBooleanResultPointParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

These params implement the [EarlyOutableIgnorableMethodParams][native.C.CoronaObjects.EarlyOutableIgnorableMethodParams], and
pertain to point-based operations on a display object, available through a [handle][native.C.PublicTypes].

The bookends have signature:

``````c
void (*method)( const CoronaDisplayObject * self, void * userData, float x, float y, int * result )`
``````

with `*result` defaulting to 0; its value after each call is interpreted as a boolean result.


