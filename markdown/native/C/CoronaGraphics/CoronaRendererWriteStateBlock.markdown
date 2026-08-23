# CoronaRendererWriteStateBlock()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaRendererWriteStateBlock
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

Update the [state block][native.C.CoronaGraphics.CoronaStateBlock]'s contents, possibly dirtying it.

Returns non-0 if the parameters were valid.

## Syntax

``````c
int CoronaRendererWriteStateBlock( const CoronaRenderer * renderer, unsigned long blockID, const void * data, unsigned int size );
``````

##### renderer
[Handle][native.C.PublicTypes] to Solar's renderer.

##### blockID
ID returned when the block was [registered][native.C.CoronaGraphics.CoronaRendererRegisterStateBlock].

##### data
Data to write to the block.

##### size
Size of `data`; `min( size, block size )` bytes will be written.
