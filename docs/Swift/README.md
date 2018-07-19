# Swift standards

## 1. Use String interpolation over String concatenation when possible because it leads to faster compile times and is more concise.

### Do:

```swift
  let three = "3"
  let title = "I am feeding \(three) cats"
```

### Don't:

```swift
  let three = "3"
  let title = "I am feeding " + three + " cats"
```

## 2. Don't nest optional binding if possible because it is more difficult to read.

### Do:

```swift
  var user: User?
  var venue: Venue?
  if let author = user, let place = venue {
    // ...
  }
```

### Don't:

```swift
  var user: User?
  var venue: Venue?
  if let author = user {
    if let place = venue {
      // ...
    }
  }
```

## 3. Don't create a reference cycle by using a strong reference to self in a closure. It may retain an object in memory after it has been deinitialized. Use weak (or unowned) self.

### Do:

```swift
  presenter.animateMapViewToAlpha(alpha: 1, completion: { [weak self] in
    self?.stopScanning()
  })
```

### Don't:

```swift
  presenter.animateMapViewToAlpha(alpha: 1, completion: {
    self.stopScanning()
  })
```

## 4. Express boolean comparisons explicitly. It is more readable.

### Do:

```swift
if isOpened == false {

}
```

### Don't:

```swift
if !isOpened {

}
```

## 5. When passing parameters to another class, prefer enums over boolean types. Enums offer better readability and expressiveness and are easily expandable.

### Do:

```swift
pushToInfoScreen(infoType: .registration)
```

### Don't:

```swift
pushToInfoScreen(registration: true)
```
