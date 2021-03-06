# <img alt="React Native typography" src="images/logo.png" width="275"/>

Pixel–perfect, native–looking typographic styles for React Native.

[![npm version](https://img.shields.io/npm/v/react-native-typography.svg)](https://www.npmjs.com/package/react-native-typography)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![npm downloads](https://img.shields.io/npm/dm/react-native-typography.svg)](https://www.npmjs.com/package/react-native-typography)

<p align="center">
<img alt="React Native Typography Human Showcase" src="images/showcase-human-ios.png" width="49.7%"/>
<img alt="React Native Typography Material Showcase" src="images/showcase-material-android.png" width="49.7%"/>
</p>

## Why

Creating great Text Styles in React Native
[is not a simple task](https://medium.com/@martin_adamko/react-native-quirks-2fb1ae0bbf80),
it requires a lot of fiddling and handling edge cases.

This library provides a good set of defaults and helpers that cover the majority
of the cases you'll need, make your code much simpler and ✨*bonus*✨ render
great [on both platforms](#cross-platform) 😄

## Quick start

Add the dependency:

```sh
yarn add react-native-typography
```

Set a style in your component:

```JSX
import { material } from 'react-native-typography'

<Text style={material.display1}>Hello Typography!</Text>
```

And it will look like this:

<p align="center">
<img alt="Material Design Collection" src="images/hello-world.png" width="40%" height="40%"/>
</p>

### Example app

* You can run the example app
  [via Expo](https://expo.io/@hectahertz/react-native-typography-example) or
  [check the code](example/App.js), all of the screenshots are taken directly
  from there!

## Typography collections

We provide a series of predefined collections for you to start with that match
the native design systems for iOS and Android.

You can **use them directly** wherever you would supply a
[textStyle](https://facebook.github.io/react-native/docs/textstyleproptypes.html).

There's also the option of [extending them](#customization-helpers) to create
your own styles.

### Material Design

Includes all the styles defined in the
[Material Design Guidelines](https://material.io/guidelines/style/typography.html#typography-styles).
Defines size, weight and color.

```JSX
import { material } from 'react-native-typography'

<Text style={material.display4}>Hello Material!</Text>
```

<img alt="Material Design Collection" src="images/material-collection-android.png" width="80%" height="80%"/>

### Human Interface Guidelines

Defined in the
[Human Interface Guidelines](https://developer.apple.com/ios/human-interface-guidelines/visual-design/typography/).
Defines size, weight and color.

```JSX
import { human } from 'react-native-typography'

<Text style={human.largeTitle}>Hello Human!</Text>
```

<img alt="Human Interface Collection" src="images/human-collection-ios.png" width="80%" height="80%"/>

### iOSUIKit

Extracted from
[the official Apple sketch file](https://developer.apple.com/design/resources/)

These are the text styles that fall under the category of iOS UIKit, and are
used to build the UI components of iOS Apps.

They build on top of the Human Interface styles, customizing some properties
such as weight or letter spacing.

```JSX
import { iOSUIKit } from 'react-native-typography'

<Text style={iOSUIKit.largeTitleEmpasized}>Hello iOS UI Kit!</Text>
```

<img alt="iOSUIKit Collection" src="images/iosuikit-collection-ios.png" width="80%" height="80%"/>

## Customization & Helpers

The collections provide every style in 2 different ways:

* As a StyleSheet, e.g.: `material.title`
* As a plain object, e.g.: `material.titleObject`

The basic way to use them is to set the StyleSheet directly where you would
supply a
[textStyle](https://facebook.github.io/react-native/docs/textstyleproptypes.html):

```JSX
<Text style={material.title}>Title</Text>
```

To extend the styles, you can **spread the object** inside your own StyleSheet
and override some of its attributes:

```JSX
const styles = StyleSheet.create({
  yellowTitle: {
    ...material.titleObject,
    color: iOSColors.yellow,
  },
});

<Text style={styles.yellowTitle}>Title</Text>
```

Another option would be to **combine the provided StyleSheet** with your own
StyleSheet.

```JSX
const styles = StyleSheet.create({
  yellow: {
    color: iOSColors.yellow,
  },
});

<Text style={[material.title, styles.yellow]}>Title</Text>
```

### Weights

A font weight in React Native is sometimes formed by a pair of a fontFamily and
a fontWeight, but not always! It depends on the typeface, sometimes it's just
defined by the fontFamily.

With these helpers, you don't have to worry about those inconsistencies.

To combine them with a collection style (or your own styles) just spread them,
as they are plain objects.

```JSX
const styles = StyleSheet.create({
  lightTitle: {
    ...material.titleObject,
    ...systemWeights.light,
  },
});

<Text style={styles.lightTitle}>Title</Text>
```

#### System Weights

```JSX
import { systemWeights } from 'react-native-typography'
```

The System weights render visually similar weights of the **San Francisco/Roboto
typefaces** on each platform.
[Read more about cross-platform here.](#cross-platform)

This is the recommended way of customizing your weights unless you really need
different visual styles for each platform.

They follow the San Francisco naming convention, as it has more steps, which
makes it more future–proof.

<img alt="System Weights iOS" src="images/system-weights-ios.png" width="80%" height="80%"/>

<img alt="System Weights Android" src="images/system-weights-android.png" width="80%" height="80%"/>

#### San Francisco Weights

```JSX
import { sanFranciscoWeights } from 'react-native-typography'
```

These weights are **only functional on iOS**, as they directly reference the
native San Francisco typeface.

<img alt="San Francisco Weights" src="images/san-francisco-weights.png" width="80%" height="50%"/>

#### Roboto Weights

```JSX
import { robotoWeights } from 'react-native-typography'
```

These weights are **only functional on Android**, as they directly reference the
native Roboto typeface.

<img alt="Roboto Weights" src="images/roboto-weights.png" width="80%" height="80%"/>

### Colors

We also include the default text color hex values for each platform.

#### iOS

```JSX
import { iOSColors } from 'react-native-typography'
```

<img alt="Colors iOS" src="images/ios-colors.png" width="50%" height="50%"/>

```JSX
const styles = StyleSheet.create({
  yellowTitle: {
    ...human.title3Object,
    color: iOSColors.yellow,
  },
});

<Text style={styles.yellowTitle}>Title</Text>
```

#### Material

```JSX
import { materialColors } from 'react-native-typography'
```

<img alt="Colors Material" src="images/material-colors.png" width="50%" height="50%"/>

```JSX
const styles = StyleSheet.create({
  tertiaryTitle: {
    ...material.titleObject,
    color: materialColors.blackTertiary,
  },
});

<Text style={styles.tertiaryTitle}>Title</Text>
```

### Spacing/Kerning

#### San Francisco

The San Francisco typeface on iOS defines its letter spacing via Kerning. This
is not compatible with the React Native text style properties, as they take
letter-spacing instead.

To perform this conversion you can use the `sanFranciscoSpacing` function, which
receives the font size and returns the appropriate letter spacing.

```JSX
import { sanFranciscoSpacing } from 'react-native-typography'

const styles = StyleSheet.create({
  customSize: {
    ..., // some other props
    fontSize: 34,
    letterSpacing: sanFranciscoSpacing(34),
  },
});
```

This is already taken care of on the collections, but if you want to define your
own sizes you can adjust the spacing with this helper.

## Cross-platform

Quoting
[the Material Design Platform recommendations](https://material.io/guidelines/platforms/platform-adaptation.html#platform-adaptation-platform-recommendations)

> The default typeface on iOS is San Francisco. Using this typeface is the
> easiest way to implement accessibility features like Dynamic Type. Using other
> typefaces may require making adjustments to get the same accessibility
> features.

This is the approach that we like to follow, and all the collections exported
from this library render nicely on both platforms with their respective native
typefaces, for that we use the [System](#system) weight helper.

You can [check the code of the example app](example/App.js) where we included a
couple of screens that follow this philosophy, this is how they render on both
platforms:

<p align="center">
<img alt="React Native Typography Human Showcase on iOS" src="images/showcase-human-ios.png" width="49.7%"/>
<img alt="React Native Typography Human Showcase on Android" src="images/showcase-human-android.png" width="49.7%"/>
</p>

<p align="center">
<img alt="React Native Typography Human Showcase on iOS" src="images/showcase-material-ios.png" width="49.7%"/>
<img alt="React Native Typography Material Showcase on Android" src="images/showcase-material-android.png" width="49.7%"/>
</p>

## F.A.Q.

#### But I don't wanna use the Material Design or Human Interface Guidelines! Is there any reason why I should use this library?

Absolutely! The helpers are very convenient to build your own text styles as
they work around
[the quirks of working with text styles on React Native](https://medium.com/@martin_adamko/react-native-quirks-2fb1ae0bbf80),
even if you want to specify your own sizes and weights, check them out!

#### The Roboto typeface line heights are not 100% accurate to the Material Styles definition

This is a
[known React Native issue](https://github.com/facebook/react-native/issues/10712).

There's a [pull request](https://github.com/facebook/react-native/pull/16448)
ready that fixes this, this library will be updated to make the heights 100%
accurate once it gets released.

#### Kerning is not 100% accurate on the Display sizes for the Material styles on Android

There's no support for letter spacing on React Native Android yet ☹️

#### Where is Roboto Black?

It's not available by default on React Native yet 😐

#### I use styled-components/glamorous/etc. Can I use react-native-typography?

Of course! There are some examples in the provided app,
[check the code!](example/App.js)

#### Why is this library exporting StyleSheets and objects instead of components?

The idea behind it is that textStyles are the universally accepted way of
styling text and this makes integration
[with many libraries](https://reactnavigation.org/docs/navigators/stack#headerTitleStyle)
easier.

The StyleSheet/Object pattern is
[already being used](https://facebook.github.io/react-native/docs/stylesheet.html#absolutefill)
in the React Native codebase to provide an easy way to extend exported
StyleSheets.

If you enjoy using already styles components for your text, you can easily
define them and just supply the desired styles from the library! 🙂

## Roadmap

* Support for
  [dense and tall scripts](https://material.io/guidelines/style/typography.html#typography-line-height)
  on the Material collection.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available,
see the
[tags in this repository](https://github.com/hectahertz/react-native-typography/tags).

## Roadmap

* Type with [Flow](https://flow.org/)

## Authors

* **[Hector Garcia](https://github.com/hectahertz)** - _Initial work_
* **[Alina Cvetkova](https://github.com/hectahertz)** - _Design, UX and visual
  fine–tuning_

See also the list of
[contributors](https://github.com/hectahertz/react-native-typography/contributors)
who participated in this project.

## License

This project is licensed under the MIT License.

## Acknowledgments

* [Kyle Hickinson](https://github.com/kylehickinson) - thanks for
  [the work on the kerning values for San Francisco](https://github.com/kylehickinson/Sketch-SF-UI-Font-Fixer)
  and for being so nice!
* [Bartol Karuza](https://github.com/bartolkaruza) &
  [Chris Lewis](https://github.com/cdlewis) - thanks for the work on fixing the
  line heights inconsistencies in React Native.

* Pictures for the demo app by:

  <a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px;" href="https://unsplash.com/@sashafreemind?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from Sasha  Freemind"><span style="display:inline-block;padding:2px 3px;"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-1px;fill:white;" viewBox="0 0 32 32"><title></title><path d="M20.8 18.1c0 2.7-2.2 4.8-4.8 4.8s-4.8-2.1-4.8-4.8c0-2.7 2.2-4.8 4.8-4.8 2.7.1 4.8 2.2 4.8 4.8zm11.2-7.4v14.9c0 2.3-1.9 4.3-4.3 4.3h-23.4c-2.4 0-4.3-1.9-4.3-4.3v-15c0-2.3 1.9-4.3 4.3-4.3h3.7l.8-2.3c.4-1.1 1.7-2 2.9-2h8.6c1.2 0 2.5.9 2.9 2l.8 2.4h3.7c2.4 0 4.3 1.9 4.3 4.3zm-8.6 7.5c0-4.1-3.3-7.5-7.5-7.5-4.1 0-7.5 3.4-7.5 7.5s3.3 7.5 7.5 7.5c4.2-.1 7.5-3.4 7.5-7.5z"></path></svg></span><span style="display:inline-block;padding:2px 3px;">Sasha
  Freemind</span></a>
  <a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px;" href="https://unsplash.com/@sethdoylee?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from Seth Doyle"><span style="display:inline-block;padding:2px 3px;"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-1px;fill:white;" viewBox="0 0 32 32"><title></title><path d="M20.8 18.1c0 2.7-2.2 4.8-4.8 4.8s-4.8-2.1-4.8-4.8c0-2.7 2.2-4.8 4.8-4.8 2.7.1 4.8 2.2 4.8 4.8zm11.2-7.4v14.9c0 2.3-1.9 4.3-4.3 4.3h-23.4c-2.4 0-4.3-1.9-4.3-4.3v-15c0-2.3 1.9-4.3 4.3-4.3h3.7l.8-2.3c.4-1.1 1.7-2 2.9-2h8.6c1.2 0 2.5.9 2.9 2l.8 2.4h3.7c2.4 0 4.3 1.9 4.3 4.3zm-8.6 7.5c0-4.1-3.3-7.5-7.5-7.5-4.1 0-7.5 3.4-7.5 7.5s3.3 7.5 7.5 7.5c4.2-.1 7.5-3.4 7.5-7.5z"></path></svg></span><span style="display:inline-block;padding:2px 3px;">Seth
  Doyle</span></a>
  <a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px;" href="https://unsplash.com/@particularangelvision?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from Angel Jimenez"><span style="display:inline-block;padding:2px 3px;"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-1px;fill:white;" viewBox="0 0 32 32"><title></title><path d="M20.8 18.1c0 2.7-2.2 4.8-4.8 4.8s-4.8-2.1-4.8-4.8c0-2.7 2.2-4.8 4.8-4.8 2.7.1 4.8 2.2 4.8 4.8zm11.2-7.4v14.9c0 2.3-1.9 4.3-4.3 4.3h-23.4c-2.4 0-4.3-1.9-4.3-4.3v-15c0-2.3 1.9-4.3 4.3-4.3h3.7l.8-2.3c.4-1.1 1.7-2 2.9-2h8.6c1.2 0 2.5.9 2.9 2l.8 2.4h3.7c2.4 0 4.3 1.9 4.3 4.3zm-8.6 7.5c0-4.1-3.3-7.5-7.5-7.5-4.1 0-7.5 3.4-7.5 7.5s3.3 7.5 7.5 7.5c4.2-.1 7.5-3.4 7.5-7.5z"></path></svg></span><span style="display:inline-block;padding:2px 3px;">Angel
  Jimenez</span></a>
  <a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px;" href="https://unsplash.com/@efekurnaz?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from Efe Kurnaz"><span style="display:inline-block;padding:2px 3px;"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-1px;fill:white;" viewBox="0 0 32 32"><title></title><path d="M20.8 18.1c0 2.7-2.2 4.8-4.8 4.8s-4.8-2.1-4.8-4.8c0-2.7 2.2-4.8 4.8-4.8 2.7.1 4.8 2.2 4.8 4.8zm11.2-7.4v14.9c0 2.3-1.9 4.3-4.3 4.3h-23.4c-2.4 0-4.3-1.9-4.3-4.3v-15c0-2.3 1.9-4.3 4.3-4.3h3.7l.8-2.3c.4-1.1 1.7-2 2.9-2h8.6c1.2 0 2.5.9 2.9 2l.8 2.4h3.7c2.4 0 4.3 1.9 4.3 4.3zm-8.6 7.5c0-4.1-3.3-7.5-7.5-7.5-4.1 0-7.5 3.4-7.5 7.5s3.3 7.5 7.5 7.5c4.2-.1 7.5-3.4 7.5-7.5z"></path></svg></span><span style="display:inline-block;padding:2px 3px;">Efe
  Kurnaz</span></a>
  <a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px;" href="https://unsplash.com/@mariosilva?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from Mário Silva"><span style="display:inline-block;padding:2px 3px;"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-1px;fill:white;" viewBox="0 0 32 32"><title></title><path d="M20.8 18.1c0 2.7-2.2 4.8-4.8 4.8s-4.8-2.1-4.8-4.8c0-2.7 2.2-4.8 4.8-4.8 2.7.1 4.8 2.2 4.8 4.8zm11.2-7.4v14.9c0 2.3-1.9 4.3-4.3 4.3h-23.4c-2.4 0-4.3-1.9-4.3-4.3v-15c0-2.3 1.9-4.3 4.3-4.3h3.7l.8-2.3c.4-1.1 1.7-2 2.9-2h8.6c1.2 0 2.5.9 2.9 2l.8 2.4h3.7c2.4 0 4.3 1.9 4.3 4.3zm-8.6 7.5c0-4.1-3.3-7.5-7.5-7.5-4.1 0-7.5 3.4-7.5 7.5s3.3 7.5 7.5 7.5c4.2-.1 7.5-3.4 7.5-7.5z"></path></svg></span><span style="display:inline-block;padding:2px 3px;">Mário
  Silva</span></a>
  <a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px;" href="https://unsplash.com/@oldskool2016?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from paul morris"><span style="display:inline-block;padding:2px 3px;"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-1px;fill:white;" viewBox="0 0 32 32"><title></title><path d="M20.8 18.1c0 2.7-2.2 4.8-4.8 4.8s-4.8-2.1-4.8-4.8c0-2.7 2.2-4.8 4.8-4.8 2.7.1 4.8 2.2 4.8 4.8zm11.2-7.4v14.9c0 2.3-1.9 4.3-4.3 4.3h-23.4c-2.4 0-4.3-1.9-4.3-4.3v-15c0-2.3 1.9-4.3 4.3-4.3h3.7l.8-2.3c.4-1.1 1.7-2 2.9-2h8.6c1.2 0 2.5.9 2.9 2l.8 2.4h3.7c2.4 0 4.3 1.9 4.3 4.3zm-8.6 7.5c0-4.1-3.3-7.5-7.5-7.5-4.1 0-7.5 3.4-7.5 7.5s3.3 7.5 7.5 7.5c4.2-.1 7.5-3.4 7.5-7.5z"></path></svg></span><span style="display:inline-block;padding:2px 3px;">paul
  morris</span></a>
  <a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px;" href="https://unsplash.com/@joelfilip?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from Joel Filipe"><span style="display:inline-block;padding:2px 3px;"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-1px;fill:white;" viewBox="0 0 32 32"><title></title><path d="M20.8 18.1c0 2.7-2.2 4.8-4.8 4.8s-4.8-2.1-4.8-4.8c0-2.7 2.2-4.8 4.8-4.8 2.7.1 4.8 2.2 4.8 4.8zm11.2-7.4v14.9c0 2.3-1.9 4.3-4.3 4.3h-23.4c-2.4 0-4.3-1.9-4.3-4.3v-15c0-2.3 1.9-4.3 4.3-4.3h3.7l.8-2.3c.4-1.1 1.7-2 2.9-2h8.6c1.2 0 2.5.9 2.9 2l.8 2.4h3.7c2.4 0 4.3 1.9 4.3 4.3zm-8.6 7.5c0-4.1-3.3-7.5-7.5-7.5-4.1 0-7.5 3.4-7.5 7.5s3.3 7.5 7.5 7.5c4.2-.1 7.5-3.4 7.5-7.5z"></path></svg></span><span style="display:inline-block;padding:2px 3px;">Joel
  Filipe</span></a> <a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px;" href="https://unsplash.com/@wldvbz?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from wild vibez"><span style="display:inline-block;padding:2px 3px;"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-1px;fill:white;" viewBox="0 0 32 32"><title></title><path d="M20.8 18.1c0 2.7-2.2 4.8-4.8 4.8s-4.8-2.1-4.8-4.8c0-2.7 2.2-4.8 4.8-4.8 2.7.1 4.8 2.2 4.8 4.8zm11.2-7.4v14.9c0 2.3-1.9 4.3-4.3 4.3h-23.4c-2.4 0-4.3-1.9-4.3-4.3v-15c0-2.3 1.9-4.3 4.3-4.3h3.7l.8-2.3c.4-1.1 1.7-2 2.9-2h8.6c1.2 0 2.5.9 2.9 2l.8 2.4h3.7c2.4 0 4.3 1.9 4.3 4.3zm-8.6 7.5c0-4.1-3.3-7.5-7.5-7.5-4.1 0-7.5 3.4-7.5 7.5s3.3 7.5 7.5 7.5c4.2-.1 7.5-3.4 7.5-7.5z"></path></svg></span><span style="display:inline-block;padding:2px 3px;">wild vibez</span></a>

## References

* https://developer.apple.com/ios/human-interface-guidelines/visual-design/typography/
* https://material.io/guidelines/style/typography.html
* https://developer.apple.com/design/resources/
* https://facebook.github.io/react-native/docs/text.html#style
* https://medium.com/@knoland/typography-in-react-native-f09c43b5b435
* https://developer.apple.com/videos/play/wwdc2015/804/
* https://medium.com/react-native-training/list-of-available-react-native-fonts-ed78b48bd45e
* https://developer.apple.com/documentation/uikit/uifontdescriptor/font_weights
* https://v1.designcode.io/iosdesign-guidelines
* http://devsign.co/notes/tracking-and-character-spacing
* https://www.raizlabs.com/dev/2015/08/advanced-ios-typography/
* https://medium.com/@sauvik_dolui/handling-fonts-in-ios-development-a-simpler-way-32d360cdc1b6
* https://readymag.com/arzamas/132908/6/
