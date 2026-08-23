# CoronaShaderUnregisterEffectDataType()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaShaderUnregisterEffectDataType
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

Unregister an effect data type.

This might be useful in an editor, or an examples browser where different samples use a common name for slightly different types.

Effects currently using the data type are unaffected.

It returns non-0 if the type was found and unregistered, otherwise 0.

## Syntax

``````c
int CoronaShaderUnregisterEffectDataType( lua_State * L, const char * name );
``````

##### L
Pointer to the Lua state from which to access some runtime details.

##### name
A name that was previously used to [register][native.C.CoronaGraphics.CoronaShaderRegisterEffectDataType].
