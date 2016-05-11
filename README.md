# Simple port of mapbox's cheap-ruler to Swift

This is a toy project to see what performance gains if any can be made from porting 
a javascript library (that was itself created specifically for speed) to Swift.

# Results

Results after having ported the entire library, tests and benchmarks:

```
➜ cheap-ruler git:(master) ✗ swift -O test.swift
swift implementation of "along" is 2.90 times faster
swift implementation of "area" is 0.13 times faster
swift implementation of "bearing" is 85.94 times faster
swift implementation of "buffer-point" is 104.71 times faster
swift implementation of "destination" is 47.14 times faster
swift implementation of "distance" is 6.77 times faster
swift implementation of "inside-bbox" is 8.61 times faster
swift implementation of "line-slice-along" is 0.17 times faster
swift implementation of "line-slice" is 0.37 times faster
swift implementation of "point-on-line" is 16.63 times faster
```

Interesting results for `buffer-point` with 104 times faster! And also `area` which only got 13% faster.

I have not tuned the Swift code at all, this is a straight port with only minor adjustments for ideomatic Swift. I'm new to Swift so that could probably be improved.

# Run benchmarks

```
git clone https://github.com/mapbox/cheap-ruler cheap-ruler-js
npm install benchmark
npm install turf
swift -O test.swift
```