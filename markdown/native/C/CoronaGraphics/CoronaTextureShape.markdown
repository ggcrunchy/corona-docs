# CoronaTextureShape

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaTextureShape
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

typedef enum {
	/**
	*/
	kTextureShape_2D,

	/**
	*/
	kTextureShape_1D,

	/**
	*/
	kTextureShape_3D,

	/**
	*/
	kTextureShape_Cube,

	/**
		non-normalized
	*/
	kTextureShape_Rectangle
	
// TODO? seems like buffer and ms probably would use an extension?
	// latter is target only, I think, and former wants potentially large buffers?
	// maybe some indirection thing?
} CoronaTextureShape;
