```swift
// Named parameters in functions
func refreshWebPage() -> (code: Int, message: String) {
    // ...try to refresh...
    return (200, "Success")
}

let status = refreshWebPage()

println("Received \(status.code): \(status.message)")
```