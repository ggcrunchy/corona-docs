# CoronaRendererIssueCommand()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			ORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaRendererIssueCommand
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

Issue a registered command, adding it to the recording command buffer.
 
## Overview

Returns non-0 if the command was issued.

Returns 0 if the renderer was invalid or the ID was never [registered][native.C.CoronaGraphics.CoronaRendererRegisterCommand].

## Syntax

``````c
int CoronaRendererIssueCommand( const CoronaRenderer * renderer, unsigned long commandID, void * data, unsigned int size );
``````

##### renderer
[Handle][native.C.PublicTypes] to Solar's renderer.

##### commandID
ID returned when the command was registered.

##### data
If the writer is absent, data to copy. This must be a non-`NULL` pointer to memory of at least `size` bytes.

Otherwise, arbitrary supplied to the command's [writer][native.C.CoronaGraphics.CoronaCommandWriter], unused by Solar
itself. It is the caller's responsibility to provide something valid.

May be `NULL` in the latter case, if it makes sense.

##### size
If the writer is absent, the size in bytes of `data` to copy.

Otherwise, Solar reserves this number of bytes and supplies this value to the writer.

May be 0 in the latter case, if it makes sense.
