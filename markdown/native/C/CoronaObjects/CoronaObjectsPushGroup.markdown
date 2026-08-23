# CoronaObjectsPushGroup()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectsPushGroup
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

[display.newEmitter][api.library.display.newEmitter]

/**
 This behaves like `display.newGroup()` but allows method customization.

 The stack contents are used as the arguments.
 @param userData Arbitrary data supplied to the group's methods. It is not owned by the
                object and it is up to the user to keep it alive while any methods use it.
 @param params Method parameter chain.
 @return number of values pushed onto stack;
         1 - means group was successfully created and is on stack
         0 - error occurred and nothing was pushed on stack
*/
