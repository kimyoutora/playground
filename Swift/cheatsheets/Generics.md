# Generics
<T> denotes there's a class here named T and anything that uses T has to be the same type.

## Basic generics
```swift
struct Stack<T> {
    var elements = T[]()

    mutating func push(element: T) {
        elements.append(element)
    }
    mutating func pop() -> T {
        return elements.removeLast()

    }
}

var intStack = Stack<Int>()
intStack.push(50)
let lastIn = intStack.pop()

var stringStack = Stack<String>()
stringStack.push("Hello")
println(stringStack.pop())
```