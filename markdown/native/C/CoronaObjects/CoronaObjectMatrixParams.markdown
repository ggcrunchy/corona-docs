# CoronaObjectMatrixParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectMatrixParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

These params implement the [IgnorableMethodParams][native.C.CoronaObjects.IgnorableMethodParams] interface, and
pertain to matrix-based operations on a display object, available through a [handle][native.C.PublicTypes].

The bookends have signature:

``````c
void (*method)( const CoronaDisplayObject * self, void * userData, float matrix[6] )
``````
