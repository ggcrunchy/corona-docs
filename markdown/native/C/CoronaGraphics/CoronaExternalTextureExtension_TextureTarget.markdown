# CoronaExternalTextureExtension_TextureTarget

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaExternalTextureExtension_TextureTarget
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

/**
	TODO: non-sampler2D target
*/
typedef struct CoronaExternalTextureExtension_TextureTarget {
	/**
		inherited
	*/
	CoronaExternalTextureExtensionBase common;

	/**
	*/
	CoronaTextureFamily family;

	/**
	*/
	CoronaTextureShape shape;
	
	/**
	*/
	int isArray;
	// TODO: these actually describe the samplers; family and array-ness is more or less right
		// TODO: want some way to specify layers (and levels, with mipmaps)...
		// any way to do so that doesn't just blow up combinatorically?
	// there are some target + array-ness combinations to work out
} CoronaExternalTextureExtension_TextureTarget;
