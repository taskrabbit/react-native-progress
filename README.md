# react-native-progress

Progress indicators and spinners for React Native using ReactART. 

![progress-demo](https://cloud.githubusercontent.com/assets/378279/11212043/64fb1420-8d01-11e5-9ec0-5e175a837c62.gif)

**Note: Full android support will come when ReactART is ported to android.**

## Installation

`$ npm install react-native-progress --save`

### ReactART based components

`$ npm install art --save`

To use the `Pie` or `Circle` components, you need to include the ART library in your project. To do this, simply add the `ART.xcodeproj` (found in `node_modules/react-native/Libraries/ART`) to the **Libraries** group and add `libART.a` to **Link Binary With Libraries** under **Build Phases**. [More info and screenshots about how to do this is available in the React Native documentation](http://facebook.github.io/react-native/docs/linking-libraries-ios.html#content).

Until [this pull request](https://github.com/facebook/react-native/pull/3308) to expose ReactART as a public API is merged, you will need to polyfill this because of packager limitations. Simply inject this code before requiring this module: 

```js
if(!React.ART) {
  React.ART = require('ReactNativeART');
}
```

## Usage

*Note: If you don't want the ReactART based components and it's dependencies, do a deep require instead: `var ProgressBar = require('react-native-progress/Bar');`.*

```js
var Progress = require('react-native-progress');

<Progress.Bar progress={0.3} width={200} />
<Progress.Pie progress={0.4} size={50} />
<Progress.Circle size={30} indeterminate={true} />
<Progress.CircleSnail colors={['red', 'green', 'blue']} />
```

### Properties for all progress components

| Prop | Description | Default |
|---|---|---|
|**`animated`**|Wether or not to animate changes to `progress`. |`true`|
|**`indeterminate`**|If set to true, the indicator will spin and `progress` prop will be ignored. |`false`|
|**`progress`**|Progress of whatever the indicator is indicating. A number between 0 and 1. |`0`|
|**`color`**|Fill color of the indicator. |`rgba(0, 122, 255, 1)`|
|**`unfilledColor`**|Color of the remaining progress. |*None*|
|**`borderWidth`**|Width of outer border, set to `0` to remove. |`1`|
|**`borderColor`**|Color of outer border. |`color`|

### `Progress.Bar`

All of the props under *Properties* in addition to the following:

| Prop | Description | Default |
|---|---|---|
|**`width`**|Full width of the progress bar. |`150`|
|**`height`**|Height of the progress bar. |`6`|
|**`borderRadius`**|Rounding of corners, set to `0` to disable. |`4`|

### `Progress.Circle`

All of the props under *Properties* in addition to the following:

| Prop | Description | Default |
|---|---|---|
|**`size`**|Diameter of the circle. |`40`|
|**`thickness`**|Thickness of the inner circle. |`3`|
|**`showsText`**|Wether or not to show a text representation of current progress. |`false`|
|**`formatText(progress)`**|A function returning a string to be displayed for the textual representation. |*See source*|
|**`textStyle`**|Styles for progress text, defaults to a same `color` as circle and `fontSize` proportional to `size` prop. |*None*|

### `Progress.Pie`

All of the props under *Properties* in addition to the following:

| Prop | Description | Default |
|---|---|---|
|**`size`**|Diameter of the pie. |`40`|

### `Progress.CircleSnail`

| Prop | Description | Default |
|---|---|---|
|**`animating`**|If the circle should animate. |`true`|
|**`hidesWhenStopped`**|If the circle should be removed when not animating. |`true`|
|**`size`**|Diameter of the circle. |`40`|
|**`color`**|Color of the circle, use an array of colors for rainbow effect. |`rgba(0, 122, 255, 1)`|
|**`thickness`**|Thickness of the circle. |`3`|

## Examples

* [`Example` project bundled with this module](https://github.com/oblador/react-native-progress/tree/master/Example) 
* [react-native-image-progress](https://github.com/oblador/react-native-image-progress)

## [Changelog](https://github.com/oblador/react-native-progress/releases)

## Todo
 - [x] Progress bar
 - [x] Circular progress indicator
 - [x] Pie progress indicator
 - [x] Animation
 - [x] Indeterminate state
 - [x] Progress percentage text
 - [ ] Optional color change on success/failure
 - [x] Snail/rainbow style spinners
 - [ ] Safari style navigation progress bar

## Thanks

To [Mandarin Drummond](https://github.com/MandarinConLaBarba) for giving me the NPM name. 

## License

[MIT License](http://opensource.org/licenses/mit-license.html). © Joel Arvidsson 2015
