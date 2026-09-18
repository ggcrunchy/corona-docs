# CoronaRendererRegisterStateBlock()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaRendererRegisterStateBlock
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

Rendering is recorded (and thus executed) in batches as much as possible: consecutive objects with matching
details will be grouped together into the same draw, reducing bandwidth pressure and the associated cost.

A state block allows a user-supplied set of details to be monitored, and a rendering batch will break if it
finds one or more of them has diverged. Furthermore, this provides the opportunity to perform an action of
some sort, such as issuing state-related commands.

Only the raw contents are compared: state that has been changed, but then changed back, will not be considered when checking for differences.

(**TODO** example)

Returns non-0 on success, and populates `blockID`.

Returns 0 if the block was invalid or incomplete.

## Syntax

``````c
int CoronaRendererRegisterStateBlock( lua_State * L, const CoronaStateBlock * block, unsigned long * blockID );
``````

##### L
Pointer to the Lua state from which to access some runtime details.

##### block
[Details][native.C.CoronaGraphics.CoronaStateBlock] used to configure the state block.

##### blockID
ID returned when the state block was registered.
