# CoronaObjectSendMessage()

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectSendMessage
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

int CoronaObjectSendMessage( const CoronaDisplayObject * object, const char * message, const void * payload, unsigned int size );

/**
 Send a message immediately to a given display object.
 @param object Boxed display object.
 @param message Null-terminated string describing the message and its payload.
 @param payload Arbitrary payload appropriate to `message`.
 @param size Number of bytes in `payload`.
 @return If non-0, the message was delivered.
*/
