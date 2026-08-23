# CoronaVertexExtension

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			iOS, CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaExternalBitmapFormat
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

(**TODO** )

/**
 Configuration for a vertex format that extends Solar's own, for use by effects and geometry.
*/
typedef struct CoronaVertexExtension {
    /**
     Required
     When creating an instance of this type, set this member to `size = sizeof(CoronaVertexExtension)`.
     This is required for identifying the API version used.
    */
    unsigned long size;

	/**
	 If non-0, extension is instanced.
	 This is instancing via a shader ID, and redundant if any attributes also request instancing.
	 To query support, call `system.getInfo( "instancingSupport" )`.
	*/
	int instanceByID;
	
    /**
     Number of extension attributes.
    */
    unsigned int count;
    
    /**
     Additional vertex attributes.
    */
    CoronaVertexExtensionAttribute * attributes;
} CoronaVertexExtension;
