# Public types

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjects.h, CoronaPublicTypes.h
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

The following represent handles to some internal Solar types.

These will be made available within various `CoronaGraphics.h` and `CoronaObjects.h` callbacks, and are
intended as `const TYPE *` arguments to several other of their APIs, or return values in a few cases.

Generally speaking, a handle should only be assumed valid within the scope where Solar makes it available.

##### CoronaRenderer
Handle to the renderer singleton.

##### CoronaRenderData
Handle to the bundle of display object data sent to the renderer, when recording rendering commands.

##### CoronaShader
Handle to the effect data that ties a shader instantiation to a display object and its paint.

##### CoronaShaderData
(**DEPRECATED** Seems to be unused now.)

##### CoronaCommandBuffer
Handle to either the recording or the executing command stream.

##### CoronaDisplayObject
Handle to a display object.

##### CoronaGroupObject
Handle to a display group. It may be cast to a `CoronaDisplayObject` handle as well.

##### CoronaAny
Placeholder handle, to be cast to other types. for any of the above, so far only for the display object types.
