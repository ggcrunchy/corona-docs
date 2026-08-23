# CoronaVertexExtensionAttributeType

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			iOS, CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaExternalBitmapFormat
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

/**
 Primitive types that may be used by extended attributes; these extend the set used by Solar's vertices.
*/
typedef enum {
    /**
     Signed 32-bit integer.
    */
    kAttributeType_Int = kAttributeType_Count,

    // TODO: signed / unsigned (short, int); float16 / 32; etc.
    
    /**
     Attempt to keep the underlying type stable yet allow new values.
    */
    kMaxVertexMemberType = 0xFFFF
} CoronaVertexExtensionAttributeType;
