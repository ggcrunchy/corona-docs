# CoronaStateBlock

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaStateBlock
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

This structure is filled in when [registering a state block][native.C.CoronaGraphics.CoronaRendererRegisterStateBlock].

``````c
typedef struct CoronaStateBlock {
    unsigned int blockSize;
    void * defaultContents;
    void * userData;
    void (*stateDirty)( const CoronaCommandBuffer * commandBuffer, const CoronaRenderer * renderer, const void * newContents, const void * oldContents, unsigned int size, int restore, void * userData );
    void (*defaultStateDirty)( const CoronaCommandBuffer * commandBuffer, const CoronaRenderer * renderer, const void * newContents, const void * oldContents, unsigned int size, int restore, void * userData );
    int dontHash;
};
``````

##### blockSize ~^(required)^~
Size of block, in bytes. Available as `size` in the dirty state handlers.
    
##### defaultContents ~^(optional)^~
The default state of the block, restored on each frame.

If non-`NULL`, memory at least `blockSize` bytes that supply the default block contents.

If absent, the block is filled with `0`s.

##### userData ~^(optional)^~
Data to be passed to the dirty state handlers. May be `NULL`. It must remain valid until recording has finished, since the last time it was written.

This data is distinct from the contents. Importantly, the contents themselves are compared to decide whether a block has changed, whereas the `userData`
is not involved in this decision. It may be used for additional context, for example, or hold references to other information.

##### stateDirty ~^(required)^~
This is called when recording a draw&mdash;after all of Solar's own business, as well as [effect callbacks][native.C.CoronaGraphics.CoronaEffectCallbacks]&mdash;if the contents have changed. In this primary use case (contrast `defaultStateDirty`), the `restore` parameter will be `0`.

This is where the actual work should be done, in particular issuing custom commands.

The `oldContents` parameter will contain the state before it became dirty (the first time, this will be the default contents), and `newContents` will contain the modified contents; untouched bytes remain intact.

After handling, the state is no longer considered dirty.

##### defaultStateDirty ~^(optional)^~
If non-`NULL` and the block has non-default contents, this will be called before restoring them.

If absent, `stateDirty` is called instead, and in either case `restore` will be non-`0`. The `oldContents` parameter will hold the final modified values; `newContents` will match `defaultContents`.

At this point, no more draws will be performed on this frame. It is still possible to issue commands, but they should be fire-and-forget in nature.

##### dontHash ~^(optional)^~
**NOT YET IMPLEMENTED** The idea here was to opt this state out of hashing, in a pipeline-based backend such as Vulkan.
