# EarlyOutableIgnorableMethodParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, EarlyOutableIgnorableMethodParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

... "Like IgnorableMethodParams" ...
but can take "before" results into consideration

 This may also be used to augment and/or override a built-in method. When `before` logic is
 provided, getting certain results might rule out any meaningful follow-up behavior, so early-outs
 are available.

 With a given method, this can take on the form:
 
 ```
   local result = default
   if before then
     result = before( ..., result )
     if CanEarlyOut( result ) then
      return result
     end
   end
   result = original( ..., result );
   result = after( ..., result );
 ```
 
 where all three functions take the same arguments.

 At the moment, the `CanEarlyOut` predicate is either "result was true" (`earlyOutIfNonZero`)
 or "result was false".

 The `before` and `after` functions may be NULL, in which case the respective function is
 not called. Similarly, the stock behavior is skipped if `ignoreOriginal` is non-0.
*/


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
its corresponding bookend functions with a specific function pointer signature.

##### header  ~^(required)^~
[Header][native.C.CoronaObjects.CoronaObjectParamsHeader] common to all params structs, used to stitch them into the list used to [build a method stream][native.C.CoronaObjects.CoronaObjectsBuildMethodStream].

##### before ~^(optional)^~
If not `NULL`, this is called before the method's built-in behavior.

##### after ~^(optional)^~
If not `NULL`, this is called after the method's built-in behavior.

##### ignoreOriginal ~^(optional)^~
If this is non-0, the stock behavior for this method&mdash;`original( ... )` in the code snippet above&mdash;is skipped.

##### earlyOutIfNonZero ~^(optional)^~
TODO

##### separateScopes ~^(optional)^~
(**TODO** "for possible future use"; deals with handle-scoping, used by the various methods)

