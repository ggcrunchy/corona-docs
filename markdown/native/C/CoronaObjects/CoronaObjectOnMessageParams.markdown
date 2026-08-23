# CoronaObjectOnMessageParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectOnMessageParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

typedef struct CoronaObjectOnMessageParams {
    CoronaObjectParamsHeader header;
    void (*action)( const CoronaDisplayObject * self, void * userData, const char * message, const void * data, unsigned int size );
    int preserveScope;
} CoronaObjectOnMessageParams;

/**
These method params belong to messages, with `action` having signature `method( const CoronaDisplayObject * self, void * userData, const char * message, const void * data, unsigned int size )`.
*/
