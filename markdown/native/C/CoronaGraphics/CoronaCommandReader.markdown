# CoronaCommandReader

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaCommandReader
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

During execution, the previously written stream of commands is visited.

(**TODO** native details)

A well-defined reader defines how to read back a specific command, which
should complement the [writer][native.C.CoronaGraphics.CoronaCommandWriter]'s
behavior.

The reader is also where any follow-up action is meant to be done, for
example to perform a low-level graphics call with the data.

## Syntax

``````c
typedef void (*CoronaCommandReader)( const CoronaCommandBuffer * commandBuffer, const unsigned char * from, unsigned int size );
``````

##### commandBuffer
[Handle][native.C.PublicTypes] to the executing command buffer.

##### from
Current offset in the stream where the command's payload is found.
This might be unaligned, so something like `memcpy()` should be used.

##### size
Size of payload, starting at `from`.
