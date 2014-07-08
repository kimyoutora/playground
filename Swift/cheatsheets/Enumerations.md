# Enumerations

## Raw values
```swift
enum Planet: Int {
   case Mercury = 1, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune
}

let earthNumber = Planet.Earth.toRaw()
// earthNumber is 3
```

## Non-integer raw values
```swift
// Swift supports non-integer values as well
enum ControlCharacter: Character {
   case Tab = "\t"
   case Linefeed = "\n"
   case CarriageReturn = "\r"
}
```

## No underlying values
```swift
enum CompassPoint {
   case North, South, East, West
}

var directionToHead = CompassPoint.West
// directionToHead is inferred to be a CompassPoint
directionToHead = .East
```

## Associated values
```swift
enum TrainStatus {
   case OnTime
   case Delayed(Int)
}

var status = TrainStatus.OnTime
// status is inferred to be a TrainStatus
status = .Delayed(42)
```

## Initializers and Properties
```swift
enum TrainStatus {
   case OnTime, Delayed(Int)
   init() {
      self = OnTime
   }
   var description: String {
      switch self {
         case OnTime:
            return "on time"
         case Delayed(let minutes):
            return "delayed by \(minutes) minute(s)"
        }
    }
}
```

## Nested types
Tie status to trains

```swift
class Train {
   enum Status {
      case OnTime, Delayed(Int)
      init() {
         self = OnTime
      }
      var description: String { ... }
   }
   var status = Status()
}
```