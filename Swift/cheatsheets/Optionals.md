# Optionals

## Basic optionals
```swift
// defualt initialized to nil, works with any types
var optionalNumber: Int?
```

## Return type
```swift
func findIndexOfString(string: String, array: String[]) -> Int? {
    for (index, value) in enumerate(array) {
        if value == string {
            return index // automatically wrapped in Optional due to return type
        }
    }
    return nil
}
```

## Control Flow
```swift
// can be used in if...else
var neighbors = ["Alex", "Anna", "Madison", "Dave"]
let index = findIndexOfString("Madison", neighbors)
if index {
    println("Hello, \(neighbors[index!])")
} else {
    println("Must've moved away")
}
```

## Optional binding
```swift
if let legCount = possibleLegCount { // legCount is of type Int
    println("An aardvark has \(legCount) legs")
}
```

## Optional chaining
Similar to messaging nil in objective-c

```swift
let addressNumber = paul.residence?.address?.buildingNumber?.toInt()
```

## Optional chaining + binding
```swift

```