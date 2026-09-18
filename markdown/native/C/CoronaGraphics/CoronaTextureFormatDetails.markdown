# CoronaTextureFormatDetails

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaTextureFormatDetails
> __See also__			[CoronaGraphics.h][native.C.CoronaGraphics]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

/**
	TODO: Color format details
*/
typedef struct
CoronaTextureFormatDetails
{
	/**
	*/
	CoronaTextureFamily family;
		
	/**
	*/
	CoronaTextureInputKind inputKind;
	
	/**
	*/
	int flags;
	
	/**
		e.g. GL format
	*/
	int format;
	
	/**
		e.g. GL internalFormat
	*/
	int internalFormat;
	
	/**
		e.g. GL type
	*/
	int type;
} CoronaTextureFormatDetails;
