# CoronaCreateViewMatrix()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaCreateViewMatrix
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

Construct a view [matrix][native.C.CoronaGraphics.CoronaMatrix4x4], using Solar's own routines.

## Syntax

``````c
void CoronaCreateViewMatrix( const CoronaVector3 eye, const CoronaVector3 center, const CoronaVector3 up, CoronaMatrix4x4 result );
``````

##### eye
Eye or camera position.

##### center
The look-at direction points from `eye` to `center`.

##### up
Direction that points up. This is the "global" up, and should remain fixed, to keep the view steady.

##### result
Out parameter: receives the view matrix.
