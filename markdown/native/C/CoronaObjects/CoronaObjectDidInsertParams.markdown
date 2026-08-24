# CoronaObjectDidInsertParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectDidInsertParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

(**TODO** ) inconsistent naming: should be "Group" rather than "Object"...

These params implement the [IgnorableMethodParams][native.C.CoronaObjects.IgnorableMethodParams] interface, and
pertain to post-insert operations on a display group, available through a [handle][native.C.PublicTypes].

The bookends have signature:

``````c
void (*method)( CoronaGroupObject * self, void * userData, int childParentChanged )`
``````
