# CoronaCommandWriter

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaCommandWriter
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

The writer is used to write a command's payload during recording.

(**TODO** native details)

The default behavior, without a custom writer, is to copy the `data`
of `size` bytes supplied when [issuing][native.C.CoronaGraphics.CoronaRendererIssueCommand]
the command.

A writer is meant for cases, for example, where some transformation
needs to take place, such as following pointers in `data` and then
flattening them.

This can be done beforehand, of course, but with the writer approach
`size` bytes are reserved in the stream and may be written directly.

## Syntax

``````c
typedef void (*CoronaCommandWriter)( const CoronaCommandBuffer * commandBuffer, unsigned char * to, const void * data, unsigned int size );
``````

##### commandBuffer
[Handle][native.C.PublicTypes] to the command buffer being recorded.

##### to
Current offset in the stream where the command's payload is to be written.
This might be unaligned, so something like `memcpy()` should be used.

##### data
Data to write.

Supplied when issuing the command.

##### size
Size of payload, starting at `to`.

Supplied when issuing the command.
