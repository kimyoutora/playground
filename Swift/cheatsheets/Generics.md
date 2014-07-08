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

## Protocol Types vs. Swift Generics
Protocol types like Any or Pullable **throw away** type information
    - Great for Dynamic Polymorphism e.g. collection of objects that are all different types
Swift Generics **conserve** type information
    - Great for type safety
    - Great for performance

## Objective-C protocols and Swift protocols
- Every objective-c protocol is also a Swift protocol
- Swift generics conserve type information so they have full type implementing Any protocol

## Protocol constraints
```swift
// Return the  first index of sought in array, or nil if not found
func indexOf<T : Equatable>(sought: T, inArray array: T[]) -> Int? {
    for i in 0..array.count {
        if array[i] == sought {
          return i
        }
    }
    return nil
}
```

## Advanced Generics
### Automatic Memoization
```swift
// T: Hashable - so that it can be used as a key
// (T)->U - returns the same type of closure that it gets
func memoize<T: Hashable, U>( body: (T)->U ) -> (T)->U {
    var memo = Dictionary<T, U>()
    return { x in
        if let q = memo[x] { return q }
        let r = body(x)
        memo[x] = r
        return r
    }
}

// This doesn't work for recursive functions because you are using
// the variable's own value to initialize itself
let factorial = memoize { x in x == 0 ? 1 : x * factorial(x - 1) }

// Want to take in a local parameter
let factorial = memoize { factorial, x in x == 0 ? 1 : x * factorial(x - 1) }

// hiding the additional parameter in the function
func memoize<T: Hashable, U>( body: ((T)->U, T)->U ) -> (T)->U {
    var memo = Dictionary<T, U>()
    var result: ((T)->U)!
    result = { x in
        if let q = memo[x] { return q } // short-circut and return result if found in cache
        let r = body(result, x)
        memo[x] = r
        return r
    }
    return result
}
```

### Typealias
```swift
protocol Generator {
    // an "associated type" requirement, satisfy by
    // writing any nested type call Element inside your generator
    // used in this case to define what comes out of next()
    typealias Element
    mutating func next() -> Element?
}

struct StackGenerator<T> : Generator {
    typealias Element = T // can leave out since T is deduced from next()
    mutating func next() -> T? {
    if items.isEmpty { return nil }
        let ret = items[0]
        items = items[1..items.count]
        return ret
    }
    var items: Slice<T>
}
```