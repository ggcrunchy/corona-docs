# CoronaObjectOnCreateParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectOnCreateParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

typedef struct CoronaObjectOnCreateParams {
    CoronaObjectParamsHeader header;
    void (*action)( const CoronaDisplayObject * self, void ** userData );
} CoronaObjectOnCreateParams;

/**
 These are method params related to create events, whose `action` has signature
 `method( const CoronaDisplayObject * self, void ** userData )`.
 
 The original value of `*userData` comes from the argument to a `CoronaObjectsPush*` function;
 its value after this method concludes will be used by any subsequent methods.
*/
