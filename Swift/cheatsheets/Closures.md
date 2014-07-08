# Closures

## Basic closures
```swift
// closure that doesn't take any param and doesnt' return any value
let greetingPrinter = {
    println("Hello World!")
}

// equivalent to above
let greetingPrinter: () -> () = {
    println("Hello World!")
}

// equivalent to above. functions are just named closures
func greetingPrinter() -> () {
    println("Hello World!")
}

greetingPrinter()
// > Hello World!
```

## Closures as parameters
```swift
func repeat(count: Int, task: () -> ()) {
    for i in 0..count {
        task()
    }
}

repeat(2, {
    println("Hello!")
})
```

## Trailing closure
```swift
// can bring closure outside of the function if it's the last parameter
repeat(2) {
    println("Hello!")
}
```