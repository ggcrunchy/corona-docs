# Runtime.getFrameStartTime()

> --------------------- ------------------------------------------------------------------------------------------
> __Type__              [Function][api.type.Function]
> __Object__            [Runtime][api.type.Runtime]
> __Library__           none
> __Return value__      [Number][api.type.Number]
> __Revision__          [REVISION_LABEL](REVISION_URL)
> __Keywords__          runtime, getFrameStartTime
> __See also__          [Runtime.getFrameID()][api.type.Runtime.getFrameID], [time]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

Returns the time (in milliseconds) at the start of this frame.

This is also available as ['time'][api.event.enterFrame.time] via enterFrame event listener functions.

## Syntax

	Runtime.getFrameStartTime( )

## Example

``````lua
if Runtime:hasEventSource( "gyroscope" ) then
    Runtime:addEventListener( "gyroscope", myListener )
end
``````
