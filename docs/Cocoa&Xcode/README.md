# Cocoa&Xcode standards

## 1. Don't forget to set storyboard ID when asigning a class to a view controller in storyboard. The ID has to match the class name exactly.

### Do:
![alt text](https://github.com/degordian/ios-coding-standards/blob/assets/docs/Cocoa/assets/storyboardIdentifierdDo.png?raw=true)

### Don't:
![alt text](https://github.com/degordian/ios-coding-standards/blob/assets/docs/Cocoa/assets/storyboardIdentifierdDont.png?raw=true)


## 2. Always create a group with folder so the project structure will look the same in Xcode and on the file system.

### Do:
![alt text](https://github.com/degordian/ios-coding-standards/blob/assets/docs/Cocoa/assets/folderDo.png?raw=true)

### Don't:
![alt text](https://github.com/degordian/ios-coding-standards/blob/assets/docs/Cocoa/assets/folderDont.png?raw=true)


## 3. Don't leave irrelevant comments in your code.

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
