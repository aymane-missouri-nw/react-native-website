---
id: image
title: Image
---

import Tabs from '@theme/Tabs'; import TabItem from '@theme/TabItem'; import constants from '@site/core/TabsConstants';

A React component for displaying different types of images, including network images, static resources, temporary local images, and images from local disk, such as the camera roll.

This example shows fetching and displaying an image from local storage as well as one from network and even from data provided in the `'data:'` uri scheme.

> Note that for network and data images, you will need to manually specify the dimensions of your image!

## Examples

<Tabs groupId="syntax" queryString defaultValue={constants.defaultSyntax} values={constants.syntax}>
<TabItem value="functional">

```SnackPlayer name=Function%20Component%20Example

import React from 'react';
import { View, Image, StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  container: {
    paddingTop: 50,
  },
  tinyLogo: {
    width: 50,
    height: 50,
  },
  logo: {
    width: 66,
    height: 58,
  },
});

const DisplayAnImage = () => {
  return (
    <View style={styles.container}>
      <Image
        style={styles.tinyLogo}
        source={require('@expo/snack-static/react-native-logo.png')}
      />
      <Image
        style={styles.tinyLogo}
        source={{
          uri: 'https://reactnative.dev/img/tiny_logo.png',
        }}
      />
      <Image
        style={styles.logo}
        source={{
          uri:
            'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADMAAAAzCAYAAAA6oTAqAAAAEXRFWHRTb2Z0d2FyZQBwbmdjcnVzaEB1SfMAAABQSURBVGje7dSxCQBACARB+2/ab8BEeQNhFi6WSYzYLYudDQYGBgYGBgYGBgYGBgYGBgZmcvDqYGBgmhivGQYGBgYGBgYGBgYGBgYGBgbmQw+P/eMrC5UTVAAAAABJRU5ErkJggg==',
        }}
      />
    </View>
  );
}

export default DisplayAnImage;
```

</TabItem>
<TabItem value="classical">

```SnackPlayer name=Class%20Component%20Example

import React, { Component } from 'react';
import { AppRegistry, View, Image, StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  container: {
    paddingTop: 50,
  },
  tinyLogo: {
    width: 50,
    height: 50,
  },
  logo: {
    width: 66,
    height: 58,
  },
});

class DisplayAnImage extends Component {
  render() {
    return (
      <View style={styles.container}>
        <Image
          style={styles.tinyLogo}
          source={require('@expo/snack-static/react-native-logo.png')}
        />
        <Image
          style={styles.tinyLogo}
          source={{uri: 'https://reactnative.dev/img/tiny_logo.png'}}
        />
        <Image
          style={styles.logo}
          source={{uri: 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADMAAAAzCAYAAAA6oTAqAAAAEXRFWHRTb2Z0d2FyZQBwbmdjcnVzaEB1SfMAAABQSURBVGje7dSxCQBACARB+2/ab8BEeQNhFi6WSYzYLYudDQYGBgYGBgYGBgYGBgYGBgZmcvDqYGBgmhivGQYGBgYGBgYGBgYGBgYGBgbmQw+P/eMrC5UTVAAAAABJRU5ErkJggg=='}}
        />
      </View>
    );
  }
}

export default DisplayAnImage;
```

</TabItem>
</Tabs>

You can also add `style` to an image:

<Tabs groupId="syntax" queryString defaultValue={constants.defaultSyntax} values={constants.syntax}>
<TabItem value="functional">

```SnackPlayer name=Function%20Component%20Example

import React from 'react';
import { View, Image, StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  container: {
    paddingTop: 50,
  },
  stretch: {
    width: 50,
    height: 200,
    resizeMode: 'stretch',
  },
});

const DisplayAnImageWithStyle = () => {
  return (
    <View style={styles.container}>
      <Image
        style={styles.stretch}
        source={require('@expo/snack-static/react-native-logo.png')}
      />
    </View>
  );
}

export default DisplayAnImageWithStyle;
```

</TabItem>
<TabItem value="classical">

