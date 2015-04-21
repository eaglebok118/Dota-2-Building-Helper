# Dota 2 Building Helper v2.1

This is an attempt at rewriting most of the Building Helper core to add or improve support for:
* Multiplayer
* Multiple builders building multiple buildings at the same time
* Shift-Queueing (like RTS games)


The intent is that this will be merged back in to Building Helper once it's working but for the moment it's very work in progress (read: NOT WORKING)
The code and API it exposes should remain the same once it's done so developers shouldn't need to change anything.

If you want the current actually functional Building Helper, go here. [Building-Helper](https://github.com/Myll/Dota-2-Building-Helper)

Update 21/4:
* First "Viable" release
	- Shift-queue implemented, needs a bit more testing
	- Should work in multiplayer, untested

Notes:

The core of the code has been restructured so that each builder owns a queue of current work for them, and they process the work from their queue. Also now using T__'s [fantastic Gridnav implementation](https://moddota.com/forums/discussion/comment/731/#Comment_731). It's somewhat expensive modifying the gridnav on the fly (generates a lot of <unit> has been thinking for <seconds>!!! warnings), might be an issue on big maps or with big buildings (multiple modifications)

API Changes
* Added onConstructionCancelled for when a player right clicks while buildings are shift queued, this is called once for each building cancelled
* Added onConstructionFailed for when a building can no longer be placed on that gridnav square