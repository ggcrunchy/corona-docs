# CoronaObjectValueParams

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectValueParams
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

(**TODO** bookend)

/**
 CoronaObjectValueParams

typedef struct CoronaObjectValueParams {
    CoronaObjectParamsHeader header;
    CoronaObjectValueBookend before, after;
    int ignoreOriginal, disallowEarlyOut, earlyOutIfZero, separateScopes;
} CoronaObjectValueParams;

 This may be used to augment and/or override the `Value` method. When `before` logic is
 provided, getting a result (or alternatively, not getting one) might rule out any meaningful
 follow-up behavior, so early-outs are available.

 This can take on the form:
 
 ```
   local result = 0
   if before then
     result = before( ..., result )
     if CanEarlyOut( result ) then
      return result
     end
   end
   result = result + original( ..., result );
   result = after( ..., result );
 ```
 
 where all three functions take the same arguments.

 At the moment, the `CanEarlyOut` predicate is either "result is 0" ( `earlyOutIfZero`), or
 "result is non-0". It is also possible to suppress early-outs by setting `disallowEarlyOut`.

 The `before` and `after` functions may be NULL, in which case the respective function is
 not called. Similarly, the stock behavior is skipped if `ignoreOriginal` is non-0.

 Although only the top value on the stack will actually be used as the ultimate value, the
 intermediate results can be accumulated, say to concatenate multiple values at the end.
 
 Its functions have signature `method( const CoronaDisplayObject * self, void * userData, lua_State * L, const char key[], int * result )`.
*/
