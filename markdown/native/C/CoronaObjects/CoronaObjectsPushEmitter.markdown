# CoronaObjectPushEmitter()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectPushEmitter
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
>                       [display.newEmitter][api.library.display.newEmitter]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

(**TODO** consider deprecating, per comments in CoronaObjectParams)

/**
 This behaves like `display.newEmitter()` but allows method customization.

 The stack contents are used as the arguments.
 @param userData Arbitrary data supplied to the emitter object's methods. It is not owned by
                the object and it is up to the user to keep it alive while any methods use it.
 @param params Method parameter chain.
 @return number of values pushed onto stack;
         1 - means emitter object was successfully created and is on stack
         0 - error occurred and nothing was pushed on stack
*/
