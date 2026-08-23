# CoronaWriteUniformParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaWriteUniformParams
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

/**
 This structure accounts for different uniform writing needs.
*/
typedef struct CoronaWriteUniformParams {
    union {
        /**
         Memory data source.
        */
        const void * data;
        
        /**
         Offset in command buffer's working memory that holds the data, cf. the details for
         `CoronaCommandBufferGetBaseAddress`.
        */
        unsigned long offset;
    } u;
    
    /**
     If non-0, the data is available through `offset; else `data`.
    */
    int useOffset;
} CoronaWriteUniformParams;
