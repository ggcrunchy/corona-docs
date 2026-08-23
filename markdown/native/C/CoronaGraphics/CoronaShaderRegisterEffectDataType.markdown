# CoronaShaderRegisterEffectDataType()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaShaderRegisterEffectDataType
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

Register an effect data type, for use in [graphics.defineEffect][api.library.graphics.defineEffect].

An "effect data" is the `effect` object used to interact between a display object's fill or stroke and the effect,
and a custom type augments and / or overrides various stock behaviors.

(**TODO** code sample?)

Returns non-0 on success.

Returns 0 if invalid callbacks were supplied, or the name is currently registered. (It may be [unregistered][native.C.CoronaGraphics.CoronaShaderUnregisterEffectDataType].)

## Syntax


``````c
int CoronaShaderRegisterEffectDataType( lua_State * L, const char * name, const CoronaEffectCallbacks * callbacks );
``````

##### L
Pointer to the Lua state from which to access some runtime details.

##### name
A non-empty name not in use by another data type. This is supplied to effect definitions and used to assign [path extensions][api.type.PathExtension]s to display objects.

##### callbacks
A [callbacks][native.C.CoronaGraphics.CoronaEffectCallbacks] struct describing the custom behaviors.
