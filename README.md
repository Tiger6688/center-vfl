# Centering a view in a super view with visual format language using Auto Layout in iOS/Swift

This is an example of centeing a label in its view using [Visual Format Language](http://developer.apple.com/library/mac/#documentation/UserExperience/Conceptual/AutolayoutPG/Articles/formatLanguage.html#//apple_ref/doc/uid/TP40010853-CH3-SW1).

Here is the code from [view controller](https://github.com/evgenyneu/center-vfl/blob/master/CenteringWithVFL/ViewController.swift) that does the trick:

```Swift
// Center horizontally
var constraints = NSLayoutConstraint.constraintsWithVisualFormat(
  "V:[superview]-(<=1)-[label]",
  options: NSLayoutFormatOptions.AlignAllCenterX,
  metrics: nil,
  views: ["superview":view, "label":label])

  view.addConstraints(constraints)

 // Center vertically
constraints = NSLayoutConstraint.constraintsWithVisualFormat(
  "H:[superview]-(<=1)-[label]",
  options: NSLayoutFormatOptions.AlignAllCenterY,
  metrics: nil,
  views: ["superview":view, "label":label])

view.addConstraints(constraints)
```
    

<img src='https://raw.github.com/evgenyneu/center-vfl/master/centering_with_vfl.png' width='568' alt='Centering in superview with VFL'>


## How it works

We use two visual format strings:

1. `@"V:[superview]-(<=1)-[label]"` with `AlignAllCenterX` option
1. `@"H:[superview]-(<=1)-[label]"` with `AlignAllCenterY` option

It aligns X and Y centres of the label and its superview. The `(<=1)` inequality constraints are needed to allow those centering constraints do their job. If we had just `[superview][label]` it would **probably** stick the edges of the label and its superview together.

## Feedback welcome

If you need help or want to improve this technique feel free to create a pull request, or comment on [this stackoverflow answer](http://stackoverflow.com/a/14917695/297131).
