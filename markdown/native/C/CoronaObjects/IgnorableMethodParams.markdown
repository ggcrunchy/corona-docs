# IgnorableMethodParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, IgnorableMethodParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

A params struct following this interface may be used to augment and / or override a built-in display object method.

The call takes on the following form, in pseudo-code:
 
``````lua
before( self, userData, ... )
original( ... )
after( self, userData, ... )
``````
 
where the `...` are any arguments common to all three functions.

Any / all of these function calls may be omitted, as described below.

## Syntax

Params with this interface have the following shape:

``````c
typedef struct
{
	CoronaObjectParamsHeader header;
	IgnorableMethodParamsBookend_FUNC before, after;
	int ignoreOriginal, separateScopes;  
} IgnorableMethodParams_TYPE;
``````

The names `IgnorableMethodParams_TYPE` and `IgnorableMethodParamsBookend_FUNC` are placeholders for the actual struct implementing this interface, and
its corresponding bookend functions&mdash;the name refers to them being called on each side of the original&mdash;with a specific function pointer signature.

##### header  ~^(required)^~
[Header][native.C.CoronaObjects.CoronaObjectParamsHeader] common to all params structs, used to stitch them into the list used to [build a method stream][native.C.CoronaObjects.CoronaObjectsBuildMethodStream].

##### before ~^(optional)^~
If not `NULL`, this is called before the method's built-in behavior.

##### after ~^(optional)^~
If not `NULL`, this is called after the method's built-in behavior.

##### ignoreOriginal ~^(optional)^~
If this is non-0, the stock behavior for this method&mdash;`original( ... )` in the code snippet above&mdash;is skipped.

##### separateScopes ~^(optional)^~
(**TODO** "for possible future use"; deals with handle-scoping, used by the various methods)
