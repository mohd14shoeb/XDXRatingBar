# XDXRatingBar

![Languages](https://img.shields.io/badge/language-swift%20|%20objc-FF69B4.svg?style=plastic)

## Table of contents
* [Introduction](#introduction)
* [Screenshots](#screenshots)
* [Installation](#installation)
* [Tips](#tips)
* [Support XDXRatingBar](#support)
* [Contact](#contact)
* [License](#license)

### <a id="introduction"></a>Introduction

The GitHub project [XDXRatingBar](https://github.com/6xieapplexia6/XDXRatingBar) was originally inspired by [iOS-RatingBar](https://github.com/saiwu-bigkoo/iOS-RatingBar) written by GitHub user [saiwu-bigkoo](https://github.com/saiwu-bigkoo) with the enhancements of: 

1. @IBDesignable and @IBInspectable for the class, so developers can set the attributes and preview the UI behaviors in Xcode storyboard or xib files;
2. The singleton class XDXRatingBarManager can help developers to configure all XDXRatingBar instances globally;
3. More little enhanced features will be introduced below.

<br/>

### <a id="screenshots"></a>Screenshots
![XDXRatingBar](https://github.com/6xieapplexia6/XDXRatingBar/one_star.png)
![XDXRatingBar](https://github.com/6xieapplexia6/XDXRatingBar/three_stars.png)
<br/>

### <a id="installation"></a>Installation
The easiest way to install this API on an iOS project is to copy the file XDXRatingBar.swift into the Xcode project folder.
Cocoapods installation will be available in the future.
<br/>

### <a id="tips"></a>Tips

#### XDXRatingBar - Variables

1. The variable "maxRating" should be the multiple of the variable "numberOfStars". In most cases, I'll recommend to set them as the same of each other.

2. The variable "animated" indicates whether XDXRatingBar instance should perform animation when the rating is changed. The value of the variable "animationTimeInterval" will be useless if "animated" is set to false.

3. The variable "isDecimalRating" indicates whether the rating of XDXRatingBar instance is a decimal or an integer.

4. The variable "isIndicator" determines whether users can change rating by tapping XDXRatingBar. However, the rating can still be changed programmatically.

5. The variable "starWidthInsetRatio" sets the gap between star images. The value should be set to 0 ~ 0.5.

6. The variable "isDisplayingUnselectedStars" indicates whether unselected star images should display or not. If it's set to false, the value of "imageForUnselectedStars" will be useless (suggesting to set image to nil).

#### XDXRatingBarManager

XDXRatingBarManager is a class containing a singleton instance for configuring all XDXRatingBar instances in the project. Let's have an example:

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool 
{
    configXDXRatingBarGlobally()
    return true
}

func configXDXRatingBarGlobally()
{
    XDXRatingBarManager.shared.minRating = 1
    XDXRatingBarManager.shared.maxRating = 5
    XDXRatingBarManager.shared.numberOfStars = 5
    XDXRatingBarManager.shared.animated = true
    XDXRatingBarManager.shared.animationTimeInterval = 0.2
    XDXRatingBarManager.shared.isDecimalRating = false
    XDXRatingBarManager.shared.isIndicator = false
    XDXRatingBarManager.shared.starWidthInsetRatio = 0.05
}
```

Simply copy this piece of code and do a little modification based on what you need in the project's AppDelegate file. So you don't have to override either in coding files or in xib / storyboard files everytime when XDXRatingBar is created. All variables in XDXRatingBarManager are optional, so you are not required to do this in AppDelegate.

#### XDXRatingBarDelegate

If you need to do something when the rating of XDXRatingBar is changed. You can simply confirm the protocol in view-controller or view-cell classes like: 

```swift
class ViewController: UIViewController, XDXRatingBarDelegate
```

You can either set delegate programmatically or drag in xib / storyboard files.

First way: 
```swift
@IBOutlet weak var ratingBar: XDXRatingBar! {
    didSet { ratingBar.delegate = self }
}
```

OR

Second way:
```swift
override func viewDidLoad()
{
    super.viewDidLoad()
        
    ratingBar.delegate = self
}
```

Then do what you want to do in the method "ratingDidChange". You are not required to implement this method (since the method in protocol is optional) even when you confirm protocol in the classes.

```swift
func ratingDidChange(_ ratingBar: XDXRatingBar, rating: CGFloat)
{
    print("ratingDidChange rating: \(rating)")
}
```

<br/>

### <a id="support"></a>Support XDXRatingBar
* [**★Star**](#) this repo 
<br/>

### <a id="contact"></a>Contact
* LinkedIn： [**@Chong Xie**](https://www.linkedin.com/in/chongx)
<br/>

### License
XDXRatingBar is available under the MIT license. Please see the LICENSE file for more info.