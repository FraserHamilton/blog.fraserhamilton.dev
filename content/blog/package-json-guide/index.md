---
title: A guide to package.json
date: '2020-06-30T11:16:00.000Z'
description: 'Getting to grips with the file at heart of many codebases in the JavaScript ecosystem'
---

If you're operating in the JavaScript ecosystem you're certain to come across the `package.json` file. It's primarily used to identify the project on `npm` and manage the projects dependencies. However due to it's placement at the heart of almost any JavaScript project it's also often used for the configuration of various modules and tools.

# Properties

## name

Sets the module name

```json
"name": "test-module"
```

</br>

There's some restrictions on this field, it must be less than 214 characters, no uppercase letters and no spaces. You can use hyphens and underscores though.

## version

Denotes current version of the module

```json
"version": "1.12.4"
```

## license

Indicates the license of the module

```json
"license": "MIT"
```

## description

Contains a brief description of the module

```json
"description": "Parse, validate, manipulate, and display dates"
```

## author

Lists the module authors name

```json
"author": {
    "name": "Fraser Hamilton",
    "email": "fraser@webuilddigital.com",
    "url": "https://fraserhamilton.dev"
}
```

## contributors

Lists people who have contributed

```json
 "contributors": [
    "Your Friend <friend@example.com> (http://friends-website.com)",
    "Other Friend <other@example.com> (http://other-website.com)"
  ]
```

## keywords

Contains a collection of keywords relating to the module

```json
"keywords": [
    "date",
    "time",
    "parse",
    "format",
    "validate",
]
```

## main

The entry point to the module

```json
"main": "index.js",
```

## repository

Defines where the source code lives

```json
"repository": {
    "type": "git",
    "url": "https://github.com/moment/moment.git"
}
```

## homepage

The URL to the landing page or documentation for your module

```json
"homepage": "https://momentjs.com"
```

## bugs

The URL to your project's issue tracker

```json
"bugs": "https://github.com/moment/moment/issues"
```

## scripts

Defines a set of scripts you can run

```json
"scripts": {
    "start": "nodemon ./index.js",
    "build": "rollup --config",
    "test": "jest",
},
```

## dependencies

Indicates your modules dependencies as well as their versions

```json
"dependencies": {
    "nodemon": "latest",
    "lodash": "^4.17.15",
    "split": "0.3.0",
  },
```

## devDependencies

Indicates your modules development dependencies as well as their versions

```json
"devDependencies": {
    "prettier": "latest",
    "jest": "26.1.0",
    "rollup": "^2.18.0",
  },
```

</br>
