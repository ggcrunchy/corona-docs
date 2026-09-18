
# graphics.defineEffect()

> --------------------- ------------------------------------------------------------------------------------------
> __Type__				[Function][api.type.Function]
> __Library__			[graphics.*][api.library.graphics]
> __Return value__		none
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			shaders, effects, graphics
> __See also__			[Custom Shader Effects][guide.graphics.customEffects] _(guide)_
>						[Filters / Generators / Composites][guide.graphics.effects] _(guide)_
>						[customFilter](https://github.com/coronalabs/sample-customFilter) _(sample)_
> --------------------- ------------------------------------------------------------------------------------------

## Overview

This function allows you to extend Corona and define a custom shader effect. Your custom effect can define either a vertex kernel or a fragment kernel (or&nbsp;both). These kernels are similar to shaders, except that they must define functions with a specific name and which conform to specific function signatures. 

See the [Custom Shader Effects][guide.graphics.customEffects] guide for a detailed explanation of how to write shader code for these kernels.

<div class="guide-notebox-imp">
<div class="notebox-title-imp">Note</div>

Custom effects are supported on iOS, Android, macOS&nbsp;desktop, and Win32&nbsp;desktop.

</div>


## Syntax

	graphics.defineEffect( effect )

##### effect ~^(required)^~
_[Table][api.type.Table]._ Table which defines a shader effect &mdash; see the next section for details.


## Effect Table Reference

The `effect` table can contain the following properties:

##### category ~^(required)^~
_[String][api.type.String]._ The category for the effect. This determines the number of input textures:

* `"generator"` &mdash; Assumes 0 input textures.
* `"filter"` &mdash; Assumes 1 input texture.
* `"composite"` &mdash; Assumes 2 input textures.

##### group ~^(optional)^~
_[String][api.type.String]._ The name of the group that the effect belongs to. While [built-in][guide.graphics.effects] effects have no name, custom effects are placed in the `"custom"` group by default. You can override this default by passing in a different group name.

##### name ~^(required)^~
_[String][api.type.String]._ A name which uniquely identifies the effect within a category. This must not conflict with a <nobr>pre-existing</nobr> name within a given category and group. Together with the `category` property and `group` property, this determines the full name of the effect that you assign to a [Paint][api.type.Paint] object as <nobr>`"<category>.<group>.<name>"`</nobr>.

##### fragment ~^(required)^~
_[String][api.type.String]._ The shader code for the fragment kernel. See __Fragment&nbsp;Kernels__ in the [Custom Shader Effects][guide.graphics.customEffects] guide. Note that this is __not__ required if the `vertex` property is set.

##### vertex ~^(required)^~
_[String][api.type.String]._ The shader code for the vertex kernel. See __Vertex&nbsp;Kernels__ in the [Custom Shader Effects][guide.graphics.customEffects] guide. Note that this is __not__ required if the `fragment` property is set.

##### isTimeDependent ~^(optional)^~
_[Boolean][api.type.Boolean]._ If the vertex or fragment kernel depends on time (the&nbsp;output varies with&nbsp;time), set this to `true`. The default <nobr>(if not provided)</nobr> assumes a value of `false`, meaning the kernel does not use time in its calculations.

(**TODO** unnecessary since version 22xx but needs hotfix)

##### timeTransform ~^(optional)^~
_[Table][api.type.Table]._ If the vertex or fragment kernel depends on time, you can use this to mitigate potentially large time values. See __Time&nbsp;Transforms__ in the  [Custom Shader Effects][guide.graphics.customEffects] guide.

##### vertexData ~^(optional)^~
_[Table][api.type.Table]._ This allows you to specify named parameters for your effect. You can specify up to four parameters, each of which is a `scalar` (float). See __Effect&nbsp;Parameters__ in the [Custom Shader Effects][guide.graphics.customEffects] guide for more information. Note that you can specify either `vertexData` or `uniformData` but not both.

##### uniformData ~^(optional)^~
_[Table][api.type.Table]._ This allows you to specify named parameters for your effect. You can specify up to four parameters, each of which can be a different type: `scalar` (float), `vec2` `vec3`, `vec4`, `mat3`, or `mat4`. See __Effect&nbsp;Parameters__ in the [Custom Shader Effects][guide.graphics.customEffects] guide for more information. Note that you can specify either `vertexData` or `uniformData` but not both.

##### dataType ~^(optional)^~
_[String][api.type.String]._ A name belonging to an [effect data type][native.C.CoronaGraphics.CoronaEffectRegisterEffectDataType]. (**N.B.** These are largely built on callbacks, most of them outside Lua, so currently this is strictly a C API.) Once the effect is assigned to a paint, its `effect` will acquire various capabilities conferred by its type. (**GL backend only**)

##### languageExtensions ~^(optional)^~
_[Table][api.type.Table]._ (**WIP, gl backend only**) Array of [Strings][api.type.String] of the form "NAME" or "NAME:behavior", where `NAME` is assumed to be an extension that the backend might or must support. These are injected before the shell. The behavior, if present&mdash;"require" being the default&mdash;should be one of those found in GLSL: "require", "enable",
"disable", or "warn".

##### vertexExtension ~^(optional)^~
_[String][api.type.String]._ A name belonging to a [vertex extension definition][api.library.graphics.defineVertexExtension]. The vertex kernel will
have the additional attributes supplied by the extension, possibly including instance-rate ones and / or instancing built-ins. (**GL backend only**)

Display objects must also be given compatible [PathExtension][api.type.PathExtension]s to be assigned such effects.

##### shellTweaks ~^(optional)^~
_[Table][api.type.Table]._ (**WIP, GL backend only**) Certain tweaks to the effect boilerplate, i.e. its "shell", can be made for special needs or convenience. Further details below.

## Example

`````lua
-- An effect that brightens each pixel
-- Usage: object.fill.effect = "filter.custom.myBrighten"
local kernel = {}
kernel.category = "filter"
kernel.name = "myBrighten"

kernel.fragment =
[[
P_COLOR vec4 FragmentKernel( P_UV vec2 texCoord )
{
	P_COLOR float brightness = 0.5;
	P_COLOR vec4 texColor = texture2D( CoronaSampler0, texCoord );

	// Pre-multiply the alpha to brightness
	brightness = brightness * texColor.a;

	// Add the brightness
	texColor.rgb += brightness;

	// Modulate by the display object's combined alpha/tint
	return CoronaColorScale( result );
}
]]

graphics.defineEffect( kernel )
`````

## Shell Tweaks Reference

(**WIP, GL backend only**)

The tweaks table can contain the following properties, all optional:

##### varFromPosZ
_[String][api.type.String]._ A name for a vertex kernel macro that reads the position attribute's z-coordinate.

This coordinate has always been standard in Solar's underlying geometry (**TODO** link), but largely goes unused. Polygons (**TODO** link) and
meshes (**TODO** link) have options to assign it, as do effect data types.

##### extraKernelArgumentFromPosZ
_[Boolean][api.type.Boolean]_ If this is true, the position attribute's z-coordinate is sent as a second argument to the vertex
kernel, which must have a signature like `P_POSITION vec2 VertexKernel( P_POSITION vec2 position, P_POSITION float extraArg )`.

It is fine to mix and match this and **varFromPosZ**.

##### posAttributeHasZ
_[Boolean][api.type.Boolean]_ If this is true and neither of the previous two properties is used, the position attribute is
interpreted as a `vec3`, and the vertex kernel must have a signature like `P_POSITION vec3 VertexKernel( P_POSITION vec3 position )`.

This is aimed at actual 3D effects and has wider workflow implications. (**TODO** links)

##### rhsZcoord
_[String][api.type.String]_ The vertex kernel does a transform like `left-hand-side matrix * right-hand-side vec4` to build the final
position. In the case of 2D positions, the vector on the right looks like "vec4( position, rhsZcoord, 1 )", with `rhsZcoord` defaulting
to "0.0". When positions are 3D, the vector is instead "vec4( position, 1 )" and this option is ignored.

Since the default vertex kernel still uses the shell, this property may be used even without **vertex**. This is also true for the
next few properties. 

##### lhsMatrix
_[String][api.type.String]_ By default the left-hand-side matrix described in the previous property is Solar's built-in orthographic
projection, but custom handling is possible with this option.

##### setPositionZ
_[String][api.type.String]_ By default the output position's z-value comes as part of the matrix-vector product described in the last
couple properties, but this allows it to be stomped on with a custom result.

##### declareUniforms
_[Boolean][api.type.String]_ or _[String][api.type.String]_ When this is true, either or both shader stages will automatically declare
the `u_UserData` uniforms, based on the corresponding index and type in their `uniformData` entries. The usual details about using uniforms
remain the same otherwise.

A value of "vertex" or "fragment" will restrict declarations to that stage only.

##### sampler0Type
_[String][api.type.String]_ A name belonging to a sampler or image type recognized by the backend, "sampler2D" being the default.
`CoronaSampler0` will be declared with this type, and Solar will discover the relevant details once the effect has been linked.
  
This has wider workflow implications. (**TODO** links)
  
##### sampler1Type
_[String][api.type.String]_ This follows the previous property, but applies to `CoronaSampler`.
