# CoronaObjectOnFinalizeParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectOnFinalizeParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

These params are meant for doing any custom cleanup, such as of resources loaded during the [create][native.C.CoronaObjects.CoronaObjectOnCreateParams] event.

## Syntax

``````c
typedef struct CoronaObjectOnFinalizeParams {
    CoronaObjectParamsHeader header;
    void (*action)( const CoronaDisplayObject * self, void * userData );
} CoronaObjectOnFinalizeParams;
``````

##### header  ~^(required)^~
[Header][native.C.CoronaObjects.CoronaObjectParamsHeader] common to all params structs, used to stitch them into the list used to [build a method stream][native.C.CoronaObjects.CoronaObjectsBuildMethodStream].

##### action ~^(optional)^~
If `NULL`, this is a no-op. Otherwise, this is called before the display object is destroyed.
