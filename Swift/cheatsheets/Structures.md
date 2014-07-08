# Structures

## Basic structs
```swift
struct Point {
    var x, y: Double
}
struct Size {
    var width, height: Double
}
struct Rect {
    var origin: Point
    var size: Size
}

var point = Point(x: 0.0, y: 0.0)
var size = Size(width: 640.0, height: 480.0)
var rect = Rect(origin: point, size: size)
```

## Properties
```swift
struct Rect {
    ...

    var area: Double {
        return size.width * size.height
    }
}
```

## Methods
```swift
struct Rect {
    ...
    func isBiggerThanRect(other: Rect) -> Bool {
        return self.area > other.area
    }
}
```

## Differences Between Structures vs. Classes
1. Structures cannot be inherited
1. Structures use pass-by-value i.e. values are copied whereas classes use pass-by-reference

## Mutating a structure
```swift
struct Point {
    var x, y: Double

    mutating func moveToTheRightBy(dx: Double) {
        x += dx
    }
}

let point = Point(x: 0.0, y: 0.0)
point.moveToTheRightBy(200.0)
// Error: Cannot mutate a constant!
```