# CoronaObjectParentParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectParentParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

These params implement the [IgnorableMethodParams][native.C.CoronaObjects.IgnorableMethodParams] interface, and
pertain to operations between a display object and its parent group, each available through a [handle][native.C.PublicTypes].

The bookends have signature:

``````c
void (*method)( const CoronaDisplayObject * self, void * userData, lua_State * L, const CoronaGroupObject * groupObject )`
``````
