Swift standards

1. Use String interpolation over String concatenation when possible because it leads to faster compile times.

Do:

```swift
  let three = "3"
  let title = "I am feeding " + three + " cats"
```

Don't:

```swift
  let three = "3"
  let title = "I am feeding \(three) cats"
```
