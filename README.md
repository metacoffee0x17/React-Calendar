<div align="center" style="margin-bottom: 30px;">
<img src="https://raw.githubusercontent.com/clauderic/react-infinite-calendar/master/.github/logo.png" width="250"/>
</div>

# React Infinite Calendar
[![npm version](https://img.shields.io/npm/v/react-infinite-calendar.svg)](https://www.npmjs.com/package/react-infinite-calendar)
![downloads](https://img.shields.io/npm/dm/react-infinite-calendar.svg)
[![build](https://travis-ci.org/clauderic/react-infinite-calendar.svg?branch=master)](https://travis-ci.org/clauderic/react-infinite-calendar)
[![coverage](https://img.shields.io/codecov/c/github/clauderic/react-infinite-calendar.svg)](https://codecov.io/gh/clauderic/react-infinite-calendar)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000)](https://github.com/clauderic/react-infinite-calendar/blob/master/LICENSE)
[![Gitter](https://badges.gitter.im/clauderic/react-infinite-calendar.svg)](https://gitter.im/clauderic/react-infinite-calendar)
### Examples available here: <a href="#">http://clauderic.github.io/react-infinite-calendar/</a>

Features
---------------

* **Infinite scroll** – Just keep scrollin', just keep scrollin'
* **Flexible** – Min/max date, disabled dates, disabled days, etc.
* **Localization and translation** – En français, s'il vous plaît!
* **Customizeable** – Customize and theme to your heart's content.
* **Year selection** – For rapidly jumping from year to year
* **Keyboard support** – ⬆️ ⬇️ ⬆️ ⬇️ ⬅️ ➡️ ⬅️ ➡️ ↩️
* **Events and callbacks** – beforeSelect, onSelect, onScroll, etc.
* **Mobile-friendly** – Silky smooth scrolling on mobile

<div style="padding:30px">
<img src="https://raw.githubusercontent.com/clauderic/react-infinite-calendar/master/.github/preview.gif" width="300" />
</div>

Installation
------------

Using [npm](https://www.npmjs.com/):

	$ npm install react-infinite-calendar --save


Then, using a module bundler that supports either CommonJS or ES2015 modules, such as [webpack](https://github.com/webpack/webpack):

```js
// Using an ES6 transpiler like Babel
import InfiniteCalendar from 'react-infinite-calendar';
import 'react-infinite-calendar/styles.css'; // Make sure to import the default stylesheet

// Not using an ES6 transpiler
var InfiniteCalendar = require('react-infinite-calendar');
require('react-infinite-calendar/styles.css');
```

Alternatively, an UMD build is also available.
```html
<link rel="stylesheet" href="react-infinite-calendar/styles.css">
<script src="react-infinite-calendar/dist/umd/react-infinite-calendar.js"></script>
<script>
var InfiniteCalendar = window.InfiniteCalendar.default;
...
</script>
```

Usage
------------
### Basic Example

```js
import React from 'react';
import { render } from 'react-dom';
import InfiniteCalendar from 'react-infinite-calendar';
import 'react-infinite-calendar/styles.css'; // only needs to be imported once

// Render the Calendar
var today = new Date();
var minDate = Number(new Date()) - (24*60*60*1000) * 7; // One week before today

render(
  <InfiniteCalendar
    width={400}
    height={600}
    selectedDate={today}
    disabledDays={[0,6]}
    minDate={minDate}
    keyboardSupport={true}
  />,
  document.getElementById('root')
);
```
For more usage examples, see [http://clauderic.github.io/react-infinite-calendar/](http://clauderic.github.io/react-infinite-calendar/)

### Prop Types
| Property             | Type             | Default                                                                                              | Description                                                                                                                                                                                                                              |
|:---------------------|:-----------------|:-----------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| selectedDate         | Date or Boolean  | new Date()                                                                                           | Value of the date that appears to be selected. Set to `false` if you don't wish to have a date initially selected.                                                                                                                       |
| min                  | Date             | new&nbsp;Date(1980,0,1)                                                                              | The minimum month that can be scrolled to.                                                                                                                                                                                               |
| max                  | Date             | new&nbsp;Date(2050,11,31)                                                                            | The maximum month that can be scrolled to.                                                                                                                                                                                               |
| minDate              | Date             | new&nbsp;Date(1980,0,1)                                                                              | The minimum date that is selectable.                                                                                                                                                                                                     |
| maxDate              | Date             | new&nbsp;Date(2050,11,31)                                                                            | The maximum date that is selectable.                                                                                                                                                                                                     |
| display              | String           | 'days'                                                                                               | Whether to display the `years` or `days` view.                                                                                                                                                                                           |
| locale               | Object           | See [default locale](https://github.com/clauderic/react-infinite-calendar/blob/master/src/locale.js) | By default, React Infinite Calendar comes with the `English` locale strings. You can use this to change the language, or change the first day of the week. See [date-fns documentation](https://date-fns.org/docs/I18n) for more details |
| theme                | Object           | See [default theme](https://github.com/clauderic/react-infinite-calendar/blob/master/src/theme.js)   | Basic customization of the colors                                                                                                                                                                                                        |
| width                | Number or String | 400                                                                                                  | Width of the calendar. Use number for pixel width, string for percentage, for example: `width={400}` or `width={'80%'}`                                                                                                                  |
| height               | Number           | 600                                                                                                  | Height of the calendar                                                                                                                                                                                                                   |
| rowHeight            | Number           | 56                                                                                                   | Height of each row in the calendar (each week is considered a `row`)                                                                                                                                                                     |
| className            | String           |                                                                                                      | Optional CSS class name to append to the root `InfiniteCalendar` element.                                                                                                                                                                |
| overscanMonthCount   | Number           | 4                                                                                                    | Number of months to render above/below the visible months. Tweaking this can help reduce flickering during scrolling on certain browers/devices.                                                                                         |
| todayHelperRowOffset | Number           | 4                                                                                                    | This controls the number of rows to scroll past before the *Today* helper appears                                                                                                                                                        |
| disabledDays         | Array<Number>    |                                                                                                      | Array of days of the week that should be disabled. For example, to disable Monday and Sunday: `[0, 6]`                                                                                                                                   |
| disabledDates        | Array<Date>      |                                                                                                      | Array of dates that should be disabled. For example: `[new Date(2017, 1, 8), new Date(), new Date(2017, 5, 17)]`                                                                                                                         |
| onSelect             | Function         |                                                                                                      | Callback invoked after beforeSelect() returns true, but before the state of the calendar updates                                                                                                                                         |
| shouldPreventSelect  | Function         |                                                                                                      | Callback invoked before the state is mutated. Can be used to prevent the state from being changed by returning true.`                                                                                                                    |
| onScroll             | Function         |                                                                                                      | Callback invoked when the scroll offset changes. `function (scrollTop: number) {}`                                                                                                                                                       |
| onScrollEnd          | Function         |                                                                                                      | Callback invoked `150ms` after the last onScroll event is triggered. `function (scrollTop: number) {}`                                                                                                                                   |
| keyboardSupport      | Boolean          | true                                                                                                 | Keyboard support (`left`, `right`, `up`, `down`, `enter`)                                                                                                                                                                                |
| autoFocus            | Boolean          | true                                                                                                 | Whether the Calendar root should be auto-focused when it mounts. This is useful when `keyboardSupport` is enabled (the calendar must be focused to listen for keyboard events)                                                           |
| tabIndex             | Number           | 1                                                                                                    | Tab-index of the calendar                                                                                                                                                                                                                |
| layout               | String           | 'portrait'                                                                                           | Layout of the calendar. Should be one of `'portrait'` or `'landscape'`                                                                                                                                                                   |
| showHeader           | Boolean          | true                                                                                                 | Show/hide the header                                                                                                                                                                                                                     |
| shouldHeaderAnimate  | Boolean          | true                                                                                                 | Enable/Disable the header animation                                                                                                                                                                                                      |
| showOverlay          | Boolean          | true                                                                                                 | Show/hide the month overlay when scrolling                                                                                                                                                                                               |
| showTodayHelper      | Boolean          | true                                                                                                 | Show/hide the floating back to `Today` helper                                                                                                                                                                                            |
| hideYearsOnSelect    | Boolean          | true                                                                                                 | Whether to automatically hide the `years` view on select.                                                                                                                                                                                |

Dependencies
------------
React Infinite Calendar has few dependencies. It relies on the great work done by [`react-virtualized/VirtualScroll`](https://github.com/bvaughn/react-virtualized) for handling virtual scrolling logic and [`date-fns`](https://github.com/date-fns/date-fns) for handling date manipulation. It also has the following peer dependencies: [`react`](https://www.npmjs.com/package/react), [`react-dom`](https://www.npmjs.com/package/react-dom), and [`react-addons-css-transition-group`](https://www.npmjs.com/package/react-addons-css-transition-group).

Reporting Issues
----------------
If you find an [issue](https://github.com/clauderic/react-infinite-calendar/issues), please report it along with any relevant details to reproduce it. The easiest way to do so is to fork this [jsfiddle](https://jsfiddle.net/clauderic/4rhn03do/).

Contributions
------------
Yes please! Feature requests / pull requests are welcome. Have a suggestion or just want to say hello? Come chat on [gitter](https://gitter.im/clauderic/react-infinite-calendar)!
