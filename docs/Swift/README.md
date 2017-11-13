# Swift standards

## 1. Use String interpolation over String concatenation when possible because it leads to faster compile times and is more concise.

Do:

```swift
  let three = "3"
  let title = "I am feeding \(three) cats"
```

Don't:

```swift
  let three = "3"
  let title = "I am feeding " + three + " cats"
```

## 2. Don't nest optional binding if possible because it is more difficult to read.

Do:

```swift
  var user: User?
  var venue: Venue?
  if let author = user, let place = venue {
    // ...
  }
```

Don't:

```swift
  var user: User?
  var venue: Venue?
  if let author = user {
    if let place = venue {
      // ...
    }
  }
```
