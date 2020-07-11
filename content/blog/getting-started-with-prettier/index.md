---
title: Getting started with Prettier in VSCode
date: '2020-07-11T11:06:00.000Z'
description: 'Consistent, easy and automatic code formatting for you and your team'
---

Formatting your code is an issue as old as programming itself, but modern developer tooling has been making big strides toward addressing it.

[Prettier](https://prettier.io/) is an opinionated code formatter that supports many languages and integrates with most editors. It's really makes code editing a hell of a lot easier, so much so it's one of the first things I reach for when starting a new project.

In this tutorial I'm going to go over getting started with Prettier in VSCode so if you don't have VSCode already you'll need to install it first. You can download it [here](https://code.visualstudio.com/).

Next you'll need to install the Prettier extension. Search for `Prettier - Code Formatter` in the extension panel and hit `install`.

Here's a little bit of sample code that you can try to format using Prettier:

<!-- prettier-ignore-start -->

```javascript
const me = 'Fraser';

const foo = { bar:     name };

console.log(foo)

console.log("Hello World!");
```

<!-- prettier-ignore-end -->

<br/>

With the extension installed you can now format the document from the command palette, to pull it up hit `CTRL + SHIFT + P`. Search for format and select `Format Document`. You should notice a change in your code, it will now be formatted to have consistent spacing, line wrapping and quotes.

This is a big improvement but what if we want to be able to format our document automatically? Well we can modify our `settings.json` to make that happen. Open up the command palette again, search for settings and select `Preferences: Open Settings (JSON)`. Then add the following rule:

```json
{
  "editor.formatOnSave": true
}
```

<br/>

Now whenever we save a document it'll be formatted by Prettier. If you want to adjust the rules being used to format the document you can set a default in the editor itself or using a configuration file in the root of each project. I'd recommend the config file method as it ensures your team will all be using the same rules.

Create a new file in the same directory as the code sample and call it `.prettierrc`. Here's the configuration I've been using lately in my projects:

```json
{
  "endOfLine": "lf",
  "semi": false,
  "singleQuote": true,
  "tabWidth": 2,
  "useTabs": false,
  "trailingComma": "es5"
}
```

<br/>

You can just adjust this file to fit your needs or checkout the [Prettier Docs](https://prettier.io/docs/en/index.html) for more examples and config instructions.

If you're using Prettier in a team setting it's probably a good idea to have it in your dev dependencies. To add it via npm use `npm install --save-dev prettier` and via yarn use `yarn add --dev prettier`. It's also worth nothing that it is possible to run prettier as part of your CI/CD process to ensure consistent formatting across your whole code base.
