# Runtime.getFrameStartTime()

> --------------------- ------------------------------------------------------------------------------------------
> __Type__              [Function][api.type.Function]
> __Object__            [Runtime][api.type.Runtime]
> __Library__           none
> __Return value__      [Number][api.type.Number]
> __Revision__          [REVISION_LABEL](REVISION_URL)
> __Keywords__          runtime, getFrameStartTime
> __See also__          [Runtime.getFrameID()][api.type.Runtime.getFrameID]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

Returns the time (in milliseconds) at the start of this frame.

ALSO enterFrame as 'time', but this is aimed at complementing getFrameID

BLAH BLAH

Determines if the device is capable of providing events for a given event source such as `"accelerometer"` or `"gyroscope"`.

This function returns `true` if the event source exists, meaning it is okay to call [EventDispatcher:addEventListener()][api.type.EventDispatcher.addEventListener] to handle its events.

It returns `false` if the event source does not exist. For example, if this returns false for `"gyroscope"` then this would indicate that the appropriate hardware was not found on the device.

## Syntax

	Runtime.getFrameStartTime( )

## Example

``````lua
if Runtime:hasEventSource( "gyroscope" ) then
    Runtime:addEventListener( "gyroscope", myListener )
end
``````
