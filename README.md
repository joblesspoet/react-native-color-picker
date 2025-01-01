# react-native-color-picker

React Native implementation of a color picker for both Android and iOS, now updated for compatibility with the latest versions of React and React Native.

![android preview](doc/preview_android.png)
![iphone preview](doc/preview_iphone.png)

* [x] Works both in controlled and uncontrolled modes.
* [x] Displays old color for visual comparison.
* [x] Includes Holo and Triangle color pickers.

## What's New

- Updated for compatibility with the latest React and React Native versions.
- Fixed issues with legacy components.
- Improved performance and ensured smoother integration with modern applications.

## Getting Started

### Installation

Install the color picker package:

```bash
npm install react-native-color-picker --save
```

### Usage

Import and use the `ColorPicker` in your application:

```javascript
import { ColorPicker } from 'react-native-color-picker';

const Picker = () => (
  <ColorPicker
    onColorSelected={color => alert(`Color selected: ${color}`)}
    style={{ flex: 1 }}
  />
);
```

> **Note:** Color picker will use the space you provide. Therefore, it is necessary to provide styles that determine the picker's size.

For the Holo Picker (`ColorPicker`), you may need to install `@react-native-community/slider` and pass it (or any other compatible slider component) as the `sliderComponent` prop to replace the deprecated React Native `Slider`.

---

## API

### Picker Types

This package provides two types of color pickers: Holo (default) and Triangle. Both have the same API and are interchangeable. Use them as follows:

```javascript
import { ColorPicker, TriangleColorPicker } from 'react-native-color-picker';
```

| ColorPicker | TriangleColorPicker |
| ----------- | ------------------- |
| ![](doc/holo.png) | ![](doc/triangle.png) |

---

### Props

Both color pickers accept the properties listed below. Each property that defines a color is represented as a [color string](https://github.com/bgrins/TinyColor#accepted-string-input).

| Property             | Type            | Description                                                                 |
|----------------------|-----------------|-----------------------------------------------------------------------------|
| `color`             | `String\|HSV`  | Selected color in controlled mode (HEX or HSV).                            |
| `defaultColor`      | `String`       | Initial selected color in uncontrolled mode.                               |
| `oldColor`          | `String`       | Old color for visual comparison.                                           |
| `style`             | `Style`        | Styles for the color picker container.                                     |
| `onColorSelected`   | `Function`     | Callback triggered on color selection, receiving the selected color (HEX). |
| `onColorChange`     | `Function`     | Callback triggered on color change (receives HSV object).                  |
| `onOldColorSelected`| `Function`     | Callback triggered when the old color is selected.                         |
| `hideSliders`       | `Boolean`      | Option to hide bottom sliders (Holo Picker only).                          |
| `hideControls`      | `Boolean`      | Option to hide bottom buttons (Triangle Picker only).                      |

#### HSV Format

When using the color picker in controlled mode, it is recommended to use the HSV format to avoid unnecessary conversions between HEX and RGB.

Example HSV format:

```javascript
{
  h: number, // <0, 360>
  s: number, // <0, 1>
  v: number, // <0, 1>
}
```

---

### Helper Functions

To assist with HSV-to-HEX/RGB conversions, this package includes the following utility functions:

```javascript
import { toHsv, fromHsv } from 'react-native-color-picker';

toHsv('blue'); // { h: 240, s: 1, v: 1 }
fromHsv({ h: 200, s: 0.4, v: 0.4 }); // #3d5866
```

---

## Examples

Try the examples on [Expo](https://snack.expo.io/@sodik82/react-native-color-picker-example).

---

## Limitations

- **ScrollView Integration:** May not work well within `ScrollView` due to touch event interference.
- **Slider Component:** React Native's `Slider` component is deprecated. You must pass `@react-native-community/slider` or another compatible component as the `sliderComponent` prop to resolve this.  
  **Known Issue:** There is an issue with slider components in some environments. If you experience problems, please check your React Native version compatibility and consider alternate solutions.
- **Known Bugs:** A known [bug](https://github.com/instea/react-native-color-picker/issues/17) affects React Native 0.61. See the issue for more details.

---

## Thanks

This implementation was inspired by [Android Holo ColorPicker](https://github.com/LarsWerkman/HoloColorPicker).
