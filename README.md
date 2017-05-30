## FlexBox for swift
  
<img width="100" alt="img" src="https://rawgit.com/stylekit/img/master/FlexBoxIcon.svg">

#### FlexBox is a layout distributor: 

- Proportionally distribute items
- Easy to use
- Supports min and max stops
- Supports fixed, proportional-values, and parent-based-values.

#### Concept:

You can implement FlexBoxItemKind and FlexBoxContainerKind 

If you can add variables to the class you can implement the FlexBoxItemKind and FlexBoxContainerKind
```swift
struct CustomItem:NSImage,FlexBoxItemKind{
    /*create vars for initRect,grow,shrink,basis*/
}
struct CustomContainer:NSView,FlexBoxContainerKind{
    /*create vars for rect,flexBoxItems,justifyContent,alignItems*/
}
```

Or you can extend classes with the Flexible protocol and then decorate with FlexBoxItem and FlexBoxContainer
```swift
extension NSImage:Felxible{
    var flexSize {/*add getter and setter here*/}
    var flexPoint{/*add getter and setter here*/}
}
```

#### Code:
https://github.com/eonist/swift-utils/tree/master/Sources/Utils/misc/layout/flexbox

#### Examples:

#### Grow: 1-1-1-3
<img width="534" alt="img" src="https://raw.githubusercontent.com/stylekit/img/master/front-grow-1-1-1-3.png">

#### Stretch-grow
<img width="592" alt="img" src="https://raw.githubusercontent.com/stylekit/img/master/stretch-grow.png">

#### Center-stretch
<img width="592" alt="img" src="https://raw.githubusercontent.com/stylekit/img/master/center-stretch.png">

#### JustifyContent: Space-Around
<img width="592" alt="img" src="https://raw.githubusercontent.com/stylekit/img/master/spacearound.png">

#### JustifyContent: Space-Between
<img width="592" alt="img" src="https://raw.githubusercontent.com/stylekit/img/master/spacebetween.png">

#### Justify:Center, Align-Items:flexStart
<img width="592" alt="img" src="https://raw.githubusercontent.com/stylekit/img/master/grow-0-justify-center-align-items-top.png">

#### Justify:Center, Align-Items:flexEnd
<img width="592" alt="img" src="https://raw.githubusercontent.com/stylekit/img/master/grow-0-justify-center-align-items-bottom.png">

#### Justify:Center, Align-Items:center
<img width="592" alt="img" src="https://raw.githubusercontent.com/stylekit/img/master/grow-0-justify-center-align-items-center.png">

#### Justify:flexEnd
<img width="592" alt="img" src="https://raw.githubusercontent.com/stylekit/img/master/grow-0-justify-flexEnd.png">

#### Justify:flexStart
<img width="592" alt="img" src="https://raw.githubusercontent.com/stylekit/img/master/grow-0-justify-flexStart.png">

#### Grow:1-1-1-3
<img width="592" alt="img" src="https://raw.githubusercontent.com/stylekit/img/master/grow-1-1-1-3.png">

#### Grow:2-1-2-1
<img width="592" alt="img" src="https://raw.githubusercontent.com/stylekit/img/master/grow-2-1-2-1.png">

#### Example code:

```swift
let size:CGSize = self.frame.size
let frame:CGRect = CGRect(10,10,size.w-20,size.h-20)/*Add inset*/
let flexibles:[Flexible] = [/*...*/]
let flexBoxItems:[FlexBoxItem] = (0..<numBoxes).indices.map{ i in
    FlexBoxItem(flexibles[i])
}
let flexBoxContainer = FlexBoxContainer(frame,flexBoxItems,.flexStart,.flexStart)
FlexBoxModifier.flex(flexBoxContainer)
```

- **Flexible** is a protocol which views must adhere to. Basically must have settable/gettable size and position  
- **FlexBoxContainer**  Holds the FlexItems and flex props that these should adhere to
- **FlexBoxItem** Has a ref to the Flexible instance, and individual flex props that apply

#### Working on:
- Implementing min max support
- Implementing shrink
- Interactive resize-demo
- Overflow support
- Add protocols to support FlexBox w/o decoration
- Column support

