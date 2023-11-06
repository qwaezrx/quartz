
## Types and variables in Swift

| Constant | Variable |
|:---------|:---------|
|A value that can't be changed|A value that can be changed|
|`let name = 10`|`var name = 10`|

## Declaration
> ❌ You can't declare two variables or constants with same name.
```swift
var exampleA = 20
var exampleA = 30 // Will raise an error
```
> ❌ Can't declare a variable that use mathematical symbols or start with a number.
```swift
var %example = 20
var 23example = 30
```

## Data types
- ### Integer
- ### Floating Point
    - **Float sub types**

        | Type | Description | Example |
        |:---- |:----------- |:------  |
        |Float |32-bit floating-point|63.23|
        |Double|64-bit floating-point|10.22345|

- ### Boolean
- ### String

## Type-safe language

    Mixing of different data types and values is restricted.

- ❗ Constants and variables must be declared before they can be used.
- ❗ Different data types can't be mixed.

```swift
let x = 5
let y = 0.33
let z = x + y // Will produce an error
// Should be
// let z = Double(x) + y
```

This is because Swift performs __type checks__ before compiling the code.

## Operators
### BIDMAS

### Compound assignment operators

- `+=`: Add
- `-=`: Subtract
- `*=`: Multiply
- `/=`: Divide

### Unary minus operator
```swift
// Toggle the sign of a numeric value by prefixing (-)
let one = 1
let negativeOne = -one
```


## Conditions

#### If else in practice
```swift
let language = "English"
if language == "English" {
	print("English")
} else if language == "Spanish" {
	print("Spanish")
} else {
	print("Wrong language")
}
```


#### Switch statements in practice
```swift
let language = "English"

switch langauge {
	case "English": print("English")
	case "Spanish": print("Spanish")
	default: print("Wrong language")
}
```


## Loops

#### For in loop

```swift
for dice in 1...6 {
	print("Roll a \(dice).")  
}
```


```swift
for char in "ABCDE" {
	print(char)
}
```

#### While loop


#### Repeat while loop
