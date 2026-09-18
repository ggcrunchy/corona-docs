# CoronaObjectParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

(**TODO** this was poorly named in that it looks like method params; also, while this union was meant to prevent
a combinatorial explosion of Push() functions + method lists, probably the way to go is a couple of factories, one
for each of these two options, and an enum of the types as one argument; and with that this and the existing Push()s
probably want to be considered deprecated)

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
