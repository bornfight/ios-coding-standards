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

## 5. Don't leave irrelevant comments in your code.

### Do:

```swift
let config = Realm.Configuration(
// Set the new schema version. This must be greater than the previously used
// version (if you've never set a schema version before, the version is 0).

schemaVersion: 15,
```

### Don't:

```swift
@implementation VideoPlaybackEAGLView {
    SCNRenderer* renderer; // Renderer
    SCNNode* cameraNode; // Camera Node
    SCNReferenceNode* refNode;
```

