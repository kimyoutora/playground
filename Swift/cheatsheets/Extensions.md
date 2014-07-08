# Extensions
Extensions are like categories in objective-c. Can extend any named-types.

## Basic extension
```swift
extension Size {
    mutating func increaseByFactor(factor: Int) {
        width *= factor
        height *= factor
    }
}
```

## Extending primative types and structs
```swift
extension Int {
    func repetitions(task: () -> ()) {
        for i in 0..self {
            task()
        }
    }
}

500.repetitions({
    println("Hello!")
})

// Short-hand for trailing closures
500.repetitions { println("Hello!") }
```