# EarlyOutableIgnorableMethodParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, EarlyOutableIgnorableMethodParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

A params struct following this interface may be used to augment and / or override a built-in display object method.

Unlike the similar [IgnorableMethodParams][native.C.CoronaObjects.IgnorableMethodParams], the `before` bookend is
given some special consideration: given a certain result, there might not be a meaningful way to continue, so early
exits are available.

The call takes on the following form, in pseudo-code:
 
``````lua
local result = default
if before then
	result = before( self, userData, ..., result )
	if CanEarlyOut( result ) then
		return result
	end
end
result = original( ..., result )
result = after( self, userData, ..., result )
``````
 
where the `...` are any arguments common to all three functions.

The `CanEarlyOut` predicate may currently be either "result was true" (non-0) or "result was false" (0).

Any / all of these function calls may be omitted, as described below.


## Syntax

Params with this interface have the following shape:

``````c
typedef struct
{
	CoronaObjectParamsHeader header;
	EarlyOutableIgnorableMethodParamsBookend_FUNC before, after;
	int ignoreOriginal, earlyOutIfNonZero, separateScopes;  
} EarlyOutableIgnorableMethodParams_TYPE;
``````

The names `EarlyOutableIgnorableMethodParams_TYPE` and `EarlyOutableIgnorableMethodParamsBookend_FUNC` are placeholders for the actual struct implementing this interface, and
its corresponding bookend functions;the name refers to them being called on each side of the original&mdash;with a specific function pointer signature.

##### header  ~^(required)^~
[Header][native.C.CoronaObjects.CoronaObjectParamsHeader] common to all params structs, used to stitch them into the list used to [build a method stream][native.C.CoronaObjects.CoronaObjectsBuildMethodStream].

##### before ~^(optional)^~
If not `NULL`, this is called before the method's built-in behavior.

##### after ~^(optional)^~
If not `NULL`, this is called after the method's built-in behavior.

##### ignoreOriginal ~^(optional)^~
If this is non-0, the stock behavior for this method&mdash;`original( ... )` in the code snippet above&mdash;is skipped.

##### earlyOutIfNonZero ~^(optional)^~
If this is non-0, the `CanEarlyOut()` predicate is "result was true". Otherwise, the predicate is "result was false".

##### separateScopes ~^(optional)^~
(**TODO** "for possible future use"; deals with handle-scoping, used by the various methods)

