# CoronaObjectOnMessageParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectOnMessageParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

These params are used to respond to [message][native.C.CoronaObjects.CoronaObjectSendMessage]s.

## Syntax

``````c
typedef struct CoronaObjectOnMessageParams {
    CoronaObjectParamsHeader header;
    void (*action)( const CoronaDisplayObject * self, void * userData, const char * message, const void * data, unsigned int size );
    int preserveScope;
} CoronaObjectOnMessageParams;
``````

##### header ~^(required)^~
[Header][native.C.CoronaObjects.CoronaObjectParamsHeader] common to all params structs, used to stitch them into the list used to [build a method stream][native.C.CoronaObjects.CoronaObjectsBuildMethodStream].

##### action ~^(optional)^~
If `NULL`, this is a no-op. Otherwise, this is called immediately after being sent a message.

##### preserveScope ~^(optional)^~
(**TODO** "for possible future use"; deals with handle-scoping, whether this remains in the sender's scope)
