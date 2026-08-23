# CoronaRendererRegisterCommand()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaRendererRegisterCommand
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

Permanently register a custom command that Solar may execute.

(**TODO** native details)
(**TODO** code sample?)

Returns non-0 on success, and populates `commandID`.

Returns 0 if an invalid [CoronaCommand][native.C.CoronaGraphics.CoronaCommand] was supplied, or
too many commands have been registered. (The arbitrary limit is around 64K, so this should be
unlikely outside something like a runaway loop.)


## Syntax


``````c
int CoronaRendererRegisterCommand( lua_State * L, const CoronaCommand * command, unsigned long * commandID ) CORONA_PUBLIC_SUFFIX;
``````

##### L
Pointer to the Lua state from which to access some runtime details.

##### command
Command operations.

##### commandID
On success, will be assigned an ID that may be used to [issue this command][native.C.CoronaGraphics.CoronaRendererIssueCommand].
