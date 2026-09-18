# CoronaCommand

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaCommand
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------

WIP WIP WIPEE

## Overview

This structure provides information used to add custom commands.

(**TODO** native details)

These are a building block to extend Solar's capabilities, especially for graphics.

## Syntax

``````c
typedef struct CoronaCommand {
    CoronaCommandReader reader;
    CoronaCommandWriter writer;
} CoronaCommand;
``````

##### reader ~^(required)^~
[Operation][native.C.CoronaGraphics.CoronaCommandReader] when the command is read back during execution.

##### optional ~^(optional)^~
[Operation][native.C.CoronaGraphics.CoronaCommandWriter] when the command is being recorded.

This may be `NULL`, in which case the operation becomes a straight copy.
