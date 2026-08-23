# CoronaObjectSetValueParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectSetValueParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview


(**TODO** bookend)

WIP WIP WIP

/**
 CoronaObjectSetValueParams
 
 
 typedef struct CoronaObjectSetValueParams {
    CoronaObjectParamsHeader header;
    CoronaObjectSetValueBookend before, after;
    int ignoreOriginal, disallowEarlyOut, separateScopes;
} CoronaObjectSetValueParams;
 
 This may be used to augment and/or override the `SetValue` method. When `before` logic
 is provided, setting a value, might rule out any meaningful follow-up behavior, so early-outs
 are available.

 This can take on the form:
 
 ```
   bool result = false
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

 At the moment, the `CanEarlyOut` predicate is "result is true": a value was assigned.
 It is also possible to suppress early-outs by setting `disallowEarlyOut`.

 The `before` and `after` functions may be NULL, in which case the respective function is
 not called. Similarly, the stock behavior is skipped if `ignoreOriginal` is non-0.
 
 Its functions have signature `method( const CoronaDisplayObject * self, void * userData, lua_State * L, const char key[], int valueIndex, int * result )`.
*/
