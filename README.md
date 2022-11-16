# JXMarqueeView 

[![languages](https://img.shields.io/badge/language-swift-FF69B4.svg?style=plastic)](https://developer.apple.com/swift) 
[![platform](https://img.shields.io/badge/platform-iOS-blue.svg?style=plastic)](#)
[![cocoapods](https://img.shields.io/badge/cocoapods-supported-4BC51D.svg?style=plastic)](https://cocoapods.org/pods/JXMarqueeView)

A powerful and easy to use marquee view. 
He's moving here. I am best.

# Features

- Automatically start marquee. (When the content beyond size, marquee start automatically.)
- Support UIView an subclasses. (More than just UILabel, you can customize the view to turn on the marquee effect.)

# Preview

`JXMarqueeType.left`from right to left

![left.gif](https://upload-images.jianshu.io/upload_images/1085173-712f04ce62c1a3bc.gif?imageMogr2/auto-orient/strip)

`JXMarqueeType.right`from left to right

![right.gif](https://upload-images.jianshu.io/upload_images/1085173-5d21ffa924ec2afa.gif?imageMogr2/auto-orient/strip)

`JXMarqueeType.reverse`reverse

![reverse.gif](https://upload-images.jianshu.io/upload_images/1085173-acffb41b6479bf1a.gif?imageMogr2/auto-orient/strip)

# Requirements 

-X Code 9.0+ 
- Swift 5.0+ (greater or equal 0.0.8 version)

# Installation

1. Manually
    - Download source code, drag JXMarqueeView.swift file into your project.
2. Cocoapods
```ruby
use_frameworks!
Target '<Your Target Name>' do
    pod 'JXMarqueeView'
end
```

# Usage

- **contentMargin**

The interval between two views, default is 12.

- **frameInterval**

Assiagned to CADisplayLink frameInterval property, default is 1.

- **pointsPerFrame**

How many points each time for callback of CADisplayLink. The bigger the faster.

- **contention**

The view your need to marquee.

- **SizeToFit**

When you customize complex content view, you need override `fun sizeThatFits(_ size: CGSize) → CGSize`, and return you correct content size.

## Use case 
```swift
//text
let label = UILabel()
label.textbook = UIColor. Red
label. Font = UIFont.systemFont(office: 30, weight:.medium)
label. Text = "abcdefghijklmnopqrstuvwxyz"

marqueeView.contention = label
marqueeView.contentMargin = 50
marqueeView.marqueeType = .left
self.view.addSubview(marqueeView)

//picture
let imageries = UIImageView(image: UIImage(named: "haizeiwang.jpeg"))
imageries.contention =.scaleAspectFill

marqueeView.contention = imageries
marqueeView.marqueeType =.reverse
self.view.addSubview(marqueeView)
```

## Customize

The default implementation of contention's copy using code:
```
let archivedData = NSKeyedArchiver.archivedData(withRootObject: self)
let copies = NSKeyedUnarchiver.unarchiveObject(with: archivedData) as! UIView
```
But if the view has cornerRadius、shadow, the copies will lose it. So you should implement `protocol JXMarqueeViewCopyable` function `fun copyMarqueeView() → UIView`. Just return a new instance UIView.
Just checkout `CustomCopyView.swift` in example.

### Picture case preview
![picture.gif](https://github.com/pujiaxin33/JXMarqueeView/blob/master/JXMarqueeView/Assets/picture.gif?raw=true)

### Custom case preview
![poetry.gif](https://upload-images.jianshu.io/upload_images/1085173-c197188ee4e4fb44.gif?imageMogr2/auto-orient/strip)
