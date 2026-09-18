# CoronaGeometryMappingLayout

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaGeometryMappingLayout
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

/**
 Structured form to allow reads / writes of specific vertex components.
*/
typedef struct CoronaGeometryMappingLayout {
    /**
     Number of primitives (1 to 4) that constitute the value.
    */
    unsigned int count;
    
    /**
     If geometry vertices are the source, the number of bytes from one source value to the next. Otherwise, 0.
    */
    unsigned int inStride;

    /**
     Number of bytes from one destination value to the next.
    */
    unsigned int outStride;

    /**
     Primitive type of value.
    */
    CoronaGeometryAttributeType type;
} CoronaGeometryMappingLayout;
