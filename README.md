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
* finger weights
* distance movement weights
  * separate weights per dimension and direction
  * separate per finger, or use the same for all
* track last keypress per finger
  * person could stay on that key or go back home, so take the better one (eg, `meme` shouldn't weight to and from home row twice for `m` and `e`, but just once)
  * assume fingers return to home row after a certain number of keys or on certain *reset characters* like space?
* travel time per finger/direction separate from weights as a separate way to optimize for same finger bigrams?