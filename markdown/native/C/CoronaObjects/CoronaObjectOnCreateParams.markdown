# CoronaObjectOnCreateParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectOnCreateParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

These params are meant for doing any custom initialization of a display object been created by a `CoronaObjectsPush*()` function.

## Syntax

``````c
typedef struct CoronaObjectOnCreateParams {
    CoronaObjectParamsHeader header;
    void (*action)( const CoronaDisplayObject * self, void ** userData );
} CoronaObjectOnCreateParams;
``````

##### header  ~^(required)^~
[Header][native.C.CoronaObjects.CoronaObjectParamsHeader] common to all params structs, used to stitch them into the list used to [build a method stream][native.C.CoronaObjects.CoronaObjectsBuildMethodStream].

##### action ~^(optional)^~
If `NULL`, this method is a no-op. Otherwise, this is called after the object has been created and pushed onto the stack.

The original value of `*userData` comes from the argument to the `CoronaObjectsPush*()` that created this object. It may be reassigned:
the original value may be used to derive a new one, for instance, or acquiring some resource might be postponed until the object is known to exist.

The value of `*userData` when this call completes is passed as `userData` to every other method.
