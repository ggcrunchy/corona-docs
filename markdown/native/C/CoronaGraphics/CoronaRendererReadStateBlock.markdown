# CoronaRendererReadStateBlock()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaRendererReadStateBlock
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

This can be used to read the current contents of a [state block][native.C.CoronaGraphics.CoronaStateBlock].

Returns non-0 if the parameters were valid.

## Syntax

``````c
int CoronaRendererReadStateBlock( const CoronaRenderer * renderer, unsigned long blockID, void * data, unsigned int * size );
``````

##### renderer
[Handle][native.C.PublicTypes] to Solar's renderer.

##### blockID
ID returned when the block was [registered][native.C.CoronaGraphics.CoronaRendererRegisterStateBlock].

##### data
If non-`NULL`, `min( *size, block size )` bytes will be read from the block's current contents.

##### size
On input, `*size` indicates the space allocated to `data`.

On successful output, `*size` will contain the block size. This may be used, even with `data` being `NULL`, to query this value.
