# CoronaTextureFormatFlags

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaTextureFormatFlags
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

	/**
		should test for renderabliity? else use defaults
	*/
	kTextureFormatFlag_ProbeRenderability = 1 << 0,
	
	/**
		assert "#1" is renderable? (mut. ex. with probe); else default is false
	*/
	kTextureFormatFlag_IsRenderable1 = 1 << 1,
	
	/**
		ditto, "#2" (viz. 1 = depth, 2 = stencil)
	*/
	kTextureFormatFlag_IsRenderable2 = 1 << 2,
	
	/**
		does this format support linear filtering?
	*/
	kTextureFormatFlag_HasLinearFiltering = 1 << 3,
	
	/**
		if word packed, is a REV format?
	*/
	kTextureFormatFlag_IsTypeReversed = 1 << 4
