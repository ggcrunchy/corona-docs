# CoronaObjectParamsHeader

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectParamsHeader
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

/**
 Each of the `CoronaObject*Params` structures has this as its first member, to effect C-style inheritance.
*/
typedef struct CoronaObjectParamsHeader {
    /**
     Link to the next method parameter structure in the chain, or `NULL` if this is the last one.
    */
    struct CoronaObjectParamsHeader * next;
    
    /**
     The appropriate member of `CoronaObjectAugmentedMethod` that identifies the payload that follows.
    */
    unsigned short method; // n.b. quite generous: all methods fit easily within a byte
} CoronaObjectParamsHeader;
