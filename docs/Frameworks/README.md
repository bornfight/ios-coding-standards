# Frameworks standards

## 1. [Realm] Don't forget to update schema version after changing models.

### Previous state:
![alt text](https://github.com/degordian/ios-coding-standards/blob/assets/docs/Frameworks/assets/SchemaVersionDont.png?raw=true)

### Do:
![alt text](https://github.com/degordian/ios-coding-standards/blob/assets/docs/Frameworks/assets/SchemaVersionDo.png?raw=true)

### Don't:
![alt text](https://github.com/degordian/ios-coding-standards/blob/assets/docs/Frameworks/assets/SchemaVersionDont.png?raw=true)


## 2. [RxSwift] Use `BehaviorRelay<T>` instead of `Variable<T>`, as `Variable<T>` is being deprecated. `BehaviorRelay<T>` is going to be included in the next major version of RxSwift; as of right now it is in RxCocoa. Read more at [this Github issue](https://github.com/ReactiveX/RxSwift/issues/1501#issuecomment-347021795).


### Do:
```swift
let myRelay = BehaviorRelay(value: false)
myRelay.accept(true)
```

### Don't:
```swift
let myVariable = Variable(false)
myVariable.value = true
```

## 3. [Realm] Only ever have a single Realm object per file

### Do:
```swift
// Foo.swift

class Foo: Object { ... }
```

### Don't:
```swift
// Foo.swift

class Foo: Object { ... }

class Bar: Object { ... }

class Baz: Object { ... }
```

## 4. [RxSwift] When subscribing to observables, if your code is more than 4 lines long, extract it into a function.

### Do:
```swift
.drive(onNext: { [weak self] (changeset, picksNeedUpdating) in
    self?.reloadWithChangeset(changeset: changeset, picksNeedUpdating: picksNeedUpdating)
})
```

### Don't:
```swift
.drive(onNext: { [weak self] (changeset, picksNeedUpdating) in
    self?.updateChangeset(changeset: changeset)
    if picksNeedUpdating {
        self?.updatePicks()
    }
    self?.tableView.reloadData()
    ...
})
```

## 5. [RxSwift] When subscribing to observables, omit the extra arguments if you don't use them.

### Do:
```swift
.drive(onNext: { [weak self] (changeset, picksNeedUpdating) in
    self?.reloadWithChangeset(changeset: changeset, picksNeedUpdating: picksNeedUpdating)
})
```

### Don't:
```swift
.drive(onNext: { [weak self] (changeset, picksNeedUpdating) in
    self?.reloadWithChangeset(changeset: changeset, picksNeedUpdating: picksNeedUpdating)
}, onError: nil, onCompleted: nil)

