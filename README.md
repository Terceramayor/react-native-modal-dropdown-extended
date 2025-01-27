[![npm version](https://badge.fury.io/js/react-native-modal-dropdown.svg)](https://badge.fury.io/js/react-native-modal-dropdown)

# react-native-modal-dropdown-extended

This is a simple fork of the library https://github.com/Kishanjvaghela/react-native-modal-dropdown (A react-native dropdown/picker/selector component for both Android & iOS.) that includes some extra props used to have more control over the rendering style of the drop down component

## Features

- Pure JS.
- Compatible with both iOS and Android.
- Auto position. (Won't be covered or clipped by the edge of screen.)
- Zero configuration. (Options are needed of course or a loading indicator will show.)
- Highly customizable.
- Controllable with API by code. (Show/Hide/Select)
- Change everything into a dropdown list trigger.

## Demo

<img src="https://github.com/sohobloo/react-native-modal-dropdown/blob/master/docs/demo_1.gif?raw=true" width = "160" height = "287.5" alt="Demo 1"/> <img src="https://github.com/sohobloo/react-native-modal-dropdown/blob/master/docs/demo_2.gif?raw=true" width = "160" height = "287.5" alt="Demo 2"/> <img src="https://github.com/sohobloo/react-native-modal-dropdown/blob/master/docs/demo_3.gif?raw=true" width = "160" height = "287.5" alt="Demo 3"/>

You can find them in the example.

## Installation

```sh
npm i https://github.com/Terceramayor/react-native-modal-dropdown-extended.git -save
```

or

```sh
yarn add https://github.com/Terceramayor/react-native-modal-dropdown-extended.git
```

## Usage

### Basic

Import this module:

```javascript
import ModalDropdown from "react-native-modal-dropdown";
```

Use as a component:

```javascript
<ModalDropdown options={["option 1", "option 2"]} />
```

Use as a wrapper / container:

```javascript
<ModalDropdown options={["option 1", "option 2"]}>...</ModalDropdown>
```

### Customization

Give the style props as your choice:

- `style`: Change the style of the button (basic mode) / container (wrapper mode).
- `textStyle`: Change the style of text of the button. _Invalid in wrapper mode._
- `dropdownStyle`: Change the style of dropdown container.

You can also render your option row and row separator by implement `renderRow` and `renderSeparator` function.

## API

### Props

| Prop                           | Type                               | Optional | Default                                                         | Description                                                                                                                                                                                                                                                                                                                                         |
| ------------------------------ | ---------------------------------- | -------- | --------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `disabled`                     | bool                               | Yes      | false                                                           | disable / enable the component.                                                                                                                                                                                                                                                                                                                     |
| `defaultIndex`                 | number                             | Yes      | -1                                                              | Init selected index. `-1`: None is selected. **This only change the highlight of the dropdown row, you have to give a `defaultValue` to change the init text.**                                                                                                                                                                                     |
| `defaultValue`                 | string                             | Yes      | Please select...                                                | Init text of the button. **Invalid in wrapper mode.**                                                                                                                                                                                                                                                                                               |
| `options`                      | array                              | Yes      |                                                                 | Options. **The dropdown will show a loading indicator if `options` is `null`/`undefined`.**                                                                                                                                                                                                                                                         |
| `animated`                     | bool                               | Yes      | true                                                            | Disable / enable fade animation.                                                                                                                                                                                                                                                                                                                    |
| `isFullWidth`                  | bool                               | Yes      | false                                                           | Disable / enable is dropdown render as full width.                                                                                                                                                                                                                                                                                                  |
| `showsVerticalScrollIndicator` | bool                               | Yes      | true                                                            | Show / hide vertical scroll indicator.                                                                                                                                                                                                                                                                                                              |
| `style`                        | object                             | Yes      |                                                                 | Style of the button.                                                                                                                                                                                                                                                                                                                                |
| `textStyle`                    | object                             | Yes      |                                                                 | Style of the button text. **Invalid in wrapper mode.**                                                                                                                                                                                                                                                                                              |
| `defaultTextStyle`             | object                             | Yes      |                                                                 | Overried Style of the button text for default value. **Invalid in wrapper mode.**                                                                                                                                                                                                                                                                   |
| `dropdownStyle`                | object                             | Yes      |                                                                 | Style of the dropdown list.                                                                                                                                                                                                                                                                                                                         |
| `dropdownTextStyle`            | object                             | Yes      |                                                                 | Style of the dropdown option text.                                                                                                                                                                                                                                                                                                                  |
| `dropdownTextHighlightStyle`   | object                             | Yes      |                                                                 | Style of the dropdown selected option text.                                                                                                                                                                                                                                                                                                         |
| `dropdownTextProps`            | object                             | Yes      |                                                                 | Add custom props to the dropdown option text                                                                                                                                                                                                                                                                                                        |
| `adjustFrame`                  | func                               | Yes      |                                                                 | This is a callback after the frame of the dropdown have been calculated and before showing. You will receive a style object as argument with some of the props like `width` `height` `top` `left` and `right`. Change them to appropriate values that accord with your requirement and **make the new style as the return value of this function**. |
| `renderRow`                    | func                               | Yes      |                                                                 | Customize render option rows: `function(option,index,isSelected)` **Will render a default row if `null`/`undefined`.**                                                                                                                                                                                                                              |
| `renderRowComponent`           | Component                          | Yes      | `TouchableOpacity` for iOS and `TouchableHighlight` for Android | Customize the touchable component of the rows                                                                                                                                                                                                                                                                                                       |
| `renderRowProps`               | object                             | Yes      |                                                                 | Add custom props to the touchable component of the rows                                                                                                                                                                                                                                                                                             |
| `renderSeparator`              | func                               | Yes      |                                                                 | Customize render dropdown list separators. **Will render a default thin gray line if `null`/`undefined`.**                                                                                                                                                                                                                                          |
| `renderButtonText`             | func                               | Yes      |                                                                 | Use this to extract and return text from option object. This text will show on button after option selected. **Invalid in wrapper mode.**                                                                                                                                                                                                           |
| `renderRowText`                | func                               | Yes      |                                                                 | Use this to extract and return text from option object. This text will show on row **Invalid in wrapper mode.**                                                                                                                                                                                                                                     |
| `renderButtonComponent`        | Component                          | Yes      | `TouchableOpacity`                                              | Customize the touchable component of the button                                                                                                                                                                                                                                                                                                     |
| `renderRightComponent`         | Component                          | Yes      | `View`                                                          | Custom component/Image to display on right side as dropdown icon                                                                                                                                                                                                                                                                                    |
| `renderButtonProps`            | object                             | Yes      |                                                                 | Add custom props to the touchable component of the button                                                                                                                                                                                                                                                                                           |
| `onDropdownWillShow`           | func                               | Yes      |                                                                 | Trigger when dropdown will show by touching the button. **Return `false` can cancel the event.**                                                                                                                                                                                                                                                    |
| `onDropdownWillHide`           | func                               | Yes      |                                                                 | Trigger when dropdown will hide by touching the button. **Return `false` can cancel the event.**                                                                                                                                                                                                                                                    |
| `onSelect`                     | func                               | Yes      |                                                                 | Trigger when option row touched with selected `index` and `value`. **Return `false` can cancel the event.**                                                                                                                                                                                                                                         |
| `accessible`                   | bool                               | Yes      | true                                                            | Set accessibility of dropdown modal and dropdown rows                                                                                                                                                                                                                                                                                               |
| `keyboardShouldPersistTaps`    | enum('always', 'never', 'handled') | Yes      | 'never'                                                         | See react-native `ScrollView` props                                                                                                                                                                                                                                                                                                                 |
| `multipleSelect`               | bool                               | Yes      | false                                                           | Remove event closing modal when calling onSelect.                                                                                                                                                                                                                                                                                                   |

### Methods

| Method        | Description                                                                                                                  |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `show()`      | Show the dropdown. **Won't trigger `onDropdownWillShow`.**                                                                   |
| `hide()`      | Hide the dropdown. **Won't trigger `onDropdownWillHide`.**                                                                   |
| `select(idx)` | Select the specified option of the `idx`. Select `-1` will reset it to display `defaultValue`. **Won't trigger `onSelect`.** |

## Next version

Any suggestion is welcome.
