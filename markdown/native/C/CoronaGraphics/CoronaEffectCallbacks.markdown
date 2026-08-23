# CoronaEffectCallbacks

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaEffectCallbacks
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

After assigning an effect to a paint, say as `paint.effect = "myEffect"`, its properties may be
read and written by working through the `paint.effect` object.

This structure contains fields that allow for augmenting this effect data, and by extension how some
of the rendering is recorded, somewhat in the spirit of Lua's [metatables][api.library.global.setmetatable].

<div class="guide-notebox">
<div class="notebox-title">Note</div>

Always initialize an instance of this structure with zeros. Some of the fields are optional and the data type can be created even if they are `NULL`. Other fields are required, however, and the data type will not be pushed if they aren't present.

``````c
CoronaEffectCallbacks callbacks;
memset(&callbacks, 0, sizeof(CoronaEffectCallbacks));
callbacks.size = sizeof(CoronaEffectCallbacks);
``````

</div>


Somewhat confusingly, internally Solar calls these `Shader`s. This is the reason behind the
`CoronaShader` name, but these are describing what this page terms "effect data".

See `extraSpace` for details on the `userData` parameters.

## Syntax

``````c
typedef struct CoronaEffectCallbacks {
	unsigned long size;
	void (*shaderBind)( const CoronaRenderer * renderer, void * userData );
	void (*shaderDetach)( const CoronaShader * shader, void * userData );
	void (*prepare)( const CoronaShader * shader, void * userData, const CoronaRenderData * renderData, int w, int h, int mod );
	CoronaShaderDrawParams drawParams;
	int (*getDataIndex)( const char * name );
	int (*getData)( lua_State * L, int dataIndex, void * userData, int * hadError );
	int (*setData)( lua_State * L, int dataIndex, int valueIndex, void * userData, int * shouldInvalidate, int * hadError );
	unsigned int extraSpace;
    CoronaEffectCallbacksExtensionHeader * next;
};
``````

##### size ~^(required)^~
When creating an instance of this type, set this member to the number of bytes the `CoronaEffectCallbacks` type is. This field is used for identifying the API version.

``````c
size = sizeof(CoronaEffectCallbacks);
``````

##### shaderBind ~^(optional)^~
During render recording, this operation is called whenever a particular variant of the effect becomes the
one currently bound by the renderer. This can happen through a regular draw or during a [raw draw][native.C.CoronaGraphics.CoronaShaderRawDraw].

A variant here means a specific combination of the active [shader version][native.C.CoronaGraphics.CoronaShaderGetVersion] and whether any rect distortion is taking place.

Note that two objects rendering in a row may both use the same version of the effect. The first object might cause the renderer's bound effect to change, but the second
will not, and so at least in that case this will not be called. This operation is therefore more useful for "global" resources used by the effect, such as resetting counters
or lists.

##### shaderDetach ~^(optional)^~
This is called when the effect data is detached from a paint, such as the display object being removed or a different paint or effect
being assigned. It can be used to clean up any "local" resources.    

##### prepare ~^(optional)^~
This is called during render recording if the effect needs to be validated, i.e some operation was performed on the display object and might have potentially left
the effect in a dirty state. In particular, assigning the effect in the first place is such an operation.

(**TODO**)A `mod` of 1 indicates the program used by rect distortion. (**TODO** link)
(**TODO**)`w` and `h` have the object's stage bounds... they might be meant for multi-pass?

##### drawParams ~^(optional)^~
Used when drawing with the effect, to perform custom operations.

Although similar in spirit to [native.C.CoronaObjects.CoronaObjectDrawParams], it operates at a different granularity. In particular, to have arrived at the
point where `drawParams` matters, a display object's "original" draw behavior will be in the middle of happening.

[The "shader" flavor][native.C.CoronaGraphics.CoronaShaderDrawParams] of draw params allow some control about how the current batch of geometry is drawn, if at all,
and this is done using [raw draws][native.C.CoronaGraphics.CoronaShaderRawDraw].

This field is ignored if all its members are `NULL` or 0.

##### nameToIndex ~^(optional)^~
If the `name` used to read or write an effect data's properties is not found among the vertex or uniform
data, this function is called. Returning an integer &lt; 0 can be used to indicate that the name is not
valid. Otherwise, the index is passed along to `getData()` or `setData()` as `dataIndex`.

##### getData ~^(optional)^~
Called when reading an effect data's property and `nameToIndex()` yields a valid data index.

If `hadError` was 0 (the default), a value pushed onto the stack is treated as the retrieved data. In this case
`getData()` should return 1, or 0 otherwise.

When there is an error, a message is printed and nothing is returned. If `getData()` returned non-0 and the top
of the stack contains a string, it will be incorporated into the message.

Note that this callback occurs during the Lua part of the frame, before any recording has begun.

##### setData ~^(optional)^~
Called when writing an effect data's property and `nameToIndex()` yields a valid data index.

If `hadError` was 0 (the default), a non-0 return value indicates that an assignment did occur.

When there is an error, a message is printed and nothing is returned. If `setData()` returned non-0 and the top
of the stack contains a string, it will be incorporated into the message.

In the non-error case, if `shouldInvalidate` is non-0 (the default), the object will be considered dirty and need
to be revalidated. (**TODO** probably this should only happen when an assignment occurs...)

Note that this callback occurs during the Lua part of the frame, before any recording has begun.

##### extraSpace ~^(optional)^~
If this is &gt; 0, the effect data will be given at least this many bytes of scratch space (initialized to 0), and made available to the
various callbacks as `userData`. Solar itself does nothing with this memory other than manage its lifetime.
    
##### next ~^(optional)^~
Not yet used; for possible expansion.
