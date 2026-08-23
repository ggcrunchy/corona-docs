# CoronaObjectParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

**
 This structure describes the method customizations for a new display object.
*/
typedef struct CoronaObjectParams {
    union {
        /**
         A chain of method parameters. This is suitable for temporary situations, for instance
         if the parameters are on the stack. A dedicated method stream is built for the object
         when pushed.
        */
        CoronaObjectParamsHeader * head;

        /**
         A Lua reference returned by `CoronaObjectsBuildMethodStream()`.
        */
        int ref;
    } u;
    
    /**
     If non-0, the method parameter chain is represented by `ref`; else `head`.
    */
    int useRef;
} CoronaObjectParams;
