# Pattern Matching

## Switch
```swift
// basic values
func describe(value: String) {
    switch value {
        case "one":
            println("a few")
        case "two":
            println("a lot")
        default:
            println("a ton")
    }
}
```

## Enumerations
```swift
enum TrainStatus {
    case OnTime
    case Delayed(Int)
}

switch trainStatus {
    case .OnTime:
        println("on time")
    case .Delayed(let minutes):
        println("delayed by \(minutes) minutes")

    // Can also match against values
    case .Delayed(1):
        println("nearly on time")
    case .Delayed(2...10):
        println("almost on time, I swear")
    case .Delayed(_):
        println("it'll get here when it's ready")
}
```

## Patterns Compose
```swift
switch vacationStatus {
  case .Traveling(.OnTime):
    tweet("Train's on time! Can't wait to get there!")
  case .Traveling(.Delayed(1...15)):
    tweet("Train is delayed.")
  case .Traveling(.Delayed(_)):
    tweet("OMG when will this train ride end #railfail")
```

## Type Patterns
```swift
func tuneUp(car: Car) {
    switch car {
      case let formulaOne as FormulaOne: // value is of type and cast it as that type
        formulaOne.enterPit()
      case let raceCar as RaceCar:
        if raceCar.hasTurbo { raceCar.tuneTurbo() }
        fallthrough // special keyword to fall through to default
      default:
        car.checkOil()
        car.pumpTires()
    }
}
```

## Tuple patterns
Each match is a separate pattern

```swift
let color = (1.0, 1.0, 1.0, 1.0)
switch color {
    case (0.0, 0.5...1.0, let blue, _):
        println("Green and \(blue * 100)% blue")
    case let (r, g, b, 1.0) where r == g && g == b:
        println("Opaque grey \(r * 100)%")
```