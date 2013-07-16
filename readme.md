FaceImageView
--------

A `UIImageView` clone with a catch:

FaceImageView automatically scales its image to fill the bounds **and keep any faces detected in view**. This can be useful if you want to display people-based dynamic content with `UIViewContentModeScaleToFill` but are having issues with it displaying the wrong part of the image, like the background, or someone's feet.

The class uses the CoreImage face detection APIs available in iOS 5.0 or later. This API works in many clear cases, but is not all that reliable. If no faces are detected in an image, FaceImageView defaults to centering the image, like `UIImageView`'s behavior with `UIViewContentModeScaleToFill`.

A small demo app is included to try out different images and view sizes.

Usage
--------

**Installing**

Add FaceImageView.{h,m} included in the demo project to your source, or, using CocoaPods, add the following to your Podfile:
```
pod 'FaceImageView'
```

**Using**

As simple as instantiating a FaceImageView object, giving it an image, and adding it to your view:
```
FaceImageView *imageView = [[FaceImageView alloc] initWithFrame:<CGRect>];
imageView.image = <UIImage>;
[self.view addSubview:imageView];
```

It may also be wise to set the image asynchronously, as face detection can sometimes take a second:

```
[imageView setImage:<UIImage> completion:^{}];
```

Demo App
---------

Watch faces automatically stay centered in the view as it changes size:

![demo](http://danhassin.com/img/face-demo3.png)

--------------

#### Further thoughts: ####
- Have it give suggestions for minimum height, as to not entirely cut off a face?
- With multiple faces, maybe prefer to keep at least one face entirely in view rather than halfway between many?
- It seems like face detection implementation has changed between iOS 6 and 7. The former detects the face in image #4, but the latter does not. Not sure what to do with this, maybe it is temporary.

Posted for the [Objective-C hackathon](https://objectivechackathon.appspot.com/) effort :)