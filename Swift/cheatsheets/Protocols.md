# Protocols

## Basic protocol
```swift
protocol Pullable {
    func pull()
}

class Boards: Thing, Pullable {
    func pull () {
        ...
    }
}
```

## Using a protocol value
```swift
func performPull(object: Thing) {
    if let pullableObject = object as Pullable {
        pullableObject.pull()
    } else {
        /* complain */
    }
}
```

## Special protocols
```swift
LogicValue                      // if logicValue {
Printable                       // "\(printable)"
Sequence                        // for x in sequence
IntegerLiteralConvertible       // 65536
FloatLiteralConvertible         // 1.0
StringLiteralConvertible        // "abc"
ArrayLiteralConvertible         // [ a, b, c ]
DictionaryLiteralConvertible    // [ a: x, b: y ]
```

## Any protocol
Empty protocol type, has no functions in it but it can hold anything

```swift
any[]
```