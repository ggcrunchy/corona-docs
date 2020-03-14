# Runtime.getFrameID()

> --------------------- ------------------------------------------------------------------------------------------
> __Type__              [Function][api.type.Function]
> __Object__            [Runtime][api.type.Runtime]
> __Library__           none
> __Return value__      [Number][api.type.Number]
> __Revision__          [REVISION_LABEL](REVISION_URL)
> __Keywords__          runtime, getFrameStartTime
> __See also__          [Runtime.getFrameStartTime()][api.type.Runtime.getFrameStartTime]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

Returns a value that identifies the current frame, say for debugging or to handle at-most-once-per-frame actions.

As an example of the latter, pathfinding might be too expensive to perform twice, or once and then not even use, so we can trigger it on demand
and then reuse the result throughout the current frame. To do this, we only need to watch a single variable.

ALSO enterFrame event as 'frame', but as free function can be used from timers or proxied transitions, too, without potential ordering concerns

BLAH BLAH

Determines if the device is capable of providing events for a given event source such as `"accelerometer"` or `"gyroscope"`.

This function returns `true` if the event source exists, meaning it is okay to call [EventDispatcher:addEventListener()][api.type.EventDispatcher.addEventListener] to handle its events.

It returns `false` if the event source does not exist. For example, if this returns false for `"gyroscope"` then this would indicate that the appropriate hardware was not found on the device.

## Syntax

	Runtime.getFrameID( )

## Example

``````lua
if Runtime:hasEventSource( "gyroscope" ) then
    Runtime:addEventListener( "gyroscope", myListener )
end
``````
