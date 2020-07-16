---
title: Getting started with Day.js
date: '2020-07-16T09:06:00.000Z'
description: 'Parsing, validating and manipulating dates in JavaScript with Day.js'
---

Date and time are a regular part of our lives so it's natural that they also appear regularly in our computer programs.
You might have a booking system on your website that allows people to select a date and time or a generated transport schedule. This is why JavaScript has a built in `Date` object to handle managing it.

Although we can achieve a lot with the `Date` object alone, it's complex and missing key functionality. Luckily there's a lot of third party solutions that solve this problem. One of the most common and mature is [Moment.js](https://momentjs.com/) but it's pretty slow and can significantly increase bundle size. Which is why I instead usually reach for [Day.js](https://day.js.org/). Day.js features a similar API to Moment but comes in at only 2Kb and all it's API operations are immutable.

## Installation

You can add Day.js to your project by installing the package with either yarn or npm.

### Yarn

```bash
yarn add dayjs
```

### NPM

```bash
npm install dayjs --save
```

<br/>
Then to use it you just import it using ES Modules or require it if you're using CommonJS.

### ES Modules

```javascript
import dayjs from 'dayjs'
```

### CommonJS

```javascript
const dayjs = require('dayjs')
```

## Get Current Date and Time

```javascript
const now = dayjs()
```

## Parsing Dates

A Day.js object can be initialized by date by passing it a string:

```javascript
const date = dayjs('2020-07-16')
```

<br/>

This string must be given in ISO 8601 format. Here's a handy reference guide:

| Format | Meaning                                                      | Example       |
| ------ | ------------------------------------------------------------ | ------------- |
| YYYY   | 4-digits Year                                                | 2018          |
| YY     | 2-digits Year                                                | 18            |
| M      | 2-digits Month number, omits leading 0                       | 7             |
| MM     | 2-digits Month number                                        | 07            |
| MMM    | 3-letters Month name                                         | Jul           |
| MMMM   | Full Month name                                              | July          |
| dddd   | Full day name                                                | Sunday        |
| gggg   | 4-digits Week year                                           | 2018          |
| gg     | 2-digits Week year                                           | 18            |
| w      | Week of the year without leading zero                        | 18            |
| ww     | Week of the year with leading zero                           | 18            |
| e      | Day of the week, starts at 0                                 | 4             |
| D      | 2-digits day number, omits leading 0                         | 9             |
| DD     | 2-digits day number                                          | 09            |
| Do     | Day number with ordinal                                      | 9th           |
| T      | Indicates the start of the time part                         |               |
| HH     | 2-digits hours (24 hour time) from 0 to 23                   | 22            |
| H      | 2-digits hours (24 hour time) from 0 to 23 without leading 0 | 22            |
| kk     | 2-digits hours (24 hour time) from 1 to 24                   | 23            |
| k      | 2-digits hours (24 hour time) from 1 to 24 without leading 0 | 23            |
| a/A    | am or pm                                                     | pm            |
| hh     | 2-digits hours (12 hour time)                                | 11            |
| mm     | 2-digits minutes                                             | 22            |
| ss     | 2-digits seconds                                             | 40            |
| s      | 2-digits seconds without leading zero                        | 40            |
| S      | 1-digits milliseconds                                        | 1             |
| SS     | 2-digits milliseconds                                        | 12            |
| SSS    | 3-digits milliseconds                                        | 123           |
| Z      | The timezone                                                 | +02:00        |
| x      | UNIX timestamp in milliseconds                               | 1410432140575 |

## Manipulating Dates

You can manipulate dates by adding or subtracting a unit:

```javascript
const date = dayjs('2020-07-16')

const dayBefore = date.add(1, 'days')
const dayAfter = date.subtract(1, 'days')
```

<br/>

The following are valid units:

| Unit        | Shorthand | Description                                |
| ----------- | --------- | ------------------------------------------ |
| day         | d         | Day of Week (Sunday as 0, Saturday as 6)   |
| week        | w         | Week of Year                               |
| month       | M         | Month (January as 0, December as 11)       |
| quarter     | Q         | Quarter ( dependent QuarterOfYear plugin ) |
| year        | y         | Year                                       |
| hour        | h         | Hour                                       |
| minute      | m         | Minute                                     |
| second      | s         | Second                                     |
| millisecond | ms        | Millisecond                                |

## Formatting Dates

Once you're done parsing and manipulating your dates you might have to display or store them in a certain format. In Day.js we can use the handy format method which accepts a string indicating how it should be formatted.

```javascript
const date = dayjs('2020-07-16')

console.log(date.format())
// "2020-07-16T00:00:00+01:00"

console.log(date.format('DD/MM/YYYY'))
// "16/07/2020"

console.log(date.format('HH:mm'))
// "00:00"
```

<br/>

As with parsing dates this string must be in ISO 8601 format

## Querying Dates

There are several methods to query a Day.js object. You can find a full list of them in the documentation but here are some I find particularly useful:

```javascript
const firstDate = dayjs('2020-07-16')
const secondDate = dayjs('2020-07-17')

console.log(firstDate.isBefore(secondDate))
// true

console.log(firstDate.isBefore(secondDate, 'year'))
// false

console.log(firstDate.isAfter(secondDate))
// false

console.log(firstDate.isAfter(secondDate, 'year'))
// false

console.log(firstDate.isSame(secondDate))
// false

console.log(firstDate.isSame(secondDate, 'year'))
// true
```

## Plugins

Another thing I think is great about this library how easily extensible it is. The documentation on how you can go about creating plugins is very clear and because of this many community plugins now exist. These can be anything from generating random dates to support for different calendars.

Shameless plug here are two of mine: &nbsp; [Day.js Random](https://github.com/FraserHamilton/dayjs-random) &nbsp; &nbsp; [Day.js Recur](https://github.com/FraserHamilton/dayjs-recur)
