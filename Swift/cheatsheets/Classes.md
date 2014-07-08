# Classes
## Creating a class
```swift
class Vehicle {
    // properties
    // methods
    // initalizers
}
```

## Properties
```swift
class Vehicle {
    // stored properties
    var numberOfWheels = 0

    // computed properties
    var description: String {
        get { // read
            return "\(numberOfWheels) wheels"
        }
        set { // adding this makes it read-write
            // ...
        }
    }

    // read-only computed property, can drop the `get{}`
    // need `var` because this is a property even if it's read-only because
    // the value can still change
    var description: String {
        return "\(numberOfWheels) wheels"
    }
}

// Initializing an instance
let someVehicle = Vehicle()
```

## Inheritance
```swift
class Bicycle: Vehicle {
    init() {
        super.init()
        numberOfWheels = 2
    }
}
```

## Overriding methods
```swift
class Car: Vehicle {
    var speed = 0.0
    init() {
        super.init()
        numberOfWheels = 4
    }
    override var description: String {
    }
}
```

## Property observers
```swift
class ParentsCar: Car {
    override var speed: Double  {
        willSet {
            // newValue is available here
        }
        didSet {
            // oldValue is available here
        }
    }
}
```

## Methods
```swift
// Defining methods
class Counter {
    var count = 0
    func incrementBy(amount: Int) {
        count += amount // do not need self because there's no ambiguity
    }
    func resetToCount(count: Int) {
        self.count = count // needs self because there's ambiguity due to parameter
    }
}


```