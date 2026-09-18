# TextureResourceCapture

> --------------------- ------------------------------------------------------------------------------------------
> __Parent__            [TextureResource][api.type.TextureResource]
> __Library__           [graphics.*][api.library.graphics]
> __Revision__          [REVISION_LABEL](REVISION_URL)
> --------------------- ------------------------------------------------------------------------------------------


## Overview

The object created by [graphics.newTexture()][api.library.graphics.newTexture] when the specified [type][api.type.TextureResource.type] is `"capture"`. This texture resource is able to capture existing screen content. 


## Properties

#### [texture.width][api.type.TextureResourceCapture.width]

#### [texture.height][api.type.TextureResourceCapture.height]

#### [texture.pixelWidth][api.type.TextureResourceCapture.pixelWidth]

#### [texture.pixelHeight][api.type.TextureResourceCapture.pixelHeight]


## Methods

#### [texture:newCaptureEvent()][api.type.TextureResourceCapture.newCaptureEvent]


## Gotchas

* All objects of this type are subject to manual texture management. In order to free them from memory, you must [release][api.type.TextureResource.releaseSelf] them when they are no longer required.

* The capture will be "upside-down" and so (at least in OpenGL) a `1 - texCoord.y` transform should be performed.
