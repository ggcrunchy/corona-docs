# CoronaVertexExtensionAttribute

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			iOS, CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaExternalBitmapFormat
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

(**TODO** )

/**
 Configuration for a vertex extension attribute.
*/
typedef struct CoronaVertexExtensionAttribute {
    /**
     Name of attribute in shader.
    */
    const char * name;

    /**
     Primitive type of attribute.
    */
    CoronaVertexExtensionAttributeType type;

    /**
     If non-0 and the type is integral, on the GPU side components resolve to
     floating point values in [0, 1] or [-1, +1], according to signedness.
    */
    unsigned char normalized;

    /**
     Number of components, from 1 to 4.
    */
    unsigned char components;

    /**
     If > 1, attributes `name .. 1`, ..., `name .. N` are registered, each with the
     remaining (non-instancing) properties that would normally go to `name`.
     The input is coalesced so that `name .. 1` sees the first value, `name .. 2`
     the second, and so on; when the attribute does advance, the window slides
     forward: `name .. 1` will be on the second value, `name .. 2` the third, etc.
     Given `M` instances, the combined stream will have `max(ceil(M / R), N)`
     elements, `R` being the instances-to-replicate count.
    */
    unsigned short windowSize;
    
    /**
     If > 0, the attribute has instance granularity: in particular, over the course of (at
     most) this many instances, all vertices use value `N`; the next batch then goes
     with value `N + 1`, and so on.
     If 0 but windowed, this is interpreted as 1.
     If not windowed, the attribute's data will comprise `ceil(M / R)` elements, where
     `M` is the instance count and `R` the instances-to-replicate count.
     To query support, call `system.getInfo( "instancingSupport" )`.
    */
    unsigned int instancesToReplicate;
} CoronaVertexExtensionAttribute;
