# CoronaCreateOrthoMatrix()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaCreateOrthoMatrix
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

Construct an orthographic projection [matrix][native.C.CoronaGraphics.CoronaMatrix4x4], using Solar's own routines.

## Syntax

``````c
void CoronaCreateOrthoMatrix( float left, float right, float bottom, float top, float zNear, float zFar, CoronaMatrix4x4 result ) ;
``````

##### left
Distance to vertical clipping plane to the left.

##### right
Distance to vertical clipping plane to the right.

##### bottom
Distance to horizontal clipping plane below.

##### top
Distance to horizontal clipping plane above.


##### zNear
Distance from eye to near clipping plane.

##### zFar
Distance from eye to far clipping plane.

##### result
Out parameter: receives the projection matrix.
