# CoronaShaderDrawParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaShaderDrawParams
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

TODO: basically IgnorableMethodParams...
very important: can be used for group; can do actions in bookends, raw draws, geometry writers

/**
 This may be used to augment and/or override how a shader draws an object.
 
 With a given method, this can take on the form:
 
 ```
   before( ... )
   original( ... )
   after( ... )
 ```
 
 where all three functions take the same arguments.

 The `before` and `after` functions may be NULL, in which case the respective function is
 not called. Similarly, the stock behavior is skipped if `ignoreOriginal` is non-0.
*/
typedef void (*CoronaShaderDrawBookend)( const CoronaShader * shader, void * userData, const CoronaRenderer * renderer, const CoronaRenderData * renderData );

typedef struct CoronaShaderDrawParams {
    /**
     Optional
     If non-0, skip the regular draw behavior.
    */
    unsigned int ignoreOriginal;
    
    /**
     Optional
     Actions to perform before and / or after the regular draw behavior.
    */
    CoronaShaderDrawBookend before, after;
} CoronaShaderDrawParams;