```SnackPlayer name=Class%20Component%20Example

import React, { Component } from 'react';
import { View, Image, StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  stretch: {
    width: 50,
    height: 200,
    resizeMode: 'stretch'
  }
});

class DisplayAnImageWithStyle extends Component {
  render() {
    return (
      <View>
        <Image
          style={styles.stretch}
          source={require('@expo/snack-static/react-native-logo.png')}
        />
      </View>
    );
  }
}

export default DisplayAnImageWithStyle;
```

</TabItem>
</Tabs>

## GIF and WebP support on Android

When building your own native code, GIF and WebP are not supported by default on Android.

You will need to add some optional modules in `android/app/build.gradle`, depending on the needs of your app.

```gradle
dependencies {
  // If your app supports Android versions before Ice Cream Sandwich (API level 14)
  implementation 'com.facebook.fresco:animated-base-support:1.3.0'

  // For animated GIF support
  implementation 'com.facebook.fresco:animated-gif:2.0.0'

  // For WebP support, including animated WebP
  implementation 'com.facebook.fresco:animated-webp:2.1.0'
  implementation 'com.facebook.fresco:webpsupport:2.0.0'

  // For WebP support, without animations
  implementation 'com.facebook.fresco:webpsupport:2.0.0'
}
```

---

# Reference

## Props

### `style`

`ImageResizeMode` is an `Enum` for different image resizing modes, set via the `resizeMode` style property on `Image` components. The values are `contain`, `cover`, `stretch`, `center`, `repeat`.

| Type  | Required |
| ----- | -------- |
| style | No       |

