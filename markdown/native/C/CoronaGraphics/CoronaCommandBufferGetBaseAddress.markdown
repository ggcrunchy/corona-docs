# CoronaCommandBufferGetBaseAddress

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaCommandBufferGetBaseAddress
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

Returns the current base address of the command buffer, whether executing or recording.

(**TODO** native details)

Given an offset, previously written data may be read back from the stream.

The address is stable during a given command buffer execution, since all commands have been set.

This is not reliable during execution, however, as the memory might be reallocated the
next time a [command is issued][native.C.CoronaGraphics.CoronaRendererIssueCommand].

For longer-term needs, the base address should be subtracted from a stream address&mdash;this
would be a [reader][native.C.CoronaGraphics.CoronaCommandReader]'s `from`, or more typically
a [writer][native.C.CoronaGraphics.CoronaCommandWriter]'s `to`, in most cases&mdash;to obtain
an offset that will remain invariant.

(**TODO** code sample)

Returns `NULL` if the command buffer is invalid.

## Syntax

``````c
const unsigned char * CoronaCommandBufferGetBaseAddress( const CoronaCommandBuffer * commandBuffer )
``````

##### commandBuffer
[Handle][native.C.PublicTypes] to a command buffer.
