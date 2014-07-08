# Subscripts

## Basic subscripts
```swift
class Place: Thing {
    var exits: Dictionary<Direction, Place>
}

// [] exposes implementation detail that exits is what connects places;
// would prefer to avoid this and instead do:
// westOfHouse[.South] = gardenPath
westOfHouse.exits[.South] = gardenPath

extension Place {
    subscript(direction: Direction) -> Place? {
        get {
            return exits[direction]
        }
        set(destination: Place?) {
            exits[direction] = destination
        }
    }
}
```

## Best practices
- Keep it natural
    - intuitive for the user
- Work by analogy
    - not taking existing syntax and making it do what other instances of that syntax are doing
- New idioms should pay for themselves
    - make sure it's worth the time to learn the new syntax