- [Image Style Props...](image-style-props#props)

- [Layout Props...](layout-props#props)

- [Shadow Props...](shadow-props#props)

- [Transforms...](transforms#props)

---

### `accessible`

When true, indicates the image is an accessibility element.

| Type | Required | Platform |
| ---- | -------- | -------- |
| bool | No       | iOS      |

---

### `accessibilityLabel`

The text that's read by the screen reader when the user interacts with the image.

| Type   | Required | Platform |
| ------ | -------- | -------- |
| string | No       | iOS      |

---

### `blurRadius`

blurRadius: the blur radius of the blur filter added to the image

| Type   | Required |
| ------ | -------- |
| number | No       |

> Tip : IOS you will need to increase `blurRadius` more than `5`

---

### `capInsets`

When the image is resized, the corners of the size specified by `capInsets` will stay a fixed size, but the center content and borders of the image will be stretched. This is useful for creating resizable rounded buttons, shadows, and other resizable assets. More info in the [official Apple documentation](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIImage_Class/index.html#//apple_ref/occ/instm/UIImage/resizableImageWithCapInsets).

| Type         | Required | Platform |
| ------------ | -------- | -------- |
| [Rect](rect) | No       | iOS      |

---

### `defaultSource`

A static image to display while loading the image source.

| Type           | Required | Platform |
| -------------- | -------- | -------- |
| object, number | No       | iOS      |
| number         | No       | Android  |

If passing an object, the general shape is `{uri: string, width: number, height: number, scale: number}`:

- `uri` - a string representing the resource identifier for the image, which should be either a local file path or the name of a static image resource (which should be wrapped in the `require('./path/to/image.png')` function).
- `width`, `height` - can be specified if known at build time, in which case these will be used to set the default `<Image/>` component dimensions.
- `scale` - used to indicate the scale factor of the image. Defaults to 1.0 if unspecified, meaning that one image pixel equates to one display point / DIP.

If passing a number:

- `number` - Opaque type returned by something like `require('./image.jpg')`.

> **Note:** On Android, the default source prop is ignored on debug builds.

---

### `fadeDuration`

Android only. By default, it is 300ms.

| Type   | Required | Platform |
| ------ | -------- | -------- |
| number | No       | Android  |

---

### `loadingIndicatorSource`

Similarly to `source`, this property represents the resource used to render the loading indicator for the image, displayed until image is ready to be displayed, typically after when it got downloaded from network.

| Type                                  | Required |
| ------------------------------------- | -------- |
| array of ImageSourcePropTypes, number | No       |

> Can accept a number as returned by `require('./image.jpg')`

---

### `onError`

Invoked on load error with `{nativeEvent: {error}}`.

| Type     | Required |
| -------- | -------- |
| function | No       |

---

### `onLayout`

Invoked on mount and layout changes with `{nativeEvent: {layout: {x, y, width, height}}}`.

| Type     | Required |
| -------- | -------- |
| function | No       |

---

### `onLoad`

Invoked when load completes successfully.

| Type     | Required |
| -------- | -------- |
| function | No       |

---

### `onLoadEnd`

Invoked when load either succeeds or fails.

| Type     | Required |
| -------- | -------- |
| function | No       |

---

### `onLoadStart`

Invoked on load start.

e.g., `onLoadStart={(e) => this.setState({loading: true})}`

| Type     | Required |
| -------- | -------- |
| function | No       |

---

### `onPartialLoad`

Invoked when a partial load of the image is complete. The definition of what constitutes a "partial load" is loader specific though this is meant for progressive JPEG loads.

| Type     | Required | Platform |
| -------- | -------- | -------- |
| function | No       | iOS      |

---

### `onProgress`

Invoked on download progress with `{nativeEvent: {loaded, total}}`.

| Type     | Required | Platform |
| -------- | -------- | -------- |
| function | No       | iOS      |

---

### `progressiveRenderingEnabled`

Android only. When true, enables progressive jpeg streaming. https://frescolib.org/docs/progressive-jpegs.html

| Type | Required | Platform |
| ---- | -------- | -------- |
| bool | No       | Android  |

---

### `resizeMethod`

The mechanism that should be used to resize the image when the image's dimensions differ from the image view's dimensions. Defaults to `auto`.

- `auto`: Use heuristics to pick between `resize` and `scale`.

- `resize`: A software operation which changes the encoded image in memory before it gets decoded. This should be used instead of `scale` when the image is much larger than the view.

- `scale`: The image gets drawn downscaled or upscaled. Compared to `resize`, `scale` is faster (usually hardware accelerated) and produces higher quality images. This should be used if the image is smaller than the view. It should also be used if the image is slightly bigger than the view.

More details about `resize` and `scale` can be found at http://frescolib.org/docs/resizing.html.

| Type                            | Required | Platform |
| ------------------------------- | -------- | -------- |
| enum('auto', 'resize', 'scale') | No       | Android  |

---

### `resizeMode`

Determines how to resize the image when the frame doesn't match the raw image dimensions. Defaults to `cover`.

- `cover`: Scale the image uniformly (maintain the image's aspect ratio) so that both dimensions (width and height) of the image will be equal to or larger than the corresponding dimension of the view (minus padding).

- `contain`: Scale the image uniformly (maintain the image's aspect ratio) so that both dimensions (width and height) of the image will be equal to or less than the corresponding dimension of the view (minus padding).

- `stretch`: Scale width and height independently, This may change the aspect ratio of the src.

- `repeat`: Repeat the image to cover the frame of the view. The image will keep its size and aspect ratio, unless it is larger than the view, in which case it will be scaled down uniformly so that it is contained in the view.

- `center`: Center the image in the view along both dimensions. If the image is larger than the view, scale it down uniformly so that it is contained in the view.

| Type                                                    | Required |
| ------------------------------------------------------- | -------- |
| enum('cover', 'contain', 'stretch', 'repeat', 'center') | No       |

---

### `source`

The image source (either a remote URL or a local file resource).

This prop can also contain several remote URLs, specified together with their width and height and potentially with scale/other URI arguments. The native side will then choose the best `uri` to display based on the measured size of the image container. A `cache` property can be added to control how networked request interacts with the local cache. (For more information see [Cache Control for Images](images#cache-control-ios-only)).

The currently supported formats are `png`, `jpg`, `jpeg`, `bmp`, `gif`, `webp`, `psd` (iOS only). In addition, iOS supports several RAW image formats. Refer to Apple's documentation for the current list of supported camera models (for iOS 12, see https://support.apple.com/en-ca/HT208967).

| Type                | Required |
| ------------------- | -------- |
| ImageSourcePropType | No       |

---

### `testID`

A unique identifier for this element to be used in UI Automation testing scripts.

| Type   | Required |
| ------ | -------- |
| string | No       |

## Methods

### `getSize()`

```jsx
Image.getSize(uri, success, [failure]);
```

Retrieve the width and height (in pixels) of an image prior to displaying it. This method can fail if the image cannot be found, or fails to download.

In order to retrieve the image dimensions, the image may first need to be loaded or downloaded, after which it will be cached. This means that in principle you could use this method to preload images, however it is not optimized for that purpose, and may in future be implemented in a way that does not fully load/download the image data. A proper, supported way to preload images will be provided as a separate API.

**Parameters:**

| Name    | Type     | Required | Description                                                                                          |
| ------- | -------- | -------- | ---------------------------------------------------------------------------------------------------- |
| uri     | string   | Yes      | The location of the image.                                                                           |
| success | function | Yes      | The function that will be called if the image was successfully found and width and height retrieved. |
| failure | function | No       | The function that will be called if there was an error, such as failing to retrieve the image.       |

---

### `getSizeWithHeaders()`

```jsx
Image.getSizeWithHeaders(uri, headers, success, [failure]);
```

Retrieve the width and height (in pixels) of an image prior to displaying it with the ability to provide the headers for the request. This method can fail if the image cannot be found, or fails to download.

In order to retrieve the image dimensions, the image may first need to be loaded or downloaded, after which it will be cached. This means that in principle you could use this method to preload images, however it is not optimized for that purpose, and may in future be implemented in a way that does not fully load/download the image data. A proper, supported way to preload images will be provided as a separate API.

Does not work for static image resources.

**Parameters:**

| Name    | Type     | Required | Description                                                                                          |
| ------- | -------- | -------- | ---------------------------------------------------------------------------------------------------- |
| uri     | string   | Yes      | The location of the image.                                                                           |
| headers | object   | Yes      | The headers for the request.                                                                         |
| success | function | Yes      | The function that will be called if the image was successfully found and width and height retrieved. |
| failure | function | No       | The function that will be called if there was an error, such as failing toto retrieve the image.     |

---

### `prefetch()`

```jsx
Image.prefetch(url);
```

Prefetches a remote image for later use by downloading it to the disk cache

**Parameters:**

| Name | Type   | Required | Description                       |
| ---- | ------ | -------- | --------------------------------- |
| url  | string | Yes      | The remote location of the image. |

---

### `abortPrefetch()`

```jsx
Image.abortPrefetch(requestId);
```

Abort prefetch request. Android-only.

**Parameters:**

| Name      | Type   | Required | Description                  |
| --------- | ------ | -------- | ---------------------------- |
| requestId | number | Yes      | Id as returned by prefetch() |

---

### `queryCache()`

```jsx
Image.queryCache(urls);
```

Perform cache interrogation. Returns a mapping from URL to cache status, such as "disk" or "memory". If a requested URL is not in the mapping, it means it's not in the cache.

**Parameters:**

| Name | Type  | Required | Description                                |
| ---- | ----- | -------- | ------------------------------------------ |
| urls | array | Yes      | List of image URLs to check the cache for. |

---

### `resolveAssetSource()`

```jsx
Image.resolveAssetSource(source);
```

Resolves an asset reference into an object which has the properties `uri`, `width`, and `height`.

**Parameters:**

| Name   | Type           | Required | Description                                                                  |
| ------ | -------------- | -------- | ---------------------------------------------------------------------------- |
| source | number, object | Yes      | A number (opaque type returned by require('./foo.png')) or an `ImageSource`. |

> `ImageSource` is an object like `{ uri: '<http location || file path>' }`
