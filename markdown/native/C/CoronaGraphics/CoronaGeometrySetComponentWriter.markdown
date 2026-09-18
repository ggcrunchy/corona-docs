# CoronaGeometrySetComponentWriter()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaGeometrySetComponentWriter
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

int CoronaGeometrySetComponentWriter ( const CoronaRenderer * renderer, const char * name, CoronaGeometryComponentWriter writer, const void * context, int update ) CORONA_PUBLIC_SUFFIX;

typedef void (*CoronaGeometryComponentWriter)( void * dest, const void * context, const CoronaGeometryMappingLayout * layout, unsigned int index, unsigned int n );

/**
 Operation performed when submitting geometry, used to assign or modify a specific component or attribute.
 The first such value will be pointed at by `dest`, and `index` says which output vertex contains the value
 (typically this will matter to user-provided contexts).
 Starting from `dest`, the layout's `outStride` may be used to step from one vertex to the next, up to the
 `n`-th instance.
 A well-behaved "normal" writer is write-only: `dest` is undefined initially and must be valid afterward.
 Update-style writers, on the other hand, are assumed to already contain valid data and thus may both read
 and write.
 In either case, a writer should restrict itself to the component or attribute it has claimed.
 When a context is supplied with the writer, it will be available as that parameter.
 Otherwise, if `context` is non-`NULL`, the input had associated geometry and it points to the corresponding
 value in the `index`-th input vertex. Similar to `dest`, the layout's `outStride` may be used to iterate
 over these values.
*/

/**
 Append a writer to the renderer's list.
 When rendering, each "normal" writer is called, then any "update" ones (in order), to create the sequence of
 vertices to be submitted. The list will always begin with some built-in behavior, e.g. a writer that copies
 source vertices over directly.
 Writers may be added within a before or after function belonging to a `CoronaShaderDrawParams`, and will remain
 in effect until said function exits.
 A custom writer might be added, say, to repurpose the "z" component for an effect, or supply "texCoord" from an
 alternate data source.
 In the case of "normal" writers, a new "position" writer will supercede any previous one, or "x" writers for
 that matter; similarly for other combinations. If possible, the shadowed functions will not even be called.
 Writers with side effects should be written with this in mind, or avoided altogether.
 Adding a writer does not affect batching.
 @param renderer Boxed renderer.
 @param name One of the following:
  "position", "texCoord", "color", "userData" (full attributes)
  "x", "y", "z" (position components)
  "u", "v", "q" (texCoord components)
  "r", "g", "b", "a" (color components)
  "ux", "uy", "uz", "uw" (userData components)
  TODO?: vertex extensions NYI
 @param writer Writer responsible for creating or updating the named vertex component or attribute.
 @param context Supplied as `context` to writer, cf. `CoronaGeometryComponentWriter`. May be `NULL`.
 @param update If non-0, this is an update-style writer, cf. `CoronaGeometryComponentWriter`.
 @return If non-0, the writer was set.
*/
