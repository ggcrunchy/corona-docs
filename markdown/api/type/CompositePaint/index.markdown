# CompositePaint

> --------------------- ------------------------------------------------------------------------------------------
> __Parent__            [Paint][api.type.Paint]
> __Library__           [display.*][api.library.display]
> __Revision__          [REVISION_LABEL](REVISION_URL)
> __Keywords__          composite paint, multitexture
> __See also__          [object.fill][api.type.ShapeObject.fill]
>						[object.stroke][api.type.ShapeObject.stroke]
>                       [Filters, Generators, Composites][guide.graphics.effects] _(guide)_
> --------------------- ------------------------------------------------------------------------------------------


## Overview

Composite paints contain multiple images, thus enabling multi-texturing.

## Syntax

``````
local paint = {
    type = "composite",
    paint1 = ,
    paint2 =
}
``````

##### type ~^(required)^~
_[String][api.type.String]._ String value of `"composite"`.

##### paint1 ~^(required)^~
_[Table][api.type.Table]._ A table that specifies a [BitmapPaint][api.type.BitmapPaint]. See __Limitations__ below.

##### paint2 ~^(required)^~
_[Table][api.type.Table]._ A table that specifies a [BitmapPaint][api.type.BitmapPaint]. See __Limitations__ below.

##### baseDir ~^(optional)^~
_[Constant][api.type.Constant]._ Specifies the base directory where filename is located. Options include `system.ResourceDirectory`, `system.DocumentsDirectory`, `system.TemporaryDirectory` and `system.CachesDirectory`. Default is `system.ResourceDirectory`.

##### extraPaints ~^(optional)^~
_[Table][api.type.Table]_ An array that specifies one or more [BitmapPaint][api.type.BitmapPaint]s. See __Limitations__ below.

This is intended for effects with more than two textures. One or more samplers may be declared in the effect, with no particular name restrictions. (**TODO** link for texture limits) If the names can be paired up with corresponding paints in this array, and
the paint can match the sampler's type, the two sides are compatible and the effect will be assigned. (**TODO** bad match...) It is fine if `extraPaints` has **more** paints than necessary for a match, so long as it can honor all the effect's needs. 

(**TODO** this is rough still)

## Limitations

Because of the way multi-texturing works, both `paint1` and `paint2` will be rendered using the same texture coordinates. Because [GradientPaints][api.type.GradientPaint] and [ImageSheetPaints][api.type.ImageSheetPaint] use different texture coordinates from plain [BitmapPaints][api.type.BitmapPaint], you will get unexpected results unless you use plain [BitmapPaints][api.type.BitmapPaint] for `paint1` and `paint2`. 

## Properties

_(Inherits properties from [Paint][api.type.Paint])_

## Example

``````lua
local paint = {
    type = "composite",
    paint1 = { type="image", filename="wood.png" },
    paint2 = { type="image", filename="dust.png" }
}

local rect = display.newRect( 200, 200, 300, 300 )
rect.fill = paint
rect.fill.effect = "composite.average"
``````
