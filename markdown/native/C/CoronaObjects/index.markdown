# index

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaObjects.h
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

## Enumerations

[CoronaObjectAugmentedMethod][native.C.CoronaObjects.CoronaObjectAugmentedMethod]

## Functions

[CoronaObjectsBuildMethodStream][native.C.CoronaObjects.CoronaObjectsBuildMethodStream]
[CoronaObjectGetAvailableSlot][native.C.CoronaObjects.CoronaObjectGetAvailableSlot]
[CoronaObjectGetParent][native.C.CoronaObjects.CoronaObjectGetParent]
[CoronaGroupObjectGetChild][native.C.CoronaObjects.CoronaGroupObjectGetChild]
[CoronaGroupObjectGetNumChildren][native.C.CoronaObjects.CoronaGroupObjectGetNumChildren]
[CoronaObjectInvalidate][native.C.CoronaObjects.CoronaObjectInvalidate]

## Base Params structs

[CoronaObjectParams][native.C.CoronaObjects.CoronaObjectParams]
[CoronaObjectParamsHeader][native.C.CoronaObjects.CoronaObjectParamsHeader]

## Param structs ("ignorable" policy)

Each of the following adheres to the [IgnorableMethodParams][native.C.CoronaObjects.IgnorableMethodParams] interface.

[CoronaObjectBasicParams][native.C.CoronaObjects.CoronaObjectBasicParams]
[CoronaObjectDrawParams][native.C.CoronaObjects.CoronaObjectDrawParams]
[CoronaObjectMatrixParams][native.C.CoronaObjects.CoronaObjectMatrixParams]
[CoronaObjectParentParams][native.C.CoronaObjects.CoronaObjectParentParams]
[CoronaObjectRectResultParams][native.C.CoronaObjects.CoronaObjectRectResultParams]
[CoronaObjectDidInsertParams][native.C.CoronaObjects.CoronaObjectDidInsertParams]
[CoronaObjectRotateParams][native.C.CoronaObjects.CoronaObjectRotateParams]
[CoronaObjectScaleParams][native.C.CoronaObjects.CoronaObjectScaleParams]
[CoronaObjectTranslateParams][native.C.CoronaObjects.CoronaObjectTranslateParams]
[CoronaGroupBasicParams][native.C.CoronaObjects.CoronaGroupBasicParams]

## Param structs ("ignorable + early-outable" policy)

Each of the following adheres to the [EarlyOutableIgnorableMethodParams][native.C.CoronaObjects.EarlyOutableIgnorableMethodParams] interface.

[CoronaObjectBooleanResultParams][native.C.CoronaObjects.CoronaObjectBooleanResultParams]
[CoronaObjectBooleanResultMatrixParams][native.C.CoronaObjects.CoronaObjectBooleanResultMatrixParams]
[CoronaObjectBooleanResultPointParams][native.C.CoronaObjects.CoronaObjectBooleanResultPointParams]

## Other Params structs

[CoronaObjectOnCreateParams][native.C.CoronaObjects.CoronaObjectOnCreateParams]
[CoronaObjectOnFinalizeParams][native.C.CoronaObjects.CoronaObjectOnFinalizeParams]
[CoronaObjectOnMessageParams][native.C.CoronaObjects.CoronaObjectOnMessageParams]
[CoronaObjectSetValueParams][native.C.CoronaObjects.CoronaObjectSetValueParams]
[CoronaObjectValueParams][native.C.CoronaObjects.CoronaObjectValueParams]

## Display Object builders

The following are like their `new*()` counterparts in the Lua [display][api.library.display] family, but
modify the resulting object by connecting it to a method stream.

[CoronaObjectsPushContainer][native.C.CoronaObjects.CoronaObjectsPushContainer]
[CoronaObjectsPushEmitter][native.C.CoronaObjects.CoronaObjectsPushEmitter]
[CoronaObjectsPushEmbossedText][native.C.CoronaObjects.CoronaObjectsPushEmbossedText]
[CoronaObjectsPushGroup][native.C.CoronaObjects.CoronaObjectsPushGroup]
[CoronaObjectsPushImage][native.C.CoronaObjects.CoronaObjectsPushImage]
[CoronaObjectsPushImageRect][native.C.CoronaObjects.CoronaObjectsPushImageRect]
[CoronaObjectsPushLine][native.C.CoronaObjects.CoronaObjectsPushLine]
[CoronaObjectsPushMesh][native.C.CoronaObjects.CoronaObjectsPushMesh]
[CoronaObjectsPushPolygon][native.C.CoronaObjects.CoronaObjectsPushPolygon]
[CoronaObjectsPushRoundedRect][native.C.CoronaObjects.CoronaObjectsPushRoundedRect]
[CoronaObjectsPushSnapshot][native.C.CoronaObjects.CoronaObjectsPushSnapshot]
[CoronaObjectsPushRect][native.C.CoronaObjects.CoronaObjectsPushRect]
[CoronaObjectsPushText][native.C.CoronaObjects.CoronaObjectsPushText]
