# texture:newCaptureEvent()

> --------------------- ------------------------------------------------------------------------------------------
> __Type__              [Function][api.type.Function]
> __Object__            [TextureResourceCapture][api.type.TextureResourceCapture]
> __Return value__      [ShapeObject][api.type.ShapeObject]
> __Library__           [graphics.*][api.library.graphics]
> __Revision__          [REVISION_LABEL](REVISION_URL)
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

This method creates a new object that can be placed in the hierarchy like any other display object.

It is like a normal [rect][api.type.ShapeObject], except it participates in neither culling nor hit
tests, and a "draw" writes the screen content it occupies to its capture texture, which may be
sampled by paints.

These rects only hold a weak reference to the texture and the "draws" will be no-ops if it has no
more strong references.


## Syntax

	texture:newCaptureEvent( [parent,] x, y, width, height )

##### parent ~^(optional)^~
_[GroupObject][api.type.GroupObject]._ An optional display group in which to insert the rectangle.

##### x / y ~^(required)^~
_[Number][api.type.Number]._ The __x__ and __y__ coordinates for the center of the rectangle.

##### width / height ~^(required)^~
_[Number][api.type.Number]._ Width and height of the rectangle.
(**TODO** Example)

## Gotchas

The placement is not pixel-perfect, so certain uses might have a little shimmer.
