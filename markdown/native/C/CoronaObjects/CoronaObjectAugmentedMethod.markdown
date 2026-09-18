# CoronaObjectAugmentedMethod

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaGraphics.h, CoronaObjectAugmentedMethod
> __See also__			[CoronaObjects.h][native.C.CoronaObjects]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIPEE

Enumerated type describing a given Solar display object method. Generally these map to underlying `virtual` methods.

This is used when building a [method stream][native.C.CoronaObjects.CoronaObjectsBuildMethodStream] to indicate the method in question,
alongside a params `struct` derived from a [common header][native.C.CoronaObjects.CoronaObjectParamsHeader].

The params are typically designed so that zeroing them out provides useful and obvious defaults.

Although summaries are given&mdash;sometimes with more enlightening details in the params&mdash;much of this assumes some familiarity with the Solar2D source, in particular from `librtt/Display`: `Rtt_MDrawable.h`, `Rtt_DisplayObject.h`, `Rtt_GroupObject.h` in particular.

**IMPLEMENTATION NOTE** These were intended to be exhaustive, given the set of overloadable methods. Many are probably pointless or
demand too much inside knowledge to be generally useful, and it might be a win to just remove them. Some new methods have also been
added in the interim, although largely these would fall into the same category.

## Basic Constants

This enum provides the following constants:

* `kAugmentedMethod_None` &mdash; No method.
* `kAugmentedMethod_Count` &mdash; The current method type count. The specific value should not be relied upon.

## Useful Method Constants

The following have come up in practice, when developing test and sample plugins:

* `kAugmentedMethod_Draw` &mdash; Called if an object is visible and unculled, when recording render calls. [PARAMS][native.C.CoronaObjects.CoronaObjectDrawParams]
* `kAugmentedMethod_CanCull` &mdash; When recording render calls, this method is invoked to ask whether an image should perform a cull test. If not, it will always be drawn, even if hidden. (This is useful, for instance, if the "draw" is actually an event.) [PARAMS][native.C.CoronaObjects.CoronaObjectBooleanResultParams]
* `kAugmentedMethod_CanHitTest` &mdash; When doing touch events and "prepare" operations (**TODO** obscure...), this method is invoked to ask whether an object should participate in hit tests: if not, it will never be hit. [PARAMS][native.C.CoronaObjects.CoronaObjectBooleanResultParams]

* `kAugmentedMethod_OnMessage` &mdash;

     This method is invoked explicitly on an object via [sending a message][native.C.CoronaObjects.CoronaObjectSendMessage]. [PARAMS][native.C.CoronaObjects.CoronaObjectOnMessageParams]

* `kAugmentedMethod_SetValue` &mdash;

     This method is invoked when writing a property to an object. [PARAMS][native.C.CoronaObjects.CoronaObjectSetValueParams]
    
* `kAugmentedMethod_Value` &mdash;

     This method is invoked when reading a property from an object. [PARAMS][native.C.CoronaObjects.CoronaObjectValueParams]
    
* `kAugmentedMethod_OnFinalize` &mdash;

     This method is invoked just before an object is destroyed. [PARAMS][native.C.CoronaObjects.CoronaObjectOnFinalizeParams]

## Miscellaneous Method Constants

The following seem to be of either lesser or no importance.

* `kAugmentedMethod_AddedToParent` &mdash;

     This method is invoked after a new object is added to a group (possibly the stage) but before
     any of its Lua-side presence is established. [PARAMS][native.C.CoronaObjects.CoronaObjectParentParams]
    
* `kAugmentedMethod_DidMoveOffscreen` &mdash;

     This method is invoked when the object stops being visible. [PARAMS][native.C.CoronaObjects.CoronaObjectBasicParams]
    
* `kAugmentedMethod_DidUpdateTransform` &mdash;

     This method is invoked following an `UpdateTransform()` and some of its subsequent steps.
     [PARAMS][native.C.CoronaObjects.CoronaObjectMatrixParams]
    
* `kAugmentedMethod_GetSelfBounds` &mdash;

     This method is invoked when an object must calculate its bounds. [PARAMS][native.C.CoronaObjects.CoronaObjectRectResultParams]
    
* `kAugmentedMethod_GetSelfBoundsForAnchor` &mdash;

     This method is invoked when an object must calculate its anchor-related bounds. [PARAMS][native.C.CoronaObjects.CoronaObjectRectResultParams]
    
* `kAugmentedMethod_HitTest` &mdash;

     This method is invoked when an object is hit-tested for touch purposes. [PARAMS][native.C.CoronaObjects.CoronaObjectBooleanResultPointParams]
    
* `kAugmentedMethod_OnCreate` &mdash;

     This method is invoked after an object has been constructed and set up.
     [PARAMS][native.C.CoronaObjects.CoronaObjectOnCreateParams]
    
* `kAugmentedMethod_Prepare` &mdash;

     This method is invoked when an object is setting up some resources it needs. [PARAMS][native.C.CoronaObjects.CoronaObjectBasicParams]
    
* `kAugmentedMethod_RemovedFromParent` &mdash;

     This method is invoked just before an object is removed, while still belonging to a parent
     (possibly the stage). [PARAMS][native.C.CoronaObjects.CoronaObjectParentParams]
    
* `kAugmentedMethod_Rotate` &mdash;

     This method is invoked when the object's rotation is assigned or updated. [PARAMS][native.C.CoronaObjects.CoronaObjectRotateParams]
    
* `kAugmentedMethod_Scale` &mdash;

     This method is invoked when the object's scale is assigned or updated. [PARAMS][native.C.CoronaObjects.CoronaObjectScaleParams]
    
* `kAugmentedMethod_Translate` &mdash;

     This method is invoked when the object's position is assigned or updated. [PARAMS][native.C.CoronaObjects.CoronaObjectTranslateParams]
    
* `kAugmentedMethod_UpdateTransform` &mdash;

     This method is invoked in various circumstances where the object's transformation matrix has
     been updated. [PARAMS][native.C.CoronaObjects.CoronaObjectBooleanResultMatrixParams]
    
* `kAugmentedMethod_WillMoveOnscreen` &mdash;

     This method is invoked when the object becomes visible. [PARAMS][native.C.CoronaObjects.CoronaObjectBasicParams]

## Group Method Constants

The following pertain specifically to group objects.

* `kAugmentedMethod_DidInsert` &mdash;

     This method is invoked after inserting a child into a group. [PARAMS][native.C.CoronaObjects.CoronaObjectDidInsertParams]

* `kAugmentedMethod_DidRemove` &mdash;

     This method is invoked after removing a child from a group. [PARAMS][native.C.CoronaObjects.CoronaGroupBasicParams]
