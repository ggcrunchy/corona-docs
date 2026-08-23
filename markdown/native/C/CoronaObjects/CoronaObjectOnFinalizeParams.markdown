# CoronaObjectOnFinalizeParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectOnFinalizeParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

typedef struct CoronaObjectOnFinalizeParams {
    CoronaObjectParamsHeader header;
    void (*action)( const CoronaDisplayObject * self, void * userData );
} CoronaObjectOnFinalizeParams;

/**
 These are method params related to finalize events, whose `action` has signature
 `method( const CoronaDisplayObject * self, void * userData )`.
*/
