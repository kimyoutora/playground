# Functions

## Basic function declaration
```swift
// Named parameters in functions
func refreshWebPage() -> (code: Int, message: String) {
    // ...try to refresh...
    return (200, "Success")
}

let status = refreshWebPage()

println("Received \(status.code): \(status.message)")
```

## Defining an operator
```swift
// tell swift how this binary operator operates with other operators
operator infix ~ {}

func ~ (decorator: ???, object: Thing) -> String {
    return decorator(object)
}

func an(object: Thing) -> String {
  return object.nameWithArticle
}
```