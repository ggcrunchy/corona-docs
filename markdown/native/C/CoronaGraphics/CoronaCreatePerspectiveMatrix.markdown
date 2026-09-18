# CoronaCreatePerspectiveMatrix()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaCreatePerspectiveMatrix
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

Construct a perspective projection [matrix][native.C.CoronaGraphics.CoronaMatrix4x4], using Solar's own routines.

## Syntax

``````c
void CoronaCreatePerspectiveMatrix( float fovy, float aspectRatio, float zNear, float zFar, CoronaMatrix4x4 result );
``````

##### fovy
The y field-of-view, in radians.

##### aspectRatio
Ratio of width to height, used to determins the x-field-of-view from `fovy`.

##### zNear
Distance from eye to near clipping plane.

##### zFar
Distance from eye to far clipping plane.

##### result
Out parameter: receives the projection matrix.
