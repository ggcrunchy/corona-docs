
# event.frame

> --------------------- ------------------------------------------------------------------------------------------
> __Type__              [Number][api.type.Number]
> __Event__             [enterFrame][api.event.enterFrame]
> __Revision__          [REVISION_LABEL](REVISION_URL)
> __Keywords__          enterframe, frame
> __See also__          [Runtime.getFrameID()][api.type.Runtime.getFrameID]
> --------------------- ------------------------------------------------------------------------------------------

## Overview

The current frame accessible by an enterFrame event listener function (which is called on every frame, until the event listener is removed).

## Example
 
``````lua
function printFrame( event )
    print ("Frame id: " .. event.frame )
end 
Runtime:addEventListener("enterFrame", printFrame)
``````
