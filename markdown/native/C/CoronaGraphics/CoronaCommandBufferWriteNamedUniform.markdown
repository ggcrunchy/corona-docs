# CoronaCommandBufferWriteNamedUniform()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaCommandBufferWriteNamedUniform
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

(**TODO** consider if worth two functions, rather than params struct; kind of a wash, but maybe clearer)

int CoronaCommandBufferWriteNamedUniform( const CoronaCommandBuffer * commandBuffer, const char * uniformName, const CoronaWriteUniformParams * params, unsigned int size );

/**
 Attempt to write data into one of the currently bound shader's uniforms. In particular, this is meant to allow
 use of uniforms outside of Solar's dedicated set, including arrays. Since updates are done explicitly through
 this API, changes will persist; any display object using the shader will see these same uniforms, as opposed
 to per-object uniform userdata.
 This sharing does not apply across shader versions or mods.
 If the uniform exists, `Type` is one of `{ float, vec2/3/4, mat2/3/4 }`, and the name is not unusually long, the
 write will proceed. The `Count` is also determined in this process: >= 1 in the case of an array, 1 otherwise.
 Uniform data is interpreted as a `Type` array. On success, `min( Count, size / sizeof( Type ) )` items are written.
 It is meant to be called from a `CoronaCommand` reader.
 Solar's own built-in uniforms are not supported.
 @param commandBuffer Boxed command buffer.
 @param uniformName Name of uniform.
 @param params Uniform write configuration.
 @param size Size of uniform data, in bytes.
 @return If non-0, the write occurred.
*/
