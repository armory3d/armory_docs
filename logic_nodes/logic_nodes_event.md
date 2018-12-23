# Event

## On Event

Activates the node\(s\) being connected to Sent Event or Sent Global Event specified in other node\(s\) tree.

![](/assets/on-event.JPG)


## On Init

Activates the node\(s\) being connected to it on the first frame of the game.

![](/assets/On-Init.JPG)


## On Timer

Activates the node\(s\) being connected to after a Timer countdown on from the beginning of the game, repeatedly when box ticked.

![](/assets/On-Timer.JPG)


## On Update

Activates the node\(s\) being connected to it every frame.

![](/assets/On-Update.JPG)


## On Volume Trigger

The lower object-input is used as Volume, the upper one as object-input for the object that enters/leaves/overlaps with it. 

Enter-mode: Activates the connected nodes on the frame the object enters the volume, on all other frames it doesn't do that.

Leave-mode: Activates the connected nodes on the frame the object leaves the volume, on all other frames it doesn't do that.

Overlap-mode: Activates the connected nodes on the frame the object overlaps with the volume, on all other frames it doesn't do that.

![](/assets/on-volume-trigger.JPG)