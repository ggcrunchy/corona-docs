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

This is also available as ['frame'][api.event.enterFrame.frame] via enterFrame event listener functions.

## Example
 
``````lua
local frameID
function updatePathfinding( ) -- might get called before any of our enterFrame event listener functions
    local id = Runtime.getFrameID()

    if id ~= frameID then -- frame is new?
        frameID = id
		doExpensivePathfinding() -- this might be too expensive to perform twice, or once and then not even use, so we only trigger it on demand
		                         -- and then reuse the result for the rest of the frame
	end
end 
timer.performWithDelay(100, updatePathfinding)
``````
