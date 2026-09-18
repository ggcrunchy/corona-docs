# graphics.defineVertexExtension()

> --------------------- ------------------------------------------------------------------------------------------
> __Type__				[Function][api.type.Function]
> __Library__			[graphics.*][api.library.graphics]
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			shaders, effects, graphics, vertices
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

Per the name, most display objects have a visual component, and at some point this consists of geometry / triangles. These in turn
consist of little packets of information called vertices: the position, a color, what part of an image this is, and some user data.

Extensions let us tack on details of our own.

When hardware support is available, we can push this further still, with instancing. In this case, our geometry might consist of
the usual vertices (or maybe augmented), plus some instance-specific detail, e.g. an index or a set of weights. The first set can
then be repeated several times at minimal cost, with each iteration paired up with one bit of this data.

(**TODO** confusing, probably add pseudo-code loop?)
(**TODO** 1000 objects each with own matrix...)

An attribute stream is termed vertex-rate in the ordinary case, or instance-rate otherwise.

Returns `true` on success, or `false` if otherwise (invalid parameters or conflicts).

## Syntax

	graphics.defineVertexExtension( extension )
	
##### extension ~^(required)^~
_[Table][api.type.Table]._ Table which defines a vertex extension &mdash; see the next two sections for details.


## Extension Table Reference

##### name ~^(required)^~
_[String][api.type.String]._ The name of this extension. It must be unique among any vertex extension currently in use.

This may be supplied to an [effect definition][api.library.graphics.defineEffect].

(**TODO** assigning *Extension property)

##### instanceByID ~^(optional)^~
_[Boolean][api.type.Boolean]_ If true, adds the following read-only, 0-based instance IDs to shaders:

`CoronaInstanceID` (`int`)
`CoronaInstanceFloat` (`float`)  to shaders.

The feature must be supported. **TODO** LINK

This is different from instance-rate attributes and allows an effect to still be instanced (**TODO** PathExtension.instances link)
without them. It will often be redundant if such attributes are being used.
							
##### array part of `extension` ~^(required)^~
1 to (**TODO** LINK to limit) component description [tables][api.type.Table]. See the next section for details.

## Component Table Reference

##### name ~^(required)^~
_[String][api.type.String]._ Unique attribute name.

In an effect using this vertex extension, we can access attributes in the vertex kernel, with names according to the following:

* "Corona" is added as a prefix
* the first character is uppercased, if not so already
* in the case of windowed attributes, an index is added as suffix

As one example, a "normal" attribute would become `CoronaNormal`. A windowed attribute like "controlPoint" becomes `CoronaControlPoint1`,
`CoronaControlPoint2`, etc.

##### type ~^(required)^~
_[String][api.type.String]._ Currently, either "byte" or "float", indicating the type of value on the CPU side.

(**TODO** have a list...)

##### normalized ~^(optional)^~
_[Boolean][api.type.Boolean]._ If true and the data type is an integer, convert it to float between 0 and 1 on the GPU side.

##### componentCount ~^(optional)^~
_[Number][api.type.Number]._ Integer from 1 to 4, describing how many components make up the attribute. The default is 1.

##### instancesToReplicate ~^(optional)^~
_[Number][api.type.Number]._ When doing an instanced draw call, this is how many times to reuse this attribute before moving on to
the next one. (If > 1, multi-instancing support is required. **TODO** LINK)

If absent, this is a vertex-rate attribute.

##### windowSize ~^(optional)^~
_[Number][api.type.Number]._ If this is an integer > 1, attributes "name1", "name2", etc. up to this size will be added, using
the type, component count, and normalization. (**N.B.** These each count toward the maximum attribute count.)

This provides a limited about of adjacency, such as for curves. To use an earlier example with a window of 2, the first vertex
will see `CoronaControlPoint1` and `CoronaControlPoint2`. The window "slides" over in the second vertex: `CoronaControlPoint1`'s
old value gets kicked out and replaced by `CoronaControlPoint2`'s value, and that in turn is replaced by something new.

This is built on the mechanism behind `instancesToReplicate`, and will implicitly set it to 1 if absent.

##### instanced ~^(required)^~
_[boolean][api.type.Boolean]._ If true, this is shorthand for `instancesToReplicate = 1`. (If another value is provided, this is ignored.)
