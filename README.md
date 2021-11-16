# aka

## Abstract Keyboard Analyzer

Keyboard - physical key locations
```
[
	{"x": 0, "y": 0},
	{"x": 1, "y": 0}
]
```
Fingers - which fingers go with which keys, home row is index 0
```
[
	[0, 3, 4, 5],
	[1, 2, 6, 7]
]
```
Weighting
* Each metric should be compared to the ideal layout for just that _one_ metric (eg, a layout fully optimized for _just_ finger travel distance)
  * Probably going with decreasing values, so smaller numbers are better. If so, then a _perfect_ value in a specific category would be a zero
  * If increasing values, then a perfect score would be 100
* finger weights
* distance movement weights
  * separate weights per dimension and direction
  * separate per finger, or use the same for all
* track last keypress per finger
  * person could stay on that key or go back home, so take the better one (eg, `meme` shouldn't weight to and from home row twice for `m` and `e`, but just once)
  * assume fingers return to home row after a certain number of keys or on certain *reset characters* like space?
* travel time per finger/direction separate from weights as a separate way to optimize for same finger bigrams?
* All units should be relative, as long as they're consistent
* Track time to get to and from the home row per finger, so next press can start sooner, but eventually we'll be waiting for fingers to return
* Take into account whole hand moving when typing consecutive keys on the same row?
  * Not sure how practical it actually is, but for example if you had to type `uio` you'd probably move your whole hand and do a roll.
  * Would mean treating all fingers as if they're already on that row after the first travel time, incuding adding the time to then get back to the home row when it eventually changes
  * Doesn't seem to be a thing for me when typing `when` for `w` and `e`, although `we` seems to produce a quicker roll.
    * Maybe have presses pull the fingers next to them some fixed amount (eg, halfway to the row) so if you're typing on a row then the initial travel for the second key is lessened